# Create-Compiler — Changelog

> Part of the [AI Marketing Operator Logs](../README.md) by [Hendry Soong](https://www.hendry.ai)
> Canonical source: [hendry.ai/ai-marketing/operator-logs](https://www.hendry.ai/ai-marketing/operator-logs/)

Article assembly pipeline with compile validator, review agent, and closed-loop feedback system.

---

## v1.3.1 to v1.3.2 — Episodic Memory + Voice Pattern Gate

**Date:** 23 February to 1 March 2026
**Type:** Architecture
**Generation:** GEN 3

Validator Expansion (v1.3.1): CV-012 (domain frequency) and CV-013 (citation specificity). Compile Validator at 13 checks. Voice Pattern Gate (v1.3.2, CV-014): deterministic PAT checks against all visible prose in compiled HTML. Runs PAT-001, PAT-002, PAT-004, PAT-013, and PAT-014.

**Principle:** Memory is infrastructure. Without structured review logs and retrieval conventions, the system cannot learn from its own history.

**Tags:** Gen 3, Create-Compiler, Validation, Memory

---

## v1.2.0 to v1.3.0 — The Feedback Loop: From Issue Detection to Closed-Loop Remediation

**Date:** 20 to 22 February 2026
**Type:** Architecture
**Generation:** GEN 3

Built the closed-loop feedback system. Compiler detects issues, classifies them through a 4-tier router, generates reverse manifests, and sends them back to upstream engines. Fix-forward-only banned.

**Principle:** Fix-forward-only creates drift between source and compiled. Every fix must flow back to the source.

**Tags:** Gen 3, Create-Compiler, Feedback, Architecture

---

## v1.1.0 — Quality Gate: Compile Validator + Review Agent + Episodic Memory

**Date:** 11 February 2026
**Type:** Architecture
**Generation:** GEN 3

Built the quality gate system: compile validator (deterministic checks), review agent (LLM-based fresh-eyes questions), and episodic memory (review logs for learning).

**Principle:** Validation-as-data. Review logs let the system prune its own rules with evidence, not guesswork.

**Tags:** Gen 3, Create-Compiler, Validation, Architecture

---

## v1.0.0 — Article Assembly Pipeline

**Date:** 5 February 2026
**Type:** Release
**Generation:** GEN 3

First release of the Compiler engine. Merges articles with images, validates the combined output.

**Principle:** Multi-engine pipelines need an explicit assembly step. Don't leave integration to chance.

**Tags:** Gen 3, Create-Compiler, Release

---
