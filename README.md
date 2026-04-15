# 📊 data-stack

> ⭐ Maturity: **L1 Growing** — 8 projects analyzed with real TEMC scores, comparison table, and best practices extracted.

Extracted best practices and deep analyses from the world's top data analysis & visualization open-source projects. Part of the [GitHub Open Source Knowledge Restructuring Project](https://github.com/bursh3347-collab).

## 📈 Leaderboard (by TEMC Score)

| Rank | Project | Stars | TEMC | License | Trend |
|------|---------|-------|------|---------|-------|
| 1 | [DuckDB](projects/duckdb.md) | 37.5k | **86** 🔴 | MIT ✅ | 🚀 |
| 2 | [Polars](projects/polars.md) | 38.2k | **83** | MIT ✅ | 🚀 |
| 3 | [Superset](projects/apache-superset.md) | 72.4k | **77** | Apache ✅ | ↑ |
| 4 | [Grafana](projects/grafana.md) | 73.2k | **73** | AGPL ⚠️ | → |
| 5 | [Pandas](projects/pandas.md) | 48.5k | **73** | BSD ✅ | → |
| 6 | [D3.js](projects/d3js.md) | 112.7k | **71** | ISC ✅ | → |
| 7 | [Plotly.js](projects/plotly.md) | 18.2k | **69** | MIT ✅ | → |
| 8 | [Metabase](projects/metabase.md) | 46.9k | **68** | AGPL ⚠️ | → |

> TEMC = **T**echnology × 0.25 + **E**cosystem × 0.20 + **M**arket × 0.30 + **C**ombo × 0.25

## 📂 Repository Structure

```
data-stack/
├── README.md                  ← You are here
├── projects/                  ← Individual project analyses (TEMC-scored)
│   ├── duckdb.md              — 🔴 86 — Embedded analytics DB (MIT)
│   ├── polars.md              — 83 — Next-gen DataFrame (MIT)
│   ├── apache-superset.md     — 77 — BI platform (Apache)
│   ├── grafana.md             — 73 — Observability (AGPL⚠️)
│   ├── pandas.md              — 73 — Python data analysis (BSD)
│   ├── d3js.md                — 71 — Web visualization (ISC)
│   ├── plotly.md              — 69 — Charting library (MIT)
│   └── metabase.md            — 68 — BI tool (AGPL⚠️)
├── best-practices/            ← Extracted patterns from all projects
│   ├── data-pipeline.md       — Lazy eval, SQL-over-files, vectorized exec
│   └── visualization-patterns.md — Plugin arch, declarative config, grammar of graphics
├── code/                      ← Extracted code (coming in L2)
├── comparison.md              ← Side-by-side comparison table
└── SOURCES.md                 ← All source projects with links & licenses
```

## 🔥 Quick Picks for Micro SaaS Developers

| Need | Pick | Why |
|------|------|-----|
| Embedded analytics in API | **DuckDB** (86) | SQL on files, zero infra, MIT |
| High-perf data processing | **Polars** (83) | 100x Pandas, MIT, Rust engine |
| Add charts to Next.js | **Plotly.js** (69) | `npm install react-plotly.js`, MIT |
| Study dashboard patterns | **Grafana** (73) | Best plugin architecture (learn only, AGPL) |
| Study embedded analytics | **Superset** (77) | Embedded SDK pattern (Apache) |
| Python data scripts | **Pandas** (73) | De facto standard, BSD |

## 🏗️ Best Practices Extracted

### From Data Processing (DuckDB + Polars + Pandas)
- **Lazy Evaluation** — Build computation graph → optimize → execute (10-100x speedup)
- **SQL-Over-Files** — Query Parquet/CSV directly without ETL
- **Vectorized Execution** — Process 1024+ values per batch for CPU cache efficiency
- **Apache Arrow** — Zero-copy data sharing between systems

### From Visualization (D3 + Plotly + Grafana + Superset)
- **Chart Plugin Architecture** — Each chart type is an independent, registerable module
- **Declarative Configuration** — JSON-serializable chart configs for storage/sharing
- **Grammar of Graphics** — Decompose viz into Scales + Shapes + Axes + Interactions
- **Dashboard Grid Layout** — 12-column grid with drag-and-drop panels

## ⚠️ License Guide

| Safe for SaaS ✅ | Study Only ⚠️ |
|---|---|
| DuckDB (MIT) | Grafana (AGPL) |
| Polars (MIT) | Metabase (AGPL) |
| Plotly.js (MIT) | |
| Superset (Apache) | |
| Pandas (BSD) | |
| D3.js (ISC) | |

---

*Powered by [TEMC scoring methodology](https://github.com/bursh3347-collab). Data updated 2026-04-15.*
