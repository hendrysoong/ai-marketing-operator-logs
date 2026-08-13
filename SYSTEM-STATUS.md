# System Status

> Current engine versions as of August 2026. Updated with each release.
> Part of the [AI Marketing Operator Logs](README.md) by [Hendry Soong](https://www.hendry.ai)

Status and version are mirrored from the engine repository's own status file. `Last Updated` is the
date that version was set, not the date the engine was last used.

| Engine | Version | Status | Last Updated |
|---|---|---|---|
| Create-Articles | v8.3.0 | Stable | August 2026 |
| Create-Images | v4.8.0 | Stable | August 2026 |
| Create-Compiler | v2.0.1 | Retired | April 2026 |
| Listen-Competitors | v3.3 | Dormant | February 2026 |
| Create-Social | v1.0.2 | Dormant | March 2026 |
| Create-Articles-Replicate | v3.0 | Production | January 2026 |
| Listen-Competitors-Replicate | v1.0 | Validated | January 2026 |

**Retired** means the engine's role moved elsewhere and its files are retained as history —
`tools/validate` is authoritative for validation. **Dormant** means the spec is frozen and the
engine has produced no new output: Listen-Competitors since February 2026, Create-Social since its
spec froze in March 2026.

## Architecture

- **Orchestration:** GitHub-based with CLAUDE.md routing
- **Pipeline:** Create-Articles → Create-Images → validation → Headless CMS (Neon + Payload + Vercel)
- **Total curated iterations:** 729 — 721 changelog entries plus 8 deep dives, across 15 tracks. Of the 714 that mirror the site, 123 are attributed to the 7 named engines and 591 to cross-engine system work; 7 exist only here (declared Create-Articles curation); 3 engines planned
- **Extracted principles:** 81
