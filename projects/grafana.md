# Grafana

> The open and composable observability and data visualization platform.

| Metric | Data |
|--------|------|
| GitHub | [grafana/grafana](https://github.com/grafana/grafana) |
| Stars | ~68,000 |
| Forks | ~12,000 |
| License | AGPL-3.0 (+ commercial) |
| Language | Go + TypeScript (React frontend) |
| Last Update | 2026-04 (very active) |
| Contributors | 3,000+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 90 | Plugin architecture, 100+ data sources, alerting, annotations, templating. Industry-standard observability. |
| E Ecosystem | 92 | 68k stars, Grafana Labs ($6B+ valuation), 3000+ contributors. De facto monitoring standard. |
| M Market | 85 | Observability market booming. Cloud-native monitoring essential. Grafana Cloud growing rapidly. |
| C Combo | 60 | Go backend (not Tianzi's stack). React/TypeScript frontend patterns useful. Plugin architecture exemplary. |
| **Overall** | **81** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 81.0 |

## ⚠️ License
**AGPL-3.0** — Study architecture, learn plugin patterns. Don't fork for commercial SaaS.

## Core Value
The universal dashboard for time-series data. Connect any data source, build dashboards, set alerts. Plugin architecture allows infinite extensibility. Industry standard for DevOps/SRE monitoring.

## Architecture Highlights
- **Plugin Architecture**: Data source plugins, panel plugins, app plugins — all independent
- **Data Source Abstraction**: Unified query interface across 100+ data sources
- **Dashboard JSON Model**: Dashboards are JSON — version control, share, template
- **Alerting Engine**: Multi-dimensional alerting with notification channels
- **Templating Variables**: Dynamic dashboards with variable substitution

## Extractable Patterns
- **⭐ Universal Code Candidate: Plugin Architecture** → code-base/patterns/plugin-system/
- **⭐ Universal Code Candidate: Dashboard-as-Code (JSON model)** → code-base/ui/dashboard-json/
- Data source abstraction layer
- Time-series query optimization patterns
- Alert rule engine design
