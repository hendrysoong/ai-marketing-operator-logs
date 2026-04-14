# Key Principles

> Part of the [AI Marketing Operator Logs](README.md) by [Hendry Soong](https://www.hendry.ai)
> Canonical source: [hendry.ai/ai-marketing/operator-logs](https://www.hendry.ai/ai-marketing/operator-logs/)

Patterns that keep showing up. Extracted from 150+ logged versions across all engines.

---

## Top 10

1. The agent is disposable. The orchestration layer is permanent.
2. The LLM generates numbers. The human sees shapes.
3. Evidence-based validation defeats hallucination.
4. Agents improvise unless explicitly forbidden.
5. Context window is a finite resource. Separate what from how.
6. One example beats 89 lines of instructions.
7. Validation-as-data. Review logs let the system prune its own rules with evidence.
8. The problems come first, then the principles, then the product.
9. Cross-session memory turns isolated agents into a learning system.
10. Version propagation across engines is the most common drift vector.

---

## All Principles

| # | Principle | Source |
|---|---|---|
| 1 | One example beats 89 lines of instructions | Create-Articles v3.8 |
| 2 | Evidence-based validation defeats hallucination | Create-Articles v7.0 |
| 3 | Match automation level to confidence level | Create-Articles v7.0 |
| 4 | Measured values must come from output, not input | Create-Articles v7.0.2 |
| 5 | Validation checks parts. Pre-output checks the whole. | Create-Articles v7.0.2 |
| 6 | Advisory rules get skipped. Make requirements structural. | Create-Articles v7.0.2 |
| 7 | Agents improvise unless explicitly forbidden | Create-Articles v6.9.5 |
| 8 | Design for integration, not standalone | Create-Articles v6.8 |
| 9 | Match the environment. Extract values from destination. | Create-Articles v6.9.9.7 |
| 10 | One source of truth. Name files so canonical source is obvious. | Create-Articles v6.5 |
| 11 | Context window is a finite resource. Separate what from how. | Create-Articles v7.9.2 |
| 12 | Rules without examples get ignored. Templates without rules sit unused. | Create-Articles v7.9.1 |
| 13 | Route to files, not directories. Agents treat options as a buffet. | Create-Articles v7.9.14 |
| 14 | Generation-time self-checks prevent problems before validation catches them. | Create-Articles v7.9.17 |
| 15 | Classify quality during collection, not after. Left-shift the gate. | Create-Articles v7.9.19 |
| 16 | Cross-session memory turns isolated agents into a learning system. | Create-Articles v7.9.20 |
| 17 | System files are training data. They must follow the same rules they enforce. | Create-Articles v7.9.22 |
| 18 | Centralise messaging. When pillars live in 4 files, they drift in 4 directions. | Create-Articles v7.9.26 |
| 19 | When writing about specs, the spec is the source of truth. | AI-SEO v7.2 |
| 20 | "Loaded" is not "read." Gates must prove comprehension, not just access. | Create-Articles v7.9.30 |
| 21 | Downstream quality gates are only useful if they can talk back. | Create-Articles v7.9.28 |
| 22 | Undocumented patterns become invisible violations. | Create-Articles v7.9.32 |
| 23 | The LLM generates numbers. The human sees shapes. | Create-Images v2.0.11 |
| 24 | Focused engines that do one thing well. | Create-Images v2.0.0 |
| 25 | When you iterate 12 times on the same type, extract the pattern. | Create-Images v2.0.17 |
| 26 | Exit gates catch what generation-time rules miss. | Create-Images v2.0.20 |
| 27 | Explicit status checks prevent implicit assumptions. | Create-Images v2.0.19 |
| 28 | Every engine that receives feedback becomes self-improving. | Create-Images v2.0.22 |
| 29 | Fix-forward-only creates drift. Every fix must flow back to source. | Create-Compiler v1.2.0 |
| 30 | The agent is disposable. The orchestration layer is permanent. | System Architecture |
| 31 | The problems come first, then the principles, then the product. | System Architecture |
| 32 | Audit the audit trail. Documentation debt compounds silently. | System Architecture |
| 33 | Separate strategy from execution. Different tools for different thinking modes. | System Architecture |
| 34 | Audit across engines, not within them. Cross-boundary drift is invisible from inside. | System Architecture |
| 35 | Voice isn't vibe. It's enforceable rules. | Create-Articles v0.1 (DEFINE) |
| 36 | ICP precision forces content precision. | Create-Articles v0.2 (UNDERSTAND) |
| 37 | Positioning is a filter that kills generic content. | Create-Articles v0.3 (POSITION) |
| 38 | Search in their language, not yours | Listen-Competitors v3.1 |
| 39 | Uncited claims are hallucination risks | Listen-Competitors v3.3 |
| 40 | Search where LLMs train | Listen-Competitors v3.3 |
| 41 | Early synthesis creates confirmation bias | Listen-Competitors v3.1 |
| 42 | Weaknesses are strategic gold | Listen-Competitors v3.2 |
| 43 | Design around constraints | Listen-Competitors v3.1 |
| 44 | Agents interpret "copy" as "recreate similar" | Replicate Brand A v2.16 |
| 45 | Slot-based architectures eliminate CSS drift | Replicate Brand A v3.0.1 |
| 46 | Self-contained templates eliminate external dependencies | Replicate Brand B v3.0 |
| 47 | Don't assume colors. Extract from actual site. | Replicate Brand C v1.1 |
| 48 | CSS extraction is the human bottleneck | Replicate v3.0 |
| 49 | Schema serves two masters: Google and LLMs | AI-SEO v7.1 |
| 50 | Context engineering is not prompt engineering. It's designing the information layer. | AI-SEO v7.1.1 |
| 51 | Contracts between engines need explicit, machine-enforceable rules. | Create-Images v2.0.25 |
| 52 | Memory is infrastructure. Without it, the system cannot learn from its own history. | Create-Compiler v1.3.2 |
| 53 | Version propagation across engines is the most common drift vector. | System Architecture (March 2026) |
| 54 | Production compiles are the real test suite for upstream engines. Every compile run reveals gaps the generator missed. | Create-Articles v7.9.33 |
| 55 | LLMs quantify experience to signal authority. The count itself is the tell — real operators describe what happened, not how many times. | Create-Articles v7.9.36 |
| 56 | Changing the output format tests whether your validation rules are coupled to structure or to quality. Ours survived because they check content, not markup. | Create-Articles v8.0.1 |
| 57 | Force the agent to show its math. Arithmetic comments before placement catch errors that visual inspection misses. | Create-Images v2.0.26 |
| 58 | When the I/O format changes but the generation rules don't, you know the rules were well-abstracted. | Create-Images v3.0.1 |
| 59 | Removing tool routing didn't remove capability — it removed decision fatigue. One tool, two modes, zero routing logic. | Create-Images v4.0.0 |
| 60 | Design for the render width, not the viewBox. 1200px SVGs that render at 760px need their minimums tuned for 0.633x. | Create-Images v4.1.0 |
| 61 | Intentional redundancy is a feature: checking the same rule at generation and compile is a safety net, not duplication. | Create-Compiler v1.3.3 |
| 62 | Moving from assembler to validator simplified the engine by removing an entire responsibility. The CMS handles assembly now — the compiler just checks the result. | Create-Compiler v2.0.1 |
| 63 | Version bumps are cross-engine operations. Grep all repos after every bump, not just the changed engine. | System Architecture |
| 64 | Shared context files need one canonical location. Per-engine copies drift with every version bump. | System Architecture |
| 65 | Centralise context once. When the same file lives in 3 engines, it diverges in 3 directions. | System Architecture |
| 66 | Migrate real content early. Speculative schema design misses every edge case that actual articles expose. | System Architecture |
| 67 | Article templates needed 3 iterations because each was driven by migrating real content, not by speculative design. | System Architecture |
| 68 | Launch preparation is a compression event — it surfaces every issue the development phase deferred. | System Architecture |
| 69 | Automated security review finds real issues but can't assess business risk. The operator's job is triage. | System Architecture |
| 70 | Moving to headless didn't just change the output format. It changed what each engine is responsible for. | System Architecture |
| 71 | Document the pipeline before automating it. Cross-repo flows need a single spec both sides can reference. | System Architecture |
| 72 | The first automated pipeline run reveals every assumption the manual process hid. Ship the pipeline, then fix what it exposes. | System Architecture |
| 73 | Time-to-live depends on content complexity, not stack complexity. | System Architecture |
| 74 | Conversation history is not version control. When three chat windows carry the system state, every session starts with a manual sync that drifts silently. | System Architecture |
| 75 | The first engine built on new infrastructure validates the infrastructure more than itself. | System Architecture |

---

> Canonical source: [hendry.ai/ai-marketing/operator-logs](https://www.hendry.ai/ai-marketing/operator-logs/)
