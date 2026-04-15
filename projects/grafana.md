# Grafana

> The open and composable observability and data visualization platform.

| Metric | Data |
|--------|------|
| GitHub | [grafana/grafana](https://github.com/grafana/grafana) |
| Stars | 73,210 |
| Forks | 13,731 |
| License | AGPL-3.0 ⚠️ (copyleft — derivatives must be open-sourced) |
| Language | TypeScript (frontend) + Go (backend) |
| Last Update | 2026-04-15 (today!) |
| Open Issues | 3,903 |
| Backed by | Grafana Labs ($300M+ raised, $6B valuation) |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 85 | Excellent plugin architecture (data source + panel + app plugins). TypeScript frontend + Go backend. Comprehensive alerting system. Provisioning via YAML/Terraform. |
| E (Ecosystem) | 90 | 73k⭐, 500+ community plugins, Prometheus/Loki/Tempo ecosystem. Industry standard for observability. Grafana Labs powers commercial adoption. |
| M (Market) | 70 | Observability market $50B+. Grafana dominates open-source dashboarding. But mature — main growth in Grafana Cloud. |
| C (Combo) | 50 | ⚠️ AGPL-3.0 limits commercial reuse. Go backend not in base stack. Plugin architecture learnable but not directly portable. |
| **Composite** | **73** | 85×0.25 + 90×0.20 + 70×0.30 + 50×0.25 |

## ⚠️ License Warning

**AGPL-3.0** means any derivative work served over a network MUST be open-sourced. Cannot be used as a base for proprietary SaaS without open-sourcing your entire codebase. **Study patterns only, do not fork for commercial use.**

## Core Value

Grafana's **plugin architecture** is the gold standard for extensible dashboard platforms. The data source plugin pattern (how Grafana connects to 100+ backends through a unified interface) is a masterclass in abstraction.

## Architecture Highlights

```
grafana/grafana/
├── pkg/                    ← Go backend
│   ├── api/                — REST API handlers
│   ├── services/           — Business logic
│   ├── plugins/            — Plugin management
│   └── tsdb/               — Time series DB interface
├── public/app/             ← TypeScript frontend
│   ├── core/               — Core UI framework
│   ├── features/           — Feature modules (dashboard, explore, alerting)
│   └── plugins/            — Frontend plugin system
├── packages/               ← Shared packages
│   ├── grafana-data/       — Data models & types
│   ├── grafana-ui/         — UI component library
│   └── grafana-runtime/    — Runtime utilities
└── devenv/                 — Development environment
```

**Key Patterns**:
- **Plugin SDK**: Standardized interface for data source, panel, and app plugins
- **Unified Alerting**: Multi-source alerting with notification routing
- **Provisioning**: Infrastructure-as-code for dashboards and data sources
- **Query Caching**: Intelligent query result caching layer

## Extractable Patterns (learn, don't copy due to AGPL)

| Pattern | Value | Target |
|---------|-------|--------|
| Plugin architecture design | 🔥 High | best-practices/visualization-patterns.md |
| Data source abstraction | 🔥 High | Conceptual reference only |
| Dashboard provisioning YAML | Medium | Reference for config-as-code |
| Alert routing engine | Medium | Conceptual reference |

## Commercial Value

- **Pain point**: Monitoring/observability dashboards → 重要级 for ops teams
- **TAM**: Observability market $50B+
- **Grafana Cloud**: $0-499/mo pricing model
- **For天子**: Study plugin architecture for building extensible SaaS platforms. Do NOT use code directly.

## Why It Might NOT Be Worth It

- **AGPL-3.0** = cannot use code in proprietary products
- Go backend requires learning a new language
- 3,900+ open issues = significant maintenance burden
- Grafana Labs captures most commercial value through Grafana Cloud
- For SaaS analytics, Superset's embedded SDK is more directly useful
