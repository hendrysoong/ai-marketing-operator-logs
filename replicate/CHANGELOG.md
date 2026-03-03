# Replicate — Changelog

> Part of the [AI Marketing Operator Logs](../README.md) by [Hendry Soong](https://www.hendry.ai)
> Canonical source: [hendry.ai/ai-marketing/operator-logs](https://www.hendry.ai/ai-marketing/operator-logs/)

Portability testing of AI marketing engines across multiple brands. Proved the architecture transfers with 80% universal, 20% brand-specific.

---

## Brand A v2.16 — Agents Interpret "Copy" as "Recreate Similar"

**Date:** January 2026
**Type:** Failure
**Generation:** REPLICATE

Workflow said "copy template to output folder." Agent rebuilt the template from memory instead of copying the file. Output had wrong CSS, missing elements. Changed instruction to explicit bash command: cp template.html output.html.

**Principle:** Agents interpret "copy" as "recreate similar." Force literal file operations.

**Tags:** Replicate, Brand A, LLM Behavior

---

## Brand A v3.0.1 — Slot-Based JSON Architecture (97% Output Reduction)

**Date:** January 2026
**Type:** Architecture
**Generation:** REPLICATE

Full HTML output was ~150KB. Every generation risked CSS corruption. Switched to slot-based architecture: agent outputs only JSON content (~5KB), assembly script merges with locked template. 97% output reduction.

**Principle:** Slot-based architectures eliminate CSS drift.

**Tags:** Replicate, Brand A, Architecture

---

## Brand B v3.0 — Self-Contained Templates with Embedded Assets

**Date:** January 2026
**Type:** Feature
**Generation:** REPLICATE

Demo failed because external font CDN was blocked. Embedded Inter font as base64 directly in template (~1.3MB but works offline). Template is now completely self-contained.

**Principle:** Self-contained templates eliminate external dependencies.

**Tags:** Replicate, Brand B, Templates

---

## Brand B v3.4 — Shell Compliance Validation

**Date:** January 2026
**Type:** Fix
**Generation:** REPLICATE

Agent changed shell HTML structure during content generation. Added compliance validation: shell HTML must match locked template exactly.

**Tags:** Replicate, Brand B, Validation

---

## Brand C v1.1 — Color Assumption Error

**Date:** January 2026
**Type:** Failure
**Generation:** REPLICATE

Built site design with assumed colors. Production site used different colors entirely. Fix: extract actual colors from live site.

**Principle:** Don't assume colors. Extract from actual site.

**Tags:** Replicate, Brand C, Failure

---

## Brand C v1.2 — Sites Use Multiple Font Families

**Date:** January 2026
**Type:** Learning
**Generation:** REPLICATE

Assumed one font family. Production site used four: Nunito (body), Cabin (nav), Roboto (labels), Montserrat (buttons). Typography extraction now includes font-by-purpose mapping.

**Principle:** Verify fonts against production output, not assumptions.

**Tags:** Replicate, Brand C, Typography

---

## Replicate v3.0 — Brand-Agnostic Base System

**Date:** 22 January 2026
**Type:** Release
**Generation:** REPLICATE

After three brand tests, extracted the portable core. Universal system = 80% (workflows, validation, templates). Brand-specific = 20% (voice, design tokens, ICP, shell HTML). New brand setup now takes ~40 minutes.

**Tags:** Replicate, Release, Architecture

---

## CSS Extraction is the Human Bottleneck

**Date:** January 2026
**Type:** Learning
**Generation:** REPLICATE

Attempted to automate design token extraction. Claude can't use browser dev tools. Automated CSS parsing misses computed styles, pseudo-selectors, and platform-specific patterns. CSS extraction remains the one manual step.

**Principle:** CSS extraction is the human bottleneck.

**Tags:** Replicate, Learning, CSS

---

## Listen-Competitors-Replicate — Configurable Comparison Entity

**Date:** January 2026
**Type:** Fork
**Generation:** REPLICATE

Forked Listen-Competitors for replication. Made the comparison entity configurable so any brand can use the same competitive intelligence workflow.

**Tags:** Replicate, Listen-Competitors, Fork

---
