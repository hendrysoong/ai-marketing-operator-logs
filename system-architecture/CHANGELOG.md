# System Architecture — Changelog

> Part of the [AI Marketing Operator Logs](../README.md) by [Hendry Soong](https://www.hendry.ai)
> Canonical source: [hendry.ai/ai-marketing/operator-logs](https://www.hendry.ai/ai-marketing/operator-logs/)

Cross-engine architecture decisions, audits, and workflow formalisation.

---

## Graph Engineering Goes in the Metadata, the Runtime Stays Cited

**Date:** 25 July 2026
**Type:** Decision
**Generation:** SYSTEM

Added Graph Engineering to llms.txt and Person.knowsAbout, bringing both topical surfaces to 44 aligned entries. The runtime tested for the work and control slice stayed out of both. Identity and topic-authority metadata carry the practice term. The specific runtime remains a cited implementation inside the articles. The build gate still held, so none of these bytes are live.

**Principle:** Put the practice term in identity metadata. Cite the runtime inside the article.

**Tags:** System, System, Decision

---

## Build Stalled at Five Minutes, So Nothing Shipped

**Date:** 24 July 2026
**Type:** Failure
**Generation:** SYSTEM

Four terms went into llms.txt and Person.knowsAbout, moving the Key Topics list from 39 to 43 entries. TypeScript passed. The production build printed its optimizing line, then sat silent for roughly five minutes and was interrupted at exit 130. The commit stayed local. A machine-readable claim guarantees nothing on its own, and neither term amendment is live.

**Principle:** No push without a terminal production build result. An interrupted build is not evidence.

**Tags:** System, System, Failure

---

## A 160-Char SEO Field Was Doing Duty as the Visible Deck

**Date:** 15 July 2026
**Type:** Decision
**Generation:** SYSTEM

The article template rendered seo.metaDescription as the visible subline under the H1. That field caps at 160 characters. It also feeds search, social and machine-readable surfaces. Added seriesLabel and subtitle as separate localized fields, with a fallback chain for older articles. Build Log 001 now carries its approved deck. Readback confirmed the 151-character meta description was untouched.

**Principle:** The visible deck and the SEO description are separate surfaces, so give them separate fields.

**Tags:** System, System, Decision

---

## 180 Guarded CMS Edits, and the Headline That Got Restored

**Date:** 14 July 2026
**Type:** Release
**Generation:** SYSTEM

One guarded Payload transaction made 180 edits across the homepage, ten articles and one media record. Code shipped first. Commit da82896 reached Vercel production READY before any content was written, and every write passed readback with a rollback proof. The pass had also rewritten the approved homepage H1. The owner rejected that, so a homepage-only transaction restored the exact prior line.

**Principle:** Framework alignment does not authorize rewriting first-person positioning claims without separate editorial approval.

**Tags:** System, System, Release

---

## 7 Typed Figure Components and the Deploy Before Migrate Rule

**Date:** 13 June 2026
**Type:** Architecture
**Generation:** SYSTEM

Built 7 typed spec-sheet figure components and migrated all 7 visuals on article 86 to Neon production. svgCode stayed in place so a revert is one line. The evaluated third-party design skill shipped zero code, since its bans fight an established identity. Ordering matters here. The live dispatcher must know a templateKey before the database references it, or the figure renders broken.

**Principle:** Deploy the component that reads a templateKey before the database starts referencing it.

**Tags:** System, System, Architecture

---

## The Engine Gate Scanned Bodies and Skipped Headings

**Date:** 7 June 2026
**Type:** Learning
**Generation:** SYSTEM

A definition article ran the full Create-Articles to Create-Images to Create-Compiler pipeline and went live as article 86. The adversarial verify pass caught a banned filler word in a section heading. The engine's own gate missed it because that gate scans body text and never reads the heading field. Two more majors and three minors were fixed in the same pass. Create-Compiler reported zero fatal and zero critical.

**Principle:** A validation gate only covers the fields it reads. Check what it skips.

**Tags:** System, System, Learning

---

## Left-Border Callouts on the Live Definition Page

**Date:** 7 June 2026
**Type:** Decision
**Generation:** SYSTEM

The generated SVGs on the live definition page read as machine made. Left border callouts sat on the stat cards and the pull quote, the documented number one anti-pattern. Captions restated their figures and the hero arrows were uneven. The hero moved to a typed layered component where grid alignment keeps the arrows even. Six restated captions came out.

**Principle:** Grid aligned components stop the drift that prompt tuning on SVGs keeps reintroducing.

**Tags:** System, System, Decision

---

## Our Own Figures Tripped Our Own Anti-Patterns

**Date:** 7 June 2026
**Type:** Learning
**Generation:** SYSTEM

The generated SVGs on the live AI-Native CMO page broke the brand's own rules. Left-border callouts, a hero-metric stat trio, six captions restating their figures, unequal hero arrows. Three design comps were built on the existing tokens, and the Swiss spec-sheet scored 9/8/9 with no hard bans. sanitizeHtmlFigure strips style tags, so class-based HTML cannot render. A typed figure component is the route.

**Principle:** Run the brand's anti-pattern list against your own generated output first.

**Tags:** System, System, Learning

---

## One Pattern, Four Surfaces

**Date:** 15 April to 6 June 2026
**Type:** Architecture
**Generation:** SYSTEM

The same architecture keeps showing up in my work. A connector that serves context a team reads but cannot edit. A self-serve editor where sales changes the copy on a brand-exact base but cannot touch the layout. A generator that injects verified facts so the model writes only the framing. One context source that many tools read. In each one, a few people author a controlled foundation and many people consume a safe surface. They get the leverage. They cannot corrupt the canon.

**Principle:** Do not hand out editable copies. Hand out a safe surface over one controlled foundation. Few authors, many consumers is the right shape for anything that has to stay consistent at scale.

**Tags:** System, Architecture, Pattern, Governance

---

## Context Connector: Install Once, Always Latest

**Date:** 5 June 2026
**Type:** Architecture
**Generation:** SYSTEM

I built a vendor-neutral context connector over MCP and shipped it to production in a day. It serves my curated context, voice rules and design rules, to any LLM through two tools: search and fetch. A team installs one URL. The content updates server-side, so nobody works from a stale copy. The usual smoke test was blocked in my harness, so I verified the protocol with in-process transport tests instead. That became permanent regression coverage, not a throwaway check. It works in Claude Code, Claude Desktop, ChatGPT, and Copilot Studio.

**Principle:** Serve context live from one source. Bundle it into a skill or hand out a file, and it starts drifting the moment it leaves your hands.

**Tags:** System, Architecture, MCP, Context

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

## The Last SVG Figure Moves to the Component Library

**Date:** 23 April 2026
**Type:** Architecture
**Generation:** SYSTEM

Build Log #1 section 7 flipped from a hand-authored SVG to the layered component. All three pilot visuals now render through the HTML figure library. The node type gained labeled zones and microcopy, so the substrate box can surface CONTEXT, CONTRACTS and STATE. svg_code stayed on both rows at 5,146 characters, so the revert is two UPDATE statements. A long-running em-dash voice violation left with the old caption.

**Principle:** Keep the old value on the row so a revert is two statements.

**Tags:** System, System, Architecture

---

## The Paragraph Warning About Aging Specifics Was Full of Them

**Date:** 20 April 2026
**Type:** Learning
**Generation:** SYSTEM

A section argued that paid-platform reporting specifics age badly, then named four of them. One was wrong on the day it was written. The attribution-window claim went stale when the platform dropped two options on 2026-01-12. The four-sentence prefix came out. The paragraph now opens on anchoring to first-party sources. Deep-dive count also corrected from 6 to 7 after an actual recount.

**Principle:** If the argument is that specifics age badly, do not ship the specifics.

**Tags:** System, System, Learning

---

## A Release Where No Article Renders Differently

**Date:** 20 April 2026
**Type:** Architecture
**Generation:** SYSTEM

Phase 1 of the HTML figures track shipped four columns, two enum values, a render branch, and a sanitiser. Nothing on the site changed. No article carried heroType html or visualType html yet, by design. The sanitiser mirrors sanitizeSvg. It strips script, iframe, form and foreignObject tags plus every on* handler. Tag pre-html-figures-v1.4.12-baseline was cut at the last pre-migration commit, so revert is one hard reset.

**Principle:** Ship the schema and the revert tag first, while nothing renders differently yet.

**Tags:** System, System, Architecture

---

## A 30 Second ISR Timer for SQL Edits That Never Landed

**Date:** 19 April 2026
**Type:** Fix
**Generation:** SYSTEM

Raw SQL edits to the article tables kept showing stale HTML on production. Two changes closed it. A POST /api/revalidate endpoint reuses PAYLOAD_SECRET as bearer auth and calls revalidatePath for each path sent. The article route also got a 30 second ISR timer, so database edits appear on production without a redeploy. Section 1 copy moved from replace to augment in the same pass.

**Principle:** Fix stale production reads at the cache layer, not with a manual purge each time.

**Tags:** System, System, Fix

---

## Four Edits, Five Gates, One Guarded Script

**Date:** 19 April 2026
**Type:** Decision
**Generation:** SYSTEM

Four targeted edits to Build Log #1 ran through a five gate sequence. Read and report, conflict resolution, delta on delta, dry run, execute. The owner resolved five conflicts inline. One script carried every mutation, with a signal string guard on each so a re-run fails loudly. The AST edits validated child counts before writing to the section table and its version mirror.

**Principle:** Guard each mutation with a signal string so a second run fails loudly.

**Tags:** System, System, Decision

---

## One Patch Script, Five Gates, Main and Version in Parity

**Date:** 19 April 2026
**Type:** Learning
**Generation:** SYSTEM

Four editorial edits to article 85 went in through a single idempotent script with signal-string anchors. The gates ran in order: read and report, conflict resolution, delta on delta, dry run, execute. Every write hit both the main table and the _v version table. The TLDR grew from 809 to 982 characters. It now leads with 30 to 35 percent net savings after QA and governance.

**Principle:** Run the edit through gates, then write main and version in the same pass.

**Tags:** System, System, Learning

---

## PAT-020: Every, Always, Never, All

**Date:** 19 April 2026
**Type:** Learning
**Generation:** SYSTEM

A full editorial pass closed Build Log #1 after nine inconsistencies surfaced in the audit. Absolute-certainty language came out of five paragraphs in S8. The rule went upstream into voice.md v7.0.11 as PAT-020, with a watch list for every, always, never and all. The exception holds when a number or a named mechanism makes the absolute provable. A second memo wrote down the database, CMS and revalidate workflow.

**Principle:** When an edit repeats across paragraphs, push the rule into the voice file.

**Tags:** System, System, Learning

---

## SQL Edits That Never Reached Production

**Date:** 19 April 2026
**Type:** Fix
**Generation:** SYSTEM

Direct SQL edits kept not surfacing on production. The permanent fix is one line: export const revalidate = 30 on the article page route. Pages now regenerate from the database every 30 seconds at most. No matter which path wrote the row. A POST /api/revalidate endpoint, bearer-authed off PAYLOAD_SECRET, handles the cases that need invalidation now.

**Principle:** Set the ISR window on the page, so any write path surfaces.

**Tags:** System, System, Fix

---

## Publish From Admin, Get a 404

**Date:** 18 to 19 April 2026
**Type:** Fix
**Generation:** SYSTEM

Articles published through the Payload admin UI returned 404 on the front end. Two fields tracked publication: Payload's own _status and a separate status field the queries read. The admin only set _status. A beforeChange hook now propagates _status published back to status. Build Log #1 ended the session unpublished, with TLDR, S9 and hero costs still out of sync.

**Principle:** Two fields for one state will drift. Sync them in the hook.

**Tags:** System, System, Fix

---

## 16 Opposite-Line Patterns in One Audit Pass

**Date:** 18 April 2026
**Type:** Learning
**Generation:** SYSTEM

A single audit pass found 16 opposite-line patterns in Build Log #1, spread across eight sections. Four of them sat inside inline link text. That volume is what LLM drafting produces by default. The same pass cut a 71 percent CMO statistic with no tier one source behind it. Eleven em dashes went too. The article published from the admin panel that night.

**Principle:** Opposite-line phrasing is default model output. Audit for it, do not spot fix.

**Tags:** System, System, Learning

---

## 32 Violations in the First Draft of Build Log #1

**Date:** 16 April 2026
**Type:** Decision
**Generation:** SYSTEM

Build Log #1 was restructured into a nine section narrative arc. Every edit went through the Payload Local API instead of raw SQL, which handles the version tables without manual sync. The first draft failed a voice audit with 32 violations. Eighteen were paragraph length, six were opposite lines, five were em dashes. The second draft cleared all of them.

**Principle:** Write through the CMS API so the version tables stay in sync automatically.

**Tags:** System, System, Decision

---

## revalidatePath Needed a Type Hint Under [locale]

**Date:** 15 April 2026
**Type:** Fix
**Generation:** SYSTEM

CMS edits stopped showing on production. Under a dynamic [locale] segment, Next.js 16 wants revalidatePath called with an explicit type. 'page' for article routes, 'layout' for the root so it cascades. Without the hint the call runs and purges nothing. Console logs were added to the hooks so Vercel logs show each path. A separate error was simpler: seoFields.ts caps metaTitle at 60 characters, and the title was 75.

**Principle:** Next.js 16 revalidatePath needs an explicit page or layout type under dynamic segments.

**Tags:** System, System, Fix

---

## The SDK Only Reads a Hero File for heroType vip

**Date:** 15 April 2026
**Type:** Learning
**Generation:** SYSTEM

The pipeline ran end to end for the first time. It produced Build Log #1 as draft article 85, with 9 sections and 6 FAQ. Two SDK contract details surfaced only at publish time. Keywords must arrive as objects with a keyword field. heroSvg is auto-read from file for heroType vip alone, so an svg hero must be inlined. The hand-made hero failed spec checks and was deferred.

**Principle:** Publish-time contract details only show up at publish time. Run the whole path once.

**Tags:** System, System, Learning

---

## Stale Counts on Five Live Surfaces

**Date:** 15 April 2026
**Type:** Fix
**Generation:** SYSTEM

Counts had drifted across five live surfaces. The Engines table, hero SVG, Deep Dives, Key Principles and FAQ each carried a different number. BASELINE.md holds the agreed figures, so all five were reconciled against it in one pass. Three planned engines went into TerminalOverview and the engineLayerMap. The hero SVG was brought onto the same figure as the other four surfaces.

**Principle:** Keep one baseline file for shared counts and reconcile every surface from it.

**Tags:** System, System, Fix

---

## 19 Entries Live, Metadata Still Said Six Engines

**Date:** 14 April 2026
**Type:** Fix
**Generation:** SYSTEM

19 new operator log entries went into the database and all 19 rendered live. The surrounding metadata had not moved. A count audit gave 106 entries, 7 engines, 93 principles and 6 deep dives. TLDR, meta description, hero alt and FAQ answers were rewritten. Lexical bodies were edited by casting JSONB to text, replacing, then casting back. Direct SQL skips afterChange revalidation, so a redeploy followed.

**Principle:** Direct SQL writes bypass the CMS revalidation hooks. Redeploy or the page stays stale.

**Tags:** System, System, Fix

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

## The Gate Opens When Its Env Var Is Missing

**Date:** 13 April 2026
**Type:** Feature
**Generation:** SYSTEM

The /os staging dashboard got a server-side gate. A server action checks the submitted value against an environment variable, then sets an httpOnly cookie scoped to /os, 7-day expiry. Auth is checked before render, so dashboard content never reaches an unauthenticated client. With the variable unset, the page renders open. That is deliberate, and it puts the risk on deploy config.

**Principle:** Check auth on the server before render, so gated content never ships to the client.

**Tags:** System, System, Feature

---

## Substrate Architecture: Six Repos Replace Three Chat Windows

**Date:** 7 to 8 April 2026
**Type:** Architecture
**Generation:** SYSTEM

Replaced three isolated AI chat windows with a six-repo substrate — versioned markdown in git, not conversation history. Three design principles: isolation prevents synthesis errors, discovery requires freedom from preconception, slots are earned not assigned. Three-state model for tracking drift: assumed state (framework spec), spec state (engine design), actual state (production code). Seven spec versions in two days.

**Principle:** Conversation history is not version control. When three chat windows carry the system state, every session starts with a manual sync that drifts silently.

**Tags:** System, Architecture, Substrate, Infrastructure

---

## Two Days of Broken Preview From One Trailing Newline

**Date:** 7 April 2026
**Type:** Fix
**Generation:** SYSTEM

The CMS admin preview button failed on production for two days. PREVIEW_SECRET had been piped into the Vercel CLI with echo, which appends a newline. Every token comparison came back false. printf sets it cleanly, and.trim() went in as a guard. Two other faults sat underneath. The preview URL resolved to localhost, and the draft query enforced access control with no session.

**Principle:** Use printf when piping a secret to a CLI. echo appends a newline.

**Tags:** System, System, Fix

---

## 20 Hex Values Mapped to CSS Variables at Runtime

**Date:** 7 April 2026
**Type:** Architecture
**Generation:** SYSTEM

Hardcoded hex fills in SVGs looked wrong in dark mode. The image engine now emits CSS custom properties, and all 15 templates moved over at 269 replacements. Older SVGs sitting in the database get a runtime fallback. themeAdaptSvg rewrites 20 hex values to variables on the way to the page. The mental model article picked it up first, one hero plus six section visuals.

**Principle:** Emit tokens from the generator and keep a runtime fallback for the old rows.

**Tags:** System, System, Architecture

---

## First Agentic Article Pipeline: Engine to CMS in One Session

**Date:** 6 to 7 April 2026
**Type:** Architecture
**Generation:** SYSTEM

Built a publishing SDK — engine generates article as JSON, SDK pushes to headless CMS via API. First full run: article from content brief through 6-phase pipeline, 3 revision passes, 5 SVGs, to CMS draft in one session. Two bugs discovered and fixed.

**Principle:** The first automated pipeline run reveals every assumption the manual process hid. Ship the pipeline, then fix what it exposes.

**Tags:** System, Architecture, Pipeline, Publishing

---

## The Agent Role Can Create Drafts and Nothing Else

**Date:** 6 April 2026
**Type:** Architecture
**Generation:** SYSTEM

Convention said the engine SDK defaults to draft. A beforeChange hook now enforces it: the agent role throws if status is published or archived. Recount hooks also stopped losing removals. Both take the union of current and previous topic or source IDs from previousDoc, so a detached item gets decremented. The source hook gained a published-only filter, which drafts had been inflating. llms.txt and schemamap moved to limit: 0.

**Principle:** Put the publish gate in a hook, so convention cannot be bypassed.

**Tags:** System, System, Architecture

---

## Four Fixes Re-Checked by a Fresh Session, Zero Discrepancies

**Date:** 6 April 2026
**Type:** Fix
**Generation:** SYSTEM

The session that wrote the audit fixes did not get to certify them. A fresh session re-inspected all four and traced the pipeline: 12 block types, 22 render paths, 8 hooks, 7 API routes. Zero discrepancies. It then closed a gap the first pass missed. beforeDelete hooks on Articles and Media throw for the agent role now, matching the publish gate. Three date spans became time elements.

**Principle:** Let a fresh session certify the fixes the previous session wrote.

**Tags:** System, System, Fix

---

## A 528-Line Contract Generated From the Schema

**Date:** 6 April 2026
**Type:** Architecture
**Generation:** SYSTEM

Engines and CMS live in separate repos, so the field contract between them drifts. payload-contract.md is now generated from CMS source. 528 lines cover 43 top-level fields, 6 Lexical blocks, agent permissions and 7 API routes. 74 contract fields were checked against Articles.ts and matched at 100 percent. Engines read the generated contract. It is regenerated whenever the schema changes.

**Principle:** Generate the cross-repo contract from source, so it cannot drift from the schema.

**Tags:** System, System, Architecture

---

## Hero VIP Throws, Inline VIP Warns

**Date:** 6 April 2026
**Type:** Fix
**Generation:** SYSTEM

A cross-repo audit of the engine to CMS flow turned up 6 alignment issues. Three were validation gaps. contentProfile was never in validateRequiredFields, so an article could publish with no quality thresholds. Articles.sections got required: true and minRows: 1, since a zero-section article is never valid. A missing hero SVG under heroType vip now throws. Inline VIPs still warn, because hero is declared mandatory in the visual plan.

**Principle:** Fail loud on the mandatory asset, warn on the optional one.

**Tags:** System, System, Fix

---

## Two Catch Blocks That Swallowed Every Error

**Date:** 6 April 2026
**Type:** Fix
**Generation:** SYSTEM

A fresh-session audit across 9 areas found 0 blockers and 3 warnings. Two shared a shape. The topic recount catch at Articles.ts:956 and the source recount at :1009 swallowed every error silently. Both now log with console.warn, plus the offending ID and the error object. Warn level was chosen because a deleted topic is the usual cause. A real DB failure still surfaces.

**Principle:** A catch block with no log is a bug you will never see.

**Tags:** System, System, Fix

---

## Hero VIP Downgraded to None Instead of Failing

**Date:** 6 April 2026
**Type:** Fix
**Generation:** SYSTEM

The engine to CMS contract had two quiet failure paths. A publish call with no contentProfile went through. A hero marked VIP with a missing SVG silently downgraded to heroType none. The article shipped with no hero and no error. Both now throw. The sections array on Articles also became required with minRows 1.

**Principle:** A contract that degrades quietly ships broken output. Make it throw.

**Tags:** System, System, Fix

---

## 6 Gaps Found After the Second Pipeline Run

**Date:** 6 April 2026
**Type:** Fix
**Generation:** SYSTEM

A post-mortem on the second agentic publish run turned up six gaps across the two repos. Section VIP SVGs were not uploading to the Media collection the way hero images did. Hero resolution now runs before section mapping. Section mapping went async through Promise.all, and dry-run output gained an inline SVG count. tsx moved into devDependencies, where it had only been transitive.

**Principle:** After a pipeline run, check what the hero path does that sections do not.

**Tags:** System, System, Fix

---

## One Command to Publish an Article

**Date:** 6 April 2026
**Type:** Feature
**Generation:** SYSTEM

The second agentic run got a one-command CLI. npm run engine:publish takes a path to article JSON, with a dry-run variant alongside. The admin preview button carried no token, so it now appends PREVIEW_SECRET. publishFromJson warns when that env var is missing. An engineCredit option writes the full pipeline credit string, and article 81 landed as a draft at 2850 words.

**Principle:** A preview URL without its token is a broken button. Append the secret.

**Tags:** System, System, Feature

---

## GA4 Renders Only When GTM Is Empty

**Date:** 6 April 2026
**Type:** Feature
**Generation:** SYSTEM

Added a ga4MeasurementId field on the SiteSettings global for sites running GA4 without a tag manager. The gtag.js snippet in layout renders only when GA4 is set and GTM is empty. The two never double-count. Preconnect hints go out conditionally for whichever origin is in play. Small change, but the guard is the part worth keeping.

**Principle:** Gate the second analytics snippet on the first being absent.

**Tags:** System, System, Feature

---

## The Agent Role Cannot Publish or Delete

**Date:** Before 6 April 2026
**Type:** Architecture
**Generation:** SYSTEM

Before the first agentic run, the agent role was fenced in. A beforeChange hook holds it to drafts, so it cannot publish or archive. beforeDelete hooks on Articles and Media block deletion outright. Separately, llms.txt and schemamap query limits went from 200 and 500 to 0. The source recount hook also started filtering on published status.

**Principle:** Fence the agent role to drafts before the first unattended run.

**Tags:** System, System, Architecture

---

## next/image Needs the Blob Hostname in remotePatterns

**Date:** Before 6 April 2026
**Type:** Learning
**Generation:** SYSTEM

All three raw img tags in ArticlePage were swapped for the Next Image component. Images hosted on Vercel Blob then failed. The blob hostname had to go into remotePatterns in next.config.js. The optimizer refuses any remote host it has not been told about. Hero images in fill mode also needed a wrapper,.featured-image-wrap, with position relative and a 16/9 aspect ratio.

**Principle:** The image optimizer only trusts hosts you list. Add the blob hostname.

**Tags:** System, System, Learning

---

## Headless Native: Legacy CMS to Headless CMS

**Date:** 5 to 6 April 2026
**Type:** Architecture
**Generation:** SYSTEM

All three production engines migrated from legacy CMS HTML fragments to headless CMS with rich text AST. CMS built from scratch over 80+ sessions. Create-Compiler changed from HTML page assembler to field validator — 22 checks replacing the old system.

**Principle:** Moving to headless didn't just change the output format. It changed what each engine is responsible for.

**Tags:** System, Architecture, Headless, CMS

---

## Pipeline Orchestration Spec

**Date:** 6 April 2026
**Type:** Architecture
**Generation:** SYSTEM

Documented the full two-repo pipeline flow. Covers: repo layout, pipeline sequence, handoff formats, publishing SDK transformations, environment requirements, failure modes, cross-repo commit rules.

**Principle:** Document the pipeline before automating it. Cross-repo flows need a single spec both sides can reference.

**Tags:** System, Architecture, Pipeline, Documentation

---

## 14 Node Types and 14 Gaps Before Any Integration Code

**Date:** 5 April 2026
**Type:** Learning
**Generation:** SYSTEM

Before upgrading the engines from WordPress HTML to native CMS output, one session did nothing but read. It produced two reference documents. One covers CMS architecture. The other documents all 14 Lexical node types, formatting bitmasks, and JWT auth for the agent role. The same pass listed 14 gaps: no agent user existed yet, firstUsed never auto-populated, no HTML-to-Lexical converter.

**Principle:** Read the target system and write the contract before writing any integration code.

**Tags:** System, System, Learning

---

## limit: 100 Meant Article 101 Returned 404

**Date:** 5 April 2026
**Type:** Fix
**Generation:** SYSTEM

generateStaticParams was capped at limit: 100, so article 101 and everything after it 404'd on first visit. Payload reads limit: 0 as no limit. The same session rebuilt PromptExample as a terminal block and added a beforeChange guard against publishing under a draft parent. A 22-check verification suite ran: 21 passed, one skipped. The schema was locked for engine sync.

**Principle:** A pagination cap you set once becomes a 404 at record 101.

**Tags:** System, System, Fix

---

## Security Review: What an AI Agent Finds vs What Matters

**Date:** 3 April 2026
**Type:** Learning
**Generation:** SYSTEM

Ran automated security review against CMS codebase. Agent flagged preview auth, missing security headers, SVG injection surface, and no rate limiting. Fixed all four in one session. The deeper learning: agent found real vulnerabilities but couldn't assess business risk.

**Principle:** Automated security review finds real issues but can't assess business risk. The operator's job is triage.

**Tags:** System, Security, Learning

---

## The Markers Array Drifted From the Text Array

**Date:** 1 April 2026
**Type:** Fix
**Generation:** SYSTEM

Localisation shipped across English, German and Polish. Payload field-level locales, next-intl routing, and a Lexical AST walker that swaps text nodes in place. The walker kept two arrays, markers and extracted texts. Body nodes reached the text array without a matching marker, so indices drifted and headings received body translations. The framework article covers 427 strings. Analytics scripts moved off the critical path, 151 KiB.

**Principle:** Parallel index arrays drift. Push to both or push to neither.

**Tags:** System, System, Fix

---

## Site Launch: 60+ Issues in 3 Days

**Date:** 29 to 31 March 2026
**Type:** Architecture
**Generation:** SYSTEM

Full launch preparation across 3 days. Performance optimization, analytics stack, mobile responsiveness, AI-SEO audit, broken link audit (17 internal links fixed), domain migration. Analytics SDK defaults were killing mobile performance.

**Principle:** Launch preparation is a compression event — it surfaces every issue the development phase deferred.

**Tags:** System, Architecture, Launch, Performance

---

## Content Migration: Every Article is a Schema Stress Test

**Date:** 14 to 27 March 2026
**Type:** Architecture
**Generation:** SYSTEM

Migrated 20+ articles from legacy CMS to headless CMS. Built per-article seed scripts. Each migration surfaced schema gaps: proficiency level, software application entity, video embed block, topic taxonomy.

**Principle:** Migrate real content early. Speculative schema design misses every edge case that actual articles expose.

**Tags:** System, Architecture, Migration, Schema

---

## Payload's _status Did Not Follow draft: false

**Date:** 24 March 2026
**Type:** Architecture
**Generation:** SYSTEM

The definitions pillar went live on 24 March. A new AutoContent collection holds versioned generated blocks, and its beforeChange hook archives the previous live record. DefinitionIndex lists published children of a pillar alphabetically, so new definitions appear without an edit. Published queries were normalized onto the custom status field. Payload's _status does not reliably follow a seed script's draft: false.

**Principle:** Query the status field your seed scripts set, since versioning fields drift.

**Tags:** System, System, Architecture

---

## One FAQ, Two Places in the Brief

**Date:** 20 March 2026
**Type:** Learning
**Generation:** SYSTEM

A QA pass on one operator log found the FAQ rendered twice. The brief had put it in the sections array and in the structured faq field. The explore feed was wrong for a different reason. Topic assignments had gone to a path the schema does not have, leaving orphaned rows. Four operator-log topics were created and written to seo.topics. FAQ is never a body section.

**Principle:** The FAQ belongs in its own field, never in the body sections.

**Tags:** System, System, Learning

---

## Ten Audit Dimensions, Six Findings, One Left Open

**Date:** 18 March 2026
**Type:** Learning
**Generation:** SYSTEM

A build audit ran the site against current Payload and Next.js docs across ten dimensions. Six findings came back. Feed and sitemap queries dropped from depth 4 to depth 3 and gained select projections. Three-level nesting is the deepest, so 3 is the safe minimum. Schemamap stayed at depth 4 because its schema builders need the full article. next/image was flagged high priority and deferred.

**Principle:** Pick the lowest query depth the deepest nesting allows, then justify the exceptions.

**Tags:** System, System, Learning

---

## Voice Centralisation + Cross-Engine Path Audit

**Date:** 17 March 2026
**Type:** Architecture
**Generation:** SYSTEM

Voice rules moved to shared context directory. Per-engine copies replaced with redirect stubs. 50+ files checked, zero broken references.

**Principle:** Centralise context once. When the same file lives in 3 engines, it diverges in 3 directions.

**Tags:** System, Architecture, Voice, Context

---

## CMS Architecture: Built From Scratch in 30 Sessions

**Date:** 5 to 14 March 2026
**Type:** Architecture
**Generation:** SYSTEM

Built entire headless CMS frontend from zero. Article template iterated 3 times. Pillar page template iterated 3 times. Hero visual system, nested routing, CMS-managed redirects, structured log entry data model, topic taxonomy.

**Principle:** Article templates needed 3 iterations because each was driven by migrating real content, not by speculative design.

**Tags:** System, Architecture, CMS, Headless

---

## Three Schema Fields Deleted After Rendering Proved Them Dead

**Date:** 13 March 2026
**Type:** Decision
**Generation:** SYSTEM

An audit of every article showed templateType, exploreLinks and exploreTopicGroup were never read by any renderer. Layout and contentProfile already drove those decisions. All three were dropped from the collection, four seed scripts, the types, and the database. The same pass filled meta titles, canonicals, keywords and 7 mentions on the AI Marketing pillar from the old JSON-LD.

**Principle:** Delete the field once you have proved that no renderer reads it.

**Tags:** System, System, Decision

---

## Four Pages Compared Line by Line Against the Old JSON-LD

**Date:** 13 March 2026
**Type:** Fix
**Generation:** SYSTEM

Staging JSON-LD was compared against the WordPress original on four pages: homepage, strategy, the AI Marketing pillar, and framework. Seven gaps came out. Headline now reads seo.metaTitle, so short pillar titles stop truncating. A definedTerms array feeds DefinedTerm entities into the graph, six on framework and three on the pillar. Nested articles now list their parent in isPartOf.

**Principle:** Compare the new page's structured data against the old page's, field by field.

**Tags:** System, System, Fix

---

## Two Root Causes Under One Broken Code Block

**Date:** 10 March 2026
**Type:** Fix
**Generation:** SYSTEM

Code blocks had been broken for several sessions. Two causes turned up together. lexicalEditor({}) does not include CodeBlock in its default features, so nothing registered the node. The seed helper also emitted a native Lexical code node where Payload expects type block with fields.blockType. Every seed script had to change. A table CSS regression surfaced in the same pass.

**Principle:** Check the editor's block format before assuming the native node is right.

**Tags:** System, System, Fix

---

## Context Centralisation + ORCHESTRATOR v1.3

**Date:** 8 March 2026
**Type:** Architecture
**Generation:** SYSTEM

Context files moved from per-engine directories to shared context. ICP enriched with social platform persona data. Context manifest added.

**Principle:** Shared context files need one canonical location. Per-engine copies drift with every version bump.

**Tags:** System, Architecture, Context, Orchestration

---

## The CLI Wanted a Full Recreation, So the SQL Went Direct

**Date:** 7 March 2026
**Type:** Feature
**Generation:** SYSTEM

Parts A to F of the schema handoff shipped in one session. Shared seoFields, article JSON-LD on a five-node graph, the public article route, RSS, a schemamap endpoint and a branded 404. The database migration went around the CMS CLI, which wanted a full recreation and interactive prompts. Direct SQL added the columns to four tables instead. Sixteen files, two commits.

**Principle:** When the CMS migration tool insists on recreation, write the SQL yourself.

**Tags:** System, System, Feature

---

## 78 Percent on the AI SEO Audit

**Date:** 7 March 2026
**Type:** Learning
**Generation:** SYSTEM

Two background agents ran in parallel on 7 March. One researched 2026 AI SEO standards, the other audited all 14 SEO files against the rules doc. Merging both gave a 78 percent score and a P0/P1/P2 gap list. The P0 fixes touched four files. Article became TechArticle, proficiencyLevel now derives from contentProfile, and reading time lands at 238 wpm.

**Principle:** Run research and implementation audit in parallel, then merge into one priority list.

**Tags:** System, System, Learning

---

## proficiencyLevel Was Hardcoded Expert on Every Article

**Date:** 7 March 2026
**Type:** Fix
**Generation:** SYSTEM

Article JSON-LD moved to TechArticle. proficiencyLevel now derives from contentProfile instead of the hardcoded Expert string every article carried. The about array comes from topics. isPartOf now points at a CollectionPage entity rather than a bare WebSite reference. Twitter cards gained reading-time labels calculated from wordCount at 238 words per minute. Article pages got a real main wrapper.

**Principle:** A hardcoded schema value looks correct in the markup and describes only one article.

**Tags:** System, System, Fix

---

## One seoFields Config, Three Collections

**Date:** 7 March 2026
**Type:** Architecture
**Generation:** SYSTEM

One seoFields config now defines the nine SEO fields. Articles, Pages and the Homepage global all import it. Article pages compose a JSON-LD graph: Article, Breadcrumb, Person, Organization, WebSite and an optional FAQPage. Two endpoints ship with it. /feed.xml caches for an hour, /schemamap for 24. This replaced the WordPress SEO plugin on article pages.

**Principle:** Define the shared field group once and import it into every collection that needs it.

**Tags:** System, System, Architecture

---

## 56KB of Frontend Source in One Handoff Document

**Date:** 6 March 2026
**Type:** Decision
**Generation:** SYSTEM

Design iteration moved to a chat UI, implementation stayed in the coding agent. docs/site-context.md bundles the whole frontend into one document, 56KB and 2550 lines. Every file sits under its own path header, inside a fenced code block with a language tag. An architecture brief and a starter prompt went with it. The zip of the same source was deleted in favour of plain text. No version bump.

**Principle:** Hand off the whole source as text when the other tool cannot read the repo.

**Tags:** System, System, Decision

---

## Two Files Hardcoded noindex and Beat robots.ts

**Date:** 5 March 2026
**Type:** Fix
**Generation:** SYSTEM

The site's SEO layer was rebuilt natively to drop the legacy plugin. First a conflict had to go. layout.tsx and generateMeta.ts both hardcoded noindex and nofollow, which overrode robots.ts on every page. An isProduction() helper made the metadata environment-aware instead. On top of that went a six-builder JSON-LD schema system and crawler rules for four AI bots. A hidden seven-field AI summary and a dynamic llms.txt shipped with them.

**Principle:** Robots directives belong in one file. Two sources means the wrong one wins.

**Tags:** System, System, Fix

---

## Two Files Hardcoded noindex Over robots.ts

**Date:** 5 March 2026
**Type:** Fix
**Generation:** SYSTEM

robots.ts said one thing and production said another. Both layout.tsx and generateMeta.ts hardcoded noindex, nofollow. The meta tag wins over the robots file, so production would have stayed out of the index whatever robots.ts said. The fix made robots environment-aware: index and follow in production, noindex on staging. The same release added a six-node JSON-LD graph and an llms.txt route.

**Principle:** A page-level robots meta tag overrides robots.ts. Grep for hardcoded noindex before launch.

**Tags:** System, System, Fix

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

## Four Documents Before the First Collection

**Date:** 27 to 28 February 2026
**Type:** Architecture
**Generation:** SYSTEM

The hendry.ai CMS started as four documents before any code. They covered the architecture brief, the legacy-to-Payload field mapping, the schema changes, and the build prompt itself. Six custom collections replaced the starter set. A Homepage global and seven frontend components followed, wired through the Local API. Two decisions held from that day: Homepage is a global, and no Tailwind anywhere.

**Principle:** Write the field mapping before the build, then let the build follow it.

**Tags:** System, System, Architecture

---

## Crawler Blocks Before the First Article

**Date:** 28 February 2026
**Type:** Decision
**Generation:** SYSTEM

The staging site went up on Vercel with crawler blocks already in place. robots.txt disallowed everything and the layout carried noindex and nofollow. Both were verified live before a single article existed. The blob storage plugin was made conditional on BLOB_READ_WRITE_TOKEN, so a missing token leaves the build working. Verification found six homepage sections rendering and one document behind /api/articles.

**Principle:** Block crawlers on day one of staging, before there is anything to index.

**Tags:** System, System, Decision

---

## A Draft Preview Route Before Anything Was Published

**Date:** 28 February 2026
**Type:** Feature
**Generation:** SYSTEM

Agents write articles as drafts through the API, and until now nobody could see one rendered. A /preview/articles/[slug] route fixes that. It pulls any article through the Local API with draft: true and depth: 2, which resolves the source relationships. The page renders in full site design behind a yellow DRAFT PREVIEW bar. The admin button builds absolute URLs via getServerSideURL().

**Principle:** Machine-written drafts need a rendered view before anyone can approve them.

**Tags:** System, System, Feature

---

## robots.txt Disallow All on the First Deploy

**Date:** 28 February 2026
**Type:** Release
**Generation:** SYSTEM

The new stack went live on Vercel while hendry.ai still ran on WordPress. Two copies of the same content would compete. The deploy shipped with robots.txt disallowing everything and a noindex, nofollow meta tag. Verified both before moving on. The repo is private, Blob storage is wired but waiting on a token, and no domain points at Vercel yet.

**Principle:** Block crawlers on a parallel build until the domain actually moves.

**Tags:** System, System, Release

---

## Six Collections, Two APIs, One Global

**Date:** 28 February 2026
**Type:** Architecture
**Generation:** SYSTEM

Phase one scaffold: Payload 3.78.0, Next.js 16, Neon Postgres. Six collections cover Articles, Pages, Topics, Sources, Media and Users. The frontend reads through the Local API with no HTTP hop, and agents get the REST API. Lexical stores content as a JSON AST instead of HTML. That is what later makes machine-written sections tractable. The homepage went in as a global rather than a Pages entry.

**Principle:** Pick the content shape first. A JSON AST lets agents write sections; HTML does not.

**Tags:** System, System, Architecture

---

## Cross-Engine Audit: 48 Checks, 43 PASS

**Date:** 23 February 2026
**Type:** Process
**Generation:** SYSTEM

Ran the first structured cross-engine audit covering Create-Articles, Create-Images, and Create-Compiler. 48 checks across 5 areas: contract compliance, version alignment, validation coverage, handoff integrity, and documentation currency. 43 PASS, 2 WARN, 3 FAIL. Failures were all documentation drift. Created backlog items. The audit framework itself is now a reusable checklist.

**Principle:** Audit the audit trail. Documentation debt compounds silently.

**Tags:** System, Process, Cross-Engine

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

## Agent Teams Validate the Framework

**Date:** 7 February 2026
**Type:** Architecture
**Generation:** SYSTEM

Ran a real-time stress test using Claude agent teams to produce articles, images, and compiled output simultaneously. The framework architecture (CLAUDE.md routing, integration contracts, shared registries) handled multi-agent coordination without modification. Problems surfaced were all engine-level, not architecture-level. The multi-engine pipeline design predicted Claude's agent teams feature before it shipped.

**Principle:** The agent is disposable. The orchestration layer is permanent.

**Tags:** System, Architecture, Agent Teams

---

## Three-Tool Workflow Split

**Date:** 7 February 2026
**Type:** Decision
**Generation:** SYSTEM

Formalised the separation between strategy and execution. Claude Projects handles strategy, planning, decisions, and reviews. Claude Code handles execution: build, validate, commit. GitHub is the single source of truth for all engine state. Nothing gets built or versioned in Claude Projects. Decisions made there become backlog items committed through Claude Code.

**Principle:** Separate strategy from execution. Different tools for different thinking modes.

**Tags:** System, Workflow, Decision

---
