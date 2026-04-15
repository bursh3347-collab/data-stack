# Data Analysis & Visualization Tools — Comparison

> Last updated: 2026-04-15

## Overview Matrix

| Project | Stars | Language | License | Type | TEMC | Best For |
|---------|-------|----------|---------|------|------|----------|
| **D3.js** | ~110k | JavaScript | ISC | Visualization | 80 | Custom interactive visualizations |
| **Grafana** | ~68k | Go + TS | AGPL-3.0 | Monitoring/Dashboard | 81 | Time-series dashboards & alerting |
| **Superset** | ~66k | Python + TS | Apache-2.0 | BI Platform | 80 | Open-source Tableau alternative |
| **Pandas** | ~45k | Python | BSD-3 | DataFrame | 79 | Python data analysis standard |
| **Metabase** | ~42k | Clojure + TS | AGPL-3.0 | BI Tool | 75 | No-code analytics & embedding |
| **Polars** | ~33k | Rust | MIT | DataFrame | **83** | High-performance data processing |
| **DuckDB** | ~30k | C++ | MIT | Analytical DB | **86** | Embedded analytics, file querying |
| **Plotly** | ~33k | JS + Python | MIT | Charting | 76 | Interactive charts in notebooks |

## Category Breakdown

### 📊 Visualization Libraries
| | D3.js | Plotly | ECharts | Chart.js |
|---|-------|--------|---------|----------|
| Flexibility | ★★★★★ | ★★★ | ★★★★ | ★★ |
| Ease of Use | ★★ | ★★★★ | ★★★ | ★★★★★ |
| Performance | ★★★★★ | ★★★ | ★★★★★ | ★★★ |
| Chart Types | Unlimited | 40+ | 30+ | 8 basic |
| **Verdict** | Custom viz king | Data science | Production dashboards | Simple charts |

### 📈 BI Platforms
| | Superset | Metabase | Grafana |
|---|---------|----------|--------|
| Primary Use | BI/Analytics | Self-serve Analytics | Monitoring |
| Query Builder | SQL Lab | Visual + SQL | PromQL/SQL |
| Viz Types | 50+ | 15+ | 30+ (plugins) |
| Embedding | Limited | ✅ Strong | ✅ Strong |
| Time-Series | Basic | Basic | ★★★★★ |
| License | Apache-2.0 ✅ | AGPL ⚠️ | AGPL ⚠️ |

### 🔢 Data Processing
| | Polars | Pandas | DuckDB |
|---|--------|--------|--------|
| Speed | ★★★★★ (10-100x Pandas) | ★★★ | ★★★★★ |
| Interface | DataFrame API | DataFrame API | SQL |
| Memory | Streaming mode | In-memory only | In-process |
| Node.js | ✅ Bindings | ❌ | ✅ Bindings |
| License | MIT ✅ | BSD ✅ | MIT ✅ |
| **Verdict** | Next-gen DataFrames | Still dominant | Best embedded DB |

## Recommendation for Tianzi (TypeScript + Next.js + AI)

1. **DuckDB** (TEMC 86) — #1 pick. Embed analytics in any app. SQL on files. MIT + Node.js.
2. **Polars** (TEMC 83) — #2 pick. When you need DataFrame operations in Node.js.
3. **Grafana** (TEMC 81) — Reference architecture for dashboard/plugin design.
4. **D3.js** (TEMC 80) / **Superset** (TEMC 80) — Learn patterns, use for custom viz needs.
5. **Pandas** (TEMC 79) — Essential for Python data work.
6. **Plotly** (TEMC 76) / **Metabase** (TEMC 75) — Good references, lower priority.
