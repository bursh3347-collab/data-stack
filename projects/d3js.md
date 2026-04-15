# D3.js

> The gold standard for data-driven document manipulation — bring data to life with SVG, Canvas, and HTML.

| Metric | Data |
|--------|------|
| GitHub | [d3/d3](https://github.com/d3/d3) |
| Stars | 112,731 |
| Forks | 22,766 |
| License | ISC ✅ |
| Language | JavaScript (Shell wrapper) |
| Last Update | 2025-12-02 |
| Contributors | 130+ |
| Open Issues | 30 |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 85 | Legendary modular architecture (30+ sub-packages), v7.9.0 stable, ISC license, VitePress docs, Rollup bundling. Each d3-* module independently usable. |
| E (Ecosystem) | 90 | 112k⭐ = top 20 all-time GitHub. Foundation for Observable Plot, Plotly, Recharts, Nivo, Victory. npm weekly downloads 3M+. |
| M (Market) | 60 | Mature/stable — the web viz standard since 2011. Not growing fast. Being abstracted away by higher-level libraries. |
| C (Combo) | 55 | Pure JS library, usable in Next.js but low-level. Learning curve high. Not directly SaaS-convertible. Value = learning resource for custom viz. |
| **Composite** | **71** | 85×0.25 + 90×0.20 + 60×0.30 + 55×0.25 |

## Core Value

D3 is the **foundational layer** of web data visualization. Almost every JavaScript charting library (Plotly, Recharts, Nivo, Victory, Observable Plot) is built on top of D3 primitives. Understanding D3 = understanding all web viz.

## Architecture Highlights

```
d3/ (umbrella package)
├── d3-selection    — DOM manipulation
├── d3-scale        — Data → visual mapping
├── d3-shape        — SVG shape generators
├── d3-axis         — Axis rendering
├── d3-force        — Force-directed layouts
├── d3-geo          — Geographic projections
├── d3-hierarchy    — Tree/treemap/pack layouts
├── d3-transition   — Animations
├── d3-zoom         — Pan & zoom
└── 20+ more sub-packages
```

**Key Pattern**: Ultra-modular — each sub-package has its own repo, tests, and npm release. Import only what you need.

## Extractable Modules

| Module | Difficulty | Time | Target |
|--------|-----------|------|--------|
| d3-scale patterns | Copy | 1h | code-base/visualization/scales/ |
| d3-force layout algorithms | Adapt | 3h | code-base/visualization/force-graph/ |
| d3-geo projection system | Heavy | 5h | Niche, skip unless needed |

⭐ **Universal Code Candidate**: d3-scale mapping patterns (linear, log, ordinal, time scales) — reusable in any data visualization context.

## Commercial Value

- **Pain point**: Custom visualizations (舒适级 — nice-to-have, not critical)
- **TAM**: Web developers needing custom charts. Massive but low willingness-to-pay for a library.
- **Monetization**: Not directly. D3 is infrastructure, not product.
- **Differentiation window**: None for D3 itself. Value is in products BUILT with D3.

## Why It Might NOT Be Worth It

- Last meaningful commit was Dec 2025 (4+ months ago) — maintenance mode
- Mike Bostock (creator) has moved focus to Observable
- High learning curve vs. higher-level alternatives (Recharts, Chart.js)
- For天子's SaaS goals, using a wrapper library (Recharts/Nivo) is 10x faster

## Competitors

| | D3.js | Chart.js | Recharts | ECharts |
|---|---|---|---|---|
| Stars | 112k | 65k | 24k | 62k |
| Approach | Low-level | Config-based | React components | Config-based |
| Learning curve | Steep | Easy | Easy | Medium |
| Customization | Unlimited | Limited | Medium | High |
| Best for | Custom viz | Quick charts | React dashboards | Enterprise |

## 天子点评

Web可视化地基，但学习曲线陡峭到离谱。天子直接用Recharts/Plotly做SaaS图表，极度定制化需求时才碰D3。
