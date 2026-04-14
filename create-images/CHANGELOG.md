# Create-Images — Changelog

> Part of the [AI Marketing Operator Logs](../README.md) by [Hendry Soong](https://www.hendry.ai)
> Canonical source: [hendry.ai/ai-marketing/operator-logs](https://www.hendry.ai/ai-marketing/operator-logs/)

SVG diagram and hero image generation with visual perception rules and an exit gate validation system. 30+ versions across three generations.

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

## v2.0.23 to v2.0.25 — Prompt Fidelity Gate + Handoff Alignment

**Date:** 23 February to 2 March 2026
**Type:** Architecture
**Generation:** GEN 3

Three versions tightening the boundary between Create-Images and its neighbours. VIP Prompt Fidelity (v2.0.23, EG-008): exit gate now extracts named visual elements from VIP prompt text and verifies corresponding SVG elements exist. Rule Health Check (v2.0.24): cross-engine pipeline version sync. Handoff Alignment (v2.0.25): source attribution standardised to HTML everywhere per contract v1.2.

**Principle:** Contracts between engines need explicit, machine-enforceable rules. Implicit assumptions drift with every version bump.

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

## v2.0.0 — Engine Born from the Split

**Date:** 1 February 2026
**Type:** Release
**Generation:** GEN 3

Create-Images created as a separate engine from the context window split. Focused exclusively on SVG diagram and hero image generation.

**Principle:** Focused engines that do one thing well. Context pressure forces good architecture.

**Tags:** Gen 3, Create-Images, Architecture

---
