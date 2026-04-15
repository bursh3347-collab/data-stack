# Apache Superset

> Modern data exploration and visualization platform — the open-source Tableau alternative.

| Metric | Data |
|--------|------|
| GitHub | [apache/superset](https://github.com/apache/superset) |
| Stars | 72,419 |
| Forks | 17,037 |
| License | Apache-2.0 ✅ |
| Language | TypeScript (frontend) + Python (backend) |
| Last Update | 2026-04-15 (today!) |
| Open Issues | 1,250 |
| Architecture | Monorepo: superset-frontend/ + superset/ + superset-embedded-sdk/ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 82 | Flask + React + TypeScript. Docker-compose ready. Plugin architecture for chart types. Embedded SDK. SQL Lab for ad-hoc queries. Comprehensive test suite. |
| E (Ecosystem) | 88 | 72k⭐, Apache Foundation governance, 1200+ contributors. Supports 40+ databases. Active commercial ecosystem (Preset.io). |
| M (Market) | 75 | BI market $33B+ growing. Tableau/Power BI alternative for self-hosted. Embedded analytics demand rising. |
| C (Combo) | 65 | TypeScript frontend matches base stack. Python backend requires learning. Docker deployment. Embedded SDK useful for SaaS. |
| **Composite** | **77** | 82×0.25 + 88×0.20 + 75×0.30 + 65×0.25 |

## Core Value

Superset is the **most complete open-source BI platform**. It combines SQL exploration, dashboard building, and chart visualization in a single platform. The embedded SDK enables white-label analytics.

## Architecture Analysis

```
apache/superset/
├── superset/              ← Python backend (Flask + SQLAlchemy)
│   ├── charts/            — Chart API & models
│   ├── dashboards/        — Dashboard management
│   ├── datasets/          — Data source management
│   ├── sql_lab/           — SQL editor
│   ├── security/          — RBAC & auth
│   └── db_engine_specs/   — 40+ database connectors
├── superset-frontend/     ← React + TypeScript
│   ├── src/components/    — UI components
│   ├── src/views/         — Page views
│   └── src/visualizations/— Chart plugins
├── superset-embedded-sdk/ ← Embeddable JS SDK
├── docker-compose.yml     — Full deployment
└── helm/                  — Kubernetes deployment
```

**Key Patterns**:
- **Chart Plugin System**: Each chart type is a plugin with schema, transform, and render
- **Database Abstraction**: db_engine_specs pattern for multi-database support
- **Embedded SDK**: iframe-based embedding with postMessage API

## Extractable Modules

| Module | Difficulty | Time | Target |
|--------|-----------|------|--------|
| Chart plugin architecture | Adapt | 4h | best-practices/visualization-patterns.md |
| Database connector pattern | Adapt | 3h | code-base/database/multi-db-connector/ |
| Embedded analytics SDK | Copy | 2h | code-base/analytics/embed-sdk/ |
| SQL Lab UI components | Heavy | 8h | Too coupled to Flask backend |

⭐ **Universal Code Candidate**: Database connector abstraction pattern (db_engine_specs) — reusable pattern for any multi-database product.

## Commercial Value

- **Pain point**: Companies need BI without paying Tableau ($70/user/mo) → 重要级
- **TAM**: BI market $33B+, self-hosted segment growing 25% YoY
- **Monetization**: Preset.io (commercial Superset) charges $20-50/user/mo
- **Differentiation**: Embedded SDK enables analytics-as-a-feature for SaaS products
- **For天子**: Study the embedded SDK pattern for adding analytics to any SaaS

## Why It Might NOT Be Worth It

- Python backend (Flask) — not aligned with天子's TypeScript base stack
- Heavy deployment (Redis + Celery + PostgreSQL + Workers)
- 1,250 open issues suggest maintenance debt
- Preset.io commercial version captures most enterprise value
- Better to study patterns than deploy entire platform

## Competitors

| | Superset | Metabase | Redash | Grafana |
|---|---|---|---|---|
| Stars | 72k | 47k | 27k | 73k |
| Backend | Python/Flask | Clojure | Python | Go |
| Frontend | React/TS | React | React | React/TS |
| Best for | SQL power users | Non-technical | SQL teams | Monitoring |
| Embedded SDK | ✅ | ✅ (paid) | ❌ | ✅ |

## 天子点评

最完整的开源BI，Embedded SDK模式值得学习。但Python后端+重部署不适合直接用，学架构后用DuckDB+自建更轻量。
