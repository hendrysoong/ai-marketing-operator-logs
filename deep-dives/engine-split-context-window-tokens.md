# The Engine Split: Context Window Survival at 84K Tokens

> **Canonical URL:** https://www.hendry.ai/ai-marketing/operator-logs/engine-split-context-window-tokens/
> **Engine:** Create-Articles v7.9.2 + Create-Images v2.0.0
> **Version:** v7.9.2 / v2.0.0
> **Author:** Hendry Soong
> **Published:** March 3, 2026

---

## TLDR

The content engine hit 84,312 tokens and Claude's context compaction triggered mid-generation, silently dropping rules and producing inconsistent output. I split one monolithic engine into three modular engines -- Create-Articles (69K tokens), Create-Images (42K tokens), and Create-Compiler (10K tokens) -- connected by 6 integration contracts and a closed-loop feedback system. The split reduced the primary engine by 18% and eliminated context compaction during generation. More importantly, it introduced a principle: engines that talk through contracts are more reliable than engines that share a context window.

---

## The Breaking Point: 84K Tokens and Counting

Version 7.9.1 of the Create-Articles engine contained everything: article generation rules, voice guidelines, SEO requirements, validation tiers, SVG template definitions, SVG rendering rules, image routing logic, compilation instructions, and quality gates. Together, the system files totaled 84,312 tokens.

Claude's context window is finite. When the combined system prompt, loaded files, conversation history, and generated output approach the limit, context compaction activates. Compaction is not a graceful degradation. It is a lossy compression of the conversation history that silently drops information the model deems less relevant.

The failure mode is subtle. The engine does not error out. It does not report that rules were dropped. It generates output that looks plausible but violates rules that were compacted away. In one generation run, the validator reported all checks passing on an article that had 4 external links (requirement: 10+), used 3 banned voice patterns, and had FAQ answers that did not match the article content. The validator itself had lost access to the validation rules it was supposed to enforce.

This is not a hypothetical risk. Research on long-context language models confirms that information in the middle of a long context is retrieved less reliably than information at the beginning or end. When an 84K-token system prompt loads, the SVG template definitions sitting in the middle 30K tokens are the first casualties of attention degradation -- even before compaction triggers.

[Diagram: Horizontal bar representing 84K tokens, divided into sections -- Article Rules (front), Voice/SEO (middle), SVG Templates (middle, highlighted as "attention degradation zone"), Validation (back). An arrow labeled "context compaction" compresses the middle section]

---

## What I Moved and Why

The split was not arbitrary. I extracted components based on two criteria: (1) they could operate independently with a well-defined input/output contract, and (2) they represented a significant token cost.

### Extraction Summary

| Component | Tokens | Destination | Rationale |
|---|---|---|---|
| SVG template definitions (A through N) | 8,420 | Create-Images | Templates are self-contained rendering specs |
| SVG golden examples | 1,890 | Create-Images | Examples belong with their templates |
| SVG validation rules (EG-001 through EG-009) | 1,205 | Create-Images | Validation rules belong with the code they validate |
| Image routing logic | 1,480 | Create-Images | Routing decisions depend on template knowledge |
| Font scale rules | 890 | Create-Images | Scale calculations are rendering concerns |
| Hero layout rules | 1,433 | Create-Images | Layout rules are rendering concerns |
| **Total extracted** | **15,318** | | |

### Token Impact

- **Before split:** 84,312 tokens (single engine)
- **After split:** 68,994 tokens (Create-Articles) + 42,000 tokens (Create-Images) + 10,000 tokens (Create-Compiler)
- **Primary engine reduction:** 18.2%

The Create-Images engine is 42K tokens because it includes the extracted components plus its own workflow rules, template library, exit gates, and rendering pipeline. It is a complete engine, not a fragment.

The Create-Compiler engine is intentionally small. Its job is narrow: match VIP placeholders in articles to generated images, merge them into final HTML, and produce a compile report. 10K tokens is sufficient for that scope.

---

## Three Engines, One Pipeline

After the split, article production follows a three-stage pipeline:

### Stage 1: Create-Articles (69K tokens)

Generates the article HTML with semantic markup, schema.org JSON-LD, FAQ blocks, and VIP (Visual Image Placeholder) markers. VIP markers are `<figure>` elements with `data-vip-id`, `data-vip-type`, and `data-vip-prompt` attributes that describe the visual needed without generating it.

