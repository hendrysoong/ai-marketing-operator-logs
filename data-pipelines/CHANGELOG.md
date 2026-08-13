# Data — Pipelines and Sources — Changelog

> Part of the [AI Marketing Operator Logs](../README.md) by [Hendry Soong](https://www.hendry.ai)
> Canonical source: [hendry.ai/ai-marketing/operator-logs/data-pipelines](https://www.hendry.ai/ai-marketing/operator-logs/data-pipelines/)

Mirrored from the canonical page above, newest first.

---

## One Join Key With Two Normalisers Is Two Keys

**Date:** 10 August 2026
**Type:** Fix
**Generation:** SYSTEM

One repository carried two versions of a host-normalising helper. They disagreed with each other, and both failed all seven cases of the cross-repository join contract. Each collapsed public suffixes and stripped subdomains, so a trailing-dot host became a bare suffix. The correct rule then rejected values the loose one had turned into keys: two-domain cells, typos, stray quotes, and a postal address. It manufactured keys from garbage.

**Principle:** Give a join key one owning module, stamp its version per record, and add a parity test.

**Tags:** System, System, Fix

---

## The Boundary Was Written Over Records, So the Logs Leaked

**Date:** 10 August 2026
**Type:** Failure
**Generation:** SYSTEM

Identifiers reached a repository through a session transcript. The rule they broke was written about records: what a seed carries, what an extractor emits. The breach used none of those routes. A shell call read a neighbouring project's git-ignored export and printed it to stdout. The session hook appended that output to four committed logs. The gate walks ledgers and raw inputs, and had never opened the session logs.

**Principle:** Ask separately what your logs, transcripts, and metrics capture, and treat a neighbour's ignored directory as readable.

**Tags:** System, System, Failure

---

## A Blank-Cell Count Was the Wrong Denominator for a Join Verdict

**Date:** 9 August 2026
**Type:** Learning
**Generation:** SYSTEM

A verdict rested on a count of records with an empty key field. The count reproduced exactly and was still wrong. Other records held values that were never keys: a phone number, a placeholder string, a bare label. Several more were one component short of joinable. The join cannot see those either. Print the rejected values in full, because they are the evidence.

**Principle:** Normalise the key the way the join will, then count what remains empty.

**Tags:** System, System, Learning

---

## Splitting on Every Colon Turned Two URLs Into One Hostname

**Date:** 9 August 2026
**Type:** Fix
**Generation:** SYSTEM

A domain normaliser stripped ports by splitting on the first colon and keeping the left side. A handful of malformed cells begin with a bare protocol prefix. Two of them normalised to the protocol itself as a hostname. That merged a real company with a blank and shifted the distinct-domain count being compared against another system. Inspect whatever a normaliser rejects. Here it also exposed a duplicated account row.

**Principle:** Strip the protocol with an anchored pattern, remove only a trailing port, then assert a dot survives.

**Tags:** System, System, Fix

---

## Fan Out Is Finders Times Findings, Not Finders

**Date:** 5 August 2026
**Type:** Learning
**Generation:** SYSTEM

An audit workflow ran six lenses and sliced twelve findings from each. That authorised roughly 78 subagents against a guideline of 15. Seventy-two actually ran and returned 64 confirmed findings, so the output looked fine and only the cost was several times what was intended. Nothing in the script warned about it. The agent count is finders multiplied by findings per finder.

**Principle:** Compute the fan-out product before launching, and cap the per-lens slice to stay inside the guideline.

**Tags:** System, System, Learning

---

## One Class Field Folded a Lifecycle Flag Into Job History

**Date:** 5 August 2026
**Type:** Fix
**Generation:** SYSTEM

I derived one routing class per CRM user, treating departure as an overriding value. That is correct for routing, since no brief should reach a leaver. It also destroyed history. Every call a departed rep logged became undirectable. That moved the account's last genuine contact back by more than 12 months, toward looking colder. No gate caught it, and I found it by reading a date that looked wrong.

**Principle:** Split what the job was from who may receive work now, and gate the historical field.

**Tags:** System, System, Fix

---

## A Role Word Regex Caught a Product Name

**Date:** 5 August 2026
**Type:** Failure
**Generation:** SYSTEM

A case-insensitive title match on a role word caught an unrelated product name. Its administrators classed as sales reps. Routing would have gone to entirely the wrong people. The identical regression was already banked in the shared definitions file, in a script whose own header cites that post-mortem. Real word boundaries were the fix. Writing it down did not stop me repeating it two hundred lines later.

**Principle:** Use real word boundaries, test the specific match before the generic one, and bank a counter-example.

**Tags:** System, System, Failure

---

## A Pipe Delimiter Inside Free Text Shifted Every Column Right

**Date:** 5 August 2026
**Type:** Fix
**Generation:** SYSTEM

Exporting four CRM tables with a hand-picked pipe separator shifted every column right of the delimiter on any row whose company string contained a pipe. A column width assertion caught it immediately. Without one, four plausible-looking files would have shipped misaligned. Separately, the client ran past a failed query and returned that section as zero rows. That is indistinguishable from an empty result.

**Principle:** Export as quoted CSV, assert each section's column count, and make the client stop on error.

**Tags:** System, System, Fix

---

## Writing New Data Classes Into Tracked Files Sets Precedent

**Date:** 5 August 2026
**Type:** Learning
**Generation:** SYSTEM

I wrote two classes of identifier into two tracked planning documents. No committed document in that repository had ever held either. Both had lived only in raw logs, which is why scrubbing those logs was an open governance item. I would have widened a debt the team was working to close. Worse, I would have set a convention while doing it. A grep of HEAD costs seconds.

**Principle:** Grep the committed tree before writing a new class of data into a tracked file.

**Tags:** System, System, Learning

---

## A Comment Character Inside A Field Truncated Rows

**Date:** 4 August 2026
**Type:** Fix
**Generation:** SYSTEM

Decision files carry a provenance banner in comment lines, so every reader opened them with the CSV parser's comment option. Three data rows held that character inside a field. The parser truncated those lines mid row, voided a band column, and a published count sat one low for weeks. The qualified set escaped by luck. A comment option is a content filter applied to every line, not a header rule.

**Principle:** Skip a header banner by counting its rows, never with a parser's comment option.

**Tags:** System, System, Fix

---

## A Zero-Row Join From Two Lengths Of One Id

**Date:** 3 August 2026
**Type:** Fix
**Generation:** SYSTEM

One cohort file wrote record ids in the long form, the decision lists in the short. Joining across them returned zero overlap. No error, no warning. The empty result read briefly as a real finding, that the cohort touched neither scored frame. The file had carried a short-form column all along, and joining on it matched every row.

**Principle:** Treat a zero overlap between two extracts of one system as a key-format bug until proven otherwise.

**Tags:** System, System, Fix

---

## A Scheduler Write That Hangs Instead Of Failing

**Date:** 1 August 2026
**Type:** Failure
**Generation:** SYSTEM

A daily pull was cron-or-nothing, since the API's lookback window makes a skipped day permanently unreachable. Listing the crontab worked and reported nothing scheduled. Every attempt to write one hung. No error, no denial, just a full tool timeout burned under the operating system's privacy protections. A per-user scheduler worked first try, and I verified it by firing the job rather than reading the config back.

**Principle:** Probe the write path, bound the call yourself, and verify a scheduler by firing its job.

**Tags:** System, System, Failure

---

## The Extractor Emits Payload and Provenance and Stops

**Date:** May to August 2026
**Type:** Decision
**Generation:** SYSTEM

The extractor emits verbatim payload, a timestamp and provenance. It never emits a state, a score, a weight or an eligibility verdict. Scoring, suppression and learned weights live on the side that owns the judgment. Recording a public field verbatim is extraction. Deciding eligibility from it is qualification. The seam exists because a predecessor's substring classifier drifted from 78 percent accuracy to 56.5 percent.

**Principle:** Extraction records what is there. Qualification decides what it means.

**Tags:** System, System, Decision

---

## Five Clauses That Keep a Cross-System Join Honest

**Date:** May to August 2026
**Type:** Decision
**Generation:** SYSTEM

Records cross the boundary keyed on a canonical domain plus an opaque account reference. The internal identity key never crosses. Exactly one canonicalisation rule lives in exactly one owning module, and its version string rides in every emitted record. Opaque references are salted and full length, because a truncated hash is enumerable. Figures cross only as dated artifacts with a stated grain.

**Principle:** One canonicalisation rule, one owning module, and its version stamped on every record.

**Tags:** System, System, Decision

---

## A Replay Renders Your DOM Without Your JavaScript

**Date:** 31 July 2026
**Type:** Learning
**Generation:** SYSTEM

A heatmap showed the hero and blank space below it. Pages ship content at opacity zero and reveal it with their own observer and a 1500 ms fallback. A replay paints a recorded DOM snapshot without running them. The tell was in the picture. Blank boxes with the right heights mean the layout is present and only paint is missing. Test with scripts on, off, and your own stripped.

**Principle:** Assume a third-party renderer never runs your scripts, and reproduce that state before blaming the tool.

**Tags:** System, System, Learning

---

## The Fix Was Already There, Behind A Dead Predicate

**Date:** 31 July 2026
**Type:** Learning
**Generation:** SYSTEM

Having root-caused a rendering failure, I designed a fix and wrote it into a handoff. All 18 files already carried the opacity rule I wanted. The override sat behind a media query for a condition that never fires here. Deleting the wrapper was the whole fix. Already important, already correct everywhere, revertible by typing six characters back. My version needed that rule found per file, in machine-flattened CSS.

**Principle:** Grep for the end state you want before designing a fix, not only for the defect.

**Tags:** System, System, Learning

---

## Read-Only Because Nobody Ever Asked For Write

**Date:** 31 July 2026
**Type:** Learning
**Generation:** SYSTEM

Asked to register a new analytics dimension, I said it needed a human in the vendor UI, because my tooling was read-only. Challenged, I checked. Every module here had always requested a read-only scope. That is our own code declining to ask, which is different from being refused. Requesting the write scope produced a 403 on create: the scope was grantable, the account-level role was not.

**Principle:** Say whether a blocked capability is the tool surface, the scope your code requests, or your grant.

**Tags:** System, System, Learning

---

## Blocked By The Vendor, Or By Our Own Credential

**Date:** 30 July 2026
**Type:** Learning
**Generation:** SYSTEM

A source registry recorded that about half of one platform's endpoints were blocked. I read that as a property of the platform and designed a data request around it. The integration's own error text said otherwise. Our credential lacked a read permission, and the error named the exact one to grant. Those grants are self-service. Nine requested fields collapsed to two, and the real action was an internal permission request.

**Principle:** Record every limitation as blocked-by an owner: the vendor, your credential and your unwritten code differ.

**Tags:** System, System, Learning

---

## Same Word, Different Sense, Across A Repository Seam

**Date:** 30 July 2026
**Type:** Learning
**Generation:** SYSTEM

A sibling team handed over two items to check during a supersession sweep. Both were wrong. One decision record looked like a match, but used the shared term for data-flow direction rather than for the policy in question. That is a homograph, not a carrier. The other cited a layer number from their methodology stack. It has no referent on our side, so adopting it would have invented a layer.

**Principle:** Confirm a matched term's sense in context, and check a borrowed identifier resolves in your own namespace.

**Tags:** System, System, Learning

---

## The 403 Came From the Edge Network, Not the API

**Date:** 28 July 2026
**Type:** Fix
**Generation:** SYSTEM

An integration read a 403 as a missing scope or excluded plan. It said the same on every regional endpoint. The body was plain text with a numeric code. An edge network had blocked a standard library user agent before the application saw it. My handler mapped the status and dropped the body, so a working key looked like billing. A browser user agent authenticated on the first try.

**Principle:** Print the response body beside the status code on every HTTP failure.

**Tags:** System, System, Fix

---

## A Positional Masking Rule Hashed the Wrong Label

**Date:** 28 July 2026
**Type:** Failure
**Generation:** SYSTEM

A masking helper assumed a fixed label order and hashed label zero. Hosts ordered differently got the wrong label hashed, and real values went out in clear text. Its four-hex identifier space also collided, so two rows shared an id. Mask by allowlist, not by token position. Hash the whole value at eight hex or more, and assert ids are unique. Grep the output for real names before committing.

**Principle:** Mask by allowlist rather than token position, and grep the output for real names before committing.

**Tags:** System, System, Failure

---

## A Predicate That Read a Diagnostic and Inverted It

**Date:** 26 July 2026
**Type:** Failure
**Generation:** SYSTEM

A classifier set a two-valued attribute from an OR of two substring tests. The second read a free-text evidence field. Its no-signal value named both values it had checked, so every record with no footprint matched. The flag fired roughly three times over. It survived because those rows failed an earlier condition anyway, and nobody re-derived the count. Inert today is a bug with a scale trigger.

**Principle:** Decide on structured fields only, and never let a string a person reads sit inside a predicate.

**Tags:** System, System, Failure

---

## A Clean Personal Data Review That Missed Three Surfaces

**Date:** 24 July 2026
**Type:** Learning
**Generation:** SYSTEM

An analysis passed a personal-data review: no names, domain-level fields, no git remote. Customer identifiers still reached three places. The agent event log persists tool output. A committed planning note quoted them, and chat output travels to the model provider. A bulk external probe disclosed its query set to the intermediaries. Mask identifiers in agent output, and rejoin real names only at an authorised serving step.

**Principle:** Ask separately whether data is personal and where confidential business data travels.

**Tags:** System, System, Learning

---

## Extend a Locked Script With a Branch, Not a Fork

**Date:** 24 July 2026
**Type:** Architecture
**Generation:** SYSTEM

A verified probe script was hardwired to one input file under a locked policy. A second cohort needed the same probe. Copying the fetch and decode functions would let one governed rule become two. So I added one extra command-line mode. It feeds the same functions from a generic input file. The heavy spreadsheet import went lazy, so the light path runs on stock Python. Policy unchanged, one implementation.

**Principle:** Extend locked code through an additive input mode that calls the existing functions verbatim.

**Tags:** System, System, Architecture

---

## Subtracting a Timestamp From a Date Did Not Give Days

**Date:** 23 July 2026
**Type:** Fix
**Generation:** SYSTEM

A recency band reported one group as active within ninety days. A parallel cut showed a larger group silent for a year. One aggregate cannot produce both. The column was a timestamp, and subtracting it from the current date does not return integer days on that engine. The explicit day-difference function gave the right answer, and a consistency query returned zero rows. Check the column type first.

**Principle:** Check the column type, then use the explicit day-difference function for any recency math.

**Tags:** System, System, Fix

---

## One Record, Two Id Forms, Zero Matching Rows

**Date:** 23 July 2026
**Type:** Fix
**Generation:** SYSTEM

A join between a frozen export and the live system of record returned zero rows. The ids matched in meaning but not in form. One side used a shorter case-sensitive canonical form, the other a longer case-insensitive one. Normalising both sides to a single form restored most matches, not all. The export was also a filtered snapshot. Quantify the remainder and explain it, rather than dropping it.

**Principle:** Normalise identifier form on both sides before joining, then quantify every row that still fails.

**Tags:** System, System, Fix

---

## Most of the Answer Was Already Built

**Date:** 22 July 2026
**Type:** Decision
**Generation:** SYSTEM

I was about to build the full warehouse layering before producing a single CRM insight. Then I checked. Mapping the sponsor's first question against existing assets showed four fifths of the answer already built, in verified outputs, unassembled and unvisualised. Infrastructure first would have delayed the value and shaped the pipeline around an unvalidated insight. Inventory what is durable, ship the assembled answer, then industrialise.

**Principle:** Inventory existing verified outputs before speccing new infrastructure.

**Tags:** System, System, Decision

---

## A Title-Driven Taxonomy Ported Onto Records With No Title

**Date:** 22 July 2026
**Type:** Learning
**Generation:** SYSTEM

I was about to port a title-driven sub-taxonomy onto a second object. That object holds no title, job, or position field, only a persona category. Two of the sub-buckets are underivable there. Check the column catalogue on the target object first. State the missing signal as an explicit gap, not a weaker lookalike bucket. Same-named buckets across grains are not the same bucket.

**Principle:** Check the column catalogue on the target grain before porting a classifier.

**Tags:** System, System, Learning

---

## A Frozen Local Copy Sets the Drill-Down Grain

**Date:** 22 July 2026
**Type:** Decision
**Generation:** SYSTEM

I was about to wire a drill-down to the live warehouse by default. Three copies of the same data existed, one a full frozen export already on disk. It carries no direct identifiers, only pseudonymous keys and derived attributes. So read the frozen copy for structure and segmentation work. Reserve the live replica for freshness. Quasi-identifiers combine, so adding one direct identifier moves a list into the identified tier.

**Principle:** Read the frozen local copy for structure work and keep the drill-down grain identifier-free.

**Tags:** System, System, Decision

---

## The Word Boundary Escape Compiled and Matched Nothing

**Date:** 22 July 2026
**Type:** Fix
**Generation:** SYSTEM

Porting a title classifier onto a warehouse engine hit three dialect traps in one sitting. The familiar backslash word boundary was accepted and silently did nothing, so a three-letter token would have rematched inside longer words. The POSIX bracket boundary form worked. Some regex functions default to case-sensitive while the match operator does not, which produced phantom zeros. And a multi-row VALUES list is not usable as a derived table.

**Principle:** Verify each regex primitive against the live engine before a classifier depends on it.

**Tags:** System, System, Fix

---

## The Schema Named Like the CRM Was Long Dead

**Date:** 20 July 2026
**Type:** Failure
**Generation:** SYSTEM

The parity case was built on the schema whose name read as the CRM. A freshness probe found it frozen eighteen months earlier behind a dead pipeline. The one named like a staging copy was live. A third had been dead for years. Object and column parity looked identical: a stale copy has identical structure. Check the max modified timestamp on every candidate schema, plus the loader's own.

**Principle:** Establish which replica is live from timestamps per schema, never from the schema's name.

**Tags:** System, System, Failure

---

## The Missing Object Was an Unticked Checkbox

**Date:** 20 July 2026
**Type:** Fix
**Generation:** SYSTEM

One high-volume object was absent from the warehouse, and the standing assumption was that it could not be replicated. In fact the ingestion tool offered it, and nobody had ever selected it. Stream availability is invisible from SQL. The warehouse holds only what already landed, so the answer lives in the ingestion tool's own interface. Field-level selection also let the stream land with every column carrying personal data untracked.

**Principle:** Check the ingestion tool's stream selection before concluding a replica cannot have the data.

**Tags:** System, System, Fix

---

## The Gating Prerequisite Was Assumed, Not Read

**Date:** 15 July 2026
**Type:** Learning
**Generation:** SYSTEM

An eligibility model had encoded an unverified assumption as the hard readiness gate for a partner product. It was plausible. It was also undetectable from outside. The vendor's own current documentation showed the real prerequisite was a different and far more common one. Correcting it re-centred eligibility on a signal already being detected, and widened the addressable base. Verify a prerequisite against the primary source before it gates anyone.

**Principle:** Confirm a prerequisite against the vendor's current documentation before it gates eligibility.

**Tags:** System, System, Learning

---

## Ask Who Builds It Before Writing the Prerequisites

**Date:** 15 July 2026
**Type:** Learning
**Generation:** SYSTEM

Two products aimed at the same platform looked alike and carried very different customer requirements. Requirements diverge on who builds what inside the customer's environment. One is vendor-built. The customer only installs and approves it. The other the customer assembles themselves, which pulls in extra licensing, a usage budget, and a new internal role. Treating them as one requirement over-gates the light product and under-specifies the heavy one.

**Principle:** Determine who builds the thing before listing what the customer must already have.

**Tags:** System, System, Learning

---

## Deleting the Files Left the Data in Git History

**Date:** 15 July 2026
**Type:** Learning
**Generation:** SYSTEM

A plan for removing sensitive data from a working copy opened with deleting the files. That leaves every record intact inside a 651 MB git history that already committed them. Removing data from a repository means rewriting history. A safer route starts fresh from the clean tree and archives the dirty clone offline. When moving ignored data between machines, copy the folder. A clone carries only tracked files.

**Principle:** Treat git history as in scope from the first line of any data removal plan.

**Tags:** System, System, Learning

---

## Pin the Data to the Secure Host and Remote In

**Date:** 15 July 2026
**Type:** Decision
**Generation:** SYSTEM

Two constraints looked opposed. Restricted data had to stay off an unmanaged device, and the operator did not want to switch laptops. Neither one has to give. Keep the data pinned to the secure host and open a remote session into it, over SSH or a hosted desktop, from whatever device you type on. Nothing sensitive touches the local disk. Confirm the host is reachable from where you work first.

**Principle:** When data locality fights workflow convenience, separate where you type from where the data lives.

**Tags:** System, System, Decision

---

## Dirty Domains Turned Into False Unknowns

**Date:** 14 July 2026
**Type:** Fix
**Generation:** SYSTEM

Malformed keys in a CRM export nearly all came back Unknown from an external probe. Almost all flipped to Yes once corrected. The failures: a trailing slash or path, a host that stopped resolving, a blank. One row carried the domain of a business spun off from it years before. Strip scheme, www, and path, then re-probe. Unknown on a bad key is a data gap, never a negative.

**Principle:** Clean and verify the key before trusting any positive-only signal computed from it.

**Tags:** System, System, Fix

---

## Name Identity Must Outrank Business Signals in a Fuzzy Match

**Date:** 13 July 2026
**Type:** Learning
**Generation:** SYSTEM

Ranking candidates by region, customer status, and contract depth above the name score let large active records beat the exact-name match. Those exact matches fell below threshold and were reported as absent from the CRM. The set-based ratio also scored a generic two-token subset a perfect 100. Use it only to build the pool. Select on a length-aware sort ratio, so name identity dominates. Business attributes break near-ties only.

**Principle:** Select on name similarity and let business attributes break ties, never lead the ranking.

**Tags:** System, System, Learning

---

## The Auto-Enriched Industry Field Was Wrong Company by Company

**Date:** 13 July 2026
**Type:** Learning
**Generation:** SYSTEM

A cross-check of a hand-built list against the CRM flagged a run of industry mismatches. Every one was the right company carrying a wrong auto-enriched sector bucket. One sat under an unrelated sector, another under its best known product line rather than its actual business. No wrong-entity matches at all. The enriched field cannot drive classification. Classify from the human-authored labels and keep it as a loose wrong-entity check.

**Principle:** Classify sectors from human-authored labels and treat an enriched industry field as a sanity check only.

**Tags:** System, System, Learning

---

## Git-Ignored Is Not Out of an Agent's Reach

**Date:** 12 July 2026
**Type:** Learning
**Generation:** SYSTEM

Asked to confirm a repository held no personal data, an audit found it in three states. Committed, ignored but on disk, and vaulted. Ignoring a file keeps it out of commits. It does nothing to stop an agent reading it, as I had done earlier that session. The only real fix is moving the data outside the folder, plus a history scrub if it was ever committed.

**Principle:** Externalize sensitive files rather than ignoring them, because ignore rules govern commits, not reads.

**Tags:** System, System, Learning

---

## Ask What an Ambiguous Term Means Before Grading It

**Date:** 12 July 2026
**Type:** Learning
**Generation:** SYSTEM

Critiquing a campaign plan, I graded one tactic as spammy and dated. The author meant something else by the phrase: harvesting engagement signals to feed an agent. It was the practice I recommended elsewhere in the same critique. I had marked their strongest idea as a weakness by not asking. The other half held. A handful of targeted searches turned a generic assessment into a cited one.

**Principle:** Ask which meaning a term carries before classifying it, and ground a critique in fresh sources.

**Tags:** System, System, Learning

---

## The Match Universe Was Missing a Whole Store

**Date:** 10 July 2026
**Type:** Learning
**Generation:** SYSTEM

A list reconciled against the CRM's two obvious person objects produced a large net-new count. A second store also holds people, and it never felt like part of the CRM. Adding it removed nearly all of the net-new rows. The genuine remainder was internal and test addresses. The build script had hashed those emails to cross-link, then dropped the hash, so no bridge existed downstream.

**Principle:** Match a list against every store that holds people, not only the obvious CRM objects.

**Tags:** System, System, Learning

---

## A Loopback OAuth Callback That Could Not Be Won

**Date:** 9 July 2026
**Type:** Failure
**Generation:** SYSTEM

A vendor CLI's browser login timed out on every network I tried, across a whole session. The callback listener bound the IPv6 loopback while the browser reached for IPv4. Forcing the address-family order fixed the bind. The callback still refused, and the login timeout is fixed with no override flag. Check the listening socket, then stop. For the data itself, an interactive report export needs no API access.

**Principle:** Time-box a loopback OAuth fight, and fall back to the export path that needs no API.

**Tags:** System, System, Failure

---

## Vault the Raw Inputs, Keep the Derived Surface Fast

**Date:** 9 July 2026
**Type:** Architecture
**Generation:** SYSTEM

Securing personal data and shipping the analysis the same day looked like a trade-off. It was not one. The analysis surface was already free of personal data by construction. A workbook, a flat export, and hash bridges: the raw files feed only the rebuild step. So the raw inputs went into an ignored vault outside the tree, read through an environment variable. Hardening that vault blocks nothing.

**Principle:** Split raw personal data from derived outputs first, then vault the raw and work off the derivatives.

**Tags:** System, System, Architecture

---

## Prove a Repository Holds No Personal Data With Commands

**Date:** 9 July 2026
**Type:** Learning
**Generation:** SYSTEM

Answering a leak worry with "it is ignored, trust me" is not an answer. A dry-run stage printed the exact file set a commit would pick up: seven recipe files, no data paths. A value-free scan counted sensitive-shaped cells and printed column names and counts, never rows. Worth stating plainly too. A local agent CLI still sends its context to a server-side model.

**Principle:** Answer a data-safety question with command output, and print column names and counts, never rows.

**Tags:** System, System, Learning

---

## An Unanchored Substring Reproduced the Wrong Number Exactly

**Date:** 9 July 2026
**Type:** Failure
**Generation:** SYSTEM

A figure from a legacy deck recomputed from source and matched to the digit. It went onto the list of numbers proved correct. It was wrong. The title filter matched CTO as an unanchored substring, and those three letters sit in the middle of Director. Most of that segment was never what the label claimed. Reproducing a number validates the arithmetic behind it, never the definition.

**Principle:** Ground every criterion in real values, and test it with must-match and must-not-match examples.

**Tags:** System, System, Failure

---

## An Extraction Hub Owes Fidelity, a Synthesis Hub Owes Truth

**Date:** 6 July 2026
**Type:** Decision
**Generation:** SYSTEM

A sibling repository carried a deep trust stack: provenance pins that fail closed, a capture-then-promote path, output verifiers, and a claim register. Porting all of it into a data-extraction repository was tempting and wrong. Extraction owes fidelity to its source. Adjudicating truth belongs downstream. Port only the source registry, the raw-immutability contract, and a checker that fails closed on orphans and duplicate ids. Leave the rest.

**Principle:** Port only the fidelity machinery into an extraction repository, and leave truth adjudication downstream.

**Tags:** System, System, Decision

---

## Renaming a Directory Breaks the Virtualenv Baked Inside It

**Date:** 6 July 2026
**Type:** Learning
**Generation:** SYSTEM

Renaming a project folder broke its virtual environment. Absolute paths are baked into the interpreter shebangs and the activation script. Rebuild instead of repairing, since the environment is disposable and untracked anyway. The same session dodged a second trap. A three-line probe against an unfamiliar library confirmed what its objects actually return, before a 150-line script was written against a guessed shape.

**Principle:** Rebuild an environment after any directory move, and probe a library's real shape before coding against it.

**Tags:** System, System, Learning

---

## Move Shared Infrastructure First, Then One Unit at a Time

**Date:** 6 July 2026
**Type:** Architecture
**Generation:** SYSTEM

Relocating 23 live integration scripts risked breaking their credentials and their landed-data paths. It went cleanly. Shared infrastructure moved first, behind temporary compatibility symlinks that came out afterwards. Every path relative to a script's own file became a repository-anchored constant. Renames preserved history, 43 of them. Each unit ran live from its new home before the next one moved, and the riskiest group went last.

**Principle:** Relocate shared infrastructure first, then prove each moved unit live before moving the next.

**Tags:** System, System, Architecture

---

## Restoring the Tag Manager Relit Every Tag Behind It

**Date:** 5 July 2026
**Type:** Failure
**Generation:** SYSTEM

A chat widget reappeared on logged-out pages, although nobody touched its tag. The real change restored the tag manager to those pages, where a template render bug had kept it dark. Everything behind it came back too: the legacy widget, plus 33 advertising pixels, every one of them with consent status unset. Map triggers to tags first. Enumerate what a restore switches on.

**Principle:** Enumerate every tag a trigger reaches before restoring a tag manager on a new surface.

**Tags:** System, System, Failure

---

## A Read-Only Pull Does Not Need a Redistributable Integration

**Date:** 25 June 2026
**Type:** Decision
**Generation:** SYSTEM

Asking for API access routed me into a wizard for building a redistributable integration that would stop receiving updates. Wrong primitive for a read-only pull against one account. The right one was an account-scoped credential with least-privilege read scopes, sent as a bearer token. Read every scope name for hidden write. One that reads as object-only granted writes as well.

**Principle:** Pick the single-account credential for a single-account read, and check every scope for hidden write.

**Tags:** System, System, Decision

---

## The Site Already Set a Flag Nobody Looked For

**Date:** 24 June 2026
**Type:** Learning
**Generation:** SYSTEM

I had built a fail-closed route allowlist and queued a page-marker request. The site already sets a per-page boolean global, in an inline script before the tag manager loads. It reads true on marketing pages and false on the app. Reading that global is self-maintaining, fail closed, and needs no one. Verify both directions in preview. A negative-only check cannot tell a correct read from a blind refusal.

**Principle:** Grep the producing site for globals it already sets per page before building an allowlist.

**Tags:** System, System, Learning

---

## A Debug Timeout Pointed Below the Browser

**Date:** 24 June 2026
**Type:** Learning
**Generation:** SYSTEM

A vendor's in-page debug tool would not attach to a page whose snippet was provably in the served HTML. A clean browser profile failed the same way. That ruled out extensions and said nothing about the machine underneath the browser. Two system firewalls and a VPN were silently dropping the debug channel. Quitting them fixed it instantly. Timeout means interception below the browser; refusal means policy inside the page.

**Principle:** Read a timeout as interception below the browser and a refusal as page-level policy.

**Tags:** System, System, Learning

---

## History Expansion Rewrote a Heredoc Before Python Saw It

**Date:** 23 June 2026
**Type:** Failure
**Generation:** SYSTEM

Two commands died in one session with the same syntax error: unexpected character after a line continuation. Python never saw the script. Zsh had already rewritten the escaped exclamation mark. It did it twice, in a format specifier and in an inequality, inside a quoted heredoc. Use repr() and a negation helper instead, or write a real file and run that.

**Principle:** Keep escaped exclamation marks out of inline heredocs, or move the code into a file.

**Tags:** System, System, Failure

---

## Most Untracked-Page Flags Were Redirects and Encoding Mismatches

**Date:** 23 June 2026
**Type:** Fix
**Generation:** SYSTEM

A sweep comparing pageviews against search clicks flagged a long list of URLs as untracked. Nearly all were artifacts of two things. Search ranks a bare path while the visitor lands on a canonical one, where analytics does record the visit. And one source stores paths percent encoded while the other stores them decoded, so the join misses. Exactly one page survived as a genuine same-path undercount.

**Principle:** Resolve redirects and normalise URL encoding on both sides before calling a page untracked.

**Tags:** System, System, Fix

---

## The Spec Assumed a dataLayer Flag the Site Never Pushed

**Date:** 23 June 2026
**Type:** Learning
**Generation:** SYSTEM

An instrumentation spec said to identify logged-out visitors from a dataLayer flag. The site source showed the value lived only in application code, never pushed to the data layer. Zero dataLayer.push calls existed. A confident implementation gated on it, with a permissive path fallback, would have fired marketing tags on an authenticated application sharing the container. Grep the producing site for the actual push before gating on it.

**Principle:** Grep the producing site for the actual dataLayer push before gating a tag on an assumed variable.

**Tags:** System, System, Learning

---

## One Redirect Alias Fabricated the Entire Headline Finding

**Date:** 19 June 2026
**Type:** Fix
**Generation:** SYSTEM

A reconciliation script compared two sources per URL and flagged one key as badly undercounted. That key is an alias that forwards visitors elsewhere. One source records almost nothing there, while the other credits it as canonical. One non-comparable key produced the whole headline. A false systematic-undercount story would have shipped. Detect alias keys first, quarantine them from the scored tally, and compute rates only on meaningful denominators.

**Principle:** Quarantine non-comparable keys before scoring a reconciliation, and treat your tool's output as a claim to attack.

**Tags:** System, System, Fix

---

## No CA Bundle, Then the Sandbox Blocked the Certifi Fix

**Date:** 19 June 2026
**Type:** Fix
**Generation:** SYSTEM

A new integration written against the standard library failed with CERTIFICATE_VERIFY_FAILED. The standalone interpreter carries no system CA bundle. Pointing it at the certifi bundle raised PermissionError instead, because the agent sandbox denies reading any .pem file. Build the context explicitly with ssl.create_default_context(cafile=certifi.where()), and expect the first live call to need a sandbox exception. Neighbouring integrations never hit this; their client libraries bundle certificates internally.

**Principle:** Give any standard-library HTTP client an explicit certifi SSL context, and expect a sandbox exception.

**Tags:** System, System, Fix

---

## The Sibling Repository Had Already Paid for Every Gotcha

**Date:** 19 June 2026
**Type:** Learning
**Generation:** SYSTEM

A neighbouring project had already wired the same external API. Its design note gave the credential convention, the exact shell profile holding the key, and the fact that outbound curl is sandbox blocked. It also recorded that a 401 there means the wrong key type, not a bad key. Each one was a failure prevented. Read the sibling first, and never write to it.

**Principle:** Before wiring an integration a neighbouring project already has, read its design note for credentials and gotchas.

**Tags:** System, System, Learning

---

## A String Arrived Where an Object Was Expected

**Date:** 17 June 2026
**Type:** Failure
**Generation:** SYSTEM

The same argument channel later delivered a JSON string instead of an object. Enumerating its keys yielded about 1,500 characters treated as work items. That fanned out to the platform's 1,000-agent ceiling, burned roughly 26 million tokens across 3.8 hours, returned an empty array, and exhausted the session limit. Parse defensively for both shapes. Cap fan-out width, twenty items or throw, before anything spawns.

**Principle:** Cap fan-out width before spawning agents, and parse an argument channel as both string and object.

**Tags:** System, System, Failure

---

## A Workflow Script Got No Arguments and Died Immediately

**Date:** 10 June 2026
**Type:** Failure
**Generation:** SYSTEM

A one-off workflow died on its first statement. The JSON argument object never reached the script as a global, so the first map call threw. Re-running with the same values written inline as a literal constant worked first try. Reserve the argument channel for saved, parameterised workflows. Validate that it is populated before iterating over anything it claims to carry.

**Principle:** Inline small known inputs into a one-off script rather than trusting the argument channel.

**Tags:** System, System, Failure

---

## Repointing After a Folder Move Without Hardcoding the New Path

**Date:** 1 June 2026
**Type:** Decision
**Generation:** SYSTEM

A project directory moved, and a wrap-up document still pointed at its old absolute location. Swapping one absolute for another would just re-break on the next move, a regression already corrected on a neighbouring project. Anything that merely locates a resource now derives from the working directory. A security scope fence stays an explicit absolute. A derived fence cannot be audited by reading it.

**Principle:** Derive paths that locate a resource, and keep paths that fence access explicit and absolute.

**Tags:** System, System, Decision

---

## A Clobber Guard Defeated by the Process It Was Protecting

**Date:** 1 June 2026
**Type:** Failure
**Generation:** SYSTEM

Per-project state is keyed to a slug of the directory path. Move the project and the old history is stranded, with the new slug empty. The migration copy skips a non-empty destination, correct in isolation. But the wrap-up routine creates that slug first, trips the guard, and strands the history for good. Run the migration before anything that writes. Then let the routine rebuild its own snapshot.

**Principle:** Run a skip-if-non-empty migration before anything else can create the destination.

**Tags:** System, System, Failure

---

## Identical Filenames, Different Systems: Read the Surrounding Code

**Date:** 1 June 2026
**Type:** Learning
**Generation:** SYSTEM

Two files shared a name and were byte identical, which argued for merging them into one shared copy. The scripts around them resolve paths from Path(__file__).parent, so the design is folder scoped on purpose. Merging would have broken it. A second near miss the same day: a populated directory did not prove history survived a migration. Only a line-by-line content comparison did.

**Principle:** Before a structural decision, read the code around the files and compare content, not names or counts.

**Tags:** System, System, Learning

---

## A Destructured Parameter Named name Shadowed a Browser Global

**Date:** 22 May 2026
**Type:** Fix
**Generation:** SYSTEM

A filter in generated browser JavaScript destructured its argument as ([name]) and compared name to the selected value. In a page context that identifier is already the browsing context name. The comparison misbehaved even inside an arrow function. Index access on the tuple, p[0], fixed it. Avoid name as a parameter or loop variable in browser code, along with event, top, self, location, and status.

**Principle:** Never bind name, event, top, self, location, or status as local identifiers in browser JavaScript.

**Tags:** System, System, Fix

---

## A JSON Sidecar Cut Ninety Seconds Off Every Rebuild

**Date:** 21 May 2026
**Type:** Architecture
**Generation:** SYSTEM

A build script re-read a large workbook on every run to load one lookup table. That cost about ninety seconds each time. One session of interface iteration burned six rebuilds waiting on data that had not changed. The fix writes the lookup to a JSON sidecar and reloads only when the source mtime is newer. Read source, write sidecar, read sidecar until the source moves.

**Principle:** Cache a slow, read-only load step to a sidecar file and invalidate it on the source mtime.

**Tags:** System, System, Architecture

---

## A Yes Regex Matched a Sentence That Said No

**Date:** 20 May 2026
**Type:** Fix
**Generation:** SYSTEM

A binary confirmation signal read free-text records. One if/elif chain checked the yes pattern first, so once the yes branch fired the no check never ran. A record stating the thing was absent came back confirmed. The rewrite runs both checks independently, lets no override yes, and adds a 15-character negation guard ahead of yes. Both false positives went, and no false negative appeared.

**Principle:** Make negative and positive extraction checks independent, and let the negative always win.

**Tags:** System, System, Fix

---

## A Short Negation Lookback Beat Full Sentence Parsing

**Date:** 20 May 2026
**Type:** Fix
**Generation:** SYSTEM

An intent classifier scored a line as high intent because the phrase it matched sat inside a negated clause. Parsing the whole sentence was not needed. A 20-character lookback for not, hadn't, wasn't, never, and no longer removed the false positive. That width cuts both ways. Too wide and you suppress a negation from a different clause. Too narrow and phrases like hadn't been ready slip past.

**Principle:** Check the 15 to 25 characters before a positive match for negation words.

**Tags:** System, System, Fix

---

## Hooks Installed Mid-Session Do Not Govern That Session

**Date:** 18 May 2026
**Type:** Learning
**Generation:** SYSTEM

An agent CLI reads its JSON settings file once, at session start. Hooks installed an hour in never fired. The wrap-up routine then found a session log with zero lines and ran its fallback path instead. Install hooks as the first action of the first session. Write the load-at-start behaviour into the project instructions so the next reader expects it.

**Principle:** Install hooks first thing in the first session, because hook changes only apply at the next start.

**Tags:** System, System, Learning

---

## Port the Mature Sibling Project, Then Add Only Deltas

**Date:** 18 May 2026
**Type:** Decision
**Generation:** SYSTEM

Two neighbouring folders already had a wrap-up command. The newer one was a deliberate second iteration. It had dropped a wrapper script, tiered config, a duplicate state file, and auto-push. Rebuilding from scratch would have re-litigated every one of those rejections. I read the anti-patterns section first, ported the mature setup as it stood, then added only the deltas.

**Principle:** Read a neighbouring project's anti-pattern list first, port what it earned, then add only the deltas.

**Tags:** System, System, Decision

---

## The Filesystem Changed While the Session Was Paused

**Date:** 18 May 2026
**Type:** Learning
**Generation:** SYSTEM

The operator renamed the project folder during a pause, moved the memory directory, and edited several tracked documents. Resuming from my earlier snapshot would have written duplicates against paths that had moved. The edit tool caught it only because it demands a prior read. A read-free write would have gone through. One grep plus a directory listing costs a single command. Run it before any write lands.

**Principle:** After any pause where a human may have edited files, re-read the filesystem before writing.

**Tags:** System, System, Learning

---
