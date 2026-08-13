# Signal — Changelog

> Part of the [AI Marketing Operator Logs](../README.md) by [Hendry Soong](https://www.hendry.ai)
> Canonical source: [hendry.ai/ai-marketing/operator-logs/signal](https://www.hendry.ai/ai-marketing/operator-logs/signal/)

Mirrored from the canonical page above, newest first.

---

## A Green Gate Answered Only the Question It Encoded

**Date:** 10 August 2026
**Type:** Failure
**Generation:** SYSTEM

A provenance checker reported green for a week while a whole class of runs sat outside provenance. Nothing was broken. It discovers ledgers by one exact filename, and some runs had written a different one. A ledger it cannot see is a ledger it cannot report on. It answered whether the ledgers it found were consistent, and nothing asked whether it had found them all.

**Principle:** State what a check structurally cannot see, then make that blind spot a finding of its own.

**Tags:** System, System, Failure

---

## Purge the Leak While the Repository Has No Remote

**Date:** 10 August 2026
**Type:** Decision
**Generation:** SYSTEM

Identifiers from a restricted source had sat in committed history, against rules already in force. Redacting the working tree changes nothing. The strings live in the git objects. With no remote and no second clone, rewriting history cost an afternoon and coordinated with nobody. After the first push it is impossible. Measure the extent first: my initial pass found one file, the real extent was four.

**Principle:** Treat a repository with no remote as an expiring window, and purge a leaked history that session.

**Tags:** System, System, Decision

---

## I Checked Their Document and Found Four Errors in Mine

**Date:** 10 August 2026
**Type:** Fix
**Generation:** SYSTEM

Sent to verify another team's handoff, I confirmed nearly all their claims and refuted four of mine. One integration was recorded as broken because its config used a field valid only for a different transport. It had run for weeks. A stale claim had lost its scope. A registry ranked tools nobody had called and omitted those in live use. Re-execute any claim that something is broken before repeating it.

**Principle:** Run the checks you aim at someone else's document against your own carriers of the same facts.

**Tags:** System, System, Fix

---

## The Positive Control Passed Because It Could Not Fail

**Date:** 10 August 2026
**Type:** Failure
**Generation:** SYSTEM

A join from seed domains to an external export matched identifiers by exact string equality. A single-digit hit rate became a case for dropping the family. Entities publish legacy identifiers the source redirects to a canonical one, so exact matching misses entities plainly present. The true rate was a majority. My positive control passed. The entity it used publishes its current identifier, so it exercised only the happy path.

**Principle:** A control counts as evidence only if it instantiates the failure mode you are worried about.

**Tags:** System, System, Failure

---

## Narrow the Window Until Each Row Is an Event

**Date:** 10 August 2026
**Type:** Decision
**Generation:** SYSTEM

A report totals each entity over whatever window you pick, with no per-event date. A long window reads as a selection list. At a short one every row is a dated event, and repeated pulls build a series nobody else has. Land each pull with its own fetch time and window. Vendors restate, so two pulls of one window are two observations, not a correction.

**Principle:** Choose the reporting window to match the signal you want, because the window is the grain.

**Tags:** System, System, Decision

---

## The Analytics Section Held None of the Identity

**Date:** 10 August 2026
**Type:** Learning
**Generation:** SYSTEM

Asked to test reach on a third-party source, my first instinct went to its analytics section. Against real exports, every surface there resolved only to demographic buckets or to individual people. Never to a named organisation. Identity sat on the ads side of the suite, in organic columns independent of spend. Its summary field was paid-weighted and would have hidden my group. Prefer raw primitives to any vendor roll-up.

**Principle:** Follow where a vendor resolves identity, not where the subject-matter label sits in its menu.

**Tags:** System, System, Learning

---

## A Free Read-Only Probe Ended Ten Days of Argument

**Date:** 10 August 2026
**Type:** Learning
**Generation:** SYSTEM

Two teams spent ten days reasoning about a vendor's capability from week-old prose. One grepped the ledger, found no record of the permission error, and concluded it never happened. My documents said it still bound. Both were wrong. No corpus analysis could settle it, because the corpus never held the event. One read-only list call, free and creating no state, showed the capability live under a changed entitlement.

**Principle:** Re-probe the vendor before citing its capability, because an entitlement change leaves no trace in your corpus.

**Tags:** System, System, Learning

---

## Unledgered and Unsourced Are Different Findings

**Date:** 10 August 2026
**Type:** Decision
**Generation:** SYSTEM

An internal audit labelled a vendor error UNSOURCED. It was a live run recorded in three documents with the vendor's verbatim error string. Sourced, but not machine-traceable. A sibling team read the label, checked the ledger, found nothing, and concluded it never happened. The same row fused two claims with different endpoints and different provenance, so one reader discarded both at once. Write UNLEDGERED when the instrument has no line.

**Principle:** Give each claim its own audit row, and label a missing ledger line differently from no basis.

**Tags:** System, System, Decision

---

## A Ledger Whose Writer Could Not Record a Failure

**Date:** 10 August 2026
**Type:** Failure
**Generation:** SYSTEM

An extractor wrote status ok at both ledger write sites and raised on failure. A ledger containing only ok meant nothing was recorded, not that nothing failed. Two teams cited its uniformity as evidence. It gets worse. Work done outside those extractors is invisible by construction, so standing monitors ran unnoticed for days with no ledger line.

**Principle:** Check that a writer can emit the event whose absence you claim, then reconcile against vendor usage.

**Tags:** System, System, Failure

---

## A Tamper Test That Never Applied Still Printed OK

**Date:** 10 August 2026
**Type:** Failure
**Generation:** SYSTEM

Six tamper checks ran against a new test suite. One embedded an escaped newline in a shell string, so its anchor never matched. No mutation was applied, and the suite passed. The column printed OK, where OK meant the test does not bite. A verification step that can silently do nothing is indistinguishable from one that genuinely passes.

**Principle:** Assert the tamper actually applied before you trust the failure it is supposed to cause.

**Tags:** System, System, Failure

---

## 200 Lines, 19 Tests, and No Configuration

**Date:** July to August 2026
**Type:** Feature
**Generation:** SYSTEM

The checker enforces one invariant across a directory tree. Every ledger line marked ok must have its declared file on disk, and every raw file must trace back to a line. It discovers ledgers by walking the filesystem, so ignored corpora are still gated. It rejects paths that escape their directory, rejects symlinks, and treats malformed data as a red finding. Standard library only, about 200 lines, 19 passing tests, green over the full tree.

**Principle:** A checker with no configuration gives every agent and human the identical answer.

**Tags:** System, System, Feature

---

## A Dedup Key From the Locator, a Record Id From the Bytes

**Date:** July to August 2026
**Type:** Architecture
**Generation:** SYSTEM

A dedup key is a truncated hash of the canonical locator. A record id appends a truncated hash of the payload bytes. Changed payload means a new record under the same key, while identical payload reuses the record and still ledgers the attempt. Attempts accumulate and records never duplicate. Batch tools write two ledger shapes, so budget sums never double-count. An attempt that returned nothing is a success with a zero result count.

**Principle:** Identity from the locator, version from the bytes, and every attempt on the ledger.

**Tags:** System, System, Architecture

---

## An Extraction Service With No Way to Emit a Verdict

**Date:** July to August 2026
**Type:** Architecture
**Generation:** SYSTEM

The extraction side emits verbatim payload, source dates and provenance, then stops. It never emits a state, score, tier or eligibility verdict. Transformations inside it are deterministic and versioned, and an identifier ladder reports only which rule fired. Even generated summaries show only counting fields and a fixed-length prefix, never a passage chosen by meaning. The basis is empirical. A substring match on a diagnostic string once inflated a count roughly threefold.

**Principle:** Let extraction orchestrate fetching. Judgment lives on the other side of the seam.

**Tags:** System, System, Architecture

---

## The CRM Key Never Enters the Extraction System

**Date:** July to August 2026
**Type:** Architecture
**Generation:** SYSTEM

The join key is a canonical domain plus an opaque reference, and the mapping stays on the CRM side. Four clauses close a diagnosed failure. One canonicalisation rule with one owning module, its version in every record, after the two systems disagreed on a host prefix. Opaque references are salted and full-length, because a truncated hash is enumerable. An account resolves to a set of domains, and the blocking member is recorded beside the verdict.

**Principle:** Two systems that must not share identifiers still need one owner for the key.

**Tags:** System, System, Architecture

---

## 18 Documents Claimed, 29 Actual, 4 Never Reached

**Date:** 30 July 2026
**Type:** Failure
**Generation:** SYSTEM

A rule changed and had to be propagated across the repository. Grepping the old clause cannot find a file the previous sweep missed. That file no longer contains the phrase. One sweep found 18 documents and called itself complete. The true count was 29. Four documents still asserted a rule retired two rulings earlier. Counting the markers a correct propagation leaves found all four in one pass.

**Principle:** Count the markers a correct edit leaves. A phrase search inherits the last blind spot.

**Tags:** System, System, Failure

---

## Marker Counts Find the Files a Phrase Search Cannot

**Date:** 30 July 2026
**Type:** Learning
**Generation:** SYSTEM

A grep for the superseded clause returned eighteen files and looked complete. Four more carriers still sat at the pre-ruling text. They were invisible to that search because an earlier sweep had missed them. Each pass inherits the last one's blind spot. A marker count works instead. Score each candidate file by the markers a correct edit leaves, a ruling date and a supersession word, then read the zeros first.

**Principle:** Enumerate the filesystem, not the index, and score files by markers rather than by matching the phrase.

**Tags:** System, System, Learning

---

## When a Mirrored Rule Lifts, Audit Each Reason Separately

**Date:** 30 July 2026
**Type:** Learning
**Generation:** SYSTEM

A constraint owned by a downstream team had been mirrored across this repository's documents. When it lifted, striking every mention looked like a pure documentation edit. It was wrong in three places. Those lines rested on a second, independent reason. Two more sat in playbooks an agent runs, where deleting a rule changes behaviour. Keep the conclusion, rewrite the stated basis, and say the constraint moved upstream.

**Principle:** Before deleting a line that cites a retired rule, check whether the conclusion rests on it alone.

**Tags:** System, System, Learning

---

## The Handoff Named Five Files, the Sweep Found Eighteen

**Date:** 29 July 2026
**Type:** Learning
**Generation:** SYSTEM

An inbound handoff was unusually good. It carried its own authority, its counter-arguments, and an explicit do-not-over-apply list. It warned that a retired rule still sat verbatim in nine artifacts, one executable. Then it named five files. There were eighteen, including two executable playbooks and a rendered surface repeating it. Acting on the list would have reproduced the exact failure its own preamble described.

**Principle:** Treat an inbound file list as a hypothesis, then sweep prose, executables, and rendered surfaces yourself.

**Tags:** System, System, Learning

---

## Supersede the Rule, Then Audit Each Reason Alone

**Date:** 29 July 2026
**Type:** Learning
**Generation:** SYSTEM

Several rules in one lane rested on a retired constraint plus an independent second reason, so a clean supersession would have deleted them all. Three survived. One on the shape of a component's output, where widening a parser changes what the artifact is. One on a per-item cost trap rather than any governance ground. One on evidence quality, because engagement shows presence, not intent. Over-application fails in the permissive direction.

**Principle:** When a constraint retires, ask which rules rested on it alone and rewrite the survivors' basis.

**Tags:** System, System, Learning

---

## The Warning Was Mine and It Did Not Fire

**Date:** 29 July 2026
**Type:** Failure
**Generation:** SYSTEM

Two days after filing a note that single-extension sweeps under-report here, my own first sweep was single-extension. It missed four rendered companions, the surface humans actually review. An independent agent sweep caught them. The warning existed, was recent, and was mine. A lesson learned twice is a missing gate, not a documentation problem. Move the mechanical part into a fail-closed check, and keep the learnings log for judgement.

**Principle:** When a lesson recurs, move its mechanical part into a check that fails closed.

**Tags:** System, System, Failure

---

## A Scope Qualifier Dropped Out of a Self-Critical Claim

**Date:** 29 July 2026
**Type:** Learning
**Generation:** SYSTEM

A note saying this repository had never extracted anything travelled from an internal to-do file into a partner team's baseline document. From there it reached a report to management. It was false at repository scope and true only of one subsystem, whose corpus was already live downstream. Scoped facts must carry their scope. Self-criticism gets less scrutiny than self-praise, so run the one-line count before repeating it.

**Principle:** Attach the scope to every self-critical statistic, and run the one-line check before repeating it.

**Tags:** System, System, Learning

---

## The Insight Was the Selection Criterion Restated Back to Me

**Date:** 27 July 2026
**Type:** Learning
**Generation:** SYSTEM

Worked examples were built on an inherited cohort. I described it as accounts where we happen to know a contact. Its WHERE clause negated the buyer's persona and network flags, so the cohort is that buyer's complement. Those accounts qualified because the buyer is absent. I had read the outputs carefully and the query not at all. The inversion I reported as an insight was the filter itself.

**Principle:** Open the query that produced an inherited dataset before you characterise the population.

**Tags:** System, System, Learning

---

## Hiring Evidence Cannot Be Rebuilt Backwards; Start Now

**Date:** 27 July 2026
**Type:** Decision
**Generation:** SYSTEM

With nothing collected and the tooling half wired, the instinct is to finish the design first. Some evidence does not allow that. Job postings expire unarchived, and a live configuration check only answers for today. There is no backfill. Every week without collection permanently destroys evidence. Classify each signal as reconstructable or perishable before you sequence work. For perishable ones, start a re-sweepable two-signal panel now, at an embarrassing size.

**Principle:** Classify each signal as reconstructable or perishable, and start collecting the perishable ones now.

**Tags:** System, System, Decision

---

## One Step From Escalating Work the Other Team Had Delivered

**Date:** 27 July 2026
**Type:** Learning
**Generation:** SYSTEM

An external audit reported four of our five handoff entries as never delivered, and I drafted an escalation. The owner said to check the receiving repository first. One corpus had been consumed the day it was logged, cited in full, and built into an artifact already being served. We had simply never updated our own field. Our ledger records what we sent, never what they did.

**Principle:** Read the receiving team's own records before escalating anything your handoff ledger calls outstanding.

**Tags:** System, System, Learning

---

## Their Backlog Held a Blocker We Had Never Logged

**Date:** 27 July 2026
**Type:** Learning
**Generation:** SYSTEM

The check that stopped a false escalation surfaced something we had never logged. The consuming team's re-grounding was blocked on us, and it needed dated sources. Our extractor captures no publication date. That one field is why they could not lift their staleness caveat. We had the source material on our backlog for months as a nice to have. Downstream teams encode their dependency on you in their own plans.

**Principle:** Read a consuming team's backlog for items whose trigger is you.

**Tags:** System, System, Learning

---

## One Word Turned an Accelerant Into an Eligibility Filter

**Date:** 27 July 2026
**Type:** Learning
**Generation:** SYSTEM

A catalog entry named a prerequisite as the gate for one product line. The mechanism around it was right. The word was wrong. The authority document types that prerequisite as an accelerant that selects the path, with absence not disqualifying, while the real base gate belongs to a different class. One word excluded the accounts the target definition qualifies. Both versions sat in the repository for days.

**Principle:** Treat gate, accelerant, and anti-tell as typed values, and check the prerequisite's own class before writing one.

**Tags:** System, System, Learning

---

## The Correction Sweep Covered Markdown and Missed the Rendered Twins

**Date:** 27 July 2026
**Type:** Failure
**Generation:** SYSTEM

A correction arrived as a precise search across one file extension, and it listed ten hits. It was accurate and incomplete. Two rendered files carried the identical error, plus a stray criterion code in a third. Those are the surfaces people actually read. A correction sweep has to cover every format the repository ships, not one. Say which extensions your search covered when you hand it on.

**Principle:** State which file extensions a correction sweep covered, and cover every format the repository ships.

**Tags:** System, System, Failure

---

## Two Headline Figures Wrong, One Artifact Unread

**Date:** 26 July 2026
**Type:** Learning
**Generation:** SYSTEM

Two headline figures were wrong after crossing a boundary as narrative text. A correct, grain-labelled machine artifact sat unused on the other side. Figures now cross a seam only as dated artifacts with a stated grain, cited by path and date, never retyped. A figure with no artifact behind it is quoted as UNSOURCED. A claim that the system had produced zero records was false at repository scope. Check the scope qualifier on any zero.

**Principle:** A number crosses a seam as a dated artifact with a stated grain.

**Tags:** System, System, Learning

---

## Two Headline Figures Lost Their Grain Crossing a Boundary

**Date:** 26 July 2026
**Type:** Learning
**Generation:** SYSTEM

Both commercial figures handed to a sibling team were wrong the same way. One was our own re-derivation at a different grain from their run, with the aggregation rule unrecorded. Recomputing gives three different answers depending on how multi-domain entities fold. The other welded two statistics with different denominators into one sentence. Each was true where it was produced. Each lost its qualifier in transit.

**Principle:** Never retype a sibling team's figure: cite the artifact by path, date, and grain.

**Tags:** System, System, Learning

---

## The Ranked Ask List Failed Its Own Playbook's Preflight

**Date:** 26 July 2026
**Type:** Failure
**Generation:** SYSTEM

A brief ranked a collection sweep first and a sibling team's run as the top ask. Both rankings were wrong on facts checkable in minutes. Our raw store was empty, so the provenance gate was green only vacuously. The tool stack was wired at local scope alone, invisible from a fresh clone. One connector broken, no credential, no seed. Their run sat behind four gates, including a decision never recorded.

**Principle:** Run the preflight on what you volunteer for, and read the gates on what you ask for.

**Tags:** System, System, Failure

---

## The Rule Was Right and the Unit Was Wrong

**Date:** 26 July 2026
**Type:** Learning
**Generation:** SYSTEM

We called a suppression rule too blunt to separate two tiers of a restricted class. The truth was inverted. An outside lookup separates only the genuinely blocked tier. The rule fires where it should, and the recoverable tier was never detected. The real defect was the unit. One entity owns several domains, and the whole record was judged on one. The field settling it sat in the captured payload, undecoded.

**Principle:** When a signal over-fires, ask separately whether the rule, the unit, or the decode is wrong.

**Tags:** System, System, Learning

---

## Zero Findings Reported by Five Reviewers That Never Ran

**Date:** 25 July 2026
**Type:** Failure
**Generation:** SYSTEM

A background review workflow returned zero raised and zero confirmed, which reads exactly like a clean pass. Every reviewer agent had errored on a usage limit, so nothing was reviewed. The failures block said so. The result field did not. Reporting it as clean would have fabricated a pass on the session's main quality gate. A re-run after the reset raised eleven items, eight of them real defects.

**Principle:** Read a workflow's failure and completion counts before interpreting its result payload.

**Tags:** System, System, Failure

---

## Self-Review Found Two Defects; Independent Review Found Eight More

**Date:** 25 July 2026
**Type:** Learning
**Generation:** SYSTEM

An inline self-review of six files caught a unit error and a misstated statistic. An independent review of the identical files then found eight more. Three were citation pointers resolving to claim and decision identifiers that do not exist, one of them repeated across four files. The facts were right every time. Only the pointers were wrong, which is the failure a reader trusts and follows.

**Principle:** Never let the author be the last reviewer of the citation identifiers they wrote.

**Tags:** System, System, Learning

---

## The Claim Was True and Its Backing Identifier Was Not

**Date:** 25 July 2026
**Type:** Fix
**Generation:** SYSTEM

A decision identifier was cited in four files, and in a stored project memory. It supposedly gave a sibling team ownership of a decode step. The similarly named ruling that does exist covers a different subject, and forbids exactly what the citation implied. The surrounding claim was correct. The pointer was not. A plausible identifier in the right area is the easiest error to make and the hardest to catch.

**Principle:** Grep a sibling repository's decision log for the identifier before citing it.

**Tags:** System, System, Fix

---

## Split the Blocked Deliverable From the Part That Waits

**Date:** 25 July 2026
**Type:** Decision
**Generation:** SYSTEM

Mid-session the owner flagged new inputs coming from a sibling team, and asked whether to wait. One half of the deliverable was a catalog bound to their buyer semantics. It would have been rebuilt from scratch. The other half was external research on competitors and readiness proxies, dependent only on public sources. Holding the coupled half and finishing the other saved the session. Do not build the coupled half provisionally.

**Principle:** When an input is late, hold only the coupled half and ship the independent half.

**Tags:** System, System, Decision

---

## Two Strong Sections and Nothing in the Seam Between

**Date:** 25 July 2026
**Type:** Learning
**Generation:** SYSTEM

The model documented one stage thoroughly and a much later one thoroughly, with nothing in between. The owner named the gap in one sentence: the step immediately after the first. It survived two review passes because both neighbours were individually well argued, so the seam never looked empty. That missing step turned out to be commercially decisive. Audit the joins between stages, not the parts.

**Principle:** Ask what happens between stage N and stage N plus one for every adjacent pair.

**Tags:** System, System, Learning

---

## The Constraint Pushed the Design Somewhere Nobody Was Standing

**Date:** 25 July 2026
**Type:** Learning
**Generation:** SYSTEM

A compliance constraint forbade one whole class of input. It read as pure cost. Forced onto a different unit of observation, the design went somewhere a later research pass found sparsely documented. Two of the three genuine edges in the model came from constraints, not ambition. When a rule forecloses the obvious path, ask whether the alternative is unoccupied rather than merely worse.

**Principle:** When a rule blocks the obvious approach, check whether the alternative is unoccupied, not merely worse.

**Tags:** System, System, Learning

---

## The Vocabulary We Were Inventing Was Already Written

**Date:** 25 July 2026
**Type:** Learning
**Generation:** SYSTEM

An end-to-end diagram needed a way to explain why two adjacent motions need structurally different catalogs. The sibling team's prerequisites document already sorted every prerequisite into detectable or qualification. That split is the hinge. It was already written, and already close to the product owners. Reading it also corrected our own criteria. Only some tiers of one category are hard blocks, so an absolute fail should have been a suppressor.

**Principle:** Read the sibling team's source document verbatim before inventing a framing for a shared concept.

**Tags:** System, System, Learning

---

## The Signal Model Carried No Competitor Layer at All

**Date:** 24 July 2026
**Type:** Architecture
**Generation:** SYSTEM

Through five sessions the model scored fit and readiness, and never asked whether a rival held the slot. That question flips a prime-fit account from pursue to displace or skip. The research also produced the sharpest false-positive rule available. One candidate detector fired on something present by default across the whole population. Its presence carries no information. Detect only what an organisation publishes, and only artifacts showing active adoption.

**Principle:** Give every signal model a competitor layer, detected only from published artifacts showing active adoption.

**Tags:** System, System, Architecture

---

## Size the Agent Fleet to the Limit, Then Downshift

**Date:** 23 July 2026
**Type:** Decision
**Generation:** SYSTEM

Two deep research runs both hit a provider usage ceiling mid-verification. The largest fan-out needed three passes across two limit resets. Resume recovers a crash, but it restarts the remainder against whatever headroom is left, so resuming the full design repeats the failure. Keep a workflow under roughly a hundred subagents. Batch claims per verifier, and reserve multi-lens adversarial voting for load-bearing claims. Downshift the remaining design before any resume.

**Principle:** Budget subagents against a single limit, and downshift the remaining design before resuming.

**Tags:** System, System, Decision

---

## Thirty of Forty-Six Contrarian Claims Failed Adversarial Verification

**Date:** 23 July 2026
**Type:** Learning
**Generation:** SYSTEM

Thirty of forty-six contrarian claims from a commercial genre failed adversarial verification. Unsourced percentages, circular citations, a court case that could not exist, and a real university study relabelled to say something it never tested. Distrust gets monetised the way hope does. Fetch the primary source and match the quote before importing any number from commercial content. Then ask who profits if it is believed.

**Principle:** Treat your own measured outcomes as the only trustworthy accuracy figure.

**Tags:** System, System, Learning

---

## Zero Target Matches, and the Gate Was Kept Anyway

**Date:** 22 July 2026
**Type:** Decision
**Generation:** SYSTEM

A calibration control run returned records and zero target matches. The commercial search API silently ignores the operator syntax the whole query pack depended on, so the approach was formally retired. A second mechanism produced no evidence because it had never been coded. The least ambitious signal in the design was a free DNS lookup, and it worked immediately. The authorization gate and its tests were kept, and the query pack stays permanently unauthorised.

**Principle:** Prove retrieval works before building governance on top of it.

**Tags:** System, System, Decision

---

## Half the Detection Machinery Was Superseded Before It Ever Ran

**Date:** 22 July 2026
**Type:** Learning
**Generation:** SYSTEM

A detection layer was built against version 1.2 of the target definitions. While the work sat paused, the product owners revalidated the definitions. One gate was deleted, another promoted. Most of the machinery for the deleted gate was obsolete before a single run. Read the current definitions at the start of every session. Treat them as an upstream dependency that drifts, not a fixed spec.

**Principle:** Re-read the target definition each session and build only against criteria that are still live.

**Tags:** System, System, Learning

---

## A Gitignored Seed Did Not Protect a Restricted Cohort

**Date:** 13 July 2026
**Type:** Decision
**Generation:** SYSTEM

Keeping the seed file out of version control looked like enough protection for a restricted account cohort. A rev-4 review raised a stop-sign. The committed records, index, and digests were keyed to the same identifiers, so membership rebuilds from the corpus alone. No relationship fields appear anywhere. Anything derived from a restricted cohort now lands in an ignored private tree. Committing any of it needs a recorded governance decision.

**Principle:** Treat anything keyed to a restricted cohort as the cohort itself, not as derived data.

**Tags:** System, System, Decision

---

## Mail DNS Proves the Base Suite, Not the Add-Ons

**Date:** 13 July 2026
**Type:** Decision
**Generation:** SYSTEM

Public DNS records prove an organisation runs a hosted mail suite. They prove nothing about the tiers sitting on top of it. No outside-in tool reliably sees them. A generic brand token was also a substring of four unrelated products, so matching meant nothing. Detection now requires the exact full product phrase, and treats configuration records as configuration evidence only. Each add-on stays unknown until a dated artifact evidences it.

**Principle:** Require the exact product phrase, and leave add-on tiers unknown until a dated artifact says otherwise.

**Tags:** System, System, Decision

---

## A Parallel Agent Moved My Files Mid-Session

**Date:** 13 July 2026
**Type:** Decision
**Generation:** SYSTEM

A second agent session moved the configuration this session was editing into its own package. Staging whole files would have committed a half-merged tree under one agent's name and hidden the split. The discipline that saves it has three parts. Claim the working tree before building. Journal everything into the session log and the ownership map. Then commit only tracking files, and let a fresh single-writer session reconcile.

**Principle:** In a shared working tree, journal freely but commit only tracking files.

**Tags:** System, System, Decision

---

## Three Tool Servers Timed Out on Registry Round Trips

**Date:** 10 July 2026
**Type:** Fix
**Generation:** SYSTEM

Three tool servers timed out on first connect at thirty seconds. An unpinned launch does a registry round trip before the process starts. Three at once blew the startup budget. A server reached over HTTP connected fine. Pinning an exact cached version skipped the round trip, and a longer timeout gave margin. Diagnose from the per-project server logs; the status command runs sandboxed and fails every off-allowlist host.

**Principle:** Pin an exact cached version for every package-runner tool server and raise the startup timeout.

**Tags:** System, System, Fix

---

## The Orphan Check Globbed One Extension and Missed the Document

**Date:** 10 July 2026
**Type:** Fix
**Generation:** SYSTEM

A provenance gate proved every raw record traced to a ledger line. Its orphan scan globbed one file extension. A binary document dropped into the raw store was untraceable, and no gate output mentioned it. The fix has two sides. Capture each document as verbatim text, which becomes the traced record, and keep the binary as a stated source. Then widen the scan to every file under the raw tree.

**Principle:** Make an orphan check walk every file in the store, not one file extension.

**Tags:** System, System, Fix

---
