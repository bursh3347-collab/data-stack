[English](README.md) | [中文](README_CN.md)

# 📊 data-stack

![Stars](https://img.shields.io/github/stars/bursh3347-collab/data-stack?style=flat-square)
![License](https://img.shields.io/github/license/bursh3347-collab/data-stack?style=flat-square)
![Last Commit](https://img.shields.io/github/last-commit/bursh3347-collab/data-stack?style=flat-square)

> ⭐ Maturity: **L2 Growing** — 18 projects analyzed with real TEMC scores, comparison table, best practices, and orchestration/quality coverage.

Extracted best practices and deep analyses from **18 top data analytics, orchestration & visualization open-source projects** on GitHub. Each project is scored using our [TEMC methodology](#temc-scoring) (Technology × Ecosystem × Market × Combo).

## 📈 Leaderboard (by TEMC Score)

| Rank | Project | Stars | TEMC | License | Category | Trend |
|------|---------|-------|------|---------|----------|-------|
| 1 | [DuckDB](projects/duckdb.md) | 37.5k | **86** 🔴 | MIT ✅ | Processing | 🚀 |
| 2 | [dbt-core](projects/dbt-core.md) | 10.5k | **84** | Apache ✅ | Transform | 🚀 |
| 3 | [Polars](projects/polars.md) | 38.2k | **83** | MIT ✅ | Processing | 🚀 |
| 4 | [Apache Airflow](projects/apache-airflow.md) | 38k | **81** | Apache ✅ | Orchestration | → |
| 5 | [Dagster](projects/dagster.md) | 12.5k | **80** | Apache ✅ | Orchestration | 🚀 |
| 6 | [Recharts](projects/recharts.md) | 25k | **80** | MIT ✅ | Visualization | ↑ |
| 7 | [Apache Arrow](projects/apache-arrow.md) | 15k | **79** | Apache ✅ | Processing | → |
| 8 | [Prefect](projects/prefect.md) | 17.5k | **78** | Apache ✅ | Orchestration | ↑ |
| 9 | [Evidence](projects/evidence.md) | 5k | **78** | MIT ✅ | BI/DataApp | ↑ |
| 10 | [Superset](projects/apache-superset.md) | 72.4k | **77** | Apache ✅ | BI/DataApp | ↑ |
| 11 | [Streamlit](projects/streamlit.md) | 38k | **76** | Apache ✅ | BI/DataApp | → |
| 12 | [Great Expectations](projects/great-expectations.md) | 10k | **75** | Apache ✅ | Data Quality | → |
| 13 | [Grafana](projects/grafana.md) | 73.2k | **73** | AGPL ⚠️ | BI/DataApp | → |
| 14 | [Pandas](projects/pandas.md) | 48.5k | **73** | BSD ✅ | Processing | → |
| 15 | [Observable](projects/observable.md) | 3k | **72** | ISC ✅ | BI/DataApp | → |
| 16 | [D3.js](projects/d3js.md) | 112.7k | **71** | ISC ✅ | Visualization | → |
| 17 | [Plotly.js](projects/plotly.md) | 18.2k | **69** | MIT ✅ | Visualization | → |
| 18 | [Metabase](projects/metabase.md) | 46.9k | **68** | AGPL ⚠️ | BI/DataApp | → |

> TEMC = **T**echnology × 0.25 + **E**cosystem × 0.20 + **M**arket × 0.30 + **C**ombo × 0.25

## 📋 What's Inside

### By Category

🔧 **Data Processing** (4): DuckDB, Polars, Apache Arrow, Pandas
🔄 **Orchestration & Quality** (5): dbt, Airflow, Dagster, Prefect, Great Expectations ← NEW in L2
📊 **BI / Data App Platforms** (6): Superset, Evidence, Streamlit, Observable, Grafana, Metabase
📈 **Visualization Libraries** (3): Recharts, D3.js, Plotly.js

### Comparison & Best Practices

- [📊 Full Comparison Table](comparison.md) — Side-by-side across all projects
- [🔄 Data Pipeline Patterns](best-practices/data-pipeline.md) — Lazy eval, SQL-over-files, vectorized execution, DAG-as-code, asset-centric orchestration
- [📈 Visualization Patterns](best-practices/visualization-patterns.md) — Plugin arch, declarative config, grammar of graphics

## 🔥 Quick Picks for Micro SaaS Developers

| Need | Pick | Why |
|------|------|-----|
| Embedded analytics in API | **DuckDB** (86) | SQL on files, zero infra, MIT |
| High-perf data processing | **Polars** (83) | 100x Pandas, MIT, Rust engine |
| SQL transformations | **dbt** (84) | Analytics engineering standard, Apache |
| Workflow orchestration | **Prefect** (78) | Easiest start, decorator-based, Apache |
| Modern orchestration | **Dagster** (80) | Best testing, asset-centric, Apache |
| Data quality checks | **Great Expectations** (75) | Embeddable library, auto-docs, Apache |
| Add charts to Next.js | **Recharts** (80) | React-native, composable, MIT |
| Study dashboard patterns | **Grafana** (73) | Best plugin architecture (study only, AGPL) |
| Study embedded analytics | **Superset** (77) | Embedded SDK pattern (Apache) |
| Python data scripts | **Pandas** (73) | De facto standard, BSD |

## 🏗️ Best Practices Extracted

### From Data Processing (DuckDB + Polars + Pandas + Arrow)
- **Lazy Evaluation** — Build computation graph → optimize → execute (10-100x speedup)
- **SQL-Over-Files** — Query Parquet/CSV directly without ETL
- **Vectorized Execution** — Process 1024+ values per batch for CPU cache efficiency
- **Apache Arrow** — Zero-copy data sharing between systems

### From Orchestration (Airflow + Dagster + Prefect + dbt)
- **DAG-as-Code** — Version-controlled, testable workflow definitions (Airflow)
- **Asset-First Design** — Declare data assets, let orchestrator figure out execution (Dagster)
- **Decorator Orchestration** — `@flow` + `@task` for zero-friction automation (Prefect)
- **ref()-as-Implicit-DAG** — Function calls define dependencies automatically (dbt)
- **IO Manager Abstraction** — Same code, different storage backends for dev/test/prod (Dagster)
- **Provider/Adapter Pattern** — Extensible integrations without core bloat (Airflow + dbt)

### From Data Quality (Great Expectations)
- **Declarative Assertions** — JSON-serializable quality rules, embeddable in any pipeline
- **Auto-Generated Data Docs** — Every validation produces browsable HTML documentation
- **Checkpoint-Action Pattern** — Validate → react (alert, halt, store) with clean separation

### From Visualization (D3 + Plotly + Grafana + Superset + Recharts)
- **Chart Plugin Architecture** — Each chart type is an independent, registerable module
- **Declarative Configuration** — JSON-serializable chart configs for storage/sharing
- **Grammar of Graphics** — Decompose viz into Scales + Shapes + Axes + Interactions
- **Dashboard Grid Layout** — 12-column grid with drag-and-drop panels

## ⚠️ License Guide

| Safe for SaaS ✅ | Study Only ⚠️ |
|---|---|
| DuckDB (MIT) | Grafana (AGPL) |
| Polars (MIT) | Metabase (AGPL) |
| dbt-core (Apache) | |
| Dagster (Apache) | |
| Prefect (Apache) | |
| Great Expectations (Apache) | |
| Airflow (Apache) | |
| Plotly.js (MIT) | |
| Recharts (MIT) | |
| Superset (Apache) | |
| Evidence (MIT) | |
| Streamlit (Apache) | |
| Pandas (BSD) | |
| D3.js (ISC) | |
| Arrow (Apache) | |
| Observable (ISC) | |

## 🏗️ Repository Structure

```
data-stack/
├── README.md              ← You are here
├── README_CN.md           ← 中文版
├── projects/              ← 18 individual project analyses (TEMC scored)
├── best-practices/        ← Extracted patterns from all projects
├── code/                  ← Extracted code (coming soon)
├── comparison.md          ← Side-by-side comparison table
└── SOURCES.md             ← All source projects with links & licenses
```

## <a id="temc-scoring"></a>📊 TEMC Scoring

**TEMC** = Technology × 0.25 + Ecosystem × 0.20 + Market × 0.30 + Combo × 0.25

- **T (Technology)**: Code quality, architecture, tech stack fit, docs
- **E (Ecosystem)**: Stars/forks, community activity, integrations, maintainer reputation
- **M (Market)**: Timing, competitive scarcity, trend alignment, commercializability
- **C (Combo)**: Stack compatibility, modularity, business combo potential, learning cost

## ⚔️ Solo Dev Verdict

**The Modern Data Stack for solo devs in 3 picks:**

1. **DuckDB** (86) — Your analytics engine. SQL on files, zero infra, MIT.
2. **dbt** (84) — Your transformation layer. SQL + Jinja, tested, documented.
3. **Prefect** (78) — Your orchestration. Decorator-based, runs anywhere Python runs.

Add **Great Expectations** (75) when you need data quality checks, and **Recharts** (80) for your frontend charts. Skip Grafana/Superset complexity unless you're building a dedicated analytics product.

---

*Powered by [TEMC scoring methodology](https://github.com/bursh3347-collab). Data updated 2026-04-16.*