The article engine does not generate SVG code. This is enforced by STR-022, a blocking rule that fails the build if any `<svg>` element appears in article output. The boundary is absolute.

### Stage 2: Create-Images (42K tokens)

Reads the article HTML, extracts VIP markers, and generates SVG diagrams for each placeholder. Each SVG is rendered according to the template library (Templates A through N), validated against 9 exit gates, and saved as a standalone file.

The image engine does not modify the article. It produces images that reference VIP IDs from the article. The connection is the VIP ID, not shared context.

### Stage 3: Create-Compiler (10K tokens)

Reads the article HTML and the generated images. Matches VIP IDs to image files. Replaces VIP placeholder elements with inline SVG code or `<img>` references. Produces the final compiled HTML and a compile report listing every VIP, its matched image, and the merge result.

[Diagram: Three boxes in a horizontal row labeled "Create-Articles (69K)", "Create-Images (42K)", and "Create-Compiler (10K)". Arrows between them labeled "VIP markers" (Articles to Images) and "Article + Images" (both feeding into Compiler). Below each box, version numbers: v7.9.x, v2.0.x, v1.x.x]

---

## Integration Contracts: How Engines Talk

The engines do not share a context window. They communicate through 6 integration contracts -- versioned documents that define the exact format of data exchanged between engines.

### Contract Registry

| Contract | From | To | Purpose |
|---|---|---|---|
| `articles-to-images.md` | Create-Articles | Create-Images | VIP marker format, prompt requirements, source attribution rules |
| `articles-to-compiler.md` | Create-Articles | Create-Compiler | Article HTML structure, VIP placement rules, schema requirements |
| `verification-manifest.md` | Create-Images | Create-Compiler | Image file listing, VIP-to-file mapping, validation status |
| `reverse-manifest.md` | Create-Compiler | Create-Articles | Defect reports, fix requests, issue classification |
| `compiler-to-articles.md` | Create-Compiler | Create-Articles | Feedback on article structure issues found during compilation |
| `compiler-to-images.md` | Create-Compiler | Create-Images | Feedback on image issues found during compilation |

Each contract specifies:

- **Version:** Semantic version of the contract format.
- **Required fields:** What the sending engine must provide.
- **Optional fields:** What the sending engine may provide.
- **Validation rules:** How the receiving engine validates incoming data.
- **Breaking change policy:** What constitutes a breaking change and how it is communicated.

Contracts are version-controlled in `shared/integration-contracts/`. When an engine changes its output format, the contract is updated first. The receiving engine reads the contract, not the sending engine's internal implementation.

---

## The Feedback Loop: Catching Defects at the Source

The split introduced a new failure mode: defects that cross engine boundaries. An article might generate a VIP prompt that the image engine cannot render. An image might use dimensions that the compiler cannot inline. Before the split, these failures were invisible because everything happened in one context. After the split, they became explicit -- and fixable.

### Issue Router: 4-Tier Classification

Every defect found during compilation is classified into one of four tiers:

| Tier | Name | Description | Action |
|---|---|---|---|
| Tier 0 | Preventable | Defect could have been blocked by a rule in the source engine | Add blocking rule to source engine |
| Tier 1 | Auto-Patch | Defect has a deterministic fix | Auto-apply fix to source + compiled output |
| Tier 2 | Scoped Re-gen | Defect requires regenerating a specific section | Re-run source engine for affected section only |
| Tier 3 | Structural | Defect reveals a design flaw in the contract or engine architecture | Escalate for manual resolution |

### Reverse Manifests

When the compiler finds a defect, it produces a reverse manifest -- a structured report sent back to the source engine. The reverse manifest includes:

- **Defect ID:** Unique identifier for tracking.
- **Source engine:** Which engine produced the defective output.
- **VIP ID:** Which visual or section is affected.
- **Classification:** Tier 0/1/2/3.
- **Evidence:** The specific output that triggered the defect.
- **Suggested fix:** For Tier 0 and Tier 1, the specific rule or patch to apply.

### Fix-Forward-Only: Banned

A critical anti-pattern emerged during early split testing: fixing defects only in the compiled output without propagating the fix to the source. This creates drift between the source article and the compiled output. The next time the article is regenerated or the compiler runs, the fix is lost.

