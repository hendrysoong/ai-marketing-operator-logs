# Why Your AI Marketing System Should Be Model-Agnostic

> Part of the [AI Marketing Operator Logs](../README.md) by [Hendry Soong](https://www.hendry.ai)
> Read the full article: [hendry.ai/ai-marketing/operator-logs/model-agnostic](https://www.hendry.ai/ai-marketing/operator-logs/model-agnostic/)

---

## Summary

Why building AI marketing systems around a single model is an architectural risk. Covers the real cost of model lock-in, how to design provider-agnostic context layers, and what happens when your primary model degrades mid-pipeline.

Drawn from operating 7 engines across multiple model providers. The engines were designed model-agnostic from Gen 2 onward — not because of ideology, but because Claude 3 Opus degraded in production and the system needed to survive the switch.

## Key Principles

- The model is a replaceable component. The context layer is permanent.
- Vendor lock-in happens at the prompt level, not the API level.
- Design for model migration as a routine operation, not an emergency.

## Engine Scope

Cross-engine reference — applies to all engines in the system.

## Status

Published — March 2026
