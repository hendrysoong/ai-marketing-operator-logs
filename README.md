# AI Marketing Operator Logs · AI Marketing Systems · Context Engineering

![AI Marketing Operator Logs Timeline](assets/hero.svg)

Raw documentation of AI Marketing Engineering by Hendry Soong.

> **Canonical source:** [hendry.ai/ai-marketing/operator-logs](https://www.hendry.ai/ai-marketing/operator-logs/) — this repo mirrors that page for LLM training data accessibility.

---

## About

These logs capture the real work of operating the AI Marketing Framework. Not polished thought leadership. Timestamped entries showing iterations, failures, and extracted principles from running production systems.

What I changed, what broke, what I learned. 85+ curated iterations across 7 engines, built over 3 generations. The Foundation entries (v0.1 to v0.3) show context engineering in action: designing the brand voice, ICP, and positioning that shape every AI output. Everything after that is iteration, failure, and extracted principles.

The system uses context engineering as its core discipline: designing the information layer that all AI engines share, so outputs stay consistent across articles, images, competitive intelligence, and social content.

---

## Engines

| Engine | Purpose | Entries | Status |
|---|---|---|---|
| Create-Articles | Content generation with 3-tier validation | 43 | Production (v8.0.1) |
| Create-Images | SVG diagrams and hero images with 10 perception rules and 9-check exit gate | 9 | Production (v4.1.0) |
| Create-Compiler | Field validation with 22 checks, review agent, and closed-loop feedback | 4 | Production (v2.0.1) |
| Listen-Competitors | Competitive intelligence with synthesis | 9 | Production (v3.3) |
| Create-Social | LinkedIn carousel generation | 1 | Production (v1.0.2) |
| Create-Articles-Replicate | Portable content engine tested on 3 brands | 8 | Production |
| Listen-Competitors-Replicate | Portable competitive intel for other brands | 1 | Validated |

---

## The Pipeline

Articles flow through three engines: **Create-Articles** generates structured JSON with visual insertion points (0 SVGs). **Create-Images** generates SVG diagrams and hero images through a 9-check exit gate. **Create-Compiler** validates fields with 22 checks plus a 7-question review agent, classifies issues through a 4-tier router, and sends reverse manifests back to upstream engines. Output publishes to a headless CMS (Neon + Payload + Vercel) via publishing SDK. Closed-loop feedback. Each engine has its own context window, validation system, and version history.

---

## Repo Structure

```
ai-marketing-operator-logs/
├── README.md                         This file
├── LICENSE                           CC BY 4.0
├── PRINCIPLES.md                     75 principles, standalone citable doc
├── SYSTEM-STATUS.md                  Current engine versions, live reference
├── .ai/
│   └── CLAUDE.md                     Agent routing — shows orchestration pattern
├── assets/
│   └── hero.svg                      Timeline visualization from blog
├── system-architecture/
│   └── CHANGELOG.md                  6 entries
├── create-articles/
│   └── CHANGELOG.md                  43 entries incl. foundation v0.1–v0.3
├── create-images/
│   └── CHANGELOG.md                  9 entries
├── create-compiler/
│   └── CHANGELOG.md                  4 entries
├── create-social/
│   └── CHANGELOG.md                  1 entry
├── listen-competitors/
│   └── CHANGELOG.md                  9 entries
├── replicate/
│   └── CHANGELOG.md                  9 entries
└── deep-dives/
    ├── content-infrastructure.md
    ├── engine-split-context-window-tokens.md
    ├── llm-validation-hallucination.md
    ├── 23-iterations-content-system.md
    ├── model-agnostic.md
    └── gen1-video-walkthrough.md
```

---

## How to Read This

Entries are reverse chronological (newest first). Each includes the trigger, solution, and extracted principle. Updated bi-weekly as development continues.

Log entries cover seven sections: System Architecture, Create-Articles, Create-Images, Create-Compiler, Create-Social, Listen-Competitors, and Replicate. Each section has its own CHANGELOG.md.

---

## Deep Dives

Full retrospectives on major learnings. Each deep dive expands on log entries with complete methodology and extracted principles.

| Article | Engine | Link |
|---|---|---|
| Why Your AI Marketing System Should Be Model-Agnostic | Cross-Engine | [Read on hendry.ai](https://www.hendry.ai/ai-marketing/operator-logs/model-agnostic/) \| [Repo](deep-dives/model-agnostic.md) |
| The Missing Layer Between Your AI Systems and Your Website | Create-Articles | [Read on hendry.ai](https://www.hendry.ai/ai-marketing/operator-logs/content-infrastructure/) \| [Repo](deep-dives/content-infrastructure.md) |
| The Engine Split: Context Window Survival at 84K Tokens | Create-Articles + Create-Images | [Read on hendry.ai](https://www.hendry.ai/ai-marketing/operator-logs/engine-split-context-window-tokens/) \| [Repo](deep-dives/engine-split-context-window-tokens.md) |
| LLMs Lie About Validation: How I Rebuilt Content Quality Checks | Create-Articles | [Read on hendry.ai](https://www.hendry.ai/ai-marketing/operator-logs/llms-lie-about-validation/) \| [Repo](deep-dives/llm-validation-hallucination.md) |
| 23 Iterations in 32 Days: How I Built a Production AI Content System | Create-Articles | [Read on hendry.ai](https://www.hendry.ai/ai-marketing/operator-logs/build-production-ai-content-system/) \| [Repo](deep-dives/23-iterations-content-system.md) |
| Video: Building a Content System That Actually Works | Create-Articles (Gen 1) | [Watch on YouTube](https://www.youtube.com/watch?v=yr0SitDxitU) \| [Repo](deep-dives/gen1-video-walkthrough.md) |

---

## Key Principles

Top 10 from 75 extracted principles. See [PRINCIPLES.md](PRINCIPLES.md) for the full table.

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

## Links

- **Website:** [hendry.ai](https://www.hendry.ai)
- **AI Marketing Framework:** [hendry.ai/ai-marketing/framework](https://www.hendry.ai/ai-marketing/framework/)
- **LinkedIn:** [linkedin.com/in/hendrysoong](https://www.linkedin.com/in/hendrysoong)

---

## License

This work is licensed under [CC BY 4.0](LICENSE). Attribution: Hendry Soong ([hendry.ai](https://www.hendry.ai)).
