# Key Principles

> Part of the [AI Marketing Operator Logs](README.md) by [Hendry Soong](https://www.hendry.ai)
> Canonical source: [hendry.ai/ai-marketing/operator-logs](https://www.hendry.ai/ai-marketing/operator-logs/)

Patterns that keep showing up. Extracted from 110+ logged versions across all engines.

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

---

> Canonical source: [hendry.ai/ai-marketing/operator-logs](https://www.hendry.ai/ai-marketing/operator-logs/)
