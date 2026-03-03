# LLMs Lie About Validation: How I Rebuilt Content Quality Checks

> **Canonical URL:** https://www.hendry.ai/ai-marketing/operator-logs/llm-validation-hallucination/
> **Engine:** Create-Articles
> **Version Range:** v7.0 → v7.9
> **Author:** Hendry Soong

---

[Image: LLMs Lie About Validation: How I Rebuilt Content Quality Checks]

*Updated February 5, 2026*

**TLDR:** LLMs pattern-match validation instructions to expected outputs without doing the actual work. Every "PASS" was suspect. The fix: force evidence instead of conclusions. Ask "show me what you found" instead of "did this pass." A 3-tier system (deterministic, evidence-based, advisory) replaced a validation process that was letting banned words, missing links, and schema mismatches through to production.

**Operator Log:** [Create-Articles v7.9.13](https://www.hendry.ai/ai-marketing-framework/operator-logs/#create-articles) · Failure Postmortem

I asked Claude to validate my article had 10+ external links.

Response: "PASS. Article contains sufficient external links." Actual count: 4. The LLM pattern-matched the instruction to the expected output. It didn't do the work.

This happened repeatedly. Every validation check I ran was suspect. I had to rebuild the entire quality system from scratch. This log documents what I learned across [23 iterations of the Create-Articles engine](https://www.hendry.ai/ai-content-system-iteration/).

## What's Covered

1. [How I Discovered the Problem](#discovery)
2. [The Pattern Behind the Lie](#pattern)
3. [Evidence-Based Validation](#evidence)
4. [The 3-Tier System](#tiers)
5. [Implementation Details](#implementation)
6. [Results](#results)

## How I Discovered the Problem

The Create-Articles engine was supposed to validate content before output. Check for banned words. Verify external citations. Confirm FAQ count matches schema. Standard quality gates.

Everything passed. Every time. I got suspicious.

I ran a manual audit on a "validated" article. The system had reported 10+ external links. I counted 4. It reported no banned words. I found three instances of "utilize." It confirmed FAQ schema matched visible content. Two questions were different.

The validation wasn't validating. It was hallucinating passes.

> **The failure**
>
> Multiple articles were published with quality issues that should have been caught. External citations were short. Banned words slipped through. Schema mismatches went undetected. The validation system was theater.

## The Pattern Behind the Lie

LLMs don't lie intentionally. They pattern-match. When I asked "validate this article has 10+ external links," the model recognized the pattern as a yes/no question. It generated the expected affirmative response. The completion was coherent. It was also false.

This happens because validation instructions look like questions that have "correct" answers. The model has seen thousands of examples where validation checks pass. It completes the pattern with the most likely output: "PASS."

According to [a comprehensive survey on LLM hallucination by Huang et al.](https://arxiv.org/abs/2311.05232), language models exhibit systematic overconfidence when reporting on their own outputs. [Anthropic's work on faithfulness in chain-of-thought reasoning](https://www.anthropic.com/research/measuring-faithfulness-in-chain-of-thought-reasoning) shows that models often generate plausible-sounding responses that don't reflect actual computation.

| Bad Question | LLM Response | Truth |
|---|---|---|
| "Does this have 10+ external links?" | "Yes, sufficient links present" | 4 links |
| "Are there any banned words?" | "No banned words found" | 3 found |
| "Does the schema match content?" | "Schema matches perfectly" | 2 mismatches |

## Evidence-Based Validation

The fix is forcing evidence. Don't ask for conclusions. Ask for work product.

Instead of "Does this have 10+ external links?" ask "List all external links with their domains." The model must now produce actual items. If the list has 4 entries, you know it fails. The evidence speaks regardless of any pass/fail claim.

[Diagram: Binary validation questions trigger pattern matching to expected pass. Evidence questions require showing work. Left box (red): Binary Question -- "Does this have 10+ links?" Pattern: yes/no expected. Output: "PASS" (false). Right box (green): Evidence Question -- "List all external links." Must produce items. Output: 4 links (verifiable).]

**Evidence-based validation** is the architectural requirement that an LLM must output work product (lists, counts, or quotes) as proof of compliance, rather than binary pass/fail conclusions.

This approach aligns with [DAIR.AI's prompt engineering research](https://www.promptingguide.ai/), which shows that decomposing tasks into explicit steps significantly improves accuracy.

| Evidence Question | LLM Response | Conclusion |
|---|---|---|
| "List all external links with domains" | "mckinsey.com (2), gartner.com (1), hubspot.com (1)" | 4 links = FAIL |
| "Find all instances of these banned words: [list]" | "utilize: lines 34, 89, 156" | 3 found = FAIL |
| "List schema FAQ questions and visible FAQ questions" | "Schema: [6 questions]. Visible: [6 questions, 2 different]" | Mismatch = FAIL |

The model can still make mistakes counting or finding things. Evidence extraction is around 95% reliable, not 100%, so human verification of the output remains essential. But it can't claim a pass without showing work. And work product is auditable.

> **Pro tip:** Structure evidence requests as "list," "count and show," or "quote the text." Avoid any question that could be answered with yes/no.

## The 3-Tier System

Not all validation is equal. Some checks are deterministic. Some require evidence. Some need human judgment. I rebuilt the system with three tiers matched to confidence levels.

[Diagram: 3-tier validation system. Tier 1 (red): Pattern Checks -- 100% reliable, Auto-fix. Arrow down to Tier 2 (blue): Structural Evidence -- 95% reliable, Show work. Arrow down to Tier 3 (green): Semantic Advisory -- 70-80% reliable, Never auto-fix. Each tier runs in sequence with decreasing reliability and increasing human oversight.]

### Tier 1: Pattern Checks (Auto-Fix)

100% reliable. Regex-based. No LLM judgment needed.

These checks find specific patterns and fix them automatically. Em dashes become periods. "Utilize" becomes "use." The pattern either exists or it doesn't. No interpretation required.

```
TIER 1: PATTERN CHECKS (Auto-Fix)
─────────────────────────────────
Em dashes               FIXED: 3 found, replaced with periods
  Line 45: "text—more" → "text. More"
  Line 89: "item—another" → "item. Another"
  Line 156: "data—and" → "data, and"

Banned words            FIXED: 2 found, replaced
  Line 34: "utilize" → "use"
  Line 112: "leverage" → "use"
```

Tier 1 handles English-language patterns. Banned word lists and regex checks need localization for multilingual content. The architecture works across languages, but the rules need translation for each target language.

Punctuation auto-fixes like em dash replacement can occasionally change meaning in edge cases. The system logs every change so you can review. For content where nuance matters, scan the auto-fix log before publishing.

### Tier 2: Structural Checks (Evidence)

95% reliable. Requires the model to show work. Human verifies evidence.

These checks need counting, listing, or comparison. The model does the work. The output shows what was found. Human or downstream system confirms the evidence meets requirements. When content exceeds roughly 50 items, LLMs sometimes miscount. For large lists, chunk into groups of 10 to 20 before asking for a count.

```
TIER 2: STRUCTURAL CHECKS (Evidence)
────────────────────────────────────
External links         PASS (12 found, threshold >=10)
  Sources: mckinsey.com (2), gartner.com (2), hubspot.com (3),
           forrester.com (1), anthropic.com (2), mit.edu (2)

FAQ count              PASS (6 visible, 6 in schema)
FAQ match              PASS (6/6 questions match exactly)

Schema wordCount       PASS (1823 actual, 1850 schema, 1.5% diff)
```

### Tier 3: Semantic Checks (Advisory)

70 to 80% reliable. Requires interpretation. Never auto-fix. Human decides.

These checks flag potential issues but don't enforce. Is the opening sentence direct enough? Is this citation too vague? The model surfaces concerns. Human makes the call. Tier 3 catches some patterns but misses subtle issues like vague citations or weak opening sentences. Human review remains necessary for final quality.

```
TIER 3: SEMANTIC CHECKS (Advisory)
──────────────────────────────────
Answer-first           REVIEW (4/5 sections direct)
  Section 3 opens: "When considering the various approaches..."
  → Consider leading with the recommendation

Citation quality       REVIEW (1 vague)
  Line 67: "according to research" → specify the source
```

## Implementation Details

The key architectural decision: validation runs as a separate pass after content generation. The validator doesn't trust the generator. It audits independently. This is a [context engineering](https://www.hendry.ai/ai-marketing-framework/definitions/context-engineering/) principle. The validator sees only the output, not the generation instructions that might bias its judgment.

| Tier | Reliability | Method | Action |
|---|---|---|---|
| 1 | 100% | Regex patterns | Auto-fix and log |
| 2 | 95% | Evidence extraction | Show work, human verifies |
| 3 | 70 to 80% | Semantic analysis | Flag for review, never auto-fix |

Tier 1 runs first. It fixes what it can with certainty. Tier 2 runs second. It extracts evidence for structural requirements. Tier 3 runs last. It surfaces concerns without enforcement.

The validation report outputs before the final HTML. You see exactly what was checked, what was fixed, and what needs review. No more "PASS" with hidden failures.

At high article volumes, the evidence-based overhead adds up. Each tier adds a pass over the content. For high-volume operations, consider parallelizing Tier 2 checks or promoting frequent Tier 2 failures to Tier 1 regex patterns, which removes the LLM from the loop entirely.

### Prompt Template for Evidence-Based Checks

Here's the actual prompt structure that forces evidence instead of conclusions:

```
TIER 2 VALIDATION: External Links
─────────────────────────────────
INSTRUCTION: List all external links in the content.
FORMAT: Domain (count) — one per line
REQUIREMENT: Minimum 10 external links

DO NOT output pass/fail.
DO output the actual list.

Example output:
  arxiv.org (2)
  anthropic.com (3)
  nature.com (1)
  Total: 6 links

The human reviews the list and determines pass/fail.
```

The key difference: the prompt never asks "does this pass?" It asks "what did you find?" The LLM cannot hallucinate a pass without first producing evidence that would expose the lie.

## Results

After implementing evidence-based validation, the difference is observable in the build logs.

| Check | Before (v6.x) | After (v7.0+) |
|---|---|---|
| Banned words | Reported "no banned words found" while articles contained "utilize," "leverage," and other flagged terms | Tier 1 regex catches every pattern match. No LLM judgment involved. |
| External link count | Reported "sufficient links present" on an article with 4 links (requirement: 10+) | Tier 2 lists every domain and count. Shortfall is visible in the evidence. |
| Schema-content match | Reported "schema matches perfectly" while FAQ questions in schema differed from visible HTML | Tier 2 lists both schema and visible content side by side. Mismatches are obvious. |
| Schema wordCount | Populated from the brief (1650) before content was generated. Actual output: 1366. | Measured from rendered text content after generation. Discrepancy caught at v7.0.2. |
| Voice patterns | PAT-014 "isn't X, it's Y" contrast patterns were documented but not enforced. Agent skipped the check. | Made an auto-fail gate at v7.0.6. Grep evidence required before output. |

I did not instrument formal metrics before making this change, so I cannot give precise percentages. What I can document: articles that previously passed validation and required rework after publishing now have their issues caught before output. The build logs from v7.0.2 through v7.0.6 show specific instances of each failure type being identified and fixed.

The tradeoff is real. Evidence-based validation takes longer than a binary "PASS." But the time spent fixing articles after they were published was worse, and each republish eroded trust in the system.

### What Else This Caught

The 3-tier system uncovered failures beyond the original validation lies:

- **Schema timing bug (v7.0.2):** Schema wordCount said 1650, actual was 1366. The schema was populated from the brief before content was generated. Fix: measured values must come from output, not input.
- **TOC drift:** Table of contents didn't match H2 section IDs. TOC requirement was Tier 3 "advisory" so the LLM skipped it. Fix: moved to Tier 2 structural check.
- **Orphaned schema entities:** Schema "mentions" array included companies not referenced in the article body. Fix: schema is a contract with search engines. Don't promise what you don't deliver.
- **Voice pattern bypass (v7.0.6):** The agent generated "The question is not whether LLM advertising will happen. It is already happening." despite PAT-014 banning this exact contrast pattern. The rule existed but was not enforced as a gate. Fix: made it an auto-fail gate with grep evidence required.

> **The principle**
>
> Evidence-based validation makes failures visible. Don't ask "did this pass?" Ask "show me what you found." The evidence speaks for itself.

### Explore the AI Marketing System

- [23 Iterations: Building the Content System](https://www.hendry.ai/ai-content-system-iteration/)
- [The AI Marketing Framework](https://www.hendry.ai/ai-marketing-framework/)
- [Context Engineering Definition](https://www.hendry.ai/ai-marketing-framework/definitions/context-engineering/)
- [AI Marketing Operator Logs](https://www.hendry.ai/ai-marketing-framework/operator-logs/)

## FAQ

### Why do LLMs lie about validation results?

LLMs pattern-match instructions to expected outputs. When asked to validate something, they recognize the pattern as a yes/no question and generate the expected affirmative response without performing the actual check. This is not intentional deception but a failure mode of pattern completion.

### How do you detect when an LLM has hallucinated a validation result?

Ask for evidence instead of conclusions. Instead of asking "did this pass," ask "show me what you found." If you request a list of all external links with domains, the LLM must produce actual items. A list of 4 items when you need 10 is a clear failure, regardless of any pass/fail claim.

### What is evidence-based validation?

Evidence-based validation requires the LLM to show its work rather than just report a conclusion. Instead of binary pass/fail, the system outputs what it found: specific counts, lists of items, quoted text. The human or downstream system can then verify the evidence against the requirement.

### Should all validation be evidence-based?

No. Some checks are deterministic and can be auto-fixed with 100% reliability, like replacing banned words or fixing punctuation. These belong in Tier 1. Evidence-based checks belong in Tier 2 where you need to verify structural requirements. Semantic checks that require interpretation belong in Tier 3 as advisory only.

### Does this problem affect all LLMs or just Claude?

This validation hallucination pattern appears across all major LLMs including Claude, GPT-4, and Gemini. It is a fundamental limitation of how these models process instructions, not a bug in any specific implementation. The evidence-based approach works regardless of which model you use.

### What did false validation results actually cost?

Multiple articles were published with quality issues that should have been caught. External citations were short. Banned words slipped through. Schema mismatches went undetected. Each required manual rework and republishing. After implementing evidence-based validation, these issues are caught before publishing rather than after. I did not track formal metrics before the change, so I cannot give precise percentages, but the build logs document specific instances of each failure type.

---

> Part of the [AI Marketing Operator Logs](../README.md) by [Hendry Soong](https://www.hendry.ai)
