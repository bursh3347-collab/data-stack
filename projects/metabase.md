# Metabase

> The simplest open-source BI tool — ask questions, get answers.

| Metric | Data |
|--------|------|
| GitHub | [metabase/metabase](https://github.com/metabase/metabase) |
| Stars | ~42,000 |
| Forks | ~5,500 |
| License | AGPL-3.0 (+ commercial license) |
| Language | Clojure + TypeScript (React frontend) |
| Last Update | 2026-04 (very active) |
| Contributors | 800+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 82 | No-code query builder, SQL mode, embedding API, caching, alerts. Clean UX. Production-grade. |
| E Ecosystem | 82 | 42k stars, established company. Self-serve analytics leader. Good embedding ecosystem. |
| M Market | 80 | Growing embedded analytics market. Competes with Superset, Redash. Commercial success proven. |
| C Combo | 55 | Clojure backend = not relevant to Tianzi's stack. Embedding API and UX patterns are valuable references. |
| **Overall** | **75** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 74.6 |

## ⚠️ License Warning
**AGPL-3.0** — Self-hosting OK for internal use. Embedding in SaaS requires commercial license. Reference patterns and UX, don't fork.

## Core Value
Democratize data access. Non-technical users can create dashboards without SQL. Embeddable analytics for SaaS products. Question-based interface (natural language → SQL → chart).

## Architecture Highlights
- **Question Builder**: Visual no-code query interface that generates SQL
- **Embedding API**: White-label dashboards inside other products (iframe + JWT)
- **Collections & Permissions**: Organize dashboards with granular access control
- **Caching Engine**: Query result caching with TTL and invalidation
- **Pulse/Alerts**: Scheduled dashboard delivery via email/Slack

## Extractable Patterns
- **⭐ Universal Code Candidate: Embeddable Analytics Pattern** → code-base/ui/embedded-analytics/
- No-code query builder UX design
- JWT-based embedding authentication
- Question → SQL translation approach
