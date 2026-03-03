# System Architecture — Changelog

> Part of the [AI Marketing Operator Logs](../README.md) by [Hendry Soong](https://www.hendry.ai)
> Canonical source: [hendry.ai/ai-marketing/operator-logs](https://www.hendry.ai/ai-marketing/operator-logs/)

Cross-engine architecture decisions, audits, and workflow formalisation.

---

## Cross-Boundary Audit: 31 Discrepancies Across 3 Engine Boundaries

**Date:** 2 March 2026
**Type:** Architecture
**Generation:** SYSTEM

Audited all three engine boundaries: Articles to Images, Images to Compiler, Compiler to Articles. Found 31+ discrepancies across contracts, examples, validation rules, and version references. Made 6 design decisions: source attribution in HTML everywhere, VIP ID required (was optional), compiler gate types aligned (BLOCKING for Tier 0/1, ROUTING for Tier 2+), deprecated post-compile-checks.md (zero unique checks remaining), preserved VIP ID in final compiled output, backlogged verification manifest emission. Root cause of most drift: version propagation across engines. Each version bump updates its own engine's files but misses cross-references in the other two engines' READMEs, pipeline diagrams, and dependency tables. 13 commits, approximately 4 hours.

**Principle:** Audit across engines, not within them. Cross-boundary drift is invisible from inside.

**Tags:** System, Architecture, Cross-Engine

---

## Cross-Engine Audit: 48 Checks, 43 PASS

**Date:** 23 February 2026
**Type:** Process
**Generation:** SYSTEM

Ran the first structured cross-engine audit covering Create-Articles, Create-Images, and Create-Compiler. 48 checks across 5 areas: contract compliance, version alignment, validation coverage, handoff integrity, and documentation currency. 43 PASS, 2 WARN, 3 FAIL. Failures were all documentation drift. Created backlog items. The audit framework itself is now a reusable checklist.

**Principle:** Audit the audit trail. Documentation debt compounds silently.

**Tags:** System, Process, Cross-Engine

---

## Agent Teams Validate the Framework

**Date:** 7 February 2026
**Type:** Architecture
**Generation:** SYSTEM

Ran a real-time stress test using Claude agent teams to produce articles, images, and compiled output simultaneously. The framework architecture (CLAUDE.md routing, integration contracts, shared registries) handled multi-agent coordination without modification. Problems surfaced were all engine-level, not architecture-level. The multi-engine pipeline design predicted Claude's agent teams feature before it shipped.

**Principle:** The agent is disposable. The orchestration layer is permanent.

**Tags:** System, Architecture, Agent Teams

---

## Source-of-Truth Audit

**Date:** 11 February 2026
**Type:** Process
**Generation:** SYSTEM

Audited every engine's README against actual file structure. Found 12 discrepancies: missing files, renamed files not updated in docs, deprecated features still listed. Fixed all 12. Root cause: READMEs treated as write-once documents. Now part of version bump checklist.

**Principle:** The problems come first, then the principles, then the product.

**Tags:** System, Process

---

## GitHub as Single Source of Truth

**Date:** 8 February 2026
**Type:** Architecture
**Generation:** SYSTEM

Formalised GitHub as the canonical location for all engine state. Claude Projects is strategy-only. Decisions made there become GitHub commits through Claude Code. No engine state lives in Claude Projects conversations. Version numbers, changelogs, backlogs, and system status all live in the repository.

**Tags:** System, Architecture

---

## Three-Tool Workflow Split

**Date:** 7 February 2026
**Type:** Decision
**Generation:** SYSTEM

Formalised the separation between strategy and execution. Claude Projects handles strategy, planning, decisions, and reviews. Claude Code handles execution: build, validate, commit. GitHub is the single source of truth for all engine state. Nothing gets built or versioned in Claude Projects. Decisions made there become backlog items committed through Claude Code.

**Principle:** Separate strategy from execution. Different tools for different thinking modes.

**Tags:** System, Workflow, Decision

---