Fix-forward-only is banned. Every fix must be applied to the source engine or the source content. The compiled output is a derivative, not a source of truth.

[Diagram: Circular flow showing Create-Articles producing an article, flowing to Create-Images producing images, flowing to Create-Compiler producing compiled output. A "Reverse Manifest" arrow flows backward from Compiler to both Articles and Images. The reverse arrow is labeled with "Tier 0-3 classification"]

---

## What I Learned: Five Principles

### Principle 11: Context Windows Are Finite Resources

Treat the context window like memory allocation. Every token in the system prompt is a budget decision. SVG templates consuming 15K tokens is a choice to spend 18% of the budget on rendering specs that are only needed during image generation -- which is a separate task from article generation. The split is a memory management strategy.

### Principle 04: Advisory Rules Get Skipped Under Pressure

Rules labeled as "advisory" or "recommended" are the first casualties of context pressure. When the model needs to compress, advisory rules are deprioritized. When the model needs to choose between following a generation rule and following an advisory validation rule, the generation rule wins. Fix: make every rule either blocking (fails the build) or remove it. There is no middle ground in automated systems.

### Principle 03: One Example Beats 89 Lines of Rules

The SVG template definitions included pages of specification text. A single golden example SVG -- a complete, correct SVG that demonstrates every rule -- proved more effective than the specification text it replaced. The model can pattern-match from an example more reliably than it can synthesize behavior from a ruleset. This held true across Templates A through N.

### Principle 13: System Files Are Training Data

The system prompt is not documentation. It is not a reference manual. It is the training data for this specific task. Every sentence that does not directly improve output quality is noise that degrades signal. The split forced each engine to justify every token in its system files. Components that existed for historical reasons but did not improve current output were removed.

### Fix-Forward Creates Drift

The compiled output is a derivative of the source article and source images. Fixing the derivative without fixing the source creates two versions of truth. The next compilation overwrites the fix. The fix must always flow backward to the source engine, never forward to the output only. This principle is now enforced by the reverse manifest system.

---

## FAQ

### What is context compaction and why does it matter?

Context compaction is a mechanism used by language models to manage conversations that approach the context window limit. When the combined size of the system prompt, conversation history, and generated output exceeds the available window, the model compresses older parts of the conversation. This compression is lossy -- it silently drops information the model considers less relevant. For an AI content engine, this means rules, examples, and validation criteria can disappear mid-generation without any error or warning.

### Why not just use a model with a larger context window?

Larger context windows delay the problem without solving it. A 200K-token window accommodates an 84K system prompt today but does not accommodate the growth trajectory. More importantly, attention degradation affects long contexts regardless of the window size. Information in the middle of a 200K context is still retrieved less reliably than information at the beginning or end. The architectural solution is modular engines with bounded context, not larger windows.

### How do integration contracts differ from API specifications?

Integration contracts are narrower than API specifications. An API spec defines all possible operations on a system. An integration contract defines the specific data format exchanged between two engines for one purpose. The `articles-to-images` contract specifies only the VIP marker format -- not the article HTML structure, not the image rendering pipeline. Each contract is minimal, versioned, and owned by both the sending and receiving engine.

### What happens when a contract needs to change?

Contract changes follow semantic versioning. A change that adds optional fields is a minor version bump. A change that modifies required fields or removes fields is a major version bump. Major version changes require both engines to update simultaneously. The contract document includes a breaking change policy that specifies which changes are breaking and the expected update timeline.

### Can the engines run in parallel?

Create-Articles and Create-Images cannot run in parallel because the image engine needs the article's VIP markers as input. However, within the image engine, multiple VIP images can be generated in parallel because each image is independent. The compiler runs after both engines complete. The pipeline is sequential at the engine level but can be parallel at the task level within an engine.

### How do you test changes across engines?

Each engine has independent version history and can be tested in isolation. Create-Articles is tested by validating its HTML output against the article schema and checking for VIP marker correctness. Create-Images is tested by rendering SVGs and validating against exit gates. Create-Compiler is tested by running compilation against known-good article/image pairs and comparing output. Cross-engine testing uses the reverse manifest: compile, check for defects, verify the feedback loop catches them.

---

> Built by AI Marketing Operator -- [hendry.ai](https://www.hendry.ai)
