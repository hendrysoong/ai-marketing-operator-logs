# Data — Verification — Changelog

> Part of the [AI Marketing Operator Logs](../README.md) by [Hendry Soong](https://www.hendry.ai)
> Canonical source: [hendry.ai/ai-marketing/operator-logs/data](https://www.hendry.ai/ai-marketing/operator-logs/data/)

Mirrored from the canonical page above, newest first.

---

## A Handoff Claimed Completeness and Dropped Four Rules

**Date:** 10 August 2026
**Type:** Failure
**Generation:** SYSTEM

A handoff gathered the binding contract for a new component. It opened by saying nothing below was new, merely collected. The list then dropped three clauses of the join contract it named, plus one ground rule, without a word. The recipient caught it. Framing turned an omission into a defect: a list presented as complete removes the reader's reason to open the source.

**Principle:** Enumerate a restated contract from source and assert the count, or say plainly the list is partial.

**Tags:** System, System, Failure

---

## An Order Check That Re-Sorted the File Before Comparing It

**Date:** 9 August 2026
**Type:** Failure
**Generation:** SYSTEM

A verifier asserted that a published list held its documented order. It re-sorted the frame on the sort keys, then compared the resulting rank column against a sorted copy of itself. Both sides are 1 to N whatever the file contains. A tamper that reordered every row passed green. Four other tampers in the same batch bit correctly, which made the gate look sound. Read the stored order instead.

**Principle:** Assert the key tuple is non-decreasing down the file exactly as it was written.

**Tags:** System, System, Failure

---

## One File, Two Boolean Encodings, Zero Rows Returned

**Date:** 9 August 2026
**Type:** Failure
**Generation:** SYSTEM

One file used a two-letter boolean encoding on some columns and a word encoding on others. An equality test hit the wrong family. Zero rows came back. Zero rows reads as an empty universe rather than an error. Two defects landed two hours apart in one session, one reporting zero reachable records across an entire population. Normalise flags through a helper that asserts both directions.

**Principle:** An all-true flag is as broken as an all-false one. Assert both directions.

**Tags:** System, System, Failure

---

## Two Correct Documents Pointing Opposite Ways at One Decision

**Date:** 9 August 2026
**Type:** Learning
**Generation:** SYSTEM

Two documents owned two halves of one decision. A strategy note deprioritised one segment and pursued others, reasoning from forward plans. Ranking our own records against that same product's stated customer profile landed the head of the list almost entirely inside the deprioritised segment. Neither document was wrong. Neither could see it, because the collision exists only when both are read against a single frame.

**Principle:** Apply the other document's ordering to your own data, then report the collision rather than settle it.

**Tags:** System, System, Learning

---

## Stronger Checks Made the Coverage Report Worse

**Date:** 7 August 2026
**Type:** Learning
**Generation:** SYSTEM

Converting nine hand-listed row expectations into cell-for-cell table comparisons made the checks far stronger. It also took the coverage sweep from 94 unverified figures to 268. The comparison emits one aggregate result where the old code emitted hundreds of check rows, so the sweep stopped seeing those cells as covered. Same change. An improvement on one report and a regression on the other.

**Principle:** Have an aggregate gate register every individual fact it proved into whatever the completeness sweep reads.

**Tags:** System, System, Learning

---

## The Tamper Never Landed, So the Green Meant Nothing

**Date:** 7 August 2026
**Type:** Failure
**Generation:** SYSTEM

A tamper test reported that corrupting a cell in a published table did not fail the build. That would have meant 540 unverified cells. The gate was fine. The one-line stream edit used a GNU address form that silently no-ops under BSD, so nothing was ever modified. The verifier correctly passed an untouched file. A negative tamper result is indistinguishable from a tamper that never happened.

**Principle:** Assert the mutation exists, by counting the pre-image in code, before believing any tamper result.

**Tags:** System, System, Failure

---

## A Forbidden List Recorded Only the Spellings Someone Remembered

**Date:** 7 August 2026
**Type:** Failure
**Generation:** SYSTEM

A lint gate for generated HTML listed the forbidden literals plus two entity forms of one. It did not list a further spelling, so a page shipped the violation in rendered output and passed. The list was the bug. It records the spellings someone happened to think of, and every new form is a silent hole. Third instance of that family in one repository.

**Principle:** Unescape the document, check what a browser renders, then tamper test with the violation that escaped.

**Tags:** System, System, Failure

---

## Every Defect in the Review Was Invisible From Inside One Document

**Date:** 5 August 2026
**Type:** Learning
**Generation:** SYSTEM

Each defect in one review was invisible from inside the document carrying it. Two documents side by side made them obvious. A quantity read one way on a page and differently on the page it cited as authoritative. A verifier stayed green because the page and its gate shared a superseded predicate. A per-document gate cannot see a seam. A repository holding three definitions of one concept has three answers.

**Principle:** Check each figure that appears in more than one place pairwise, across the documents.

**Tags:** System, System, Learning

---

## Pixel Values in a Style Block Read as Unverified Claims

**Date:** 5 August 2026
**Type:** Fix
**Generation:** SYSTEM

A page-scoped style block made a coverage sweep fail on five unverified figures that were pixel sizes. It stripped script content and not style content. An older verifier already did both. The same false positives came from ISO dates splitting on hyphens, SHA-256 yielding its bit length, and a number pattern swallowing a sentence comma. A sweep needs a tokenizer, not a regex. Every strip needs a comment saying why.

**Principle:** Tokenize the rendered document and strip script and style content before sweeping for unverified numbers.

**Tags:** System, System, Fix

---

## A Tamper Test Restored the Input and Poisoned the Outputs

**Date:** 5 August 2026
**Type:** Failure
**Generation:** SYSTEM

The harness altered a page, ran the verifier, restored it byte for byte, reported success. Both verifiers write a backing index on every run. The restore left those indexes holding the tampered output, and the poisoned rows were staged and committed. The checksum passed throughout: it watched only the input. A restore and verify that watches one file misses every side effect. Check the working tree, not just the checksum.

**Principle:** Enumerate a gate's outputs before tamper testing it, then re-run clean and check the working tree.

**Tags:** System, System, Failure

---

## A Name-Free Gate That Hardcoded the Names It Forbade

**Date:** 5 August 2026
**Type:** Failure
**Generation:** SYSTEM

I wrote a gate asserting that a shareable document holds no personal names. I implemented it as a regex listing those names. The gate passed and the document was clean. The checker itself carried real people's names into version control, and a sweep found them in the one file nobody thinks to check. Read the deny list from restricted data at runtime. The list then cannot drift from the data.

**Principle:** Read a sensitive deny list at runtime, and run every content check against the checker.

**Tags:** System, System, Failure

---

## I Reasoned About a Deliverable for Hours Without Rendering It

**Date:** 5 August 2026
**Type:** Learning
**Generation:** SYSTEM

I extracted the text of the v1 brief and reasoned about it correctly for hours. Then I built a visually weaker replacement. Someone pointed at the original later and said it looked good. It did, and I had never rendered it. Its layout carried most of its value: a glance strip, a year timeline, and numbered play cards. Text extraction is blind to every one of those.

**Principle:** Render any artifact whose format is part of its value before deciding to replace it.

**Tags:** System, System, Learning

---

## An Option Nobody Had Ever Used Contradicted Its Own Assertion

**Date:** 5 August 2026
**Type:** Failure
**Generation:** SYSTEM

A build script carried an option to keep links to companion documents that ship alongside a page. Its own assertion, that no dead sibling link survives, did not exempt those kept links. Declaring a companion aborted the build. The option had existed since the file was written and had never run. Feature and assertion were authored minutes apart and never exercised together. An unused path is an untested one.

**Principle:** Exercise an option in the session you add it, and treat any never-run path as broken.

**Tags:** System, System, Failure

---

## A Registry Listing Is Not Evidence a Job Ran

**Date:** 5 August 2026
**Type:** Learning
**Generation:** SYSTEM

A scheduler listing run from a non-GUI shell returned nothing for a job. Its definition sat on disk, and it had fired at the same minute on three straight days, exit clean. I already knew that probe reports false health on this machine. Here it reported false death. That is the same error pointed the other way. A listing probe from a different session context answers a different question.

**Principle:** Judge a scheduled job by its artifact or log line, never by a registry listing.

**Tags:** System, System, Learning

---

## The Tamper Test Passed Because a Warning Never Touched the Exit Code

**Date:** 4 August 2026
**Type:** Failure
**Generation:** SYSTEM

A coverage verifier was tamper-tested by dropping one invented figure into the document prose. It came back green. The direction that finds unverified numbers printed a warning and left the exit code alone. An earlier verifier had inherited the same defect. Coverage failures now exit non-zero. Every new gate is tamper-tested by breaking the thing it claims to catch.

**Principle:** A gate that only prints a warning passes every tamper you throw at it.

**Tags:** System, System, Failure

---

## A Green Verifier Whose Checks Read the Same Constant Twice

**Date:** 4 August 2026
**Type:** Failure
**Generation:** SYSTEM

A verifier reported all of its checks passing. Five of its assertions put the same constant on both sides, one buried inside a computed expression. They also sat on the coverage allowlist, so neither direction could see them. They surfaced only when an underlying rule changed. The remedy is a grep for expected and actual sharing a literal.

**Principle:** A check whose left side never reads raw data is documentation.

**Tags:** System, System, Failure

---

## The Checker Compared Against a Number Typed Into the Checker

**Date:** 4 August 2026
**Type:** Failure
**Generation:** SYSTEM

The first figure checker recomputed every number from raw, then compared it against a value typed into the checker itself. It reported 98 of 98 passing while the page said otherwise. It proved the arithmetic, not the artifact. A verifier has to parse the document, both ways. Every claimed value must appear on the page, and every printed number must be covered. Direction two found a table no code produced.

**Principle:** Make a verifier parse the document, and require every printed number to be covered by a check.

**Tags:** System, System, Failure

---

## Reducing Over a Set Picked a Different Winner Each Run

**Date:** 4 August 2026
**Type:** Fix
**Generation:** SYSTEM

Resolving a person to their best-scoring account reduced over a set with max and a key. Ties break on set iteration order. That order varied between runs, so a published count drifted by one and the losing value reached a page. Sort before reducing over any set. A published figure's producer has to be deterministic, so run it twice and diff the output before believing it.

**Principle:** Sort before reducing over a set, and prove a published figure's producer deterministic by running it twice.

**Tags:** System, System, Fix

---

## It Passed Contrast and Still Failed the Type Floor

**Date:** 4 August 2026
**Type:** Learning
**Generation:** SYSTEM

A report stylesheet was called hard to read. It measured 5.94:1 and passed WCAG, so contrast was not the fault. The design system sets minimum body and caption sizes. The sheet ran body under that floor at weight 300, with nine labels smaller still. Contrast maths assumes solid glyph coverage, and a thin stroke at small size has none. Audit computed styles in the rendered DOM rather than the source.

**Principle:** Check the design system's stated size and weight floors before trusting a passing contrast ratio.

**Tags:** System, System, Learning

---

## A Narrowed Exclusion Gate Passed by Excluding Everyone

**Date:** 4 August 2026
**Type:** Failure
**Generation:** SYSTEM

The fail-closed check read: no output file contains a member of the held population. The country-level hold was then narrowed, so most of that population should have been released. The check passed anyway. Absence is exactly what it asserts, so nothing failed and nobody was released. A narrowed gate fails as a quiet non-event. Assert both directions with counts, the same shape the page verifiers already use.

**Principle:** Assert a narrowed gate both ways: what stays excluded is absent, what was released is present.

**Tags:** System, System, Failure

---

## A Quick Recomputation Raised a False Alarm

**Date:** 4 August 2026
**Type:** Learning
**Generation:** SYSTEM

I reported two published figures as failing to reproduce and needing chasing. They reproduced exactly. My ad hoc query had omitted an exclusion the real verifier applies to the same population. I computed a different set and called the difference a defect, in a session where I was auditing others for that same class of error. Suspect the fast recomputation first. State the population predicate in full, every time.

**Principle:** Run the existing producer or verifier, not a fresh expression, before calling a published figure unreproducible.

**Tags:** System, System, Learning

---

## Correct In The Source, Broken In The Render

**Date:** 3 August 2026
**Type:** Fix
**Generation:** SYSTEM

Two defects in a generated deck read as correct in source. A tabular numeral setting sat on body, not on the elements holding digits, so every glyph on every slide widened. A structural selector out-specified the utility class it should have deferred to. Eleven of twelve navigation dots rendered as transparent circles. Auto-fit grids left orphan cells, because a minimum sets a floor and nothing set a ceiling.

**Principle:** Screenshot every generated page and read the render, because specificity and auto-fit grids fail silently in source.

**Tags:** System, System, Fix

---

## Both Wrong Figures Passed Their Own Selftests

**Date:** 3 August 2026
**Type:** Learning
**Generation:** SYSTEM

Two figures published earlier in the same session did not survive a deliberate attempt to refute them. An overlap of zero came from pairing two cohorts selected on incompatible criteria. It was an artifact, not an absence. A count was several times too low, because the query demanded an exact link into one system and dropped every record only a second system held. Both passed their own checks.

**Principle:** After publishing a figure, spend a pass refuting it by a different method.

**Tags:** System, System, Learning

---

## A 190 Line Checker That Exits 1 on a Missing Provenance Sidecar

**Date:** May to August 2026
**Type:** Architecture
**Generation:** SYSTEM

One JSON control plane on enterprise work declares every upstream data source. Each entry names what it answers, what it must not be used for, and where its output lands. A checker of about 190 lines walks the registry and the committed output tree. It exits non zero on a malformed registry, a missing script path, or a file with no provenance sidecar. The automation it governs can never write the registry.

**Principle:** The registry a checker enforces must never be writable by the automation it governs.

**Tags:** System, System, Architecture

---

## A Debt Registry With Mandatory Owner, Due Date and Reason

**Date:** May to August 2026
**Type:** Architecture
**Generation:** SYSTEM

A fail-closed gate needs somewhere to put inherited failures. A companion JSON registry takes them. Each entry names an owner, a due date and a written reason. The checker rejects an entry missing any of the three. Every run prints the registry, and a passed due date fails the gate again. Fixing a gap means deleting its entry, never extending the date.

**Principle:** A registered exception needs an owner, a due date and a written reason.

**Tags:** System, System, Architecture

---

## Six Refusal Rules Written Into the Only Module That Writes

**Date:** May to August 2026
**Type:** Architecture
**Generation:** SYSTEM

Governance for the one component that mutates an external platform lives in code. No publish method exists anywhere in the module. Writes are refused outside workspaces with an agent-owned prefix. Deletes are refused on entities the automation does not own and on consent records. Created entities stay paused until a human passes a live flag. An append-only ledger records pending before each call.

**Principle:** Put the refusal rules in the module that writes, enforced on every call.

**Tags:** System, System, Architecture

---

## Direction A Proves the Claims, Direction B Finds the Unchecked Numbers

**Date:** May to August 2026
**Type:** Architecture
**Generation:** SYSTEM

Numbered build scripts produce the deliverable, and numbered verify scripts re-derive every published figure from the base of record. Direction A asserts each claim in the document is reproducible. Direction B sweeps the rendered document for any number nothing verified. Coverage failures exit non-zero. An explicit allowlist is the only escape hatch. Each verifier is tamper-tested against the thing it claims to catch.

**Principle:** Pair every build script with a verifier that re-derives each figure from raw.

**Tags:** System, System, Architecture

---

## The Source Registry Field That Records What a Source Cannot Answer

**Date:** May to August 2026
**Type:** Decision
**Generation:** SYSTEM

Every source entry carries a not-for field beside its answers field. That one field prevents the expensive errors, because most bad analysis is a correct number aimed at the wrong question. A companion register records the hard limits per source. Retention windows hide an earlier period. Row caps truncate silently. Each limit carries an owner, so "we cannot get this" stays separate from "we never asked".

**Principle:** Record what each source cannot answer, and attach an owner to every stated limit.

**Tags:** System, System, Decision

---

## Each Definition Written Three Ways, Including the Recipe That Fails

**Date:** May to August 2026
**Type:** Architecture
**Generation:** SYSTEM

The provenance contract writes each routinely-miscomputed quantity three ways. First the correct recipe with its grain. Then the plausible recipe that fails, which is the one that looks reasonable. Then what the failure looked like: the wrong number, the wrong conclusion, the wrong remedy. A definition stated only correctly does not stop the error.

**Principle:** State the failing recipe beside the correct one so readers recognise their own mistake.

**Tags:** System, System, Architecture

---

## Deterministic Scripts Hold the Numeric Authority

**Date:** May to August 2026
**Type:** Decision
**Generation:** SYSTEM

Compute and verification live in deterministic scripts that emit a tiny summary. Raw rows are never ingested to be recomputed in-head. Backing artifacts are script byproducts. Adversarial model-based verification is held back for high-stakes judgment claims, while routine numbers get a second-path recompute in code. It is a cost decision as much as a correctness one. Human sign-off meets the zero-mistake standard, and the agent does not.

**Principle:** Scripts compute and verify. The agent reads the summary and writes the prose.

**Tags:** System, System, Decision

---

## Gate Red on 86 Unregistered Breaches, One Tier Still a Placeholder

**Date:** May to August 2026
**Type:** Learning
**Generation:** SYSTEM

Two gaps belong in any honest positioning of this work. The fail-closed gate exits 1 today on roughly 86 unregistered breaches. Several hundred committed data files carry provenance sidecars across about a third of that surface. The debt registry covers well under half the breaches. The gate is real and it runs. The documented store tier holds only a placeholder file, so one declared layer is aspirational.

**Principle:** Publish the red gate next to the engine. The admission is what makes it credible.

**Tags:** System, System, Learning

---

## Two Counts Differ, And Neither Names A Direction

**Date:** 31 July 2026
**Type:** Learning
**Generation:** SYSTEM

A build tree and the live site reported different counts of hidden elements. I reported the live figure, correctly, then called the build stale. It was not. The build came from an unpublished branch and was ahead. Two numbers that differ support only the claim that the states differ, and I supplied the direction from an assumption about how repositories drift.

**Principle:** Say two states differ and stop there, until a distinguishing marker proves which one is newer.

**Tags:** System, System, Learning

---

## One Named Hole In The Guard, Not A Weaker Guard

**Date:** 31 July 2026
**Type:** Architecture
**Generation:** SYSTEM

An ownership guard refused to attach a tracking parameter to the one object that owns the event. That guard stops the automation mangling configuration it did not create. Every alternative cost more. A duplicate object double-counts, a separate event name forks the stream, and bypassing the guard ends the safety model. The route taken matches one entity by exact name, in its own flag and ledger label.

**Principle:** Cut the smallest named hole that lets the work through, make it loud, keep other guards live.

**Tags:** System, System, Architecture

---

## Both Findings Against The Other Team Were Ours

**Date:** 30 July 2026
**Type:** Learning
**Generation:** SYSTEM

I drafted two findings against a sibling repository. Both were wrong. The first cited runtime traffic as proof that withheld work had shipped. The handoff predicted exactly that traffic from a different serving path, and version history showed no matching commit. The second looked like a security defect. The cause was ours: a shared layout defaulted an access flag to off, so our own instrumentation misreported the state.

**Principle:** Before filing a cross-team defect, build the version where it is yours, then ask rather than assert.

**Tags:** System, System, Learning

---

## The Absence Test Ran Through A Script-Stripping Converter

**Date:** 30 July 2026
**Type:** Learning
**Generation:** SYSTEM

A fetch tool converts pages to markdown, which drops script tags. Asked whether one analytics tag was on the homepage, it reported nothing, and reported nothing for a second tag that was live and serving. At face value that is a false negative about production. A raw fetch found the live tag twice and the other zero times. The control is what exposed the tool.

**Principle:** Test for presence with a tool that does not transform the document, and include a known-present control.

**Tags:** System, System, Learning

---

## Verified Against The Docs, But Which Row

**Date:** 30 July 2026
**Type:** Learning
**Generation:** SYSTEM

A memory note recorded a 30-day retention window as verified against a vendor's documentation. It became a deadline another team quoted back to us. That page lists three periods, and heatmaps are drawn from data held nine months. The note had read the 30-day row and generalised it. The verification claim stopped anyone re-checking. Worse, the collector was paused, so nothing was being retained at all.

**Principle:** Name the granularity a verification actually read, and confirm collection runs before pricing an expiry deadline.

**Tags:** System, System, Learning

---

## The Record Said Scoped, Production Said Everywhere

**Date:** 30 July 2026
**Type:** Learning
**Generation:** SYSTEM

Notes, memory, and a session narrative all recorded a tracking tag as narrowly scoped. The published container had it firing on all pages. That narrowing trigger existed only in an unpublished workspace: created, ledgered, committed, never shipped. The automation has no publish method by design, so every write stops at the staging boundary. Version history settled it. The tag had genuinely run unscoped for nine minutes.

**Principle:** Read the deployed state, never the staged state, and name which one you read.

**Tags:** System, System, Learning

---

## The Rule Lived In The Summary, Not The Decision

**Date:** 30 July 2026
**Type:** Learning
**Generation:** SYSTEM

A constraint was recorded as one line in a backlog summary of a decision record. Two architecture diagrams drew it in. It was never written into the decision itself. So anyone who read the decision, the correct thing to do, would not learn the rule existed. The artifacts stating it most plainly were the ones shown to people who act.

**Principle:** Write every locked constraint into the decision record, then sweep each summary and diagram that paraphrases it.

**Tags:** System, System, Learning

---

## When A Gate Lifts, Its Substitute Obligation Comes Due

**Date:** 30 July 2026
**Type:** Learning
**Generation:** SYSTEM

A gate had been shut for a reason people had stopped restating. The system had no way to perform a step the blocked action would require, so blocking stood in for doing it. Authorising the action built that capability. The substituted step became a direct obligation rather than a moot one. Read as pure relaxation, the ruling would have shipped a path with no such step.

**Principle:** When a gate lifts, ask what it substituted for and file the new obligation with an owner.

**Tags:** System, System, Learning

---

## A Gate Red for Unrelated Reasons Gets Skimmed

**Date:** 28 July 2026
**Type:** Architecture
**Generation:** SYSTEM

A fail-closed checker exited non-zero on nearly forty inherited gaps. Nobody was acting on them, so the output got skimmed. Registering that debt with a mandatory owner and a due date restored the signal. The gate went green on exactly those paths. Its first clean run caught orphans a filtered grep had missed, and a registry path with prose appended. That had hidden a live source for many sessions.

**Principle:** Never leave a fail-closed check red as a to-do: fix it, or register it with an owner.

**Tags:** System, System, Architecture

---

## The Retired Figure Lived in the Generator, Not the Documents

**Date:** 27 July 2026
**Type:** Fix
**Generation:** SYSTEM

A withdrawn population figure was hardcoded three times in a deck builder, and once in its check. The check asserted the value equalled a literal. That proved the source file was read, not that the population was live. The ledger passed, and regeneration reproduced the error. Correcting the documents that quote it fixes nothing. A figure from another team is a lead to recompute, never a value to paste.

**Principle:** Trace a wrong figure to the code that produces it, and make checks assert source and grain.

**Tags:** System, System, Fix

---

## Right Arithmetic, Wrong Mechanism, a Fix That Still Fails

**Date:** 27 July 2026
**Type:** Learning
**Generation:** SYSTEM

An incoming brief named a real defect and got its arithmetic exactly right. It blamed a not-a-number coercion for two scoring components. Instrumenting the path showed one component was never missing. Its helper returns a strict boolean, so every never-engaged record scored a hard zero. The prescribed one-line fix would have raised the ceiling, still failed acceptance, and looked right. A failed precondition is not evidence of absence.

**Principle:** Verify a handed-over cause separately from the handed-over symptom by instrumenting the path.

**Tags:** System, System, Learning

---

## Two Figures Drifted While the Correct Artifact Sat Unread

**Date:** 26 July 2026
**Type:** Learning
**Generation:** SYSTEM

Two headline numbers crossed a repository boundary as prose and arrived wrong. One re-derived at a different grain under an unrecorded folding rule. It could not be reproduced. The other welded an in-flight count to a population figure from another system. A dated, grain-labelled artifact with the right measures had existed all along. Cite path, date, and grain. The choice a figure requires is part of the figure.

**Principle:** Cite a number by path, date, and grain, and label every re-derivation as a separate figure.

**Tags:** System, System, Learning

---

## A Sign-Off Validates the Framing, Not the Facts Underneath

**Date:** 24 July 2026
**Type:** Learning
**Generation:** SYSTEM

I re-checked a partner integration's prerequisites against the owner's live docs a week after sign-off. The re-check found two factual corrections, a renamed component, and a deprecated toolkit. Approval had confirmed the framing, not the facts underneath. Third parties keep changing those. Register the re-grounding as a routine, and re-fetch every quoted excerpt in an independent pass. Route conflicts to an owner instead of overwriting your own product truth.

**Principle:** Treat a third party's live documentation as a source you re-verify on a schedule.

**Tags:** System, System, Learning

---

## Two Figures Computed and Never Shown on the Page

**Date:** 22 July 2026
**Type:** Architecture
**Generation:** SYSTEM

A verifier recomputes every published figure from raw. It also greps the built page to assert each figure appears there. The presence check caught two figures computed into the figures file, never shown. A recompute-only check would have stayed green. The page and its backing would have diverged in silence. Assert both directions: every published figure is in the recomputed set, and every recomputed headline is on the page.

**Principle:** Assert that each computed headline appears in the artifact, not only that it recomputes.

**Tags:** System, System, Architecture

---

## The Banner Showed One Address, the Record Another

**Date:** 21 July 2026
**Type:** Learning
**Generation:** SYSTEM

An injected context banner displayed a personal address, which raised a real alarm that the session was processing data under a personal account. The stored OAuth account object said otherwise: an organisation seat, with the org type recorded on it. A banner is a display field. The account governs data handling. Confirm a consequential fact from the system of record, never from an intuitive-sounding identifier.

**Principle:** Confirm a consequential fact from the system of record, never from a displayed label.

**Tags:** System, System, Learning

---

## The Verbatim Quote Came From a Summariser

**Date:** 16 July 2026
**Type:** Learning
**Generation:** SYSTEM

A line cited as verbatim actually came from a fetch tool's summary, a small model paraphrasing. The reviewer could not find it. The string was real, but it sat inside a collapsed accordion on a client-rendered page that a shell-only fetch never sees. Rendering the page confirmed the quote, and that section already answered most of the questions queued for a stakeholder. Two internal pages also contradicted each other.

**Principle:** Confirm a quoted string against the rendered page before citing it as verbatim.

**Tags:** System, System, Learning

---

## Send the Two Open Questions, Not the Documents

**Date:** 16 July 2026
**Type:** Decision
**Generation:** SYSTEM

The fastest way to lose a volume-averse stakeholder is to forward the internal briefs. They are long, dense, and carry material that should not leave the working set. The note acknowledged their earlier steers, listed the documents already read, and asked only the two things their own published material could not settle. Framed as confirm or correct my reading. Same-day answer. Give a busy expert a draft to react to.

**Principle:** Give a busy stakeholder your best guess to correct, plus evidence you did the reading.

**Tags:** System, System, Decision

---

## An External Probe Engine Filed Under a Report Tree

**Date:** 15 July 2026
**Type:** Architecture
**Generation:** SYSTEM

An external probe component had grown three levels deep inside a tree named for one source system. That framed it as a report on a system it read nothing from. Misfiled, it was hard to find and harder to lift to its eventual home. File work by where its data comes from. Authenticated pulls, unauthenticated probes, and analysis derived from one named source each get a top-level tree.

**Principle:** File a component by the provenance of its data, not by the report that needed it.

**Tags:** System, System, Architecture

---

## A Chat Go-Ahead Does Not Clear a Bulk Egress Gate

**Date:** 14 July 2026
**Type:** Learning
**Generation:** SYSTEM

A restricted list of company domains sent to public lookup endpoints was blocked under a data-handling rule, despite an explicit in-chat approval. The classifier gates the semantics of the action. A chat message does not clear it. It also fairly objected to an authorized_by field I had hard-coded into the run manifest. Unblock with a git-ignored allow rule scoped to the exact command. Record what triggered the run.

**Principle:** Clear a bulk egress gate with a scoped permission rule, never by self-certifying inside an artifact.

**Tags:** System, System, Learning

---

## A Smoke Mode With One Known Negative Control

**Date:** 14 July 2026
**Type:** Architecture
**Generation:** SYSTEM

A new probe leg risked a silent decode bug across the full batch. A smoke mode ran the identical probe and decode functions over a handful of hand-picked domains: several known positives with visible evidence strings, plus one known negative control. It validated the positive path and the honest Unknown path in seconds. It also caught a network sandbox block early. Rerunning a locked probe is a zero-drift reproducibility check.

**Principle:** Exercise a new probe leg over a tiny known set with a negative control first.

**Tags:** System, System, Architecture

---

## A Concurrent Session Invalidated a Proof I Had Committed

**Date:** 14 July 2026
**Type:** Failure
**Generation:** SYSTEM

I committed a proof pack reconciling a workbook. Another session then corrected rows in the same workbook and committed too. Nothing warned me. My proof was stale, and several corrected rows had no committed raw evidence. It surfaced only because a status check diffed the workbook against my run directory instead of restating remembered numbers. The targeted re-probe that fixed it also reproduced the other session's verdicts, zero mismatches.

**Principle:** After any gap on a shared checkout, diff the artifact against its backing data first.

**Tags:** System, System, Failure

---

## A Value Corrected in One Sheet, Stale in Three

**Date:** 14 July 2026
**Type:** Fix
**Generation:** SYSTEM

A batch of corrected domains landed in the output workbook's main sheet only. Three other places still held the old values: the source workbook, and a filtered view inside each file. The stale source meant the next probe run would quietly regress the fix. Enumerate every place a denormalized value is stored. Sync them from one authority keyed on a stable id, assert zero mismatches, and commit the script.

**Principle:** Correct a denormalized value in every copy, from one authority, and assert zero mismatches.

**Tags:** System, System, Fix

---

## One Number Improved, Two Artifacts Now Disagree

**Date:** 13 July 2026
**Type:** Learning
**Generation:** SYSTEM

Two deliverables carried the same market statistics. A better source moved one figure by four points in the first, and I softened a claim there too. That silently desynced it from the second, and both were headed for the same audience. The closing reconciliation caught it only because I re-extracted the second file's text and diffed the shared claims. Regenerate every carrier inside the fix.

**Principle:** Extract and diff every shared figure across artifacts before calling a set reconciled.

**Tags:** System, System, Learning

---

## Two Lanes of Proof: Recompute Internal, Cite External

**Date:** 13 July 2026
**Type:** Architecture
**Generation:** SYSTEM

The ask to back up every claim splits into two lanes. Internal numbers must recompute from the source export into a ledger: the claim, the recomputed value, the file, the field, and the filter behind it, and a pass or fail. External market statistics only trace to a named institution, and they are never our data. Coverage ratios are grain-sensitive too. Per-person and per-account answers differ materially.

**Principle:** Sort each claim into recomputable and citable before building the ledger, and never blend the two.

**Tags:** System, System, Architecture

---

## A Rollup Table Is Derived, So Citing It Proves Nothing

**Date:** 13 July 2026
**Type:** Architecture
**Generation:** SYSTEM

A shortlist was defended by pointing at the summary table it came from. That table is itself derived, so citing it proves nothing. The proof pack ran two directions. Re-parse the raw inputs and account for every input name: zero dropped, zero orphans. Then recompute each decision-driving figure from the raw files and diff it against the summary. Ship a rerunnable script plus a pass or fail verdict.

**Principle:** Prove a derived table by re-deriving its figures and accounting for every input name.

**Tags:** System, System, Architecture

---

## The Number on the Slide Was a Hardcoded String

**Date:** 13 July 2026
**Type:** Failure
**Generation:** SYSTEM

Two headline figures in a deck turned out to be static text inside the build script, not values read from the data. The same metric also had three valid nested scopes, so two figures that looked contradictory were measured over different populations. Recompute from source before defending a number. Name its scope. The example grid on a slide is rarely the set the caption counted.

**Principle:** Recompute a slide's numbers from source and state the population each one covers.

**Tags:** System, System, Failure

---

## Build the Deck in the Format You Can Render

**Date:** 12 July 2026
**Type:** Decision
**Generation:** SYSTEM

HTML decks render to PDF through a headless browser. That check caught a real CSS overflow bug, text spilling past its box. The binary slide format has no renderer installed here, so generated slides get a structural pass only: slide count, shape bounds, text present. Reflow inside a box stays unproven until someone opens the file. Keep unverifiable layouts conservative.

**Principle:** Prefer the output format you can render and inspect, and treat the rest as a human-checked export.

**Tags:** System, System, Decision

---

## Bind the Eval Harness to a Snapshot, Not the Pipeline

**Date:** 9 July 2026
**Type:** Decision
**Generation:** SYSTEM

Reconciliation had to run against static exports now, live pulls later. Coupling the checks to the ingestion path would force a rewrite at every source change. So the harness reads one environment variable naming a canonical snapshot directory, and every check resolves from it. Structural sums and definition tests then carry across sources unchanged. Anchor values get re-baselined per snapshot. The export-versus-live gap is a signal of its own.

**Principle:** Point checks at a canonical snapshot directory so they survive a change of source system.

**Tags:** System, System, Decision

---

## The Screenshot Width Was Cropping a Clean Render

**Date:** 9 July 2026
**Type:** Learning
**Generation:** SYSTEM

A report looked clipped in a headless screenshot taken at 430 pixels wide. I chased a phantom overflow. An in-page probe of document scroll width against window inner width showed a 500 pixel layout with no overflow at all. The window-size flag sizes the captured image, not the layout viewport. Measure inside the page, or use device emulation, before touching any CSS.

**Principle:** Measure the layout inside the page, never from the width of a screenshot.

**Tags:** System, System, Learning

---

## A Gate Keyed on Ignored Files Passes Only Locally

**Date:** 6 July 2026
**Type:** Learning
**Generation:** SYSTEM

An integrity gate was about to read its richest evidence from a gitignored cache directory. That directory is missing on a fresh clone, so the gate could only pass on the machine that just pulled. Plan review caught it before it shipped. A blocking gate reads committed artifacts only. Two modes, one script: committed fails closed, cache reports and exits zero.

**Principle:** Let a blocking gate read committed artifacts only, and put freshness checks in a non-blocking mode.

**Tags:** System, System, Learning

---

## Verify a Tag Change in the Config Plane

**Date:** 5 July 2026
**Type:** Learning
**Generation:** SYSTEM

Confirming that a widget's tag was paused by fetching the page HTML proves nothing. The tag manager injects the widget client-side, so it never appears in the served markup. The API settled it: published version 315, tag 838, paused true. Config state is immediate. The compiled script strips paused tags, but it stays cached for minutes at the CDN and in browsers.

**Principle:** Check the config plane for a live setting, never a cached artifact or a page fetch.

**Tags:** System, System, Learning

---

## Registered Is Not Queryable, So Verify the Pipe

**Date:** 25 June 2026
**Type:** Learning
**Generation:** SYSTEM

Five newly registered custom dimensions came back unset on every report row. That was expected. The platform does not backfill, so events recorded before registration can never carry the field. Standard tables also trail live data by a day or two. Do not wait for a report to fill. Confirm registration, confirm the tag emits the parameter under its exact name, case included, and confirm the event fires now.

**Principle:** Verify a new dimension at registration, at emission, and at live firing, then wait out the latency.

**Tags:** System, System, Learning

---

## Stage the Exact End State Before a Human Publishes

**Date:** 24 June 2026
**Type:** Failure
**Generation:** SYSTEM

Two releases shipped incomplete because a manual un-pause was dropped when the platform merged the working copy back. The human at the publish gate approved a state nobody intended. Author the exact end state through the automation itself. Leave the human one action. Separately, one working copy per task hit the concurrent-draft limit, since publishing consumes one. Keep a single long-lived working copy owned by the automation.

**Principle:** Leave a human publish gate exactly one action, never a toggle they must remember.

**Tags:** System, System, Failure

---

## A Shared Tag Container Needs an Allowlist, Not a Default

**Date:** 23 June 2026
**Type:** Architecture
**Generation:** SYSTEM

One tag container served two surfaces owned by different teams, and we controlled only one. A gate reading fire where page type is logged out defaults unknown pages into the firing set. Tags leak onto pages you do not own. The safe shape is a positive allowlist of the routes you control, with a default of other. Prove it offline against URLs that must and must not match.

**Principle:** Gate a shared container with a positive allowlist and a deny default, then prove it offline.

**Tags:** System, System, Architecture

---

## The Credential Gate Held and a Human Published Anyway

**Date:** 19 June 2026
**Type:** Failure
**Generation:** SYSTEM

An agent was blocked from publishing to a live tag platform. That is the gate working as designed. A human then published the agent's staged change, believing preview required it, and a test tag fired on every page. Create staged entities paused, keep the live flag human supplied, and give the tool no way to unpause. A gate on the agent does not make staged work safe.

**Principle:** Make agent-staged artifacts inert by default, so an accidental human publish changes nothing.

**Tags:** System, System, Failure

---

## An In-Tool Ledger Records Intent, Not What Went Live

**Date:** 19 June 2026
**Type:** Architecture
**Generation:** SYSTEM

A change log written by the tool that performs the writes is blind to edits made elsewhere. The platform's own interface and its raw API both bypass it. That is exactly how the accidental publish happened. It surfaced only on a re-pull of the live container, diffed against a version-stamped baseline. Keep the ledger authoritative for intent: pending before the call, committed with the entity id after.

**Principle:** After every publish, diff live against a version-stamped baseline; your ledger is not ground truth.

**Tags:** System, System, Architecture

---

## A Server Fetch Kept Missing a Snippet That Was There

**Date:** 19 June 2026
**Type:** Learning
**Generation:** SYSTEM

A script fetching the production page reported the tracking snippet missing, despite a cache-buster query, a real browser user agent, and trailing slashes. Viewing source on the same URL showed it. A real visit landed in the analytics realtime view. Believe the data plane, and treat a bot fetch as evidence only when positive. The CDN serves an unidentified client a variant cached copy. The absence was an artifact.

**Principle:** Verify a live tag by whether its events arrive, not by fetching the HTML from a server.

**Tags:** System, System, Learning

---

## Two Status Documents Disagreed, the Output File Settled It

**Date:** 20 May 2026
**Type:** Learning
**Generation:** SYSTEM

Two documents in the same pipeline directory reported completion states far apart. One was a snapshot written mid-run and never updated. Neither was evidence. A single wc -l on the output file matched one of them exactly. Resolve documentation conflicts by measuring the artifact, then mark the stale document superseded so the next reader skips the comparison.

**Principle:** When two documents disagree on progress, count the output records rather than trusting either.

**Tags:** System, System, Learning

---

## Self-Contained HTML Beat a Spreadsheet for a Read-Only Report

**Date:** 20 May 2026
**Type:** Decision
**Generation:** SYSTEM

A stakeholder report that people read and never edit shipped as one self-contained HTML file. The same script builds it and the spreadsheet. Data sits in the page as inline JSON, with filtering and sorting in vanilla JavaScript. No build step, no dependency, nothing that expires. Regeneration after fresh input is one command. Pivot tables need a manual refresh and cannot carry custom filtering or deep links.

**Principle:** Emit read-only stakeholder output as self-contained HTML from the script that builds the working file.

**Tags:** System, System, Decision

---
