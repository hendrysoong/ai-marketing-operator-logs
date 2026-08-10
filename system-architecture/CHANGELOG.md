# System Architecture — Changelog

> Part of the [AI Marketing Operator Logs](../README.md) by [Hendry Soong](https://www.hendry.ai)
> Canonical source: [hendry.ai/ai-marketing/operator-logs](https://www.hendry.ai/ai-marketing/operator-logs/)

Cross-engine architecture decisions, audits, and workflow formalisation.

---

## Context Connector: Install Once, Always Latest

**Date:** 5 June 2026
**Type:** Architecture
**Generation:** SYSTEM

I built a vendor-neutral context connector over MCP and shipped it to production in a day. It serves my curated context, voice rules and design rules, to any LLM through two tools: search and fetch. A team installs one URL. The content updates server-side, so nobody works from a stale copy. The usual smoke test was blocked in my harness, so I verified the protocol with in-process transport tests instead. That became permanent regression coverage, not a throwaway check. It works in Claude Code, Claude Desktop, ChatGPT, and Copilot Studio.

**Principle:** Serve context live from one source. Bundle it into a skill or hand out a file, and it starts drifting the moment it leaves your hands.

**Tags:** System, Architecture, MCP, Context

---

## One Pattern, Four Surfaces

**Date:** 15 April to 6 June 2026
**Type:** Architecture
**Generation:** SYSTEM

The same architecture keeps showing up in my work. A connector that serves context a team reads but cannot edit. A self-serve editor where sales changes the copy on a brand-exact base but cannot touch the layout. A generator that injects verified facts so the model writes only the framing. One context source that many tools read. In each one, a few people author a controlled foundation and many people consume a safe surface. They get the leverage. They cannot corrupt the canon.

**Principle:** Do not hand out editable copies. Hand out a safe surface over one controlled foundation. Few authors, many consumers is the right shape for anything that has to stay consistent at scale.

**Tags:** System, Architecture, Pattern, Governance

---

## Hardening the Agent Workspace: Downloads to Dev

**Date:** 31 May 2026
**Type:** Learning
**Generation:** SYSTEM

I moved 19 agent projects off a cloud-synced Downloads folder onto a dedicated dev workspace, one project per folder, each git-baselined. Downloads is an injection-prone, auto-syncing inbox, the wrong substrate for agents that read and write files. While hardening it I found something I had assumed away: the command sandbox and the file-tool permissions are separate layers. A file tool could still write into the SSH key directory even though the bash sandbox blocked it. I only found it by running the write that should have failed. I closed the gap with a permissions wall and a pre-tool hook, then re-ran the probe to confirm.

**Principle:** A configured guard is not an enforced one. The only proof a boundary holds is running the operation it should block.

**Tags:** System, Security, Learning

---

## Machine-Readable Positioning: 7 to 37 Topics

**Date:** 25 April 2026
**Type:** Feature
**Generation:** SYSTEM

I expanded the surfaces AI systems actually read, so they parse my positioning directly. The llms.txt key topics went from 7 to 37. Person.knowsAbout went from 14 to 37. I added Organization and WebSite schema, plus DefinedTerm entities for the concepts I want cited. AI-native describes how I work, agent-first and grounded by construction. My title stays AI Marketing Operator and Leader.

**Principle:** If you want AI systems to cite you for a topic, declare it in the surfaces they read. Treat llms.txt and schema as positioning, not plumbing.

**Tags:** System, Feature, Schema, AI-SEO

---

## Agent Website Building: Three Sites on Neon + Payload + Vercel

**Date:** 18 March to 14 April 2026
**Type:** Architecture
**Generation:** SYSTEM

Built three websites using AI agents on the same headless stack: Neon Postgres, Payload CMS, Vercel. hendry.ai took 80+ sessions — 20+ article migrations, structured data models, publishing SDK, i18n, search, analytics. growthsetting took 28 sessions — consulting site from scaffold to production. A client site took 24 sessions — built in the same headless stack, delivered as HubSpot HUBL templates. Same stack, different content complexity, 3x difference in time-to-live.

**Principle:** Time-to-live depends on content complexity, not stack complexity.

**Tags:** System, Architecture, Headless, CMS

---

## Listen Engine: Signal-to-Brief Pipeline Validated

**Date:** 8 to 14 April 2026
**Type:** Architecture
**Generation:** SYSTEM

First engine built on the substrate. Scaffolded discuss/build repo pair, then iterated from architecture redesign to live pipeline in 6 days across 20 commits. Signal-to-brief pipeline tested on real targets — 5 thought leaders yielded 83 ICP matches. Tested 8 source types: podcast transcripts scored highest signal density (70%), job scrapers failed for Swiss market coverage. Three-workflow architecture locked. 65-field marketing capabilities schema designed.

**Principle:** The first engine built on new infrastructure validates the infrastructure more than itself.

**Tags:** System, Architecture, Listen, Pipeline

---

## Substrate Architecture: Six Repos Replace Three Chat Windows

**Date:** 7 to 8 April 2026
**Type:** Architecture
**Generation:** SYSTEM

Replaced three isolated AI chat windows with a six-repo substrate — versioned markdown in git, not conversation history. Three design principles: isolation prevents synthesis errors, discovery requires freedom from preconception, slots are earned not assigned. Three-state model for tracking drift: assumed state (framework spec), spec state (engine design), actual state (production code). Seven spec versions in two days.

**Principle:** Conversation history is not version control. When three chat windows carry the system state, every session starts with a manual sync that drifts silently.

**Tags:** System, Architecture, Substrate, Infrastructure

---

## First Agentic Article Pipeline: Engine to CMS in One Session

**Date:** 6 to 7 April 2026
**Type:** Architecture
**Generation:** SYSTEM

Built a publishing SDK — engine generates article as JSON, SDK pushes to headless CMS via API. First full run: article from content brief through 6-phase pipeline, 3 revision passes, 5 SVGs, to CMS draft in one session. Two bugs discovered and fixed.

**Principle:** The first automated pipeline run reveals every assumption the manual process hid. Ship the pipeline, then fix what it exposes.

**Tags:** System, Architecture, Pipeline, Publishing

---

## Pipeline Orchestration Spec

**Date:** 6 April 2026
**Type:** Architecture
**Generation:** SYSTEM

Documented the full two-repo pipeline flow. Covers: repo layout, pipeline sequence, handoff formats, publishing SDK transformations, environment requirements, failure modes, cross-repo commit rules.

**Principle:** Document the pipeline before automating it. Cross-repo flows need a single spec both sides can reference.

**Tags:** System, Architecture, Pipeline, Documentation

---

## Headless Native: Legacy CMS to Headless CMS

**Date:** 5 to 6 April 2026
**Type:** Architecture
**Generation:** SYSTEM

All three production engines migrated from legacy CMS HTML fragments to headless CMS with rich text AST. CMS built from scratch over 80+ sessions. Create-Compiler changed from HTML page assembler to field validator — 22 checks replacing the old system.

**Principle:** Moving to headless didn't just change the output format. It changed what each engine is responsible for.

**Tags:** System, Architecture, Headless, CMS

---

## Security Review: What an AI Agent Finds vs What Matters

**Date:** 3 April 2026
**Type:** Learning
**Generation:** SYSTEM

Ran automated security review against CMS codebase. Agent flagged preview auth, missing security headers, SVG injection surface, and no rate limiting. Fixed all four in one session. The deeper learning: agent found real vulnerabilities but couldn't assess business risk.

**Principle:** Automated security review finds real issues but can't assess business risk. The operator's job is triage.

**Tags:** System, Security, Learning

---

## Site Launch: 60+ Issues in 3 Days

**Date:** 29 to 31 March 2026
**Type:** Architecture
**Generation:** SYSTEM

Full launch preparation across 3 days. Performance optimization, analytics stack, mobile responsiveness, AI-SEO audit, broken link audit (17 internal links fixed), domain migration. Analytics SDK defaults were killing mobile performance.

**Principle:** Launch preparation is a compression event — it surfaces every issue the development phase deferred.

**Tags:** System, Architecture, Launch, Performance

---

## Voice Centralisation + Cross-Engine Path Audit

**Date:** 17 March 2026
**Type:** Architecture
**Generation:** SYSTEM

Voice rules moved to shared context directory. Per-engine copies replaced with redirect stubs. 50+ files checked, zero broken references.

**Principle:** Centralise context once. When the same file lives in 3 engines, it diverges in 3 directions.

**Tags:** System, Architecture, Voice, Context

---

## Content Migration: Every Article is a Schema Stress Test

**Date:** 14 to 27 March 2026
**Type:** Architecture
**Generation:** SYSTEM

Migrated 20+ articles from legacy CMS to headless CMS. Built per-article seed scripts. Each migration surfaced schema gaps: proficiency level, software application entity, video embed block, topic taxonomy.

**Principle:** Migrate real content early. Speculative schema design misses every edge case that actual articles expose.

**Tags:** System, Architecture, Migration, Schema

---

## Context Centralisation + ORCHESTRATOR v1.3

**Date:** 8 March 2026
**Type:** Architecture
**Generation:** SYSTEM

Context files moved from per-engine directories to shared context. ICP enriched with social platform persona data. Context manifest added.

**Principle:** Shared context files need one canonical location. Per-engine copies drift with every version bump.

**Tags:** System, Architecture, Context, Orchestration

---

## CMS Architecture: Built From Scratch in 30 Sessions

**Date:** 5 to 14 March 2026
**Type:** Architecture
**Generation:** SYSTEM

Built entire headless CMS frontend from zero. Article template iterated 3 times. Pillar page template iterated 3 times. Hero visual system, nested routing, CMS-managed redirects, structured log entry data model, topic taxonomy.

**Principle:** Article templates needed 3 iterations because each was driven by migrating real content, not by speculative design.

**Tags:** System, Architecture, CMS, Headless

---

## Cross-Engine Version Sync: 30+ Stale References

**Date:** 2 to 3 March 2026
**Type:** Fix
**Generation:** SYSTEM

Meta-documentation version sync across 14 files. 21 cross-engine version refs updated. Ban "actually" added to Tier 1 banned words.

**Principle:** Version bumps are cross-engine operations. Grep all repos after every bump, not just the changed engine.

**Tags:** System, Fix, Version Sync

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
