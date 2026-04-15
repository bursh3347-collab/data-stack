# Apache Superset

> Modern data exploration and visualization platform.

| Metric | Data |
|--------|------|
| GitHub | [apache/superset](https://github.com/apache/superset) |
| Stars | ~66,000 |
| Forks | ~15,000 |
| License | Apache-2.0 |
| Language | Python + TypeScript (React frontend) |
| Last Update | 2026-04 (very active) |
| Contributors | 1,800+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 85 | Full BI platform. SQL Lab, 50+ viz types, dashboard builder, RBAC, caching. Python/Flask backend + React/TypeScript frontend. |
| E Ecosystem | 88 | 66k stars, Apache Foundation, 1800+ contributors. Preset.io (commercial cloud). Enterprise-grade. |
| M Market | 82 | Growing as open-source Tableau/Looker alternative. Cloud BI market expanding. Preset.io proving commercial viability. |
| C Combo | 68 | Python backend (not Tianzi's primary stack). React frontend patterns useful. Dashboard design patterns valuable. |
| **Overall** | **80** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 79.8 |

## Core Value
Open-source business intelligence platform that rivals Tableau and Looker. SQL-first approach, 50+ visualization types, interactive dashboards, and RBAC security. Self-hostable with Docker.

## Architecture Highlights
- **SQL Lab**: Interactive SQL IDE with auto-complete, query history, result visualization
- **Dashboard Builder**: Drag-and-drop dashboard composition with filters, cross-filtering
- **Visualization Plugins**: Plugin architecture for custom chart types (ECharts-based)
- **Security Model**: RBAC with row-level security, dataset permissions
- **Caching Layer**: Redis/Memcached for query results and dashboard rendering
- **Database Connectors**: SQLAlchemy-based, supports 30+ databases

## Key Modules
1. **SQL Lab** (Large) — SQL IDE, query execution, result caching
2. **Dashboard Engine** (Large) — Layout, filters, cross-filtering, embedding
3. **Viz Plugin System** (Medium) — ECharts-based chart types, custom plugins
4. **Security/RBAC** (Medium) — Roles, permissions, row-level security
5. **Database Connector** (Medium) — SQLAlchemy adapters for 30+ databases

## Extractable Patterns
- **⭐ Universal Code Candidate: Dashboard Layout Engine** → code-base/ui/dashboard-layout/
- SQL query builder with parameterization
- RBAC permission model design
- Chart plugin architecture
