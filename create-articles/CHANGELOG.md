# Create-Articles — Changelog

> Part of the [AI Marketing Operator Logs](../README.md) by [Hendry Soong](https://www.hendry.ai)
> Canonical source: [hendry.ai/ai-marketing/operator-logs](https://www.hendry.ai/ai-marketing/operator-logs/)

Content generation engine with 3-tier validation (Pattern, Structural, Semantic). 50+ versions across three generations.

---

## 17 Executable, 58 Declared, One Rule Retired

**Date:** 7 August 2026
**Type:** Decision
**Generation:** GEN 3

Nothing the engine produces needs a gate before publishing. The live site already names its engines in a footer colophon. So STR-031 came out whole: the rule, the loader, the CLI flag, the validator exception, the checklist row. The ID was retired as DECLARED N/A rather than deleted, so the coverage gate stays truthful. Validator v1.3.0 reports 17 executable and 58 declared rules. Suite back to 28 of 28.

**Principle:** Retire a removed rule ID as declared N/A so the coverage count stays honest.

**Tags:** Gen 3, Create-Articles, Decision

---

## 13 Regressions for a Gate That Defines No Fields

**Date:** 7 August 2026
**Type:** Feature
**Generation:** GEN 3

STR-031 blocks any article dated 7 August 2026 or later that lacks a top-level aiDisclosure block. The engine defines none of those fields. It reads spec_version, surface_class, mode and label from the control-plane disclosure spec at check time. Malformed dates and unresolvable specs fail closed. Artifacts dated earlier validate unchanged, since the back catalogue is a later decision. Validator v1.2.0 shipped with 13 new regressions.

**Principle:** Consume the shared spec at check time rather than restating its fields in the checker.

**Tags:** Gen 3, Create-Articles, Feature

---

## 75 to 300 Words per Citation Leaf

**Date:** 25 July 2026
**Type:** Fix
**Generation:** GEN 3

CQ-007 needed a clear boundary for articles that nest H3 headings under an H2. The corrected rule measures the leaf. Each leaf carries 75 to 300 visible editorial words, and H2 bridge prose attaches to the first H3 below it. Headings and code do not count. Unsupported nodes now fail closed in the flagship builders. Regressions cover boundaries, nesting, tables, empty leaves and required fields.

**Principle:** Define the unit a rule measures before setting its threshold.

**Tags:** Gen 3, Create-Articles, Fix

---

## One Inline URL, One Registered Source

**Date:** 25 July 2026
**Type:** Feature
**Generation:** GEN 3

STR-030 is opt-in and blocking. Every inline URL maps to exactly one registered source, with no spares on either side. Each source binds to a unique section. Records must be canonical HTTPS, and provenance is judged relative to the claim, independent of the legacy credibility tier. Regressions fail closed on both Lexical URL shapes, known aggregators and empty inventories. The 2026 framework article migrated to direct-only-v1.

**Principle:** Bind each source to the claim it supports, one URL to one record.

**Tags:** Gen 3, Create-Articles, Feature

---

## 20 Stacked Contrasts That Passed Every Word Check

**Date:** 14 June 2026
**Type:** Fix
**Generation:** GEN 3

A framework draft cleared every banned-word check and still read like a machine. It stacked over 20 contrast constructions on one metronomic rhythm. PAT-021 through PAT-026 went into voice.md v7.0.12: cadence stacking, sentence-length variance, copula avoidance, trailing -ing, puffery, specificity anchors. The reusable gate is 01-RULES/anti-slop.md, wired into validation.md. A do-not-over-strip rule keeps it from flattening honest prose.

**Principle:** Word-level checks miss rhythm. Read the draft aloud before calling it clean.

**Tags:** Gen 3, Create-Articles, Fix

---

## v8.0.1 — Headless Native: Legacy CMS to Headless CMS JSON

**Date:** 5 to 6 April 2026
**Type:** Architecture
**Generation:** GEN 3

Migrated output format from HTML fragments (legacy CMS) to structured JSON (headless CMS). Validation rules were coupled to content, not markup — all checks survived the format change. JSON is now primary output; HTML preview is human-review only.

**Principle:** Changing the output format tests whether your validation rules are coupled to structure or to quality. Ours survived because they check content, not markup.

**Tags:** Gen 3, Create-Articles, Architecture, Headless

---

## v7.9.36 — PAT-019: Experience-Counting Pattern

**Date:** 8 to 10 March 2026
**Type:** Architecture
**Generation:** GEN 3

LLMs quantify personal experience to signal authority ("five times," "after the third collapse"). The count is the tell — real operators describe what happened, not how many times. PAT-019 added as Tier 3 flag-for-review. Exception: counting artifacts/data is fine. Q18 added to QUICK-CHECK. voice.md updated to v7.0.9.

**Principle:** LLMs quantify experience to signal authority. The count itself is the tell — real operators describe what happened, not how many times.

**Tags:** Gen 3, Create-Articles, Voice, Validation

---

## v7.9.33 to v7.9.35 — Domain Frequency + Voice Sync + Rule Health Check

**Date:** 23 February to 2 March 2026
**Type:** Architecture
**Generation:** GEN 3

Domain Frequency (v7.9.33): CV-015 compile check for source domain over-reliance. Voice Sync (v7.9.34): voice.md and AI-SEO rules aligned after spec verification incident. Rule Health Check (v7.9.35): cross-engine pipeline version sync, 21 stale refs updated.

**Principle:** Production compiles are the real test suite for upstream engines. Every compile run reveals gaps the generator missed.

**Tags:** Gen 3, Create-Articles, Validation, Voice

---

## A 9-Step Table That Overstated the Pain

**Date:** 28 February 2026
**Type:** Learning
**Generation:** GEN 3

Section 1 of the agent-addressable-content article opened with a 9-step table. The table overstated what a single article actually costs to produce. It came out. In went a library-evolution table with five cross-article scenarios, plus the argument for the automation path. Two earlier passes on the same piece fixed a PAT-014 violation and cut filler. The schema wordCount was wrong too.

**Principle:** Do not exaggerate the pain your tool solves. The honest number is more persuasive.

**Tags:** Gen 3, Create-Articles, Learning

---

## v7.9.32 — PAT-018: The Ghost Rule

**Date:** 22 February 2026
**Type:** Fix
**Generation:** GEN 3

Article audit found 9 instances of dramatic thesis sentences in FAQ schema. The pattern existed in voice.md examples but had no validation rule, no grep pattern, no quick-check question. A ghost rule: the system taught the pattern through examples but never enforced it. PAT-018 defined with grep pattern and added to quick-check.

**Principle:** Undocumented patterns become invisible violations.

**Tags:** Gen 3, Create-Articles, Voice, Validation

---

## v7.9.30 to v7.9.31 — Absorption Gate + SVG Boundary Check

**Date:** 22 February 2026
**Type:** Architecture
**Generation:** GEN 3

Context Absorption Gate (v7.9.30): Phase 1.3 requires extracting key elements from context files after loading. Prevents "listed as loaded but never read" failure. SVG Boundary Check (v7.9.31): STR-022 BLOCKING — article output must contain 0 SVGs. All visuals as VIP blocks.

**Principle:** "Loaded" is not "read." Gates must prove comprehension, not just access.

**Tags:** Gen 3, Create-Articles, Validation, Architecture

---

## v7.9.28 to v7.9.29 — Compiler Feedback + Profile-Aware Density

**Date:** 22 February 2026
**Type:** Architecture
**Generation:** GEN 3

Feedback Integration (v7.9.28): Phase 5 added for receiving compiler reverse manifests. Articles engine now reads issue classifications and applies fixes before next generation. Profile-Aware Density (v7.9.29): content profiles now define target word counts and structural expectations per content type.

**Principle:** Downstream quality gates are only useful if they can talk back.

**Tags:** Gen 3, Create-Articles, Architecture, Feedback

---

## AI-SEO v7.2 — Spec Verification: 7 Hallucinated Claims Caught After Publication

**Date:** 20 February 2026
**Type:** Failure
**Generation:** GEN 3

Article contained 7 hallucinated claims about a "Declarative API" with HTML attributes that do not exist in the actual WebMCP spec. The spec is purely JavaScript-based. Also had 3 unverifiable "postMessage" claims. Fix: Section rewritten, SVGs rebuilt, FAQ/schema/table/AI-summary all corrected. Part 9 (Emerging Standards & Spec Verification) added to AI-SEO rules.

**Principle:** When writing about specs, the spec is the source of truth.

**Tags:** Gen 3, Create-Articles, AI-SEO, Failure

---

## v7.9.25 to v7.9.27 — Messaging Framework + Brand Alignment

**Date:** 20 February 2026
**Type:** Architecture
**Generation:** GEN 3

Three versions building messaging infrastructure. Messaging framework centralises pillars, proof points, and ICP hooks in one file. Brand alignment ensures consistency across articles.

**Principle:** Centralise messaging. When pillars live in 4 files, they drift in 4 directions.

**Tags:** Gen 3, Create-Articles, Messaging, Architecture

---

## v7.9.22 to v7.9.24 — Date Architecture: From Em Dashes to Semantic HTML

**Date:** 12 to 13 February 2026
**Type:** Feature
**Generation:** GEN 3

Three versions refining how dates work. Em Dash Generation Gate (v7.9.22), Date Placement Flip (v7.9.23), Semantic Dates (v7.9.24) with <time datetime> tags. Triple-layer date consistency: JSON-LD + <time> attribute + visible text.

**Principle:** System files are training data. They must follow the same rules they enforce.

**Tags:** Gen 3, Create-Articles, Schema, Voice

---

## Both Dates Moved Under the Title

**Date:** 12 February 2026
**Type:** Feature
**Generation:** GEN 3

Version 7.9.21 put both dates where the reader looks first. Published and updated now sit in.post-meta, directly under the title. The footer carries neither. The schema contract was updated to match, so JSON-LD and the visible meta read the same values. Template timestamps were normalised to YYYY-MM-DD.

**Principle:** The structured data and the visible page should read from one source.

**Tags:** Gen 3, Create-Articles, Feature

---

## v7.9.20 — Source Registry: Cross-Article Memory

**Date:** 11 February 2026
**Type:** Architecture
**Generation:** GEN 3

Built cross-article memory through a shared source registry. Sources collected during one article are available to the next. Read at Phase 2.1, write at Phase 4.0.1. Append-only. Prevents re-discovery of the same sources.

**Principle:** Cross-session memory turns isolated agents into a learning system.

**Tags:** Gen 3, Create-Articles, Memory, Architecture

---

## v7.9.19 — Tier-First Sources: Classify During Collection

**Date:** 11 February 2026
**Type:** Decision
**Generation:** GEN 3

Sources were collected first, classified later. Quality issues only caught during validation. Moved classification to collection time. Each source gets a tier (Strong/Moderate/Weak) when first recorded.

**Principle:** Classify quality during collection, not after. Left-shift the gate.

**Tags:** Gen 3, Create-Articles, Sources, Decision

---

## v7.9.18 — Sitemap Auto-Sync

**Date:** 11 February 2026
**Type:** Feature
**Generation:** GEN 3

approved-urls.md was manually synced. New articles published after that date triggered false validation flags. Phase 1.0 now auto-syncs from live sitemaps before preflight. Sitemap is source of truth.

**Principle:** Automate from the source of truth. Manual sync processes drift.

**Tags:** Gen 3, Create-Articles, Automation

---

## v7.9.17 — Opposite-Line Hard Stop: Generation-Time Prevention

**Date:** 10 February 2026
**Type:** Architecture
**Generation:** GEN 3

Test article contained a long-form opposite-line pattern that slipped validation. Root cause: voice.md examples covered only short-form patterns. Fix: expanded voice.md with long-form examples, added a self-check during generation.

**Principle:** Generation-time self-checks prevent problems before validation catches them.

**Tags:** Gen 3, Create-Articles, Voice, Validation

---

## v7.9.16 — Stale Knowledge After Knowledge Cutoff

**Date:** 10 February 2026
**Type:** Failure
**Generation:** GEN 3

Article cited an API feature that was deprecated after the LLM's training cutoff. The LLM confidently wrote about it as current. Fix: mandatory live verification for any technical claim about APIs, libraries, or tools.

**Principle:** LLMs are confidently wrong about anything that changed after training cutoff. Force live verification.

**Tags:** Gen 3, Create-Articles, Failure, Verification

---

## v7.9.15 — Source Diversity Enforcement

**Date:** 10 February 2026
**Type:** Fix
**Generation:** GEN 3

Three articles in a row used the same 4 sources. Root cause: the agent found sources that satisfied tier requirements and stopped looking. Added diversity rule: no source domain appears more than twice per article.

**Principle:** Diversity requirements must be structural, not advisory.

**Tags:** Gen 3, Create-Articles, Sources

---

## v7.9.16 — Published Date + Dual-Date Schema

**Date:** 10 February 2026
**Type:** Feature
**Generation:** GEN 3

Readers and LLMs need to distinguish “when was this first published” from “when was it last updated.” Added two-line footer with immutable published date. Schema contract: datePublished matches footer, dateModified matches .post-meta. First publication date never changes.

**Tags:** Gen 3, Create-Articles, Feature

---

## v7.9.15 — Contrast Pattern Gap

**Date:** 9 February 2026
**Type:** Failure
**Generation:** GEN 3

During production article build, two issues passed validation that should have been caught: an opposite-line pattern slipped through PAT-014, and a broken URL wasn’t caught because link liveness checks weren’t enforced as blocking. Expanded PAT-014 with two new checks, promoted STR-020 from advisory to blocking gate, and added curl-based link liveness to quick-check.

**Principle:** Production articles are the real test suite.

**Tags:** Gen 3, Create-Articles, Failure

---

## v7.9.14 — Workflow Enforcement: Agent Skipped Everything

**Date:** 8 February 2026
**Type:** Failure
**Generation:** GEN 3

Asked to write an article, the agent loaded voice.md and a template but bypassed the entire 7-phase workflow. Root cause: CLAUDE.md routed to a directory. Fix: CLAUDE.md now names exact workflow files. Mandatory first output is the preflight checklist.

**Principle:** Route to files, not directories. Agents treat options as a buffet.

**Tags:** Gen 3, Create-Articles, Failure, LLM Behavior

---

## The Limitations Box Came Out

**Date:** 5 February 2026
**Type:** Decision
**Generation:** GEN 3

Version 7.9.6 removed the limitations box. Caveats had been collected into a single block, separate from the claims they qualify. They are now written into the paragraphs that make those claims. The information is the same. A reader has to pass through it to finish the sentence.

**Principle:** Write the caveat into the sentence it qualifies. A box is easy to skip.

**Tags:** Gen 3, Create-Articles, Decision

---

## v7.9.7 to v7.9.13 — Seven Versions in One Day: Content Profiles to CSS Dividers

**Date:** 5 February 2026
**Type:** Release
**Generation:** GEN 3

Seven incremental versions in a single day. Content profiles (v7.9.7), video embeds (v7.9.8), visual source class (v7.9.9), explore section redesign (v7.9.10-12), CSS dividers (v7.9.13).

**Principle:** Ship small, test in production, iterate same-day. Seven focused versions beat one ambitious release.

**Tags:** Gen 3, Create-Articles, Iteration

---

## AI-SEO v7.1.1 — Context Engineering as Core Operator Skill

**Date:** 4 February 2026
**Type:** Architecture
**Generation:** GEN 2

Defined context engineering as the core skill that distinguishes AI marketing operators from prompt engineers. Not about writing better prompts; about designing the information layer all AI systems share.

**Principle:** Context engineering is not prompt engineering. It's designing the information layer all AI systems share.

**Tags:** AI-SEO, Architecture

---

## A Visual Decision Tree From Production Runs

**Date:** 3 February 2026
**Type:** Learning
**Generation:** GEN 3

Running real articles through the engine surfaced friction that the spec never showed. The fixes were usability changes. The durable artifact is a Visual Decision Tree. It draws the decision points in the article build. It came out of production runs rather than from planning on paper.

**Principle:** Production runs find the usability gaps that a written workflow hides.

**Tags:** Gen 3, Create-Articles, Learning

---

## Gen 3 Stable, With Retrofit Mode for the Back Catalogue

**Date:** 1 February 2026
**Type:** Release
**Generation:** GEN 3

Gen 3 reached its first stable release on 1 February 2026, after the split into separate engines. Splitting the monolith left a back catalogue written under the old rules. Retrofit mode handles those. It brings an existing article up to the current structure without a full rewrite.

**Principle:** A stable release needs a path for the work produced before it.

**Tags:** Gen 3, Create-Articles, Release

---

## One File Holds Every viewBox Width

**Date:** 1 February 2026
**Type:** Architecture
**Generation:** GEN 3

SVG templates had drifted apart on viewBox width. They now take that width from a single file, svg-template-lab.html, and match each other. Templates F through N joined the set. Diagrams inside one article now line up at the same measure. A width change starts in the lab file.

**Principle:** Pick one file to hold the geometry and sync the rest to it.

**Tags:** Gen 3, Create-Articles, Architecture

---

## v7.9.2 — The Engine Split: Context Window Survival

**Date:** 1 February 2026
**Type:** Architecture
**Generation:** GEN 3

v7.9.1 loaded at 84,312 tokens. Context window compacted before the agent could finish writing. Separated into two engines: Create-Articles and Create-Images. Connected by integration contracts.

**Principle:** Context window is a finite resource. Separate what from how.

**Tags:** Gen 3, Create-Articles, Architecture

---

## v7.9.1 — Visual Rhythm System

**Date:** 1 February 2026
**Type:** Feature
**Generation:** GEN 3

Added visual rhythm rules: VIP placement frequency, image diversity requirements, and template variety enforcement.

**Principle:** Rules without examples get ignored. Templates without rules sit unused. You need both.

**Tags:** Gen 3, Create-Articles, Visual

---

## Five Stable Templates After One Baseline Fix

**Date:** 31 January 2026
**Type:** Fix
**Generation:** GEN 3

Text inside the SVG diagram templates would not centre vertically against its shape. The attribute that fixed it is dominant-baseline set to central. Arrows are placed manually. With those settled, five templates, A through E, reached a stable state. PAT-015 was defined in the same version.

**Principle:** A diagram system is only reusable once its text centres the same way every time.

**Tags:** Gen 3, Create-Articles, Fix

---

## Three Prompt Patterns That Repeated

**Date:** 31 January 2026
**Type:** Learning
**Generation:** GEN 3

Three prompt patterns, labelled A, B and C, were run repeatedly against Gemini. The question was whether each returns the same shape of output run after run. All three held. Stability was confirmed, and the three were recorded as the tested set for the engine. A pattern that has not been repeated is a guess.

**Principle:** Run a prompt until it repeats before you write it into the spec.

**Tags:** Gen 3, Create-Articles, Learning

---

## Hidden Image Markers Replaced With Visible Prompts

**Date:** 31 January 2026
**Type:** Decision
**Generation:** GEN 3

Image Insertion Points were markers only the pipeline could see. A human reading the draft had no idea what image was coming. Visible Image Prompts replaced them. The prompt text sits in the draft where the image goes, readable by whoever reviews it. The same version set the SVG-first rule: use a diagram before reaching for a generated image.

**Principle:** A handoff marker the reviewer cannot see is a handoff nobody can check.

**Tags:** Gen 3, Create-Articles, Decision

---

## STR-017 and STR-018: The First Image Handoff

**Date:** 31 January 2026
**Type:** Feature
**Generation:** GEN 3

Image Insertion Points are the markers that pass work from the article engine to the image engine. STR-017 and STR-018 govern them. This is the first version where the two engines share a written contract. The markers were invisible to a reader of the draft, which the following version fixed.

**Principle:** Give the handoff between two engines a rule ID before it grows conventions.

**Tags:** Gen 3, Create-Articles, Feature

---

## Nine Components, Four Voice Updates, One Registry

**Date:** 31 January 2026
**Type:** Feature
**Generation:** GEN 3

Components C01 through C09 reached completion. Voice updates V01 to V04 landed in the same pass. A component registry lists them all. Without it, a builder has to grep the templates to find what exists. The registry is the index, and the templates are the implementation.

**Principle:** Without a registry, the only index of your components is the source.

**Tags:** Gen 3, Create-Articles, Feature

---

## One validation.md, Three Depths

**Date:** 30 January 2026
**Type:** Architecture
**Generation:** GEN 3

Validation rules had been spread across several files in the engine. They now live in validation.md. Depth is a mode, selected as QUICK, STANDARD or FULL. A fast pass and a full audit read the same rule text, so they cannot disagree. Only the count of checks changes.

**Principle:** One rule file, with the depth of the pass as a mode.

**Tags:** Gen 3, Create-Articles, Architecture

---

## PAT-013 and PAT-014 Become Auto-Fail

**Date:** 30 January 2026
**Type:** Feature
**Generation:** GEN 3

PAT-013 covers filler words. PAT-014 covers the contrast construction LLMs reach for, the line that states a thing by first stating its opposite. Both were made auto-fail gates on 30 January 2026. A draft carrying either stops. Later versions widened both patterns, and the auto-fail behaviour dates from here.

**Principle:** Some voice rules earn an auto-fail. Filler and manufactured contrast are two of them.

**Tags:** Gen 3, Create-Articles, Feature

---

## CSS Out of the Article, Into the Theme

**Date:** 30 January 2026
**Type:** Architecture
**Generation:** GEN 3

Article output carried its own styles. The CSS moved out to the CMS theme, so one edit reaches every published article. Schema went to v7.1 in the same version. It adds TechArticle, DefinedTerm and an AI Summary block. Those three types tell a machine reader what kind of document it has.

**Principle:** Presentation belongs in the theme so a style change never touches old output.

**Tags:** Gen 3, Create-Articles, Architecture

---

## Six Link Rules and an Approved-URL Registry

**Date:** 30 January 2026
**Type:** Feature
**Generation:** GEN 3

Six rules, L01 through L06, govern links. They cover external link targets, duplicate detection and the direct sourcing of claims. approved-urls.md holds the registry. A URL outside that file does not get written into a draft. Duplicate detection catches the same source cited more than once.

**Principle:** Maintain an allowlist of URLs the engine may cite and check every draft.

**Tags:** Gen 3, Create-Articles, Feature

---

## AI-SEO v7.1 — AI-SEO Schema Rebuild for LLM Authority

**Date:** 28 January 2026
**Type:** Architecture
**Generation:** GEN 2

Rebuilt schema markup to serve two audiences: Google for rich results, LLMs for citation authority. Added DefinedTerm schema for technical concepts. Schema now includes enough context for AI systems to cite accurately.

**Principle:** Schema serves two masters now. Google for rich results, LLMs for citation authority. Serve both or serve neither.

**Tags:** AI-SEO, Schema

---

## v7.0.3 — Voice Drift from Skill File

**Date:** 21 January 2026
**Type:** Fix
**Generation:** GEN 2

Content started sounding generic. Traced to skill file overriding voice.md settings. The skill file had "helpful assistant" defaults that diluted brand voice. Fix: voice.md loads after skill file to override defaults.

**Tags:** Create-Articles, Gen 2, Voice

---

## v7.0.3 — Renamed Content System to Create-Articles

**Date:** 21 January 2026
**Type:** Decision
**Generation:** GEN 2

Renamed from "Content System" to "Create-Articles" to match the multi-engine naming convention. All references updated.

**Tags:** Create-Articles, Gen 2, Naming

---

## v7.0.2 — TOC Missing Despite Rule Existing

**Date:** 18 January 2026
**Type:** Failure
**Generation:** GEN 2

Table of contents was missing from generated articles even though there was a rule requiring it. The rule existed but was advisory, not structural. Agent skipped it because there was no validation check.

**Principle:** Advisory rules get skipped. Make requirements structural.

**Tags:** Create-Articles, Gen 2, Validation

---

## v7.0.2 — Schema Mentions Must Match Content

**Date:** 18 January 2026
**Type:** Feature
**Generation:** GEN 2

Schema "mentions" array listed entities not in the article text. Added validation: every schema mention must appear in visible content.

**Tags:** Create-Articles, Gen 2, Schema

---

## v7.0.2 — Pre-Output Checklist

**Date:** 18 January 2026
**Type:** Feature
**Generation:** GEN 2

Articles passing validation but still having issues. Individual checks passed, cross-checks weren't happening. TOC didn't match H2 IDs. Solution: Pre-output checklist runs AFTER validation passes.

**Principle:** Validation checks parts. Pre-output checks the whole. Both are necessary.

**Tags:** Create-Articles, Gen 2, Validation

---

## v7.0.2 — Schema Timing Bug

**Date:** 18 January 2026
**Type:** Failure
**Generation:** GEN 2

Schema wordCount validation failed on every run. Schema said 1650, actual content was 1366. Root cause: Schema populated from content brief BEFORE content generated. Validating against a goal, not a measurement.

**Principle:** Measured values must come from output, not input. Never validate predictions as measurements.

**Tags:** Create-Articles, Gen 2, Schema, Failure

---

## v7.0.1 — Tables Hard to Scan

**Date:** 17 January 2026
**Type:** Fix
**Generation:** GEN 2

Generated comparison tables had too many columns, inconsistent alignment, and no visual hierarchy. Fix: max 4 columns, left-align text, bold first column.

**Tags:** Create-Articles, Gen 2, Formatting

---

## v7.0 — Rebuilt Validation as 3-Tier System

**Date:** 13 January 2026
**Type:** Architecture
**Generation:** GEN 2

Previous validation was a single pass checklist. Rebuilt as 3-tier system: Pattern (100% automated, regex/grep), Structural (95% automated, DOM checks), Semantic (70-80%, LLM-judged with rubrics).

**Principle:** Evidence-based validation defeats hallucination.

**Tags:** Create-Articles, Gen 2, Validation, Architecture

---

## v7.0 — LLMs Lie About Validation

**Date:** 13 January 2026
**Type:** Learning
**Generation:** GEN 2

Asked the LLM to validate its own output. It reported all checks passed. Manual review found 6 failures. The LLM pattern-matched the expected output format without doing the work. Key discovery that led to the 3-tier validation rebuild.

**Principle:** Match automation level to confidence level.

**Tags:** Create-Articles, Gen 2, LLM Behavior, Learning

---

## v6.9.9.8 — Gen 1 Complete. Production Stable

**Date:** 11 January 2026
**Type:** Release
**Generation:** GEN 1

Final Gen 1 release. Production-stable content generation with voice rules, CMS integration, and golden reference files.

**Tags:** Create-Articles, Gen 1, Release

---

## v6.9.9.7 — Font Mismatch

**Date:** 11 January 2026
**Type:** Failure
**Generation:** GEN 1

Generated CSS referenced Inter font but the site used system fonts. Fix: extract actual font-family from live site CSS.

**Principle:** Match the environment. Extract values from destination.

**Tags:** Create-Articles, Gen 1, CSS

---

## v6.9.7 — Regression Check

**Date:** 10 January 2026
**Type:** Fix
**Generation:** GEN 1

Fix for one article type broke another. No regression testing existed. Added: after any rule change, re-validate against last 3 articles.

**Tags:** Create-Articles, Gen 1, Testing

---

## v6.9.5 — Header/Footer Drift

**Date:** 7 January 2026
**Type:** Failure
**Generation:** GEN 1

Agent modified header and footer HTML each generation. Root cause: no explicit "do not modify" instruction. Added forbidden zones: header and footer markup is locked.

**Principle:** Agents improvise unless explicitly forbidden.

**Tags:** Create-Articles, Gen 1, LLM Behavior

---

## v6.9.4 — FAQ Schema as Standard

**Date:** 7 January 2026
**Type:** Decision
**Generation:** GEN 1

Added FAQ schema to all articles. Decided on standard 5-question format. FAQ schema serves both Google rich results and LLM citation.

**Tags:** Create-Articles, Gen 1, Schema

---

## v6.9.3 — Missing Internal Links

**Date:** 7 January 2026
**Type:** Fix
**Generation:** GEN 1

Articles had no internal links. Added rule: minimum 2 internal links per article, must link to existing published URLs from approved-urls.md.

**Tags:** Create-Articles, Gen 1, SEO

---

## v6.9.4 — FAQ Count Insufficient

**Date:** 7 January 2026
**Type:** Decision
**Generation:** GEN 1

Posts generating 3 to 5 FAQs. Need minimum 6 for schema richness. Added explicit minimum, updated validation checklist, added to common mistakes table.

**Principle:** Make requirements explicit and enforceable.

**Tags:** Gen 1, Create-Articles, Decision

---

## v6.9 — Mobile Padding Iteration

**Date:** 6 January 2026
**Type:** Fix
**Generation:** GEN 1

Generated pages had tighter spacing than existing website. Tested values iteratively: v6.8 at 3.2vw was too tight. v6.9 at max(5vw, 16px) was still tight. v6.9.2 at max(10vw, 40px) for 768px finally matched. Three attempts with screenshot comparisons.

**Principle:** Test against production. Screenshots don’t lie.

**Tags:** Gen 1, Create-Articles, Fix

---

## v6.8 — CMS Fragment Mode

**Date:** 6 January 2026
**Type:** Release
**Generation:** GEN 1

Generated complete HTML pages with DOCTYPE, html, head, body tags. CMS theme already provides page structure. Result: duplicate headers, duplicate navigation, style conflicts. Switched to fragment mode.

**Principle:** Design for integration, not standalone. Output format depends on destination.

**Tags:** Create-Articles, CMS, Architecture

---

## v6.5 — GitHub Versioning + Golden Reference Files

**Date:** 2 January 2026
**Type:** Release
**Generation:** GEN 1

Set up version control. Created golden reference files for each format type. Fixed CSS variable naming mismatch.

**Principle:** One source of truth. Name files so the canonical source is obvious.

**Tags:** Create-Articles, Version Control, CSS

---

## The Engine Writes as a Named Person

**Date:** 1 January 2026
**Type:** Architecture
**Generation:** GEN 3

The engine writes as a named person, Hendry Soong. That persona drives what the draft claims and what it refuses to claim. Data collection was added so the persona has facts to work from. Rewrite mode came in the same version. Schema moved to an @graph structure, so the entities in one article link to each other.

**Principle:** Name the person the engine writes as. A house style has no opinions.

**Tags:** Gen 3, Create-Articles, Architecture

---

## 5 of 9 Techniques Actually Implemented

**Date:** 1 January 2026
**Type:** Failure
**Generation:** GEN 3

The engine publishes advice on nine content techniques. An audit on 1 January 2026 checked whether its own output actually used them. Five did. The other four had been written up in the spec and never wired into the build. All nine are implemented now, and the gap only showed because someone checked.

**Principle:** Audit your own output against the advice you publish. Half of it was missing.

**Tags:** Gen 3, Create-Articles, Failure

---

## v5.0 — Rolled Back to Simplicity

**Date:** 30 December 2025
**Type:** Release
**Generation:** GEN 1

v3.8 broke GPT compatibility. Rolled back to v2.2 structure. Added one thing: a completed HTML example showing exactly what good output looks like. GPT followed workflow correctly for the first time.

**Principle:** One example beats 89 lines of instructions.

**Tags:** Create-Articles, Gen 1, Simplicity

---

## v3.8 — Over-Engineering Collapse

**Date:** 29 December 2025
**Type:** Failure
**Generation:** GEN 1

Added too many rules, too many files, too many validation steps. GPT couldn't hold all of it in context. Output quality degraded. The system was smarter than the tool could handle.

**Tags:** Create-Articles, Gen 1, Failure

---

## v3.0 — Multi-Format Content Generation

**Date:** 27 December 2025
**Type:** Release
**Generation:** GEN 1

Added support for multiple content formats beyond articles. Templates for each format type. Workflow now selects format first, then applies format-specific rules.

**Tags:** Create-Articles, Gen 1, Formats

---

## v3.8 — The 89-Line Disaster

**Date:** 29 December 2025
**Type:** Failure
**Generation:** GEN 1

Added 89 lines of validation checklists with MANDATORY and CRITICAL warnings everywhere. Renamed folders. Added 8 separate validation sections. GPT stopped following the workflow entirely. Output quality dropped. Workflow grew from 205 to 294 lines. The LLM got confused by competing priorities.

**Principle:** One example beats 89 lines of instructions. LLMs pattern-match examples better than they parse rules.

**Tags:** Gen 1, Create-Articles, Failure

---

## v3.0 — Restructured to Core/Create Architecture

**Date:** 27 December 2025
**Type:** Release
**Generation:** GEN 1

Separated core (brand, design) from creation (templates, workflow). Attempting to add organization. This would break things.

**Tags:** Gen 1, Create-Articles, Release

---

## v2.0 — First Content Generation Workflow

**Date:** 25 December 2025
**Type:** Release
**Generation:** GEN 1

First working workflow that produced usable content. Voice rules, basic validation, HTML output.

**Tags:** Create-Articles, Gen 1, Workflow

---

## v1.0 — Initial Folder Structure

**Date:** 25 December 2025
**Type:** Release
**Generation:** GEN 1

Created the initial folder structure for the content system. System files, templates, outputs.

**Tags:** Create-Articles, Gen 1, Setup

---

## Foundation Build (Pre-v1.0)

Before Create-Articles could generate anything useful, the Foundation layer had to produce its outputs. These entries document DEFINE, UNDERSTAND, and POSITION engine work that feeds the content system.

---

## v0.3 — Engine Output: POSITION (Competitive Differentiation)

**Date:** 22 December 2025
**Type:** Foundation Layer
**Generation:** POSITION

Third foundation engine. Competitive positioning analysis. Output: differentiation framework that gates content generation.

**Principle:** Positioning is a filter that kills generic content.

**Tags:** Foundation, Position

---

## v0.2 — Engine Output: UNDERSTAND (ICP Development)

**Date:** 20 December 2025
**Type:** Foundation Layer
**Generation:** UNDERSTAND

Second foundation engine. ICP (Ideal Customer Profile) development. Output: persona definitions that shape content targeting.

**Principle:** ICP precision forces content precision.

**Tags:** Foundation, ICP

---

## v0.1 — Engine Output: DEFINE (Voice & Brand)

**Date:** 18 December 2025
**Type:** Foundation Layer
**Generation:** DEFINE

First foundation engine. Voice and brand definition. Output: voice rules, brand guidelines, tone parameters.

**Principle:** Voice isn't vibe. It's enforceable rules.

**Tags:** Foundation, Voice, Brand
