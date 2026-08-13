# Governance — Changelog

> Part of the [AI Marketing Operator Logs](../README.md) by [Hendry Soong](https://www.hendry.ai)
> Canonical source: [hendry.ai/ai-marketing/operator-logs/governance-log](https://www.hendry.ai/ai-marketing/operator-logs/governance-log/)

Mirrored from the canonical page above, newest first.

---

## Eleven Corrections, and the Rule That Followed Them

**Date:** 10 August 2026
**Type:** Decision
**Generation:** SYSTEM

The previous session produced eleven corrections. A cited file that did not exist had already carried a decision the owner approved. A git query measured.gitkeep scaffolding and inverted a damning answer. Agents reliably find where a thing is, and unreliably say what it does. Open the file. Nine research records, roughly 6.0M subagent tokens, get read and never regenerated.

**Principle:** Open the file before telling the owner what his own code does.

**Tags:** System, System, Decision

---

## A Required Check Blocked Four of the Seven Approved Pull Requests

**Date:** 10 August 2026
**Type:** Fix
**Generation:** SYSTEM

check:content went red when the first content edit landed on a branch. It runs inside the required verify job, so any pull request touching content cannot merge. That was 4 of the 7 approved. Regenerating the digest would have made it pass and left the real risk untouched. Instead its contract changed: the tree must match what was reviewed, under a named ledger authority. It still fails on an edit that skipped the script.

**Principle:** Change what a check asserts. Do not regenerate the artifact so it passes.

**Tags:** System, System, Fix

---

## 47 Against 46 Passed the Check While Only 40 Titles Matched

**Date:** 10 August 2026
**Type:** Fix
**Generation:** SYSTEM

The specified check compared per track counts: mirror total equals site total plus a curation delta. Create Articles held 47 against the site's 46, so the plus one relationship held exactly. The two sets shared 40 titles. Six site entries were missing from the mirror, seven mirror entries from the site. The net had been plus one the whole time. The drift script now asserts per entry, red checked five ways.

**Principle:** A net count can hold while both sets are wrong. Assert per entry.

**Tags:** System, System, Fix

---

## One Field Made Every Re-Export Look Like 43 Files of Change

**Date:** 9 August 2026
**Type:** Fix
**Generation:** SYSTEM

A fresh export differed from the tracked content tree on exactly one field, in all 43 articles. provenance.migratedFrom.websiteCommit is stamped from the website HEAD at export time. So every re-export rewrote every article and moved the content manifest digest while nothing had changed. Zero content drift since W1. The field moves to the manifest, recorded once. The same change tracked snapshot.mjs, which had never been a tracked file and blocked pre-flight P4.

**Principle:** A per record field stamped at export time destroys the manifest as a change signal.

**Tags:** System, System, Fix

---

## A New Permission Added at Human Gated Instead of Allow

**Date:** 9 August 2026
**Type:** Decision
**Generation:** SYSTEM

The owner asked for a read only database enumeration permission without naming a decision level. Added as allow, the agent could have enumerated the production database without a per instance grant. That is the agent widening its own permissions. It went in as decision human, gated on a read only transaction and owner approval. The permissions file moved to 1.1.0. Nothing the agent may do changed, but the class became expressible.

**Principle:** An agent asked to add a permission should add the narrowest one that works.

**Tags:** System, System, Decision

---

## A One Hour Token the Owner Alone Can Mint

**Date:** 9 August 2026
**Type:** Decision
**Generation:** SYSTEM

The installation token lives one hour, and only the owner can mint it. That suits a supervised session. It breaks the 261 opener run, which has to open pull requests with nobody present. A launchd job now re-runs the token helper on a timer. The blast radius is exactly opening pull requests. Merging, editing the checks and touching a ruleset all stay out of reach.

**Principle:** An hour long credential minted by hand cannot support a run that nobody attends.

**Tags:** System, System, Decision

---

## Nine Honest Closes That Could Not Move the Runtime State

**Date:** 9 August 2026
**Type:** Failure
**Generation:** SYSTEM

wrapup.mjs builds its active run list by querying the LangGraph checkpointer for threads whose status is waiting_human. A superseded disposition was prose in a tracked markdown file. No code path ever connected the two. Four runs sat superseded for eighteen days while nine consecutive closes wrote nine true sentences about them. The fix is a tracked retirement register whose script refuses to append without a reason and an issuing AUTH id.

**Principle:** A gate satisfied by prose cannot change the runtime state that prose describes.

**Tags:** System, System, Failure

---

## 29 Claims That the Media Binaries Were Untracked

**Date:** 9 August 2026
**Type:** Fix
**Generation:** SYSTEM

binaryTracked is measured only when to-files.mjs gets --repo, and defaults to false otherwise. The session omitted the flag and produced 29 claims that the media binaries are untracked. The catch came from a check in another repository. That is luck about placement. The transform now refuses to run without --repo or an explicit acknowledgement. The owner's recollection about the CMS became a measurement by digest comparison.

**Principle:** A fail closed default that silently produces false claims should refuse instead.

**Tags:** System, System, Fix

---

## A Six Hour Restore Window Makes the Snapshot the Only Rollback

**Date:** 9 August 2026
**Type:** Learning
**Generation:** SYSTEM

Point in time restore on the project is 21600 seconds, six hours. It will not reach back past a cutover that happened yesterday. So the branch is the only durable rollback, which raises it from prudent to load bearing. It was created with no expiry. An auto deleted rollback is worse than none, because nobody is told. A second unused project, one character apart in name, went on record as a decommission hazard.

**Principle:** An expiring rollback is worse than none, because nobody is told when it goes.

**Tags:** System, System, Learning

---

## The Cutover, With Three Stale Premises Named at Grant Time

**Date:** 9 August 2026
**Type:** Release
**Generation:** SYSTEM

Four tracked records disagreed on whether pointing a session at the prompt was the grant. The session stopped before any byte changed and asked. The owner confirmed the file as written, and Step 1 flipped the content source default to files. Three premises in the draft were stale, and each was named at grant time. Those were the ledger id, two pull requests since merged, and a deployment readback that now returns 403.

**Principle:** What grants authority is the owner saying so. The mechanism is not the point.

**Tags:** System, System, Release

---

## 212 Bytes Reported as Zero, From a Row Nobody Re-Measured

**Date:** 9 August 2026
**Type:** Failure
**Generation:** SYSTEM

The bake sweep found the live site unmoved. 38 pages at 200, 42 redirects landing where declared, 29 media at 285,611 bytes. Three derived surfaces were off baseline by 22, 24 and 166 bytes. The record called all five identical and reordered only. Its evidence file had an mtime of 09:42:53Z, before the first merge at 11:25:32Z, and was never rewritten. A permutation cannot change a byte total.

**Principle:** Re-measure the evidence after the merge, or a stale row reads as verified.

**Tags:** System, System, Failure

---

## Three Attempts, Three 405s: The Push Actor Was the Approver

**Date:** 9 August 2026
**Type:** Failure
**Generation:** SYSTEM

Retiring the database project ends the second arm permanently, so two unmeasured claims were run against live data first, read only. Then merges deadlocked. GitHub resolves a push made with an App installation token back to the App owner. That is the same identity whose approval require_last_push_approval then disqualifies. Three attempts on two pull requests all returned 405. The owner turned the rule off and turned dismiss_stale_reviews_on_push on in its place.

**Principle:** An irreversible retirement is the only real clock on a two arm comparison.

**Tags:** System, System, Failure

---

## RUN-0001 Authorised, and Kendall W of 0.024 on One Brief

**Date:** 9 August 2026
**Type:** Decision
**Generation:** SYSTEM

RUN-0001 is the lab's first authorised autonomous run. It runs offline, makes no model call, touches no network, and refuses a dirty tree. The positive control fires first or the run halts. On mismatch it opens one pull request and stops. A three family judge panel did exist, and the claim that none had run was retracted. Kendall W across its arms was 0.024, 0.272 and 0.328.

**Principle:** Two lanes with opposite rules need the lane named on every finding.

**Tags:** System, System, Decision

---

## A Permissions Gate That Did Not Exist

**Date:** 8 August 2026
**Type:** Learning
**Generation:** SYSTEM

The agent had asked for a registry permissions change as the unblocking gate, across several turns, without reading the resolver. The resolver fails closed on any write defaultAccess outside the control plane, and there is no scoped write level. The change was also unnecessary. Consumer writes run under a human-gated permission that the owner's approval already satisfies, with two prior website writes as precedent. The correction was recorded before anything executed.

**Principle:** Read the resolver before you claim a permission blocks you.

**Tags:** System, System, Learning

---

## A Yes That Meant Wait

**Date:** 8 August 2026
**Type:** Decision
**Generation:** SYSTEM

Five decisions came back at once. The first was a yes that meant wait. The seven drafts were approved in principle, with the voice pass held until after the git-to-live transition. The owner named them the first work for autonomous agents. That reversed the agent's own sequencing and avoids editorial work inside a CMS being retired. Where the owner answered a whole item, the agent's defaults were written down so they stay correctable.

**Principle:** When an approval carries a condition, the condition sets the sequence.

**Tags:** System, System, Decision

---

## A Switch That Stays Off, and a Void Clause

**Date:** 8 August 2026
**Type:** Decision
**Generation:** SYSTEM

The owner handed over a path; the prompt said pasting the body was the grant. The session recorded its reading and added a clause. If the reading is wrong, the entry is void and everything under it reverts. W2 put the file path behind a switch that stays off. The database stayed authoritative, and absence of the switch had to reproduce current behaviour byte for byte. The AutoContent path measured 0 rows and went.

**Principle:** Swap a data layer behind an opt-in switch and prove both paths render the same.

**Tags:** System, System, Decision

---

## The Only Unrecoverable Item on the Board

**Date:** 8 August 2026
**Type:** Feature
**Generation:** SYSTEM

Twenty-nine media files, 28 SVG and one JPEG, existed only in blob storage with public/media/ gitignored. They were tracked nowhere and would have gone with the store. They were pulled in first and verified against the filesizes the census recorded. The checks workflow landed with CODEOWNERS over the check definitions, because an agent that can edit a check has no check. Local parity had not proven the deployed file path worked.

**Principle:** Put CODEOWNERS over the check definitions. An agent that can edit a check has none.

**Tags:** System, System, Feature

---

## Six Render Paths and a Build With No Credentials

**Date:** 8 August 2026
**Type:** Decision
**Generation:** SYSTEM

Proceed arrived without a scope, so the session declined to infer one. It costed the remaining work as four tiers and asked. The owner picked wiring six CMS-only render paths to the file switch, the blocker in front of a hermetic build. Doing it means the build check needs no production database credentials in CI. The switch default stayed off, so production was unaffected. The option text is the scope.

**Principle:** Continue is an instruction without a scope. Offer costed tiers and take the one chosen.

**Tags:** System, System, Decision

---

## 8 Truncated JSON-LD URLs, Fixed by a Depth Change from 1 to 2

**Date:** 8 August 2026
**Type:** Fix
**Generation:** SYSTEM

The DefinedTermSet JSON-LD emitted 8 URLs that 404. The cause was findDefinitionChildren walking at depth 1. Its sibling DefinitionIndex already ran depth 2, and those visible links were correct, so the fix was one field. Measurement came before the tier menu. H2 openers sat at 0 of 261 inside the 100 to 150 word band. Defects went ahead of doctrine.

**Principle:** Fix current damage before rewriting the doctrine that governs it.

**Tags:** System, System, Fix

---

## 76 Locale Routes Serving English Text Under German and Polish URLs

**Date:** 8 August 2026
**Type:** Decision
**Generation:** SYSTEM

The database held no translated article content. articles_locales was 43 rows, all en, so /de and /pl served English text under German and Polish URLs. Nav links there were dead. Both prefixes now 301 to their English equivalents. The parity surface fell from 116 routes to 40. hreflang and the sitemap followed on their own, because both iterate the locales list rather than being edited.

**Principle:** Untranslated locale routes are worse than absent. Remove them, do not fill them.

**Tags:** System, System, Decision

---

## An Identity GitHub Could Not Tell Apart from the Owner's

**Date:** 8 August 2026
**Type:** Architecture
**Generation:** SYSTEM

The agent committed under the owner's own name and email, so GitHub saw one person. Code owner review meant the owner approving his own PRs. Revert telemetry had nothing to point at. The brief required an identity that can push branches and open pull requests, and cannot merge. Availability was verified on the owner's plan before any console step was written. Three earlier sessions had written steps for a screen the plan lacks.

**Principle:** An agent identity indistinguishable from the owner's makes code owner review unenforceable.

**Tags:** System, System, Architecture

---

## The App Keeps the Merge Endpoint and Still Cannot Merge Unapproved Work

**Date:** 8 August 2026
**Type:** Decision
**Generation:** SYSTEM

Three structured selections closed ADR-0003 and ADR-0004. The identity chosen is a gated GitHub App rather than the structural fork model. The App retains the merge endpoint, so the delivered property is that it cannot merge anything the owner has not approved. That is weaker than literal merge incapability, and it was accepted knowingly. Console steps already existed in agent-identity.md section 7.

**Principle:** Name the property a design actually delivers, then accept it or reject it.

**Tags:** System, System, Decision

---

## A Ledger Saying the Prompt Was Never Written, Beside the Prompt

**Date:** 8 August 2026
**Type:** Decision
**Generation:** SYSTEM

recorded that prompt-0009 would deliberately not be written in that session. The owner then asked for it. The ledger is append-only, so the earlier consequence is superseded by reference and the original selection stands. Editing it away would leave the record and the repository disagreeing, which is the divergence this lab keeps finding. The prompt itself grants nothing until the owner hands it over.

**Principle:** Record a superseded consequence by reference, never by editing the entry that holds it.

**Tags:** System, System, Decision

---

## Commits That Said Bot While the Push Authenticated as an Admin

**Date:** 8 August 2026
**Type:** Fix
**Generation:** SYSTEM

prompt-0009 asked the next session to prove the merge loop with the first bot authored pull request. Without an installation token, the push carries the owner's classic PAT. GitHub records the author as the pusher, and that identity is a repository admin who bypasses main-review. The commits would still say hendry-ai-agent bot, and the gate would never fire. The helper became a precondition. It fails closed if workflows or administration is granted.

**Principle:** Attribution and authentication are different things, and only the second one gates a merge.

**Tags:** System, System, Fix

---

## Thresholds Set Before a Single Run Existed

**Date:** 8 August 2026
**Type:** Decision
**Generation:** SYSTEM

The gate for create.revertRate was fixed before the first run produced any number. That ordering is the substance. Revert rate under 10 percent, over a sample of at least 30 merged pull requests. A rejection at review counts as the gate working, so it is reported and does not gate. Check passed but wrong is zero, where one instance disqualifies. Zero reverts across 37 pull requests reads as weak evidence.

**Principle:** Set the passing grade before any result exists, or you have not evaluated anything.

**Tags:** System, System, Decision

---

## The First Bot Authored Pull Request, on Check Machinery Under CODEOWNERS

**Date:** 8 August 2026
**Type:** Release
**Generation:** SYSTEM

The owner minted a one hour installation token: contents write, metadata read, pull requests write, nothing else. The session stat'd its path and mode, never its value. Item one was a drift check against numbers already recorded, which is a stronger test than discovery. The first bot authored pull request fixed parity-render.ts. It was chosen because it is check machinery under CODEOWNERS, which exercises code owner review rather than avoiding it.

**Principle:** A drift check against recorded numbers tests more than discovery does.

**Tags:** System, System, Release

---

## Chosen for SQL Queryability, Rebuilt on Files and Checks

**Date:** 7 August 2026
**Type:** Architecture
**Generation:** SYSTEM

Enforcement code was dropped for a read-only ADR. It had to record why the CMS was chosen in the first place. Postgres queryability, on the belief that SQL was the more agent-ready substrate. That premise inverted. Files, git, and required checks proved better for agents, with queryability served by a rebuildable index derived from git. The marketing adapters still landed test-first.

**Principle:** Record the premise behind an old choice, then check whether it still holds.

**Tags:** System, System, Architecture

---

## Do Not Block Any Article

**Date:** 7 August 2026
**Type:** Decision
**Generation:** SYSTEM

Three messages retired article and image disclosure gating. The agent stated the regulatory exposure once, the owner reaffirmed, and it was not re-litigated. The instruction was read narrowly: remove every path by which anything disclosure-related can block an article. Two carve-outs were kept and reported for veto. The site had already carried a visible AI colophon for about a year.

**Principle:** State the risk once, record the answer, then execute without re-litigating it.

**Tags:** System, System, Decision

---

## Proceed on a Gate Whose Check No Longer Existed

**Date:** 7 August 2026
**Type:** Decision
**Generation:** SYSTEM

The owner said proceed on Phase C. The session did not build it. Phase C was specified as a ruleset requiring the disclosure check, and that check had been removed the day before. The required check needed re-specifying first, so the question went into the next session's prompt. Removal of the disclosure machinery went ahead in full. That included the architecture doc describing a gate that no longer exists.

**Principle:** When the premise changed since the request, re-specify the scope before building.

**Tags:** System, System, Decision

---

## A Preview URL That Could Carry a Secret

**Date:** 7 August 2026
**Type:** Fix
**Generation:** SYSTEM

The CMS adapter had been holding the dry run since July. It dropped seriesLabel and subtitle, demanded an explicit numeric parent, and could emit a preview URL carrying a secret. Fixing it came first, as its own commit with an acceptance test. One environment note went into the record: the sandbox denies.env reads, so git rendered the tracked.env.example as a phantom deletion. The tree was clean.

**Principle:** Repair the publish path before the content, or the defect ships with it.

**Tags:** System, System, Fix

---

## Four Voice Violations Behind Eleven Unaudited Rules

**Date:** 7 August 2026
**Type:** Learning
**Generation:** SYSTEM

The owner asked whether the voice rules had been followed. The honest answer took a manual pass, because eleven voice rules are declared manual and no gate reads them. The prose had passed every executable check. The audit still found four violations in the agent's own new writing: three opposite-line patterns and one dramatic thesis. Build Log 02 was then grounded in 80 dated session entries and 125 recorded engine versions.

**Principle:** Green gates cover only the rules that execute. Audit the manual ones by hand.

**Tags:** System, System, Learning

---

## The Digest Moved After the Owner's Last Look

**Date:** 7 August 2026
**Type:** Release
**Generation:** SYSTEM

Publication was conditioned on the owner's go on the exact bytes. The Build Log digest had moved since their last rendered look, after three takeaway blocks came out at their request. The new digest and a re-rendered preview were in the message they replied to, so the go covered the current bytes. That reasoning went into the record rather than being assumed. The Framework update had no draft stage and went live on write.

**Principle:** When approved bytes change, name the change and the moment approval covered it.

**Tags:** System, System, Release

---

## Seven Grid Columns for a Five-Step Flow

**Date:** 7 August 2026
**Type:** Fix
**Generation:** SYSTEM

Two figures broke on a live page. The flow template hardcodes seven grid columns, which fits four steps and three arrows exactly. A five-step flow wraps its last arrow onto a second row. The P&L template got 40 to 50 character sentences in a slot sized for short values. The component fix keeps four-step flows emitting the identical column string, so three other articles stay provably unchanged. Six unrelated viewport-unit rules were left alone.

**Principle:** Fix the defect you were sent for. Queue the ones you found on the way.

**Tags:** System, System, Fix

---

## Export From the Database, Never From the Seeds

**Date:** 7 August 2026
**Type:** Decision
**Generation:** SYSTEM

Every count in the ADR was inferred from code and session logs. W0 replaced them with a read-only enumeration of the live database. The export tool reads database state and writes a candidate file tree into lab-owned staging, with a round-trip integrity report. Replaying seeds or engine JSON was forbidden, because both are stale and would silently roll back sessions of design work. Five owner sub-decisions were held conditionally: stop, do not work around.

**Principle:** Export from live state. Seeds and generator output roll back work you cannot see.

**Tags:** System, System, Decision

---

## An Autonomy Definition Left Open on Purpose

**Date:** 7 August 2026
**Type:** Architecture
**Generation:** SYSTEM

The ADR designs delegated-authority envelopes: scope, expiry, revocation, and machine-checkable predicates. It decides and builds nothing. A published article already states an autonomy position that conflicts with the internal direction. The entry records that tension and leaves it open. The primitives are designed level-agnostic, so they hold wherever the definition lands. The owner reserved the definition of full autonomy for a later discussion with its own starting material.

**Principle:** Design the primitive to be level-agnostic when the level itself is still undecided.

**Tags:** System, System, Architecture

---

## English Only, and a Path Shape That Survives It

**Date:** 7 August 2026
**Type:** Architecture
**Generation:** SYSTEM

Research produced the definitive sitemap and the agentic layer spec. The site went English-only in the same exchange, so de and pl were dropped and Chinese deferred to 2027. That removed per-locale variants, hreflang emission, per-locale sitemaps, and locale-aware routing from the migration. One cheap hedge stayed: content lives at slug/index.json, so a locale later is an additive sibling file. Also recorded for later, cn is a country code and hreflang wants zh.

**Principle:** Pick the path shape now so a future locale is only an added sibling file.

**Tags:** System, System, Architecture

---

## One Sanctioned Write Path Outside the Repository

**Date:** 6 August 2026
**Type:** Feature
**Generation:** SYSTEM

The owner wanted the wrap-up kit reusable and un-nested. Moving it above the repo would have cost history, receipts, and test protection. The kit stayed at kits/wrapup-kit/ and gained a carried copy at a carried copy of wrapup-kit, refreshed by npm run kit:carry. That script is the only sanctioned out-of-repo write path. It never runs from a gate and refuses uncommitted kit state.

**Principle:** Keep the canonical copy under version control and carry a stamped distribution copy.

**Tags:** System, System, Feature

---

## Two Dated Deadlines Behind One Disclosure Gate

**Date:** 6 August 2026
**Type:** Decision
**Generation:** SYSTEM

A session prompt opened the provenance and disclosure gate work as research and design only. The regulatory frame was dated and specific: EU AI Act Article 50 and California CAITA operative from 2 August 2026. A machine-readable marking backstop lands 2 December 2026, alongside C2PA 2.4. Orientation came from tracked records only. The prior session's green receipt had to be confirmed before anything was created.

**Principle:** Name the dated deadline in the authorization, so the scope has a clock.

**Tags:** System, System, Decision

---

## The Word Move Granted No Relocation

**Date:** 5 August 2026
**Type:** Decision
**Generation:** SYSTEM

The owner wrote you recommend and move. The entry reads that as adopting the recommendation, and records that the word move grants no filesystem relocation. Relocation keeps its own gate, after M1 and M2 acceptance. His one reservation was cloud storage, and it became a hard rule. Archives default to an external disk. Any cloud destination needs encryption under an owner-held key that never enters tracked evidence, plus its own authorization.

**Principle:** Encrypt before any cloud archive, with a key that never enters tracked evidence.

**Tags:** System, System, Decision

---

## M1 Accepted at main@b5cd031, 62 Tests Green

**Date:** 5 August 2026
**Type:** Release
**Generation:** SYSTEM

M1 is accepted at lab main@b5cd031 with 62 tests green. The shipped set is registry v2 with a workspace-identity recovery marker, a realpath-aware resolver, and six migrated consumers. It also carries permissions-digest pinning, out-of-process approval receipts, and run-location pinning that refuses on mismatch. The acceptance grants nothing beyond gate state. Remaining scope continues under the authority that opened it.

**Principle:** Pin acceptance to a commit. Later work continues under the authority that opened it.

**Tags:** System, System, Release

---

## Three Root-Neutralizations, Three Commits, Three Acceptance Tests

**Date:** 5 August 2026
**Type:** Decision
**Generation:** SYSTEM

Three absolute paths become root-neutral: the sibling derivation in the marketing tooling, the preview CSS derivation, and the website's marketing-artifact path. Each lands as its own commit in the repository that owns it, under sequential handoff, each shipping an acceptance test. Nothing else in those repositories is touched. Git status is captured in all three checkouts before any write. Enterprise paths stay outside the grant.

**Principle:** One repair, one commit, one acceptance test, in the repository that owns the file.

**Tags:** System, System, Decision

---

## M2 Accepted at Four Exact Heads

**Date:** 5 August 2026
**Type:** Release
**Generation:** SYSTEM

M2 is accepted at the exact heads presented, all four re-verified clean immediately before the entry. The dual-topology fixtures and the historical-path consumer tests are green. Two post-move path changes are unavoidable, and both are named in advance. One is an owner-gated sync at the new root, forced by a drift gate that fails closed on the legacy stamp. The other is doc-string edits. No future path was activated.

**Principle:** Bind acceptance to exact heads and name the path changes the move will force.

**Tags:** System, System, Release

---

## A Presence-Only Sweep for Bindings Outside the Repo

**Date:** 5 August 2026
**Type:** Decision
**Generation:** SYSTEM

Before moving anything, the sweep looks for references to the five registered roots that live outside them. It probes editor storage, shell profiles, deployment config names, crontab, user LaunchAgents, scheduler files and live process working directories through lsof. Every probe is filtered to the five root path strings, and only presence and location are recorded. No secret is read. Repointing what it finds is a separate grant.

**Principle:** The word continue authorizes the named step and nothing after it.

**Tags:** System, System, Decision

---

## A 60-Minute Abort Threshold Written Down Before the Move

**Date:** 5 August 2026
**Type:** Decision
**Generation:** SYSTEM

The owner waived the external disk verification and handed decisions D3 to D7 to the session. The session wrote down its own picks before acting. Durability meant full-ref bundles with clone-back fsck proofs. The window was two hours, the abort threshold 60 minutes to green M5, retention 14 days. Staging sat outside the moving trees, and M8 acceptance stayed with the owner.

**Principle:** Write down the defaults you were delegated before you execute them.

**Tags:** System, System, Decision

---

## Three Local-Only Commits in a Repo Marked Retire

**Date:** 5 August 2026
**Type:** Learning
**Generation:** SYSTEM

The agent's P0 disposition read Retire across both Listen repositories. The owner corrected it: retire the coupling and listen-build, keep listen-discuss, which holds early GTM and signal rails. A metadata read confirmed nothing had changed. listen-discuss stood at 38 MB, last commit 957ec6b on 31 May 2026, main ahead 3 of origin. Those three commits exist only on this machine.

**Principle:** A retire label needs a named object, the coupling or the repository.

**Tags:** System, System, Learning

---

## Lineage Says hendry.ai, Dependencies Say Stay in Dev

**Date:** 5 August 2026
**Type:** Decision
**Generation:** SYSTEM

listen-discuss belongs to hendry.ai by lineage. It was the early GTM signal engine, the peer of the create-articles engine. It stays in the old dev tree anyway. Many folders read from it. Those inbound dependencies get inventoried and closed before it moves. Durability closed first: HEAD matched origin/main at f0e7cb1, tree clean, 4.4 MB of untracked data preserved by design.

**Principle:** Brand lineage decides where a repository belongs. Inbound dependencies decide when it moves.

**Tags:** System, System, Decision

---

## Accept, and the Snapshots That Outlive the Move

**Date:** 5 August 2026
**Type:** Release
**Generation:** SYSTEM

One word, accept, closed Wave 1. The new root is authoritative after a day of the owner's own use with no defect reported. Six repository heads were re-verified clean and aligned before recording. The acknowledgment carries a caveat worth keeping. APFS local snapshots and Time Machine hold the pre-move tree independently, so a restore can resurrect old paths. Rollback material stays until 19 August 2026.

**Principle:** Record what the filesystem retains after a move, not only what moved.

**Tags:** System, System, Release

---

## The Learning Index May Never Gate a Run

**Date:** 5 August 2026
**Type:** Decision
**Generation:** SYSTEM

Fourteen read-only researchers and a completeness critic produced the frontier recalibration record. No writes, boundaries held. The Pilot A design was approved: a deterministic learning index, a fail-closed drift check in wrapup:check, and an operator-log compiler. Every compiled claim has to resolve to an index entry. One constraint bounds all of it. The index may never become a runtime dependency of any gate, loop, or run.

**Principle:** A derived index earns its place by being rebuildable, never by being depended on.

**Tags:** System, System, Decision

---

## Four Owner Answers and a Lab-Only Write Grant

**Date:** 4 August 2026
**Type:** Decision
**Generation:** SYSTEM

The first ledger entry records four owner answers taken as structured choices. The umbrella is the lab umbrella, deliberately not a Git repository. The pending Listen disposition blocks only the context move, so the authority-model work can continue. Durability goes remotes first. The grant covers lab writes for redlines R1 to R15 and nothing else. Architecture acceptance was held back so it could bind post-redline digests.

**Principle:** Defer acceptance until the redlines land, so the signature binds the corrected digest.

**Tags:** System, System, Decision

---

## Architecture Accepted, Zero Implementation Authority

**Date:** 4 August 2026
**Type:** Decision
**Generation:** SYSTEM

Gate A accepted the architecture: the umbrella, the perimeter, one control plane, and registry v2 with model-first sequencing. The grant attached to that acceptance is nothing. Implementation needs its own authority, which later entries cite back to this line. It binds two digests. Status annotations added later change those digests without changing what was accepted.

**Principle:** Accepting an architecture grants no implementation authority. Say so in the entry.

**Tags:** System, System, Decision

---

## A Sibling Pointer Classified Stale, Zero Bytes Changed

**Date:** 4 August 2026
**Type:** Decision
**Generation:** SYSTEM

One canon file, line 159, points sideways at a growthsetting document through a relative path. The owner classified that pointer stale for migration. The entry records the classification and nothing else. Severing it is a separate canon patch under its own permission class, so no canon byte moved on this decision. Deciding what something is stays apart from acting on it.

**Principle:** Classifying a pointer stale and severing it are two grants.

**Tags:** System, System, Decision

---

## One Read-Only Pass Over Two Listen Checkouts

**Date:** 4 August 2026
**Type:** Decision
**Generation:** SYSTEM

The owner authorized one read-only pass over listen-build and listen-discuss to produce the P0 evidence record. Writes, registry admission and any dismantling stayed out of the grant. He also said the coupling was a tested experiment that did not work, and leaned toward leaving it alone. The inventory recommends retiring it. The disposition itself is recorded as its own entry, after confirmation.

**Principle:** Authorizing the inventory is one grant. The disposition it recommends is another.

**Tags:** System, System, Decision

---

## Retire Means Non-Active and Preserved Byte for Byte

**Date:** 4 August 2026
**Type:** Decision
**Generation:** SYSTEM

The P0 disposition is retire. Both Listen checkouts stay byte-for-byte as they are, including the dirty working tree in one of them. Neither enters the perimeter or the registry, and nothing is dismantled. If a retired session is ever revived after the move, its bootstrap halts fail-closed and its pointer is repaired then. Retirement here changed zero bytes and unblocked the context relocation.

**Principle:** A disposition that changes zero bytes is still a decision worth recording.

**Tags:** System, System, Decision

---

## One Permission, One File, One Row Mirrored

**Date:** 4 August 2026
**Type:** Decision
**Generation:** SYSTEM

The owner's permission was broad and vague: go take it, I do not know where it is. The grant written down was one read of one exact path. The decision row sat at the head of that file and was mirrored here verbatim. It locks a separate Hendry-owned workspace, brand-first roots for hendry-ai and growthsetting, and repositories moved intact. Adjacent rows from enterprise work were not copied across.

**Principle:** Write the narrow grant the broad permission implies, then read exactly that.

**Tags:** System, System, Decision

---

## The Invalid Token Was the Sandbox Blocking the Keychain

**Date:** 4 August 2026
**Type:** Learning
**Generation:** SYSTEM

The push failed with what looked like an invalid token. The sandbox was blocking keychain access, and the token was fine. After that, four Wave-1 histories went off device to private remotes, each verified local against remote. Proof is an independent clone back, with git fsck --full clean and the cloned head equal to local main. Credential values were used by git and never read.

**Principle:** Prove a push by cloning it back. Local equals remote is not enough.

**Tags:** System, System, Learning

---

## Three SHA-256 Digests Bound Before the Task Ran

**Date:** 4 August 2026
**Type:** Decision
**Generation:** SYSTEM

The owner's authorization message sets its own order of operations. Read the ledger, compute SHA-256 over the three governing documents, record the authorization quoting the message in full, then execute. The task is bound to those exact revisions, so a later edit cannot quietly widen it. The hard limits name registered repositories only, with enterprise paths excluded. Two of the digests differ from an earlier acceptance because status rows were appended.

**Principle:** Bind the authorization to digests, so the scope cannot be edited after the grant.

**Tags:** System, System, Decision

---
