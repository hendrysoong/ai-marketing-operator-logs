# Orchestrate — Changelog

> Part of the [AI Marketing Operator Logs](../README.md) by [Hendry Soong](https://www.hendry.ai)
> Canonical source: [hendry.ai/ai-marketing/operator-logs/orchestrate](https://www.hendry.ai/ai-marketing/operator-logs/orchestrate/)

Mirrored from the canonical page above, newest first.

---

## 29 Tracked Binaries, 4 Actually Referenced

**Date:** 10 August 2026
**Type:** Failure
**Generation:** SYSTEM

Of 29 tracked binaries, four are referenced by any prerendered page. The other 25 are linked from nothing. The count came out wrong twice, at 30 and then at 3, both times on the one filename with a space. Printing the sum caught both. The close gate runs none of the four commands the repo requires before a commit. A clean close is compatible with a red suite.

**Principle:** Print the intermediate sum. Re-reading the code found neither of the two miscounts.

**Tags:** System, System, Failure

---

## Three of Six Promoted Grades Were Wrong as Written

**Date:** 10 August 2026
**Type:** Learning
**Generation:** SYSTEM

Six of the ten readiness grades were promotions the prompt asserted and nobody re-derived. Re-deriving them found three wrong. Each had dropped a caveat that its own source record carried, which would have overclaimed in public. A required check then blocked four of the seven approved pull requests. The content gate runs inside the verify job, and all four edit content.

**Principle:** Re-derive an inherited grade before publishing it. The prompt is not the evidence.

**Tags:** System, System, Learning

---

## The Baseline Counted Characters, the Sweep Counted Bytes

**Date:** 9 August 2026
**Type:** Learning
**Generation:** SYSTEM

A live sweep said three derived surfaces had moved, by 22, 24 and 166. All three regenerate from the tracked tree byte-identical to what production serves. The baseline counted characters and the sweep counted UTF-8 bytes, so only the surfaces carrying multibyte typography appeared to change. The script that produced the baseline was never tracked. That is the third time an untracked check has been rebuilt differently.

**Principle:** An untracked check gets rebuilt differently, and the difference reads as a real change.

**Tags:** System, System, Learning

---

## One Action Added to permissions.json, Gated at human

**Date:** 9 August 2026
**Type:** Decision
**Generation:** SYSTEM

The owner said to add the action, without naming a decision level. Added as allow, the agent could enumerate the production database with no per-instance grant, which widens its own permissions. It went in at human with an owner-approval gate, so nothing the agent may do changed. Only what an envelope can express changed. permissions.json moved 1.0.0 to 1.1.0 and the suite stayed at 117/117.

**Principle:** The agent is the scribe. Deciding and typing are different acts.

**Tags:** System, System, Decision

---

## Zero Writes in 9.5 Hours, and a Freeze Gate With Two Halves

**Date:** 9 August 2026
**Type:** Learning
**Generation:** SYSTEM

A re-export of the live database produced the same manifest digest, 97b0a2eb, 9.5 hours later. Zero writes. The newest updated_at across all 43 articles is 2026-08-07, and both recent writes were the pipeline's own. That closed the historical half of the freeze gate. The other half is a promise about the future, and only the owner can make it.

**Principle:** Freeze the writes reads as one instruction. It is a measurement and a commitment.

**Tags:** System, System, Learning

---

## Eight Primitives Scored 0 to 3, With a README Capped at 1

**Date:** 9 August 2026
**Type:** Architecture
**Generation:** SYSTEM

The loop and graph audit scores every system 0 to 3 on eight primitives. Four cover the loop: trigger, verifier, stop condition, repair. Four cover the graph: state, control flow, human gates, write-back. Six evidence rules bind the scoring. A spec or README caps a score at 1. A file named evaluator.ts scores 0 until someone reads it.

**Principle:** A README caps the score at 1. Read the file before scoring what it is named.

**Tags:** System, System, Architecture

---

## A Six Hour Restore Window Behind a Snapshot With No Expiry

**Date:** 9 August 2026
**Type:** Learning
**Generation:** SYSTEM

The pre-cutover snapshot is a database branch forked from main, carrying all 54 tables. Point-in-time restore on the account reaches back 21600 seconds, six hours. That is shorter than the bake window, so the branch is the only rollback that survives the night. No expiry was set on it, deliberately. A snapshot that deletes itself on a timer disappears silently.

**Principle:** Check the retention window before calling a provider snapshot a rollback.

**Tags:** System, System, Learning

---

## Nine Closes Superseded Four Runs and Retired None

**Date:** 9 August 2026
**Type:** Failure
**Generation:** SYSTEM

The close gate asked for a superseded disposition and accepted a regex match on markdown prose. The waiting-run count came from the checkpointer. No code path ran between the two. Nine consecutive closes wrote a true sentence and none of them could ever have been the last. Retiring the four runs through a register took the stale failures from four to zero.

**Principle:** A gate whose satisfying artifact cannot reach the state it asks about generates paperwork.

**Tags:** System, System, Failure

---

## A Token 8h19m Old, Rejected

**Date:** 9 August 2026
**Type:** Architecture
**Generation:** SYSTEM

The agent's write token lives one hour. One that was 8h19m old came back rejected, so the expiry is real. Across two mints the website went about eight hours unwritable. The friction the owner complained about and the blocker to an unattended run are the same fact. A launchd job on his own machine mints the token now. Unloading it revokes the capability in one line.

**Principle:** The complaint about token friction and the autonomy blocker are one property.

**Tags:** System, System, Architecture

---

## 490 ms Against 36.8 Seconds

**Date:** 9 August 2026
**Type:** Release
**Generation:** SYSTEM

The cutover flipped the site from database reads to files. With the variable unset, static generation finished in 490.2 ms with zero Postgres references in the log. The same 48 routes took 36.8 seconds against the database. Two of the plan's mechanisms did not hold. Dropping the request parameter left three routes dynamic, because this framework version stopped caching GET handlers by default and needs force-static.

**Principle:** Diagnosing the cause correctly does not mean the prescribed cure works.

**Tags:** System, System, Release

---

## 43 Article Files Rewritten by One Stamp

**Date:** 9 August 2026
**Type:** Fix
**Generation:** SYSTEM

P4 could not run: the parity step called snapshot.mjs, and that file had never existed. The parity script had referenced it since the day it was written, and the step lived in a session runbook. Exporting the same database at two website heads used to rewrite 43 article files. Moving the per-run stamp into the manifest took that to zero. Head and JSON-LD then matched 40/40.

**Principle:** A step that only ever lived in a transcript is not a runnable gate.

**Tags:** System, System, Fix

---

## A Token With workflow Scope Can Edit the Check That Gates It

**Date:** 8 August 2026
**Type:** Architecture
**Generation:** SYSTEM

Read-only probes measured the identity design before any console step. The review rule was already live, at zero required approvals and no bypass actors. With one collaborator, raising it to one would deadlock every pull request. Fork pull requests never start their checks, so the fork model would leave every one blocked. The agent's own token carries repo and workflow scope. It can merge its work and edit the gate.

**Principle:** An identity that can edit its own gate is not gated.

**Tags:** System, System, Architecture

---

## 8 Structured-Data URLs Short by One Segment

**Date:** 8 August 2026
**Type:** Fix
**Generation:** SYSTEM

The DefinedTermSet block emitted all 8 term URLs one segment short. Every one returned a 404, and the 42 row redirect table did not cover a single one. A depth of 1 stopped the path walk early. Separately, the rule file asked for 40 to 60 word section openers, and 0 of 261 reach 100. The corpus complies with the wrong number.

**Principle:** A corpus can comply perfectly with a number that was calibrated wrong.

**Tags:** System, System, Fix

---

## PR #2: Green Checks, Blocked Merge, Bot Author

**Date:** 8 August 2026
**Type:** Architecture
**Generation:** SYSTEM

PR #2, the first pull request authored by the agent identity, ran verify and build green, then sat at BLOCKED. Nothing was merged. The claim that nothing ships without approval now has an observation behind it. The first envelope covers half its intended class, because permissions.json declares no action for database enumeration. That refusal is the design working.

**Principle:** A gate becomes a fact the day it refuses a green pull request.

**Tags:** System, System, Architecture

---

## The App Returns 404 to Its Own Agent

**Date:** 8 August 2026
**Type:** Learning
**Generation:** SYSTEM

Two rulesets read back from the API rather than the settings screen. The checks ruleset keeps an empty bypass list, while the review ruleset adds one approval and admin bypass. GitHub pre-ticked deletion and force-push rules nobody asked for, and both were removed before enforcement. GET on the App returns 404, so its granted permissions are unreadable. A human reading a settings page is the only check there.

**Principle:** State plainly which verification a human did, and which the agent measured.

**Tags:** System, System, Learning

---

## 76 Locale URLs Retired, and Middleware Runs First

**Date:** 8 August 2026
**Type:** Fix
**Generation:** SYSTEM

The German and Polish prefixes served English prose under 76 URLs, with nav links rendering as dead anchors. Retiring them took the route surface from 124 to 48. The trap sat in ordering: middleware runs before next.config redirects, so next-intl would have returned 404 before the 301 fired. The matcher now excludes those prefixes. A running server confirmed 308s on every sampled path.

**Principle:** Verify redirect behaviour against a running server, since ordering decides what fires first.

**Tags:** System, System, Fix

---

## Three Sessions of Console Steps for a Screen Behind a Paywall

**Date:** 8 August 2026
**Type:** Failure
**Generation:** SYSTEM

Rulesets did not exist on a private repository at the free tier. The endpoints returned 403 with an upgrade message. One API call would have surfaced that. The agent wrote exact console steps three times instead, across three handoff records. The CODEOWNERS file committed alongside was inert. After the upgrade, a deliberate red pull request proved the gate blocks.

**Principle:** One API call would have shown the feature was absent. Make it first.

**Tags:** System, System, Failure

---

## A Gate Piped Into tail Reported Success

**Date:** 8 August 2026
**Type:** Failure
**Generation:** SYSTEM

The wrap-up check was run as wrapup:check piped into tail, then chained with &&. The check failed on an unstaged CHANGELOG. The shell reported tail's exit status, so the commit went through on red. Nobody argued with the gate or overrode it. It was formatted into irrelevance. Separately, the owner-executed redirect repair took dead destinations from 25 to 0 across 42 rows.

**Principle:** Run a gate alone and read its exit status. A pipe hides it.

**Tags:** System, System, Failure

---

## An Approved Change That Could Not Be Applied

**Date:** 8 August 2026
**Type:** Learning
**Generation:** SYSTEM

The registry permissions change the agent asked for could not be applied. There is no scoped write level, and the resolver fails closed on any non control-plane write default. It was also unnecessary, since two prior writes landed under the existing rule. The ADR states the requirement twice and is wrong both times. W1 then transformed 43 articles into 50 files, 10/10 validations, every log entry intact.

**Principle:** Check an approval against the code that would enforce it before asking for it.

**Tags:** System, System, Learning

---

## The File Tree Called 21 Live Pages Drafts

**Date:** 8 August 2026
**Type:** Fix
**Generation:** SYSTEM

The transform read Payload's version status while the public route filters on a custom status column. They disagree on 21 of 43 rows, every one published and reachable. The database build prerendered 37 routes and the file build 16. The check and the thing it checked shared the same wrong column, so validation had reported 10/10. Route-level rendering also caught a whole sidebar block family dropped in silence.

**Principle:** Compare rendered routes, since a field-list check only sees fields someone enumerated.

**Tags:** System, System, Fix

---

## A Config Key That Matched l, o, c, a or e

**Date:** 8 August 2026
**Type:** Learning
**Generation:** SYSTEM

29 media binaries were pulled out of blob storage and tracked, 285,611 bytes. Each was verified four ways before anything was written. The ADR specifies a hermetic build for this phase. Built against a dead connection string, it dies with ECONNREFUSED, because four render paths still query the database. The tracing config key is a glob, so a bracketed locale segment is a character class. It matches no route at all.

**Principle:** Probe a config key's behaviour; a glob can look literal and match nothing.

**Tags:** System, System, Learning

---

## 9 of 14 Topic Counts Disagreed, and the Column Was Right

**Date:** 8 August 2026
**Type:** Fix
**Generation:** SYSTEM

The build now completes with the database pointed at 127.0.0.1:1: 124 routes, exit 0, zero Postgres connection attempts. The derived topic counts disagreed with the CMS on 9 of 14 topics. My first hypothesis blamed a stale hook column, and measuring it showed the CMS was exactly right. The index builder excluded pillar layouts for no stated reason. That value had no consumer, so its semantics drifted freely.

**Principle:** A derived value with no consumer drifts from the thing it replaces.

**Tags:** System, System, Fix

---

## The Authority Envelope Shipped With Autonomy Left Undefined

**Date:** 7 August 2026
**Type:** Decision
**Generation:** SYSTEM

The owner asked for a frontier agentic and autonomous system on 7 August 2026. I designed the authority envelope around that and left the definition of full autonomy open on purpose. Defining it now would fix the wrong thing early. The envelope holds the parts that are settled. The open question is recorded as open, and the reason for leaving it open is attached.

**Principle:** Record an open definition as open. Do not build against a placeholder you invented.

**Tags:** System, System, Decision

---

## Marketing Adapters Built, and a Git-to-Live ADR for the Website

**Date:** 7 August 2026
**Type:** Feature
**Generation:** SYSTEM

Phase B built the marketing surface adapters for the disclosure gate on 7 August 2026. Each adapter reads the spec at run time and carries no copy of the rules. Each one fails closed. No retrofitting of already-published content was allowed. A read-only survey of the headless website repositories answered the deployment question. That answer is recorded as a git-to-live ADR.

**Principle:** Adapters should consume the spec, so one rule change reaches every surface.

**Tags:** System, System, Feature

---

## Built and Retired the Same Day on One Instruction

**Date:** 7 August 2026
**Type:** Decision
**Generation:** SYSTEM

The owner reviewed the disclosure gate on 7 August 2026, the same day it was built. The review declined further work on AI regulation. The instruction was direct: do not block any article. So I removed every path where a disclosure or provenance state could block an article or an image. The gate had been built ahead of a requirement nobody asked for.

**Principle:** Do not build for a requirement the owner has not asked for.

**Tags:** System, System, Decision

---

## Every Disclosure Path Deleted, Receipt Schema 2 to 3

**Date:** 7 August 2026
**Type:** Decision
**Generation:** SYSTEM

The disclosure gate is gone from the lab and the image generator. Seven files deleted, the npm script unwired, receipt schema bumped 2 to 3. Suites finished 105/105. One wrong report along the way came from a probe that called parseImageTier1Report with one argument instead of three. Git-to-live was accepted as direction on 7 August, which grants no implementation.

**Principle:** A probe is code too. Check the instrument before rewriting the subject.

**Tags:** System, System, Decision

---

## Zero Gates, Then Five Voice Violations Found by Hand

**Date:** 7 August 2026
**Type:** Learning
**Generation:** SYSTEM

The validator returned zero gates and an advisory profile byte-identical to the accepted baseline. A manual pass against voice.md then found five violations in the same prose. Four were the single-sentence inversion its regexes never reach. Eleven rules carry MANUAL or ENGINE status and print under NOT EXECUTABLE HERE on every run. That line is a standing declaration that the check did not happen.

**Principle:** A green validator reports what it checked, and eleven rules said they checked nothing.

**Tags:** System, System, Learning

---

## Two Artifacts Credited a Validator Three Versions Behind

**Date:** 7 August 2026
**Type:** Fix
**Generation:** SYSTEM

The Build Log builder read tools/validate/VERSION at build time, so the validator moving 1.1.1 to 1.3.0 broke a protected digest. The Framework hardcoded the same field and reproduced fine while being wrong. Both credited engine versions three releases stale. Four CMS adapter defects were fixed alongside, including a preview URL that interpolated the secret. The acceptance test went red before green, 9/9.

**Principle:** A digest is protected only while everything its builder reads is pinned too.

**Tags:** System, System, Fix

---

## 97 Percent of llms.txt Files Got Zero Requests

**Date:** 7 August 2026
**Type:** Learning
**Generation:** SYSTEM

Five research sweeps, then an adversarial verifier told to default to refuted. Ten load-bearing claims were corrected before use. Across 137,210 domains, 97 percent of valid llms.txt files received zero requests in May 2026. AI retrieval bots were 1.1 percent of the requests. Of 20,185 hosts, 65 served an A2A agent card and 10 passed structural checks.

**Principle:** Hand every shipped-and-adopted claim to a verifier told to default to refuted.

**Tags:** System, System, Learning

---

## A Seven-Column Grid That Fits Exactly Four Steps

**Date:** 7 August 2026
**Type:** Failure
**Generation:** SYSTEM

Two figures rendered badly on a published Build Log after every gate came back green. The flow template hardcoded seven grid columns, which fits four steps and three arrows, so a five-step figure wrapped. The rendered review had measured horizontal overflow at 1440, 690 and 390 pixels. It never looked at a figure. Both defects were visible at every width it used.

**Principle:** Overflow is containment; a figure can be contained, intact and still wrong.

**Tags:** System, System, Failure

---

## A Prompt That Named an Authority ID Consumed That Morning

**Date:** 7 August 2026
**Type:** Learning
**Generation:** SYSTEM

A tracked handoff prompt was drafted in the morning and went stale by evening. It told the next session to record, a number consumed that same day along with three more. It capped the ledger read at, which hid four entries. It also called two articles pending review after both had been published. Every stale field encoded state at drafting time rather than a rule that fails loudly.

**Principle:** Refresh a tracked prompt before handing it over. Seven hours was enough to expire one.

**Tags:** System, System, Learning

---

## Two Articles Published, One Without a Social Card

**Date:** 7 August 2026
**Type:** Release
**Generation:** SYSTEM

Article 8 was updated in place and article 94 created, both live on 7 August. The publish path resolved the parent from parentSlug, confirmed as 9 by a pre-flight read. Four alt-text values were truncated at the 125 character cap. An inline SVG hero skips the media branch, so Build Log 02 has no OG image. A mentions probe reported a false miss because it walked body sections only.

**Principle:** Read production before writing to it; the pre-flight is what protected the live URL.

**Tags:** System, System, Release

---

## 25 of 42 Redirects Point at Drafts

**Date:** 7 August 2026
**Type:** Architecture
**Generation:** SYSTEM

The 301 pass was supposed to redistribute link equity. Measured against the live table, 25 of 42 redirects land on drafts, including four former blog permalinks. The flagship operator-logs page carries five dead outbound links. Seven finished articles of about 14,200 words sit unpublished. The 116 live log entries map onto the eight published engines with 65 under Create and zero under Measure.

**Principle:** Audit the redirect table before redistributing equity; the leak may already be open.

**Tags:** System, System, Architecture

---

## 43 Rows, 54 Tables, Zero Blob URLs

**Date:** 7 August 2026
**Type:** Learning
**Generation:** SYSTEM

Every count in the publishing ADR came from reading code. Measured, the locale risk it called highest is one global's fields, because all 43 article rows are English. A sweep of all 54 tables found zero blob URLs. The exposure runs the other way. 29 media binaries live only in blob storage, in a folder the repository gitignores.

**Principle:** Measure the database before an architecture decision commits to its counts.

**Tags:** System, System, Learning

---

## A Session-Close Kit a Fresh Repository Can Adopt Green

**Date:** 6 August 2026
**Type:** Architecture
**Generation:** SYSTEM

Session-close conventions from other workspaces got merged into the lab on 6 August 2026. I took what was better there and kept the lab properties that could not be traded away. The result ships as an owner-carried installation rather than a per-repository rewrite. A fresh repository can adopt the whole thing and come back green end to end. Details from enterprise repositories stay out of this record.

**Principle:** Ship shared conventions as one carried installation a fresh repository can adopt.

**Tags:** System, System, Architecture

---

## Adversarial Review Found What the First Gate Implementation Missed

**Date:** 6 August 2026
**Type:** Fix
**Generation:** SYSTEM

Phase A of the provenance and disclosure gate landed on 6 August 2026. Four requirements bound it: fail closed, convergent remedy, deterministic output, dormancy on transfer. I then reviewed the implementation adversarially. The review found gaps the first pass had missed and the hardening landed the same session. A green run was not sufficient evidence.

**Principle:** Review your own implementation adversarially before you call the green run evidence.

**Tags:** System, System, Fix

---

## Docs-First Remedies Landed While the Owner Decisions Stayed Open

**Date:** 6 August 2026
**Type:** Fix
**Generation:** SYSTEM

A defect report carried remedies I could not fully act on, because several depended on owner decisions still open. On 6 August 2026 I sorted them and landed only the docs-first, lab-owned ones, plus the review follow-ups for the wrap-up kit. The kit also got its disclosure wiring. Everything went in green. The remaining items are still parked, and they are parked for a stated reason.

**Principle:** Split a remedy list by what needs a decision. Land the rest now.

**Tags:** System, System, Fix

---

## A Byte-Rebuildable Learning Index and the Log Compiler On Top

**Date:** 6 August 2026
**Type:** Architecture
**Generation:** SYSTEM

Pilot A went in on 6 August 2026 exactly as the approved design sketch described. The learning index is derived from the tracked substrate and rebuilds byte for byte, so drift is detectable rather than assumed. A fail-closed drift gate runs at session close. The operator-log compiler sits on top of the index and is deterministic too. One segment rule had a defect and was corrected.

**Principle:** Make the derived index byte-rebuildable so drift fails the gate at session close.

**Tags:** System, System, Architecture

---

## Two Laws Live on 2 August, Three Public Surfaces to Cover

**Date:** 6 August 2026
**Type:** Architecture
**Generation:** SYSTEM

EU AI Act Article 50 and California CAITA both became operative on 2 August 2026. The EU machine-readable marking backstop follows on 2 December 2026. I mapped what each requires of three public surfaces. Those are the hendry.ai website, the CMS draft and publish path, and the public Operator Logs mirror. The design is fail closed and cuts across all three. Only the statute text and C2PA documentation are cited.

**Principle:** Read the statute yourself and map each obligation to a named public surface.

**Tags:** System, System, Architecture

---

## Four Heads Captured Before the First Write

**Date:** 5 August 2026
**Type:** Decision
**Generation:** SYSTEM

Before any byte moved, I captured four repository heads, all clean and aligned. The item names three code sites. Context sync already derives canon as a sibling, but its stamp writes an absolute path that the check never compares. The preview footer leaks an absolute path when the input sits outside the repository. One website script hardcodes the article path at line 9. The stamp stays unregenerated until after the move.

**Principle:** Capture every head before the first write. Name the exact code sites.

**Tags:** System, System, Decision

---

## 121 Routes Green, Two Patches Parked

**Date:** 5 August 2026
**Type:** Fix
**Generation:** SYSTEM

The website change landed, the hardcoded article path is gone, and the build stayed green at 121 of 121 routes. Both marketing changes proved green in the working tree. A canon advance on 3 August then made the pre-commit drift gate fail closed. I captured both changes as patches, restored the tree byte-identical to c78c4a8, and left the fix parked. The consumer checkout stayed pristine.

**Principle:** When a gate outside your authority blocks a proven patch, park it with evidence.

**Tags:** System, System, Fix

---

## Three Delegated Answers, Written Down as Defaults Before M3

**Date:** 5 August 2026
**Type:** Decision
**Generation:** SYSTEM

On 5 August 2026 the owner answered three decisions by delegating them back to me. I wrote each answer out as an explicit default in the authorization record before M3 started. The waiver covered those three questions only. I did not read it as blanket permission for the cutover. Anything outside the three still needed a fresh ask.

**Principle:** Write a delegated answer down as an explicit default before the work starts.

**Tags:** System, System, Decision

---

## A July Gap List, Rechecked Against August Practice

**Date:** 5 August 2026
**Type:** Learning
**Generation:** SYSTEM

The July 2026 frontier and durability gap list went back under review on 5 August. Each gap was rechecked against how the harness, loops and graphs actually run now. Most held. One new gap surfaced, a provenance and disclosure obligation with a date attached. Only public regulation and vendor documentation were cited. The refreshed list became the design input for Pilot A.

**Principle:** Recheck an old gap list against current practice before you rebuild it.

**Tags:** System, System, Learning

---

## Calling Preserved Work Retired Cost an Alarmed Correction

**Date:** 5 August 2026
**Type:** Learning
**Generation:** SYSTEM

I described listen-discuss as a retired experiment. The owner corrected that sharply on 5 August 2026. What was retired is the coupling, and the repository itself is intact exactly as the P0 preservation contract promised. Nothing in the recorded state changed, only the wording I used. A durability gap surfaced alongside it, since no check enforces how preserved work gets described.

**Principle:** Name what was retired precisely. Preserved work must never be described as discarded.

**Tags:** System, System, Learning

---

## listen-discuss Belongs to hendry.ai by Lineage, Not by Location

**Date:** 5 August 2026
**Type:** Decision
**Generation:** SYSTEM

listen-discuss belongs to hendry.ai by lineage, so the brand question was settled on 5 August 2026 without moving a single file. The directory stays where it is until every inbound dependency is closed. Ownership and location are separate decisions here. Recording the first one costs nothing. Acting on the second would break whatever still points at the old path.

**Principle:** Settle where work belongs first. Move the files after the dependencies close.

**Tags:** System, System, Decision

---

## One Privacy Sentence Demoted the Cloud Archive to Encrypt First

**Date:** 5 August 2026
**Type:** Decision
**Generation:** SYSTEM

The owner authorized the M1 move on 5 August 2026 with a single added line about not sharing data unnecessarily. That sentence changed the secondary archive design. The cloud destination dropped from default to a gated option, and any copy off device now has to be encrypted first. Private Git remotes stayed as the only unqualified path. No further instruction was needed.

**Principle:** A plain privacy instruction is a design constraint. Gate the off-device copy.

**Tags:** System, System, Decision

---

## Registry v2 Resolves Identically While Every Path Went Relative

**Date:** 5 August 2026
**Type:** Architecture
**Generation:** SYSTEM

Items 1 to 7 of the M1 slice landed on 5 August 2026. The registry now stores relative paths and a realpath resolver reconstructs them at read time. Resolution behaviour is identical and surface ids stayed byte compatible. Escapes outside the registered roots fail closed. Consumers were migrated in the same pass and the gates came back green.

**Principle:** Store paths relative and resolve at read time. Verify the ids stay identical.

**Tags:** System, System, Architecture

---

## The Commit That Records Acceptance Is Never the Accepted Head

**Date:** 5 August 2026
**Type:** Decision
**Generation:** SYSTEM

The owner accepted M2 on 5 August 2026. The acceptance binds to the exact commit heads presented at item 10, re-captured at decision time. Every Runbook 8.2 condition went on record independently. The commit that writes the acceptance down lands after those heads, so it sits outside what was accepted. That ordering has to be stated or the record reads ambiguously later.

**Principle:** Bind acceptance to re-captured heads. The recording commit sits outside what was accepted.

**Tags:** System, System, Decision

---

## One Committed Registry, Two Roots, No Edits Between

**Date:** 5 August 2026
**Type:** Architecture
**Generation:** SYSTEM

With M1 accepted, the remaining lab slices tested the dual-topology contract on 5 August 2026. One committed registry, two roots. It resolved against the current root and a simulated target root with no edits between runs. Nested and subtree Git ownership came out correct in both. Historical absolute paths were refused. A reader with zero dependencies handles the immutable history.

**Principle:** Prove a path registry against a simulated target root before you move anything.

**Tags:** System, System, Architecture

---

## M8 Accepted by Use, and the Retention Clock Starts

**Date:** 5 August 2026
**Type:** Release
**Generation:** SYSTEM

The owner accepted M8 on 5 August 2026 and Wave 1 closed. Acceptance came from working in the relocated tree, which is stronger evidence than a readback. Every Runbook 16 criterion was re-verified defect free first. The accept also starts a retention clock. Rollback material stays until that clock runs out, then it gets disposed of deliberately.

**Principle:** Acceptance by owner use beats a readback. Start the retention clock at accept.

**Tags:** System, System, Release

---

## One Bounded Run at the New Root, Approval Deliberately Terminal

**Date:** 5 August 2026
**Type:** Architecture
**Generation:** SYSTEM

On 5 August 2026 the relocated control plane executed a complete bounded workflow run at the lab umbrella/hendry-ai. Envelope creation, repository pinning, research provenance and the terminal state all held. The content-approval interrupt survived across process boundaries, so the owner decision came back to a durable record. Resume checked freshness before continuing. The approval is not transferable to another run by design.

**Principle:** A durable approval interrupt must survive process death and stay bound to one run.

**Tags:** System, System, Architecture

---

## Six Classes of Path Binding, and Almost All Self Re-Key

**Date:** 5 August 2026
**Type:** Learning
**Generation:** SYSTEM

Before M3 I inventoried everything outside the six registered Git roots that binds to their absolute paths. The Runbook names six classes to check: IDE state, tasks, environment, deployment, scheduler and working directory. Nearly all of it re-keys itself once the directory moves. Nothing found blocked M3 or M4. The checklist is reusable, which matters more than this particular result.

**Principle:** Inventory path bindings by class before a move, even when most re-key themselves.

**Tags:** System, System, Learning

---

## Seven Files Synced, Two Patches Landed, Patch Files Kept

**Date:** 5 August 2026
**Type:** Release
**Generation:** SYSTEM

The execution landed on 5 August 2026: a seven-file sync plus two digest-bound patches for the marketing handoffs parked earlier. Every repository closed clean and verified. The patch files stayed on disk after application. They are the immutable record of exactly which bytes went in, which a commit diff alone does not give you. Item 10 is complete.

**Principle:** Keep the patch file after applying it. It records the bytes a diff omits.

**Tags:** System, System, Release

---

## Bind the Authorization to Patch Digests Before You Execute

**Date:** 5 August 2026
**Type:** Decision
**Generation:** SYSTEM

The owner said proceed as recommended on 5 August 2026. Before anything ran I pinned what that phrase covered. That meant the digest of each patch and the head of each repository at decision time. Some of those repositories are enterprise work and stay out of the log. The binding is what makes the later execution checkable. Without it, proceed means whatever the tree looked like at run time.

**Principle:** Pin patch digests and decision-time heads before executing a proceed as recommended.

**Tags:** System, System, Decision

---

## Six Roots Moved, M3 to M7 Green at the New Path

**Date:** 5 August 2026
**Type:** Release
**Generation:** SYSTEM

The sealed cutover packet executed on 5 August 2026. Durability was proven first, the freeze was honored, and all six registered roots moved intact to the lab umbrella/hendry-ai. Every M5 to M7 readback came back green. Enterprise work stayed behind at the old root and is out of scope for this log. Only the owner acceptance at M8 remained after that.

**Principle:** Prove durability and freeze the tree before a move, then read every root back.

**Tags:** System, System, Release

---

## One Edge Breaks, and Only If Someone Starts a Session

**Date:** 4 August 2026
**Type:** Decision
**Generation:** SYSTEM

Both Listen repositories have been dormant since 31 May 2026. The coupling is front-matter plus a fail-closed bootstrap, and the protocol already skips a null sibling. Only one edge breaks when Context moves: listen-build reading its canon sibling. It breaks only if someone starts a session there, and the bootstrap halts by design. The inventory changed zero bytes in either repository.

**Principle:** Retire a dormant coupling by leaving it in place and letting it fail closed.

**Tags:** System, System, Decision

---

## A Plan Citing an Audit That Was Never Written

**Date:** 4 August 2026
**Type:** Fix
**Generation:** SYSTEM

The audit returned ready with conditions. The plan cited a 2026-07-27 dependency audit that does not exist in the lab. Three of six planning baselines were stale. The same M-labels meant different milestones in the research record and the runbook. One step fingerprinted the source before the backup reopened it, which would invalidate the fingerprint. Fifteen redlines landed, and the authority ledger starts here.

**Principle:** Check that every cited evidence record actually exists before accepting the plan.

**Tags:** System, System, Fix

---

## Two of Three Digests Had Moved Since Acceptance

**Date:** 4 August 2026
**Type:** Decision
**Generation:** SYSTEM

Two of the three bound documents had changed since acceptance. Their revision histories show status annotations only, each with no authority effect. So binds today's digests and writes down the reconciliation rather than ignoring the drift. A second conflict surfaced: the prompt forbids pushes, and its closeout requires a verifier that fails unless HEAD matches upstream. Filename-only authorization stays invalid.

**Principle:** Bind an authorization to digests you computed today, and explain every drift.

**Tags:** System, System, Decision

---

## A Bundle Carries Refs and Nothing Else

**Date:** 4 August 2026
**Type:** Architecture
**Generation:** SYSTEM

All seven registered roots were clean, aligned 0/0, and on HTTPS remotes only. The read of primary Git documentation confirmed that a bundle carries refs alone, without index, working tree, or hooks. That changes what a backup can promise. Three new findings landed: divergent cleanliness semantics, lexical containment in check-boundaries.mjs, and no surface-to-root ownership model. Two active controls still carry absolute paths.

**Principle:** Read the primary documentation before you plan a backup you have not tested.

**Tags:** System, System, Architecture

---

## Six First-Person References in a Whole Draft

**Date:** 1 August 2026
**Type:** Learning
**Generation:** SYSTEM

Feedback-v1 read the under-20-word preference as a hard ceiling. It scanned clean and did not sound like me. Six first-person references and one reader-facing you across the whole draft, plus 12 runs of similarly sized sentences. Feedback-v2 runs 2,537 words with 103 of its 135 sentences at 20 words or fewer. It opens on the 27 February 2026 build and five isolated Claude Projects.

**Principle:** Apply voice as a writing system. A clean surface scan proves nothing.

**Tags:** System, System, Learning

---

## A Branch Does Not Protect Ignored Output Files

**Date:** 31 July 2026
**Type:** Decision
**Generation:** SYSTEM

The owner wanted a second direction for Framework v2 and no overwrite of the first. A new branch alone would not have protected the outputs. Generated JSON, preview, and hero are Git-ignored, so only recorded digests identify them. So the variant gets a separate builder path and separate output filenames, and the baseline freezes at commit cc1ce23. The paths are a handoff convention for one session.

**Principle:** A branch protects source history. Ignored outputs need distinct filenames and recorded digests.

**Tags:** System, System, Decision

---

## 2,106 Words Against 5,911

**Date:** 31 July 2026
**Type:** Learning
**Generation:** SYSTEM

The flagship asked a first-time reader to absorb architecture, terminology, market evidence, roles, and legal context at once. Two external model critiques said so, and I agreed. The new draft runs 2,106 words against a 5,911-word baseline, roughly 36 per cent of the reading load. No ROI figure appears, because no operator-hours or token cost exists to reconstruct one. The baseline stays protected.

**Principle:** Cut the reading load without inventing a number the evidence cannot support.

**Tags:** System, System, Learning

---

## A Ledger Narrowed to One Domain

**Date:** 31 July 2026
**Type:** Fix
**Generation:** SYSTEM

The previous revision narrowed the evidence ledger to hendry.ai alone. That understated work done outside the public site. The previews also had real presentation defects: a hero artefact, uneven arrow clearance, and table columns that could collapse into unreadable widths. One callout and figure contract now spans the preview builder and the website renderer. Autonomy is per task, so L4 holds only inside bounded local guardrails.

**Principle:** Publish from one surface without pretending it bounds the work you have done.

**Tags:** System, System, Fix

---

## Six Registered Roles, Fewer Than Six Checkouts

**Date:** 26 July 2026
**Type:** Learning
**Generation:** SYSTEM

The registry names six absolute role paths under one workspace root. One has no repository of its own and resolves to the parent checkout. Marketing cannot move alone either. Context sync derives canon as a sibling, and a pre-commit hook runs that check on every commit. The sync stamp stores the old root under the dev umbrella and never compares it. A post-move check could pass while provenance still names it.

**Principle:** Check what each registered path actually resolves to before planning a move.

**Tags:** System, System, Learning

---

## A Rejection With No Brief Attached

**Date:** 26 July 2026
**Type:** Decision
**Generation:** SYSTEM

The owner rejected the latest editorial result on both articles. No replacement direction came with the rejection. I closed the session without changing a single line of prose. The baseline stays frozen at marketing commit 54fc6ee, and the record keeps both generated JSON digests. Guessing the direction buys another wrong rewrite.

**Principle:** On rejection, freeze the baseline and collect concrete direction before editing anything.

**Tags:** System, System, Decision

---

## 79 Advisories to Three, 22 to One

**Date:** 26 July 2026
**Type:** Fix
**Generation:** SYSTEM

Every repair went into the maintained builders, never the generated JSON. Framework v2 moved from 79 advisories down to three reviewed exceptions, with its 43 paragraph-length flags at zero. Build Log 02 went from 22 to one. Four semantic alarms stayed visible and I dispositioned each by hand. The Framework builder now writes the slug-bound hero, and both heroes pass all nine image checks.

**Principle:** Repair prose in the builder that generates it. The JSON is an output.

**Tags:** System, System, Fix

---

## The LangGraph Example That Sat Too Close to the Definition

**Date:** 25 July 2026
**Type:** Fix
**Generation:** SYSTEM

Build Log 02 put its LangGraph evidence right after a generic workflow-graph explanation. That adjacency left the wider term underspecified. Both articles now describe graph engineering as a broader house synthesis, and LangGraph as one runtime for one bounded work slice. Framework v2 carries 47 direct source records and 79 retained advisories. The shared citation-leaf-v1 rule sets 75 to 300 words per leaf.

**Principle:** One vendor example placed next to a general claim reads as the definition.

**Tags:** System, System, Fix

---

## The Immutable Judge That Was Doing Three Jobs

**Date:** 25 July 2026
**Type:** Learning
**Generation:** SYSTEM

The audit changed no bytes. It read the 13-section Framework candidate and separated a durable kernel from claims with a shorter half-life. Checkpoints, interrupts, and human-in-the-loop have become ordinary durable-workflow features. Calling Measure an immutable judge merges three jobs with different graders and consequences. A published audit of a widely used coding benchmark found roughly thirty percent of its tasks broken.

**Principle:** Evaluators need versions and audits of their own before you call them immutable.

**Tags:** System, System, Learning

---

## Four Graph Views Behind One Unsettled Word

**Date:** 25 July 2026
**Type:** Decision
**Generation:** SYSTEM

In July 2026 there was no standards body and no settled definition for graph engineering. I wrote the house synthesis and labelled it as one. It separates four views: work and control, context and knowledge, improvement, and evidence and trace. LangGraph covers the first and part of the last. A knowledge graph is an information model, so governed Context needs no graph database.

**Principle:** Label a house synthesis as a house synthesis, not as a settled discipline.

**Tags:** System, System, Decision

---

## A Closed Loop in the Hero, Unbuilt in the Body

**Date:** 25 July 2026
**Type:** Fix
**Generation:** SYSTEM

The hero and summary called the model a working closed loop. The body said Measure and Iterate were unbuilt. Independent review caught the contradiction, and every public-facing field now says governed target architecture. Section counts hid a similar gap. Five H2 containers ran 800 to 950 words while some H3 leaves held 28. The corrected loop routes Measure evidence to an Iterate proposal, then to owner approval.

**Principle:** Fold new learning into the article body instead of appending dated notes.

**Tags:** System, System, Fix

---

## The Validator Was Green and the Sources Were Aggregators

**Date:** 25 July 2026
**Type:** Fix
**Generation:** SYSTEM

The article passed its structural validator while still citing aggregators and carrying unsupported precision. The two checks ask different questions. The rebuild carries 44 direct source records, mixing 26 official-primary, 12 original-research, and 6 practitioner-primary sources. STR-030 now blocks on that inventory and rejects known aggregator hosts. Routing never promotes an advisory into a gate.

**Principle:** A structural pass says nothing about whether the sources support the claim.

**Tags:** System, System, Fix

---

## 79 Advisories Behind Zero Blocking Gates

**Date:** 25 July 2026
**Type:** Failure
**Generation:** SYSTEM

Zero blocking gates had been read as ready for human review. Framework v2 retained 79 advisories, including 43 paragraph-length flags and one paragraph that ran eleven sentences. Build Log 02 retained 22 advisories. Its final playbook section had all nine paragraphs over the three-sentence maximum. A list item also broke mid-sentence in both the JSON and the preview.

**Principle:** Deterministic gates do not measure voice. Read the prose word by word.

**Tags:** System, System, Failure

---

## 39 Terms to 43, and Nothing Pushed

**Date:** 24 July 2026
**Type:** Decision
**Generation:** SYSTEM

Four terms went into /llms.txt Key Topics and Person.knowsAbout, among them Loop Engineering and Bounded Agent Loop. Both lists moved from 39 entries to 43. Google's own guidance says it ignores llms.txt for rankings and requires structured data to match visible content. So the terms only went in once the article text supported them. Both repositories stayed local and unpushed.

**Principle:** Add a term to the metadata only after the visible page can support it.

**Tags:** System, System, Decision

---

## Same Fourteen Advisories After the Copy Amendment

**Date:** 24 July 2026
**Type:** Decision
**Generation:** SYSTEM

Build Log 02 picked up the loop and graph vocabulary, and the release chronology was left alone. The payload still holds eleven sections, nine figures, eight FAQs and eleven audited links. Zero blocking gates, and the same fourteen advisories as before. Adding prose inside an existing section did not earn a tenth body figure in the visual contract. Amending the source superseded the approved packet, so approval restarts.

**Principle:** An amended source invalidates the approved packet. Get a fresh one before resuming.

**Tags:** System, System, Decision

---

## A.trim() That Hid the First Unstaged File

**Date:** 24 July 2026
**Type:** Fix
**Generation:** SYSTEM

The Framework figure presented three named practices as a dated sequence labelled the discipline, renamed twice. The revision shows scope widening, with graph and loop design as parts of one system. Alt text came back at 178 characters against a 125 cap. The final is 117. Closeout then exposed a fail-open bug.trim() dropped the leading porcelain status column, so an unstaged first file could vanish from the report.

**Principle:** Never trim a git porcelain line before you read its two status columns.

**Tags:** System, System, Fix

---

## 161 Visual Checks, Zero Failures, One Stop Before Links

**Date:** 24 July 2026
**Type:** Feature
**Generation:** SYSTEM

The adapter ran the Build Log 02 builder without changing a line of it. Two passes in a selected-file temporary mirror produced identical bytes. Network and child processes were denied. The article validator exited zero with fourteen non-blocking advisories, and the visual validator cleared 161 checks over nine figures. The slice stopped at validate_links, before any network or CMS boundary.

**Principle:** An adapter earns trust by leaving the builder unchanged and stopping where authority ends.

**Tags:** System, System, Feature

---

## Eight Checks Pass, IMG-T1-006 Fails, No Waiver Written

**Date:** 24 July 2026
**Type:** Feature
**Generation:** SYSTEM

The image validator exits 1 on the hero. Eight checks pass and IMG-T1-006 fails. Its dated filename rule contradicts the naming rule that the live CMS integration requires. I did not rename the hero or add a waiver. The red result routes through validate_article to stop_evidence. The manifest now binds thirteen inputs instead of twelve, so every earlier packet is stale.

**Principle:** Keep a red validator red. Rename nothing, waive nothing, and let the graph stop.

**Tags:** System, System, Feature

---

## One Ignored File Split Two Views of a Clean Repository

**Date:** 24 July 2026
**Type:** Fix
**Generation:** SYSTEM

Attempt 001 stopped with stale repository evidence for website-build-history. The checkpoint had pinned all six repositories clean. Checkpointing inherited ambient Git config, while the artifact adapter stripped HOME and XDG. Git then reported one otherwise ignored untracked file,.claude/settings.local.json. HEAD, branch, and tracked bytes were all equal to the approved pins everywhere. The evidence allocator also allowed 9,999 attempts against a two-retry budget.

**Principle:** Two readers of the same repository must agree on what clean means.

**Tags:** System, System, Fix

---

## Take LangGraph's Runtime, Leave the Agent Loop

**Date:** 23 July 2026
**Type:** Decision
**Generation:** SYSTEM

Researched on 23 July 2026 against the official docs. No dependency was installed. LangChain, LangGraph and LangSmith are three separate layers, and one can be taken without the others. The lab already owns typed state, terminal outcomes, evidence gates and human approvals. LangGraph's checkpoints and interrupts fill the real gap. Domain authority stays in plain files and TypeScript modules.

**Principle:** A resumed graph re-runs node code, so every write needs an idempotency key.

**Tags:** System, System, Decision

---

## A Byte-Deterministic Builder That Overwrites Three Files

**Date:** 23 July 2026
**Type:** Learning
**Generation:** SYSTEM

The Build Log builder uses only Node built-ins. No clock, no randomness, no network, no model call, so identical inputs give identical bytes. It is not filesystem-pure. It writes three fixed paths, one of them tracked in the marketing repository. Running it in that checkout would overwrite tracked work. The slice runs it twice inside a selected-file temporary mirror.

**Principle:** Deterministic output does not make a script safe to run in a tracked checkout.

**Tags:** System, System, Learning

---

## 13 Tests, One 64-Character Digest

**Date:** 23 July 2026
**Type:** Architecture
**Generation:** SYSTEM

The first three canonical nodes now run on LangGraph: pin_repositories, research_provenance, content_approval. The graph pauses at approval. It resumes only when the receipt matches the exact 64-character packet digest, and anything else routes to stop_authority. A dirty registered repository stops the run before research is collected. Thirteen tests pass, covering pause, cross-process SQLite resume and digest mismatch.

**Principle:** Bind approval to the exact packet digest, and route any mismatch to a stop.

**Tags:** System, System, Architecture

---

## Loop Engineering Is a New Name for Shipped Mechanics

**Date:** 23 July 2026
**Type:** Learning
**Generation:** SYSTEM

Checked the July 2026 vocabulary against first-party docs from IBM, Anthropic, OpenAI, LangGraph and Google ADK. The loop mechanics already ship: goal-directed cycles, termination rules, retry budgets, durable state, human escalation. What is new is treating the loop as the designed product. Graph engineering remains a non-standard label. So the copy describes graph mechanics directly.

**Principle:** Name the mechanism you actually run before adopting the label the market just coined.

**Tags:** System, System, Learning

---

## Two Commands That Refuse to Close a Dirty Session

**Date:** 23 July 2026
**Type:** Architecture
**Generation:** SYSTEM

Session close was a protocol applied by hand, which means it was applied when remembered. It now runs in three layers. AGENTS.md states the requirement. A repo-scoped wrapup skill directs the judgment calls, and scripts/wrapup.mjs fails closed on the mechanical ones. Two commands: wrapup:check on staged files before the commit, wrapup:verify on a clean tree after it.

**Principle:** A script cannot write honest session learning. It can refuse to close without it.

**Tags:** System, System, Architecture

---
