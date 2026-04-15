# 📊 Data Stack — Side-by-Side Comparison

> Updated: 2026-04-15 | Based on real GitHub data

## Overview Matrix

| Project | Stars | License | Language | TEMC | Category | Active |
|---------|-------|---------|----------|------|----------|--------|
| **DuckDB** | 37.5k | MIT ✅ | C++ | **86** 🔴 | Embedded Analytics DB | ✅ Daily |
| **Polars** | 38.2k | MIT ✅ | Rust+Python | **83** 🟡 | DataFrame Engine | ✅ Daily |
| **Superset** | 72.4k | Apache-2.0 ✅ | TS+Python | **77** 🟡 | BI Platform | ✅ Daily |
| **Grafana** | 73.2k | AGPL-3.0 ⚠️ | TS+Go | **73** 🟡 | Observability | ✅ Daily |
| **Pandas** | 48.5k | BSD-3 ✅ | Python | **73** 🟡 | DataFrame Library | ✅ Daily |
| **D3.js** | 112.7k | ISC ✅ | JavaScript | **71** 🟡 | Visualization | ⚠️ Dec 2025 |
| **Plotly.js** | 18.2k | MIT ✅ | JavaScript | **69** 🟢 | Charting Library | ✅ Active |
| **Metabase** | 46.9k | AGPL-3.0 ⚠️ | Clojure | **68** 🟢 | BI Tool | ✅ Daily |

## Dimension Breakdown

| Project | T (Tech) | E (Eco) | M (Market) | C (Combo) |
|---------|----------|---------|------------|----------|
| DuckDB | 92 | 85 | 88 | 80 |
| Polars | 90 | 82 | 85 | 75 |
| Superset | 82 | 88 | 75 | 65 |
| Grafana | 85 | 90 | 70 | 50 |
| Pandas | 80 | 92 | 65 | 60 |
| D3.js | 85 | 90 | 60 | 55 |
| Plotly.js | 75 | 72 | 65 | 65 |
| Metabase | 75 | 80 | 72 | 45 |

## License Compatibility

| License | Projects | Commercial Use |
|---------|----------|---------------|
| MIT ✅ | DuckDB, Polars, Plotly.js | Full freedom |
| Apache-2.0 ✅ | Superset | Full freedom (patent grant) |
| BSD-3 ✅ | Pandas | Full freedom |
| ISC ✅ | D3.js | Full freedom |
| AGPL-3.0 ⚠️ | Grafana, Metabase | **Cannot use in proprietary SaaS** |

## Category Comparison

### 🏗️ Data Processing Engines

| | Polars | Pandas | DuckDB |
|---|---|---|---|
| Speed | 🔥🔥🔥 (10-100x Pandas) | 1x (baseline) | 🔥🔥🔥 (columnar) |
| Memory | Low (Arrow) | High (copies) | Low (columnar) |
| Interface | Python/Rust API | Python API | SQL |
| Best for | Large DataFrame ops | Quick analysis | SQL analytics |
| License | MIT | BSD | MIT |

### 📊 BI / Dashboard Platforms

| | Superset | Grafana | Metabase |
|---|---|---|---|
| Target user | SQL analysts | DevOps/SRE | Business users |
| Embedded SDK | ✅ Yes | ✅ Yes | ✅ (Paid) |
| Self-hosted | Docker | Docker | Java JAR |
| License | Apache ✅ | AGPL ⚠️ | AGPL ⚠️ |
| Best for | Data exploration | Monitoring | Non-technical BI |

### 📈 Visualization Libraries

| | D3.js | Plotly.js | (Recharts) | (ECharts) |
|---|---|---|---|---|
| Level | Low-level | Mid-level | High-level | High-level |
| Customization | Unlimited | Good | Limited | Good |
| Learning curve | Steep | Medium | Easy | Medium |
| Bundle size | Modular | ~3MB | ~200KB | ~800KB |
| Best for | Custom viz | Interactive charts | React dashboards | Enterprise |

## 🎯 Recommendations for天子 (Micro SaaS)

### Must-Have
1. **DuckDB** (86) — Embed in API routes for analytics features. MIT. Zero infra.
2. **Polars** (83) — Backend data processing. MIT. 100x Pandas performance.

### Study & Learn
3. **Superset** (77) — Study embedded SDK pattern for white-label analytics
4. **D3.js** (71) — Foundation knowledge for any visualization work

### Reference Only (AGPL)
5. **Grafana** (73) — Study plugin architecture, don't use code
6. **Metabase** (68) — Study UX patterns for data tools

### Quick Wins
7. **Plotly.js** (69) — `npm install react-plotly.js` for quick charts in Next.js
8. **Pandas** (73) — Essential Python skill for data scripts
