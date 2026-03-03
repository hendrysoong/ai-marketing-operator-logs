# 23 Iterations in 32 Days: How I Built a Production AI Content System

> **Canonical URL:** https://www.hendry.ai/ai-marketing/operator-logs/build-production-ai-content-system/
> **Engine:** Create-Articles
> **Version:** v1.0 to v7.0.3
> **Author:** Hendry Soong
> **Updated:** February 5, 2026

---

## TLDR

23 versions across 3 generations of an AI content engine, built over 32 days. The system takes a brief and produces a publish-ready HTML article with schema markup, structured data, visual placeholders, and validated content. This retrospective documents the 5 biggest failures, the principles extracted from each, and the architecture decisions that emerged. Every principle was learned the expensive way.

---

## Version Timeline

### Gen 1: v1.0 to v6.9.9.8 (Production Stable)

The foundational generation. Started as a simple prompt and grew into a 25-version system with workflow phases, voice rules, SEO requirements, and HTML output formatting. Gen 1 reached production stability at v6.9.9.8 -- articles were publishable without manual editing.

Key milestones:
- **v1.0:** Basic prompt. Output was unusable without heavy editing.
- **v3.0:** Introduced structured workflow (brief, outline, draft, review).
- **v3.8:** The 89-line disaster (see Failure #1).
- **v5.0:** Added schema.org JSON-LD generation.
- **v6.0:** Added voice rules and brand consistency.
- **v6.9.5:** Header/footer drift fix (see Failure #4).
- **v6.9.9.7:** Font mismatch fix (see Failure #5).
- **v6.9.9.8:** Gen 1 complete. Production stable.

### Gen 2: v7.0 to v7.0.8 (Validation Rebuild)

Triggered by the discovery that the Gen 1 validator fabricated results. Gen 2 rebuilt the validation system from scratch with evidence-based checking (see Failure #2 and the companion article "LLMs Lie About Validation").

Key milestones:
- **v7.0:** 3-tier validation system introduced.
- **v7.0.2:** Schema timing fix (see Failure #3).
- **v7.0.3:** Content profiles introduced -- reusable configurations for different article types.
- **v7.0.8:** Gen 2 complete. Validation trustworthy.

### Gen 3: v7.9 to v7.9.11+ (Split Architecture)

Triggered by context window exhaustion at 84K tokens. Gen 3 split the monolithic engine into three modular engines connected by integration contracts (see companion article "The Engine Split").

Key milestones:
- **v7.9.0:** Create-Images extracted as independent engine.
- **v7.9.2:** Integration contracts formalized. Create-Compiler created.
- **v7.9.11:** Closed-loop feedback system with reverse manifests.

---

## The 5 Biggest Failures

### Failure 1: The 89-Line Disaster (v3.8)

**What happened:** The engine at v3.7 was producing good articles but missing some formatting requirements. I added 89 lines of detailed formatting rules covering heading hierarchy, list formatting, paragraph length, code block styling, and 12 other requirements.

The next generation run produced an article that followed none of the original workflow rules. The model read the 89 new lines and treated them as the primary instruction set, deprioritizing the existing workflow that had been working.

**Root cause:** LLMs do not process instructions as a priority queue. They process them as context. 89 lines of formatting rules displaced the workflow rules in the model's attention. More rules did not mean better compliance. It meant less compliance with the rules that mattered most.

**Fix:** I deleted the 89 lines and replaced them with one completed HTML example -- a single article that demonstrated every formatting requirement through example rather than instruction. The model pattern-matched the example more reliably than it synthesized behavior from 89 rules.

**Principle 03:** One example beats 89 lines of specification. When you need to communicate a complex output format, show the output. Do not describe it.

---

### Failure 2: LLMs Lie About Validation (v7.0)

**What happened:** The Gen 1 validator reported perfect scores on every article for months. A manual audit revealed that external link counts were fabricated, banned word detection was skipped, and FAQ consistency checks were invented. The model recognized validation as a yes/no task and generated the expected affirmative without performing the checks.

**Root cause:** Validation instructions formatted as yes/no questions invite affirmative answers. The model optimizes for plausible text, not for mechanical verification. Asking "Does this have 10+ external links?" is a generation task, not a validation task. The model generates the expected answer.

**Fix:** Rebuilt the validator as a 3-tier system. Tier 1: regex checks (100% reliable). Tier 2: evidence extraction followed by mechanical verification (~95% reliable). Tier 3: semantic advisory with human review (70-80% reliable, never auto-fix). Full details in the companion article.

**Principle 06:** Ask for evidence, not conclusions. When you need to verify a property of generated content, ask the model to extract the relevant data, then verify the data yourself.

---

### Failure 3: Schema Timing (v7.0.2)

**What happened:** The schema.org JSON-LD included a `wordCount` field. The value was pulled from the brief (target: 1,650 words) rather than measured from the generated article (actual: 1,366 words). The published schema told search engines the article was 1,650 words when it was 1,366 words.

**Root cause:** The schema generation step ran before the article body was finalized. It had access to the brief's target word count but not the actual word count of the generated content. The model used the number it had, not the number it should have computed.

**Fix:** Schema generation now runs after content generation. Measured values (word count, section count, FAQ count) are computed from the final output, not from the brief. The brief provides targets; the schema records actuals.

**Principle 08:** Measured values come from output, not input. Any schema field or metadata value that describes the generated content must be computed from the generated content, not estimated from the brief.

---

### Failure 4: Header/Footer Drift (v6.9.5)

**What happened:** The article template included a specific header and footer structure -- exact HTML with specific class names, links, and text. After several generation runs, the model started "improving" the header and footer: adding classes, changing link text, reorganizing elements, and inserting decorative markup.

**Root cause:** LLMs improvise. Given a template with elements that could be "better," the model will make them "better" by its own judgment. The header and footer were treated as suggestions, not as verbatim requirements.

**Fix:** The header and footer are now marked as verbatim blocks with explicit instructions: "Output this HTML exactly as shown. Do not modify, add to, or remove any element." The model respects verbatim instructions when they are explicit. It improvises when they are implicit.

**Principle 02:** Agents improvise unless explicitly forbidden. If a piece of output must be exact, say so. If you do not mark it as verbatim, the model will treat it as a starting point.

---

### Failure 5: Font Mismatch (v6.9.9.7)

**What happened:** The engine generated articles with CSS referencing Inter as the body font. The website theme used DM Sans. Every article published to the website had a visible font mismatch until manually corrected.

**Root cause:** The engine's CSS rules were written based on an assumption about the website's font stack. The assumption was never verified. The model faithfully used the font specified in its instructions, which happened to be wrong.

**Fix:** The engine's CSS now references the exact font stack from the website theme. The font specification was verified by inspecting the live website's computed styles, not by assumption. The content profile includes a `fontStack` field that is set per-brand, not per-engine.

**Principle 09:** Match the environment, do not assume it. Every output specification that depends on the deployment environment (fonts, colors, spacing, breakpoints) must be verified against the actual environment, not assumed from documentation or memory.

---

## Architecture Decisions in Gen 3

The 5 failures drove architecture decisions that shaped Gen 3:

### Engine Split

The monolithic engine grew to 84K tokens. Context compaction triggered mid-generation, silently dropping rules. The split into three engines (Create-Articles, Create-Images, Create-Compiler) bounded each engine's context and introduced integration contracts for inter-engine communication. Full details in the companion article.

### Content Profiles

Different article types (deep dives, tutorials, comparisons, news analysis) require different configurations: different word count targets, different section structures, different visual density, different schema types. Content profiles are reusable configuration objects that customize engine behavior without modifying the engine itself.

### Visual Source Lines

Every SVG diagram includes a source attribution line linking to the data source or article section that supports the visual claim. This emerged from a defect where diagrams presented statistics without attribution, making them unverifiable. Source lines are now enforced by the integration contract between Create-Articles and Create-Images.

### CMS Fragment Mode

The engine outputs HTML fragments, not complete HTML documents. Fragments are designed to be inserted into a CMS template. This removes the header/footer drift problem: the engine does not generate headers or footers because those belong to the CMS template, not the article content.

### 3-Tier Validation

Validation is stratified by reliability. Pattern checks are deterministic. Evidence checks force the model to show its work. Semantic checks are advisory only. This architecture accepts that LLM-based validation has inherent reliability limits and designs around them rather than pretending they do not exist.

---

## Brand Portability Test

To test whether the engine was brand-specific or generalizable, I configured it for a second brand with different voice rules, visual identity, schema requirements, and content focus.

**Result:** 80% of the engine is universal (workflow, validation tiers, schema generation, HTML structure, integration contracts). 20% is brand-specific (voice patterns, visual templates, font stacks, color palettes, content profiles). The brand-specific 20% took approximately 2.5 hours to configure.

The universal/specific split is embedded in the engine architecture: brand-specific configuration lives in content profiles and template files, not in the workflow rules. Switching brands means swapping profiles, not rewriting the engine.

---

## 10 Extracted Principles

| # | Principle | Source Failure | Summary |
|---|---|---|---|
| P01 | Verbatim means verbatim | Header/Footer Drift | Mark exact-output requirements explicitly |
| P02 | Agents improvise unless forbidden | Header/Footer Drift | If it should not change, say so |
| P03 | One example beats 89 lines | The 89-Line Disaster | Show the output format, do not describe it |
| P04 | Advisory rules get skipped | Context pressure | Make every rule blocking or remove it |
| P05 | Validation is not generation | LLM Validation Lies | Separate the validator from the generator |
| P06 | Evidence over conclusions | LLM Validation Lies | Ask for data, not judgments |
| P07 | Tier your reliability | 3-Tier system | Match method to confidence level |
| P08 | Measure from output | Schema Timing | Computed values come from results, not inputs |
| P09 | Match the environment | Font Mismatch | Verify deployment context, do not assume |
| P10 | Separate the universal from the specific | Brand Portability | Architecture enables brand switching |

---

## FAQ

### How long does each article take to generate?

A single article generation run takes 3-5 minutes with Claude. This includes preflight checks, source verification, content generation, visual plan creation, and validation. The validation pass adds approximately 90 seconds. The total time from brief to publish-ready HTML is typically under 10 minutes, including human review of the validation evidence report.

### What model does the engine use?

The engine is designed for Claude (Anthropic) and has been tested primarily with Claude 3.5 Sonnet and Claude 3 Opus. The principles (evidence-based validation, example over specification, verbatim marking) apply to any LLM, but the specific token budgets and context management strategies are tuned for Claude's context window and attention patterns.

### Can this system generate content in languages other than English?

The workflow, validation system, and integration contracts are language-agnostic. The language-specific components are voice rules, banned word lists, and content profiles. Supporting a new language requires creating language-specific profiles and voice rules. The engine architecture does not change. This has not been tested beyond English.

### What is the cost per article?

At current Claude API pricing, a single article generation run (including validation) costs approximately $0.15-0.30 depending on article length and the number of validation checks. Image generation (Create-Images) adds approximately $0.10-0.20 per article depending on the number of visuals. Total cost per publish-ready article with images: approximately $0.25-0.50.

### How do you handle factual accuracy?

Factual accuracy is addressed at two points: source verification during preflight (Phase 2) and evidence-based validation during the check phase (Phase 5). The source verification step requires every factual claim to reference a specific source. The validation step extracts all claims and their attributed sources, producing a list that can be manually verified. The engine does not guarantee factual accuracy -- it makes accuracy auditable.

### What would you do differently if starting over?

Start with the split architecture from day one. The monolithic engine was faster to iterate on initially but created technical debt that required a generation-level rewrite to resolve. Build the 3-tier validation from the first version, not as a retrofit. And write one golden example article before writing a single line of specification. The example would have prevented the 89-line disaster and several smaller formatting issues that consumed multiple versions to resolve.

---

> Built by AI Marketing Operator -- [hendry.ai](https://www.hendry.ai)
>
> Watch the Gen 1 walkthrough: [Building a Content System That Actually Works](https://www.youtube.com/watch?v=yr0SitDxitU)
