# The Engine Split: Context Window Survival at 84K Tokens

> **Canonical URL:** https://www.hendry.ai/ai-marketing/operator-logs/engine-split-context-window-tokens/
> **Engine:** Create-Articles, Create-Images
> **Version Range:** v6.5 → v7.0
> **Author:** Hendry Soong

---

[Diagram: Engine split diagram showing monolithic 84K token system splitting into three modular engines with integration contracts]

## The Engine Split: Context Window Survival at 84K Tokens

Last updated March 3, 2026

**TLDR:** My AI content engine hit 84,312 tokens and Claude's context compaction triggered mid-generation. The fix: split one monolithic engine into three (Create-Articles at 69K, Create-Images at 42K, Create-Compiler at 10K), connected by 6 integration contracts and a closed-loop feedback system. This is the build log of that split, with version numbers, failure evidence, and the principles I extracted.

On February 1, 2026, my content engine broke. Create-Articles v7.9.1 loaded voice rules, 14 SVG templates, AI-SEO schema definitions, validation checks, context files, and format templates into a single context window. The total: 84,312 tokens.

Claude's context compaction kicked in before article generation completed. The output was truncated mid-section. The system that had shipped 40+ stable versions could no longer finish a single article.

This is the operator log of what happened next: how I split one engine into three, built integration contracts between them, and closed a feedback loop that catches defects at the source. Every claim in this article is verifiable against the [GitHub repository](https://github.com/nickhendry/hendry-ai-marketing-system-v1), where 80+ versions are documented in changelogs.

## What's Covered

1. [The Breaking Point: 84K Tokens and Counting](#breaking-point)
2. [What I Moved and Why](#what-i-moved)
3. [Three Engines, One Pipeline](#three-engines)
4. [Integration Contracts: How Engines Talk](#integration-contracts)
5. [The Feedback Loop: Catching Defects at the Source](#feedback-loop)
6. [What I Learned: Five Principles from the Split](#what-i-learned)

## The Breaking Point: 84K Tokens and Counting

Create-Articles v7.9.1 was the culmination of [32 days of iteration](https://www.hendry.ai/ai-marketing/operator-logs/build-production-ai-content-system/). The engine contained everything needed to produce a publication-ready article: voice rules, 14 SVG templates with exact geometry, AI-SEO schema definitions, three tiers of validation checks, five context files (ICP, company, messaging, offerings, brand voice), three format templates, three golden reference HTML files, and a 7-phase workflow. It was comprehensive. It was also too large.

Every component worked. Forty-plus stable versions proved that. But language models have finite attention. [Anthropic's context engineering guide](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) describes this directly: every token attends to every other token, so as the total grows, pairwise relationships get stretched thin. The guide calls this **context rot**, the phenomenon where accuracy and recall degrade as token count increases.

Research from Stanford and Meta confirmed the same finding from a different angle. Their ["Lost in the Middle" paper](https://arxiv.org/abs/2307.03172) (published in TACL 2023) demonstrated that model performance degrades significantly when relevant information sits in the middle of long contexts. Performance follows a U-shaped curve: highest at the beginning and end, lowest in the middle. Dumping 84K tokens of system files into one window meant critical rules were getting lost.

The breaking point was measurable. v7.9.1 at 84,312 tokens triggered compaction. The visual rhythm system alone (SVG templates, category rotation rules, density formulas) consumed 11,595 tokens. Those templates defined exact viewBox dimensions, coordinate geometry, and font calculations that Create-Articles never modified during article generation. They were reference material for a downstream process, sitting in the middle of the context window, degrading everything around them.

[Diagram: Stat card showing 84,312 total tokens in Create-Articles v7.9.1 before the engine split]

## What I Moved and Why

The split extracted 15,318 tokens of content that Create-Articles loaded but never modified during generation. SVG templates (14 templates, 11,595 tokens), SVG validation rules (PAT-010, PAT-015, PAT-016), and image generation routing logic all moved to a new engine: Create-Images v2.0.0. The remaining handoff contract (753 tokens) replaced the full image specification.

The decision was guided by a question: what does Create-Articles need in context to generate an article? Voice rules, component definitions, schema requirements. SVG coordinate geometry, template viewBox dimensions, and Gemini prompt patterns belong to the image engine. They were consuming [context window](https://www.hendry.ai/ai-marketing/definitions/context-engineering/) budget without contributing to article generation.

Anthropic's context engineering guide describes the principle as finding the smallest possible set of high-signal tokens that maximize the likelihood of the desired outcome. Their recommended pattern is just-in-time context loading: maintain lightweight identifiers (file paths, stored queries) and dynamically load data at runtime rather than pre-loading everything.

That is exactly what the split achieved. Create-Articles retained a slim handoff file that described the VIP block format (what images are needed and where). Create-Images loaded the full template library and validation rules only when processing those VIP blocks. Neither engine carried the other's weight.

| Component | Before (v7.9.1) | After (v7.9.2) | Moved To |
|---|---|---|---|
| SVG templates (A through N) | 11,595 tokens | 0 tokens | Create-Images v2.0.0 |
| SVG validation (PAT-010/015/016) | ~1,800 tokens | 0 tokens | Create-Images v2.0.0 |
| Image routing logic | ~1,900 tokens | 0 tokens | Create-Images v2.0.0 |
| Image handoff contract | 0 tokens | 753 tokens | New (replaced image-spec.md) |
| **Net change** | **84,312 tokens** | **68,994 tokens** | **18% reduction** |

## Three Engines, One Pipeline

The split created a linear pipeline where each engine has a scoped responsibility, its own context budget, and its own version history. Create-Articles (69K tokens) generates HTML with VIP placeholder blocks. Create-Images (42K tokens) processes those VIP blocks into SVG diagrams. Create-Compiler (10K tokens) merges the two outputs, validates cross-boundary integrity, and routes defects back to the source.

Each engine evolved independently after the split. Create-Articles went from v7.9.2 to v7.9.35, adding content profiles, an absorption gate, messaging framework integration, and source registry memory. Create-Images went from v2.0.0 to v2.0.25, adding visual perception rules, font scaling, text centering formulas, and an 8-check exit gate. Create-Compiler went from v1.0.0 to v1.3.4, adding a 14-check compile validator, a 7-question review agent, a 4-tier issue router, and reverse manifest feedback.

The version numbers tell the real story. Before the split, every improvement to image handling required loading all 84K tokens of article generation rules too. After the split, image template changes (v2.0.3 through v2.0.16 refined arrow spacing, font scaling, and source attribution placement across 14 iterations) happened without touching article generation context. Seven versions of image refinement that would have pushed the monolith well past its breaking point.

[Diagram: Three-engine pipeline showing Create-Articles producing HTML, Create-Images producing SVGs, and Create-Compiler merging with quality validation]

## Integration Contracts: How Engines Talk

Splitting a monolith creates a coordination problem. Three separate engines need to agree on data formats, validation boundaries, and handoff protocols. This is the [integration tax](https://www.hendry.ai/ai-marketing/definitions/integration-tax/): the cost of making independent systems work together. I solved it with 6 documented integration contracts, each stored as a markdown file in a shared directory that all engines can read.

The contracts define three things: what crosses the boundary, in what format, and who validates what. The articles-to-images contract specifies that Create-Articles outputs VIP blocks with `data-vip-id` attributes, prompt text, and template hints. Create-Images matches those VIP IDs and outputs `<figure>` elements with the same IDs. The compiler matches VIP blocks to figures by ID during assembly.

The verification manifest contract (inspired by Stripe's incremental verification pattern) lets each engine embed a machine-readable record of checks performed into its output. Downstream engines trust upstream manifests rather than re-running checks. Create-Articles reports which validation rules passed. Create-Images reports which exit gate checks passed. The Compiler reads both manifests and only runs cross-boundary checks that neither upstream engine could perform alone.

| Contract | From | To | What It Defines |
|---|---|---|---|
| articles-to-images | Create-Articles | Create-Images | VIP block format, prompt structure, template hints |
| articles-to-compiler | Articles + Images | Create-Compiler | Input files, expected structure, merge rules |
| verification-manifest | All engines | Downstream engines | Machine-readable check results for incremental trust |
| reverse-manifest | Create-Compiler | Articles + Images | Structured feedback for defect routing |
| compiler-to-articles | Create-Compiler | Create-Articles | Tier 2 scoped re-generation requests |
| compiler-to-images | Create-Compiler | Create-Images | Tier 0 rule addition requests |

[Diagram: Layer grid showing 6 integration contracts connecting Create-Articles, Create-Images, and Create-Compiler with forward and feedback flows]

## The Feedback Loop: Catching Defects at the Source

The Compiler started as a simple merge tool (v1.0.0, February 5, 2026). It matched VIP blocks to figures and concatenated HTML. Then I discovered that assembly creates new failure modes that neither upstream engine can catch: schema word counts change after merge, TOC anchors break when sections move, FAQ schema drifts from visible content, and CSS class references span both article and image output.

v1.1.0 added a quality gate: 9 deterministic Compile Validator checks and 7 LLM-based Review Agent questions. The Compile Validator runs cross-boundary checks that require the final assembled HTML. The Review Agent reads only the compiled output (no generation history) to catch issues that familiarity blindness would miss.

The real breakthrough came with v1.2.0. The first full-pipeline production run revealed three issues: SVG images left-aligned because centering was applied to hero images only, the footer credited only Create-Articles (missing the other two engines), and a source removal required a manual fix that created drift between source and compiled output. Research into CI/CD patterns, build systems, and quality engineering confirmed that [**shift-left testing**](https://www.sei.cmu.edu/blog/four-types-of-shift-left-testing/) (beginning testing as early as practical in the lifecycle) is the production-grade pattern.

v1.2.0 introduced the Issue Router, a 4-tier classification system that routes every discovered defect back to the source engine:

> **Issue Router: 4-Tier Classification**
>
> **Tier 0 (Preventable):** Fix the issue and add a rule to the upstream engine so it never recurs. Example: SVG centering rule added to Create-Images validation.
>
> **Tier 1 (Auto-Patch):** Deterministic fix applied to both source and compiled output. Example: missing `target="_blank"` on external links.
>
> **Tier 2 (Scoped Re-Gen):** Fix request routed to Create-Articles for a single section regeneration. Maximum 2 retries.
>
> **Tier 3 (Structural):** Escalate to the operator. Recommend full pipeline re-run.

v1.3.0 closed the loop with reverse manifests. The Compiler generates a structured manifest that routes Tier 0 and Tier 2 entries back to upstream engines. Create-Articles receives them through Phase 5 and can regenerate a single H2 section (Section-Patch Mode) without re-running the full pipeline. Create-Images receives Tier 0 entries through its Feedback Receiving Protocol and adds or strengthens validation rules.

The system now has guards against infinite loops: an idempotency rule prevents duplicate entries, and an overflow guard stops processing if more than 3 Tier 2 entries target the same article (recommending a full re-run instead). Fix-forward-only, where you fix the compiled output without updating the source, was formally banned as an anti-pattern. It creates the content equivalent of "works on my machine."

[Diagram: Cycle diagram showing the closed-loop feedback system from compiler validation through issue routing to source engine fixes]

## What I Learned: Five Principles from the Split

The engine split produced five principles that apply to any system where AI agents process structured content through multi-step pipelines. Each principle was extracted from a specific failure, tested across multiple production runs, and documented in the changelogs.

### 1. Context windows are finite resources. Separate what from how.

This is Principle P11, extracted directly from v7.9.2. Create-Articles needed to know what images to place: VIP blocks with prompt descriptions. SVG coordinate geometry, viewBox calculations, and font scaling formulas belong to a different engine. Loading both into the same window meant procedural drawing instructions competed with article content for attention. The split separated declarative intent from procedural execution.

### 2. Advisory rules get skipped. Make requirements structural.

Principle P04, learned across dozens of versions. The most reliable improvements came from [making violations structurally impossible](https://www.hendry.ai/ai-marketing/operator-logs/llms-lie-about-validation/) rather than advising against them. When I added STR-022 (SVG Boundary Check) as a BLOCKING gate, articles immediately stopped containing inline SVGs. The advisory note in the workflow that said "prefer VIP blocks" had been ignored for 7 consecutive builds. The structural check that fails on `grep -c "<svg" $FILE` returning anything above zero has never been bypassed.

### 3. One example beats 89 lines of instructions.

Principle P03, from the v3.8 disaster. I added an 89-line validation checklist and output quality dropped. Claude got confused by the volume of rules. v5.0 fixed it by showing one completed HTML example (the golden reference). Claude followed the workflow correctly again. The engine split preserved this lesson: each engine has its own golden references and worked examples rather than exhaustive rule lists.

### 4. System files are training data. They must follow the same rules they enforce.

Principle P13, from v7.9.22. The em dash generation-time rule existed in voice.md, but voice.md itself contained em dashes in its prose. The LLM learned the pattern from the system file it was supposed to use for enforcement. The fix: purge em dashes from all system file prose. Every rule file was audited for self-contradiction. This principle now applies to every system file change: if you ban a pattern, your system files cannot use it.

### 5. Fix-forward creates drift. Fix at the source.

Principle from v1.2.0. When the Compiler found an issue in the compiled output, the temptation was to fix it in place and move on. But the next compilation would overwrite that fix because the source article still had the original defect. The reverse manifest system (v1.3.0) formalized the alternative: every fix flows back to the source engine. The Compiler generates the fix request, the source engine applies it, and the next compilation produces a clean output without manual intervention.

### Explore the AI Marketing System

- [LLMs Lie About Validation: How I Rebuilt Content Quality Checks](https://www.hendry.ai/ai-marketing/operator-logs/llms-lie-about-validation/)
- [23 Iterations in 32 Days: Building a Production AI Content System](https://www.hendry.ai/ai-marketing/operator-logs/build-production-ai-content-system/)
- [All Operator Logs](https://www.hendry.ai/ai-marketing/operator-logs/)
- [The AI Marketing Framework](https://www.hendry.ai/ai-marketing/framework/)

## Frequently Asked Questions

### What caused the engine split at 84K tokens?

Create-Articles v7.9.1 loaded voice rules, AI-SEO rules, 14 SVG templates, validation checks, context files, and format templates into a single context window. At 84,312 tokens, Claude's context compaction triggered before article generation completed. The output was truncated mid-section.

### How much did the split reduce token usage?

Create-Articles dropped from 84,312 tokens to 68,994 tokens, an 18% reduction. The extracted content became Create-Images at 37,399 tokens. Create-Compiler added 10,000 tokens for quality validation. Each engine now fits comfortably within a single context window.

### What are integration contracts in this system?

Integration contracts are documented agreements between engines that define inputs, outputs, and validation rules. The system uses 6 contracts: articles-to-images, articles-to-compiler, verification-manifest, reverse-manifest, compiler-to-articles, and compiler-to-images. Each contract specifies what data crosses the boundary and in what format.

### What is the reverse manifest feedback loop?

When the Compiler discovers issues during assembly, it generates a reverse manifest that routes fixes back to the source engine. Tier 0 entries add prevention rules. Tier 2 entries trigger scoped re-generation of a single article section. This closes the feedback loop so defects are fixed at the source, preventing drift between source and compiled output.

### Why was fix-forward-only banned as an anti-pattern?

Fix-forward-only means fixing issues only in the compiled output without updating the source article. This creates drift between source and compiled versions. The next compilation overwrites the fix. Research from CI/CD, build systems, and quality engineering confirmed that tiered feedback with shift-left gates is the production-grade pattern. Fix-forward creates the content equivalent of "works on my machine."

### Can this modular engine pattern apply to other AI content systems?

Yes. The core principle is separating what from how. Any AI content system that loads generation rules, validation rules, and template definitions into a single context window will eventually hit the same constraint. The pattern of scoped engines with documented contracts and a quality gate applies to any multi-step content pipeline.

---

Built by [AI Marketing Operator](https://www.hendry.ai/ai-marketing/operator-logs/) · Create-Articles v7.9.35 · Create-Images v2.0.25 · Create-Compiler v1.3.4

Published March 3, 2026

---

> Part of the [AI Marketing Operator Logs](../README.md) by [Hendry Soong](https://www.hendry.ai)
