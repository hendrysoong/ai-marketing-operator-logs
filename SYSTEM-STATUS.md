# System Status

> Current engine versions as of April 2026. Updated with each release.
> Part of the [AI Marketing Operator Logs](README.md) by [Hendry Soong](https://www.hendry.ai)

| Engine | Version | Status | Last Updated |
|---|---|---|---|
| Create-Articles | v8.0.1 | Production | April 2026 |
| Create-Images | v4.1.0 | Production | April 2026 |
| Create-Compiler | v2.0.1 | Production | April 2026 |
| Listen-Competitors | v3.3 | Production | January 2026 |
| Create-Social | v1.0.2 | Production | January 2026 |
| Create-Articles-Replicate | v3.0 | Production | January 2026 |
| Listen-Competitors-Replicate | v1.0 | Validated | January 2026 |

## Architecture

- **Orchestration:** GitHub-based with CLAUDE.md routing
- **Pipeline:** Create-Articles → Create-Images → Create-Compiler → Headless CMS (Neon + Payload + Vercel)
- **Total documented versions:** 150+
- **Extracted principles:** 75
