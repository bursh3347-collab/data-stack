# 📊 Data Stack — Side-by-Side Comparison

> Updated: 2026-04-16 | 13 projects analyzed | Based on real GitHub data

## Overview Matrix

| Project | Stars | License | Language | TEMC | Category | Active |
|---------|-------|---------|----------|------|----------|--------|
| **DuckDB** | 37.5k | MIT ✅ | C++ | **86** 🔴 | Embedded Analytics DB | ✅ Daily |
| **Polars** | 38.2k | MIT ✅ | Rust+Python | **83** 🟡 | DataFrame Engine | ✅ Daily |
| **Recharts** | 25k | MIT ✅ | TypeScript | **80** 🟡 | React Chart Library | ✅ Daily |
| **Apache Arrow** | 15k | Apache-2.0 ✅ | Multi-lang | **79** 🟡 | Columnar Memory Format | ✅ Daily |
| **Evidence** | 5k | MIT ✅ | JS/Svelte | **78** 🟡 | Code-Driven BI | ✅ Daily |
| **Superset** | 72.4k | Apache-2.0 ✅ | TS+Python | **77** 🟡 | BI Platform | ✅ Daily |
| **Streamlit** | 38k | Apache-2.0 ✅ | Python | **76** 🟡 | Python Data Apps | ✅ Daily |
| **Pandas** | 48.5k | BSD-3 ✅ | Python | **73** 🟡 | DataFrame Library | ✅ Daily |
| **Grafana** | 73.2k | AGPL-3.0 ⚠️ | TS+Go | **73** 🟡 | Observability | ✅ Daily |
| **Observable** | 3k | ISC ✅ | TypeScript | **72** 🟡 | Data App Framework | ✅ Active |
| **D3.js** | 112.7k | ISC ✅ | JavaScript | **71** 🟡 | Visualization | ⚠️ Slow |
| **Plotly.js** | 18.2k | MIT ✅ | JavaScript | **69** 🟢 | Charting Library | ✅ Active |
| **Metabase** | 46.9k | AGPL-3.0 ⚠️ | Clojure | **68** 🟢 | BI Tool | ✅ Daily |

## Dimension Breakdown

| Project | T (Tech) | E (Eco) | M (Market) | C (Combo) |
|---------|----------|---------|------------|----------|
| DuckDB | 92 | 85 | 88 | 80 |
| Polars | 90 | 82 | 85 | 75 |
| Recharts | 75 | 82 | 75 | 90 |
| Apache Arrow | 95 | 90 | 70 | 65 |
| Evidence | 78 | 68 | 80 | 82 |
| Superset | 82 | 88 | 75 | 65 |
| Streamlit | 82 | 92 | 78 | 55 |
| Pandas | 80 | 92 | 65 | 60 |
| Grafana | 85 | 90 | 70 | 50 |
| Observable | 80 | 55 | 72 | 78 |
| D3.js | 85 | 90 | 60 | 55 |
| Plotly.js | 75 | 72 | 65 | 65 |
| Metabase | 75 | 80 | 72 | 45 |

## Category Comparison

### 🏗️ Data Processing Engines

| | Polars | Pandas | DuckDB | Arrow |
|---|---|---|---|---|
| Speed | 🔥🔥🔥 (10-100x) | 1x (baseline) | 🔥🔥🔥 (columnar) | ∞ (format layer) |
| Memory | Low (Arrow) | High (copies) | Low (columnar) | Zero-copy |
| Interface | Python/Rust API | Python API | SQL | Multi-lang |
| Best for | Large DataFrames | Quick analysis | SQL analytics | Interop |
| License | MIT | BSD | MIT | Apache-2.0 |

### 📊 BI / Data App Platforms

| | Superset | Evidence | Streamlit | Observable | Grafana | Metabase |
|---|---|---|---|---|---|---|
| Paradigm | Drag-drop | SQL+Markdown | Python script | JS+Markdown | Config | No-code |
| Language | Python/TS | JS/Svelte | Python | TypeScript | TS/Go | Clojure |
| Deploy | Docker | Vercel/static | Cloud/Docker | Static/CDN | Docker | JAR |
| License | Apache ✅ | MIT ✅ | Apache ✅ | ISC ✅ | AGPL ⚠️ | AGPL ⚠️ |
| Best for | Data exploration | Code-driven BI | Python prototypes | JS data apps | Monitoring | Non-tech BI |

### 📈 Visualization Libraries

| | Recharts | D3.js | Plotly.js |
|---|---|---|---|
| Level | High-level | Low-level | Mid-level |
| React native | ✅ Yes | ❌ No | ⚠️ Wrapper |
| TypeScript | ✅ Full | ❌ No | ⚠️ Types |
| Bundle size | ~200KB | Modular | ~3MB |
| Customization | Good | Unlimited | Good |
| Best for | Next.js dashboards | Custom viz | Interactive charts |

## 🎯 Recommendations for天子 (Micro SaaS)

### Must-Have (use directly)
1. **DuckDB** (86) — Embed in API routes for analytics. MIT. Zero infra.
2. **Recharts** (80) — `npm install recharts` for any Next.js dashboard. MIT. 5min setup.
3. **Polars** (83) — Backend data processing. MIT. 100x Pandas.

### High Value (study patterns)
4. **Evidence** (78) — Study SQL+Markdown BI paradigm for data features
5. **Apache Arrow** (79) — Understand why modern data tools are fast
6. **Observable** (72) — Study data loader + static output architecture

### Study & Reference
7. **Streamlit** (76) — Study reactive data app patterns (Python)
8. **Superset** (77) — Study embedded SDK for white-label analytics
9. **D3.js** (71) — Foundation knowledge for visualization

### Reference Only (AGPL/Legacy)
10. **Grafana** (73) — Study plugin architecture, don't use code
11. **Metabase** (68) — Study UX patterns for data tools
12. **Pandas** (73) — Essential Python skill
13. **Plotly.js** (69) — Quick charts alternative
