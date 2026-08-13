# Create-Images — Changelog

> Part of the [AI Marketing Operator Logs](../README.md) by [Hendry Soong](https://www.hendry.ai)
> Canonical source: [hendry.ai/ai-marketing/operator-logs](https://www.hendry.ai/ai-marketing/operator-logs/)

SVG diagram and hero image generation with visual perception rules and an exit gate validation system. 30+ versions across three generations.

---

## The Generator Stopped Reading Outside Its Own Repo

**Date:** 7 August 2026
**Type:** Decision
**Generation:** GEN 3

An owner decision pulled the last of the disclosure machinery out of svg-generator.mjs. No spec read, no metadata block, no ACTIVE_DISCLOSURE state. The --disclosure-spec flag is swallowed with a note so a stale caller never breaks. The generator now reads nothing outside its own repository. Two hardening fixes stayed: realpath entry-point detection, and unknown-flag rejection after a stray flag once became the output filename. Suite 7/7.

**Principle:** Keep the hardening a bad feature exposed, even after the feature goes.

**Tags:** Gen 3, Create-Images, Decision

---

## A Missing Spec Now Produces a Plain SVG

**Date:** 7 August 2026
**Type:** Decision
**Generation:** GEN 3

An owner decision removed Tier-1 check SVG-T1-009 and the --require-disclosure flag. SVG checks fell back to nine, so the lab's nine-check schema matched again with no lab change. loadDisclosureSpec now returns null instead of throwing. A missing, unreadable or invalid spec yields a plain unmarked SVG, so generation can never fail on provenance state. Tier-1 suite 9/9, generator 11/11.

**Principle:** A provenance marker is optional metadata. Never let its absence stop the build.

**Tags:** Gen 3, Create-Images, Decision

---

## A Strip Mandate That Would Have Erased the New Metadata

**Date:** 7 August 2026
**Type:** Feature
**Generation:** GEN 3

Phase B of the disclosure gate under an owner decision. svg-generator.mjs emits one IPTC DigitalSourceType block as the first child of every SVG. Values come from a control-plane spec held in the lab. New Tier-1 check SVG-T1-009 requires any present metadata to match the spec exactly, and legacy assets still pass. The existing strip mandate IMG-T1-005 would have deleted it, so stripping now preserves the disclosure namespaces. 14 new regressions across both suites.

**Principle:** A metadata strip rule and a metadata write rule must be reconciled in the same pass.

**Tags:** Gen 3, Create-Images, Feature

---

## A Hero From Another Article Used to Pass

**Date:** 25 July 2026
**Type:** Fix
**Generation:** GEN 3

IMG-T1-006 was reconciled with the live publishFromJson() contract. Hero validation now demands a lowercase slug and the exact basename hero-{slug}.svg, so a hero from a different article fails. Every SVG uses the documented 50KB cap and non-SVG assets keep the older dated rule. The validator also stopped advertising a --fix mode that did not exist. Eight regressions added, and both live heroes pass 9/9.

**Principle:** Check the validator against the live publish contract before trusting either.

**Tags:** Gen 3, Create-Images, Fix

---

## Two Hero Lanes, Only One of Them Stable

**Date:** 20 June 2026
**Type:** Architecture
**Generation:** GEN 3

Hero generation splits into two capability lanes, and the provider is a swappable detail. structural-svg is the stable default for system and architecture heroes. editorial-raster evokes a feeling and never states facts. It stays documented and not stable until the R01 provenance wiring lands. A new heroLane field carries the choice. Gates RAS-001 to RAS-006 run only on the raster lane.

**Principle:** Name lanes by capability so a provider swap is a config change.

**Tags:** Gen 3, Create-Images, Architecture

---

## Eight Spec Templates and Two Blocking Gates

**Date:** 17 June 2026
**Type:** Architecture
**Generation:** GEN 3

The Swiss spec-sheet register became the canonical system for structured body figures. 03-TEMPLATES/spec-sheet.md holds eight templates, from spec-flow through spec-diagram. Routing changed with it. Structured figures emit visualType html component data. Bespoke diagrams use SVG line art inside spec chrome, and the legacy A to N SVGs are fallback only. One register per figure and a 680px mobile check are both blocking gates.

**Principle:** One visual register per figure, and the mobile width check blocks the output.

**Tags:** Gen 3, Create-Images, Architecture

---

## The Generator Was Right, the Spec Was Stale

**Date:** 14 June 2026
**Type:** Fix
**Generation:** GEN 3

Brand tokens were reconciled against the live hendry.ai design system and svg-generator.mjs. The generator already emitted Instrument Serif, which the spec never mentioned. Mono went from JetBrains to IBM Plex Mono across three files and the golden SVG. The accent hex moved from #410EB7 to #534AB7, including inside validate_tier1.py. Two reference hexes stay flagged until the live CMS confirms them. Tracking files caught up from v4.1.0.

**Principle:** When spec and generator disagree, check which one the live site already matches.

**Tags:** Gen 3, Create-Images, Fix

---

## Six Design-Law Bans, Numbered IMP-001 to IMP-006

**Date:** 7 June 2026
**Type:** Feature
**Generation:** GEN 3

The impeccable skill was vendored into the engine as 01-RULES/impeccable.md. It names six design-law bans: side-stripe accents, hero-metric trios, identical card grids, gradients, captions that restate the figure, and em dashes. An AI-slop test sits alongside them. Exit gate IMP-001 to IMP-006 enforces the set. Flow, stack, hub and two-panel patterns route to HTML components with CSS-grid arrows. Freehand SVG is reserved for bespoke illustration.

**Principle:** Ban the specific visual tell by name so the gate can check it.

**Tags:** Gen 3, Create-Images, Feature

---

## v4.1.0 — 760px-Proof Hero: Primitive Library + Render-Width Tuning

**Date:** 8 April 2026
**Type:** Architecture
**Generation:** GEN 3

Hero SVGs rendered at 760px (0.633x viewBox) were too small to read. Tuned all minimums for actual render width: titles ≥38px, headings ≥26px, body ≥22px, absolute min 18px. Built primitive library (P1–P8): Content Box, Schema Card, Document Icon, Flow Arrow, Browser Frame, Database Cylinder, Stat Callout, Dashed Connection.

**Principle:** Design for the render width, not the viewBox. 1200px SVGs that render at 760px need their minimums tuned for 0.633x.

**Tags:** Gen 3, Create-Images, Hero, Typography

---

## v4.0.0 — SVG-Only: Two Visual Systems + Programmatic Generator

**Date:** 7 to 8 April 2026
**Type:** Architecture
**Generation:** GEN 3

Removed tool routing entirely. One tool, two modes (hero and inline), zero routing logic. Added programmatic generator for data-heavy visuals. Decision fatigue eliminated — the agent picks mode, not tool.

**Principle:** Removing tool routing didn't remove capability — it removed decision fatigue. One tool, two modes, zero routing logic.

**Tags:** Gen 3, Create-Images, Architecture, Simplification

---

## v3.0.1 — Headless Native: VIP Blocks to CMS Fields

**Date:** 5 April 2026
**Type:** Architecture
**Generation:** GEN 3

Migrated output format from VIP block HTML to headless CMS field structure. Generation rules unchanged — format wrapper updated only. I/O format changed, generation rules didn't.

**Principle:** When the I/O format changes but the generation rules don't, you know the rules were well-abstracted.

**Tags:** Gen 3, Create-Images, Architecture, Headless

---

## v2.0.26 — Arithmetic-Proof Generation

**Date:** 3 March 2026
**Type:** Architecture
**Generation:** GEN 3

Mandatory SVG comments before every text block and every arrow, showing arithmetic before placement. EG-009 added: exit gate checks arrow breathing arithmetic. 9 checks total. Proportional spacing formula replaces fixed table. Text centering now recalculates from formula on every render.

**Principle:** Force the agent to show its math. Arithmetic comments before placement catch errors that visual inspection misses.

**Tags:** Gen 3, Create-Images, Architecture, Exit Gate

---

## v2.0.22 — Feedback Receiving Protocol

**Date:** 22 February 2026
**Type:** Architecture
**Generation:** GEN 3

Create-Images can now receive reverse manifests from Create-Compiler. Issues classified as IMAGE type are routed back and applied before next generation.

**Principle:** Every engine that receives feedback becomes self-improving. Close the loop for all producers, not just one.

**Tags:** Gen 3, Create-Images, Feedback

---

## v2.0.20 to v2.0.21 — Exit Gate: Centering Enforcement at 7 Checks

**Date:** 20 February 2026
**Type:** Architecture
**Generation:** GEN 3

Exit gate expanded to 7 checks. EG-007 checks text centering in boxes. Inline centering rule (Rule 11): every SVG must include inline style for display block and margin auto.

**Principle:** Exit gates catch what generation-time rules miss. No SVG leaves the engine without passing structural checks.

**Tags:** Gen 3, Create-Images, Exit Gate, Centering

---

## v2.0.19 — Hero Skip Prevention: Image Scan Summary Gate

**Date:** 11 February 2026
**Type:** Architecture
**Generation:** GEN 3

When an article has existing inline SVGs from a previous draft, the agent was skipping hero SVG generation. Added Image Scan Summary gate to explicitly confirm hero status.

**Principle:** Explicit status checks prevent implicit assumptions. Make the agent state what it found.

**Tags:** Gen 3, Create-Images, Hero, Gate

---

## v2.0.17 to v2.0.18 — Hero Production Hardening: From 12 Iterations to 10 Rules

**Date:** 11 February 2026
**Type:** Architecture
**Generation:** GEN 3

Hero SVGs required 12 iterations to get right. Extracted 10 production rules including fill requirements, global centering, edge-based arrows, and label scale minimums.

**Principle:** When you iterate 12 times on the same type, extract the pattern. Rules prevent repeat debugging.

**Tags:** Gen 3, Create-Images, Hero, Rules

---

## Content at x=2, Text at x=30

**Date:** 10 February 2026
**Type:** Fix
**Generation:** GEN 3

Template H figures were left-aligned with the article body text. Content starts at x=2 and text at x=30 inside the SVG. Inline styles were applied to four elements: the figure, the SVG, the source line and the caption. Each element carries its own alignment rather than inheriting it. The whole block lands on one left edge.

**Principle:** Give the figure the same left edge as the body text.

**Tags:** Gen 3, Create-Images, Fix

---

## SVG Every Time, the Prompt Kept as an Escape Hatch

**Date:** 10 February 2026
**Type:** Decision
**Generation:** GEN 3

Hero VIPs always get a generated SVG now. Routing no longer chooses between the deterministic path and a generative one. The generative image prompt is still written into the output, kept as an optional manual artifact. The tool selection matrix was updated to match. One default, one escape hatch, and no per-run decision.

**Principle:** Make the deterministic path the default and keep the generative one as an artifact.

**Tags:** Gen 3, Create-Images, Decision

---

## v2.0.14 to v2.0.16 — Font Scale Rule + Source Attribution Journey

**Date:** 10 February 2026
**Type:** Fix
**Generation:** GEN 3

All templates wider than 540px must scale fonts by viewBox_width/540. Applied to templates A, I, I-L, M, N. Spacing scale rule: title-to-box gap also scales. Source attribution moved through three approaches before settling on HTML.

**Principle:** Test architectural decisions across all variants. What works for centered templates fails for left-aligned ones.

**Tags:** Gen 3, Create-Images, Templates, Typography

---

## v2.0.11 — Visual Perception Rules: The LLM Generates Numbers, the Human Sees Shapes

**Date:** 10 February 2026
**Type:** Architecture
**Generation:** GEN 3

LLMs place SVG elements at mathematically correct coordinates, but the visual output looks wrong. Built 7 core perception rules: visibility floor, clearance principle, arrow breathing room, connection clarity, visual weight balancing, label readability, and whitespace distribution.

**Principle:** The LLM generates numbers. The human sees shapes. Bridge the gap with explicit perception rules.

**Tags:** Gen 3, Create-Images, Perception, Architecture

---

## v2.0.5 to v2.0.10 — Template Production Hardening

**Date:** 5 February 2026
**Type:** Release
**Generation:** GEN 3

Six versions hardening SVG templates for production use. Template-specific fixes for alignment, spacing, and text overflow.

**Tags:** Gen 3, Create-Images, Templates

---

## A ViewBox Height Formula Replaces Ad Hoc Numbers

**Date:** 3 February 2026
**Type:** Fix
**Generation:** GEN 3

Four fixes landed together on 3 February 2026. A viewBox height formula replaced the ad hoc numbers. Arrow spacing became an explicit rule and text length got written guidelines. The golden example was corrected too, which matters because later templates are checked against it. All four are corrections to existing templates.

**Principle:** Fix the golden example first. Every later template gets checked against it.

**Tags:** Gen 3, Create-Images, Fix

---

## Hex Codes in a Prompt Render as Literal Text

**Date:** 1 February 2026
**Type:** Learning
**Generation:** GEN 3

PAT-017 got a font size auto-fix. ViewBox scaling compensation came with it, so a resized frame does not shrink text below the floor. The image-prompt guidelines picked up one rule: no hex codes in prompts. A hex code in the prompt renders as literal text inside the image rather than as a colour. It came out of a rendered failure.

**Principle:** Name colours in words when prompting an image model, never in hex.

**Tags:** Gen 3, Create-Images, Learning

---

## v2.0.0 — Engine Born from the Split

**Date:** 1 February 2026
**Type:** Release
**Generation:** GEN 3

Create-Images created as a separate engine from the context window split. Focused exclusively on SVG diagram and hero image generation.

**Principle:** Focused engines that do one thing well. Context pressure forces good architecture.

**Tags:** Gen 3, Create-Images, Architecture

---

## A Python Validator Before Any Model Judged the Image

**Date:** 31 January 2026
**Type:** Feature
**Generation:** GEN 3

The first Tier-1 validation script landed on 31 January 2026, the same day the engine's foundation shipped. It is Python with Pillow. The checks are mechanical. Open the image, measure it, pass or fail, with no model asked for a judgement. A deterministic floor arrived before any of the graded checks, which is the right order.

**Principle:** Build the mechanical check first. Model judgement is the layer above it.

**Tags:** Gen 3, Create-Images, Feature

---

## v2.0.23 to v2.0.25 — Prompt Fidelity Gate + Handoff Alignment

**Date:** 23 February to 2 March 2026
**Type:** Architecture
**Generation:** GEN 3

Three versions tightening the boundary between Create-Images and its neighbours. VIP Prompt Fidelity (v2.0.23, EG-008): exit gate now extracts named visual elements from VIP prompt text and verifies corresponding SVG elements exist. Rule Health Check (v2.0.24): cross-engine pipeline version sync. Handoff Alignment (v2.0.25): source attribution standardised to HTML everywhere per contract v1.2.

**Principle:** Contracts between engines need explicit, machine-enforceable rules. Implicit assumptions drift with every version bump.

**Tags:** Gen 3, Create-Images, Architecture, Exit Gate

---
