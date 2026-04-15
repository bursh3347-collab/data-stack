# Plotly.js

> Open-source JavaScript charting library — interactive charts for web and Dash.

| Metric | Data |
|--------|------|
| GitHub | [plotly/plotly.js](https://github.com/plotly/plotly.js) |
| Stars | 18,173 |
| Forks | 1,989 |
| License | MIT ✅ |
| Language | JavaScript |
| Last Update | 2026-04-15 |
| Open Issues | 811 |
| Backed by | Plotly Inc. (commercial company, Dash ecosystem) |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 75 | Built on D3.js + regl (WebGL). 40+ chart types. Declarative JSON schema. WebGL for large datasets (100k+ points). |
| E (Ecosystem) | 72 | 18k⭐, Dash (Python) ecosystem. Plotly.py (Python), Plotly.R. React wrapper (react-plotly.js). |
| M (Market) | 65 | Chart library market is mature and crowded (D3, Chart.js, ECharts, Highcharts, Recharts). |
| C (Combo) | 65 | JavaScript + MIT = directly usable in Next.js. react-plotly.js wrapper available. Good for adding charts to SaaS. |
| **Composite** | **69** | 75×0.25 + 72×0.20 + 65×0.30 + 65×0.25 |

## Core Value

Plotly.js offers the **best balance of interactivity and ease-of-use** among charting libraries. Its declarative JSON-based API means you describe WHAT you want, not HOW to draw it. WebGL mode handles datasets that would crash D3.

## Architecture Highlights

- **Declarative Traces**: Define chart data as JSON objects with `type`, `x`, `y`, `mode`
- **Layout System**: Unified layout config for axes, annotations, shapes
- **WebGL Rendering**: `scattergl`, `heatmapgl` for large datasets
- **Built on D3**: Uses D3 for SVG rendering, regl for WebGL

## Extractable Modules

| Module | Difficulty | Time | Target |
|--------|-----------|------|--------|
| Declarative chart config pattern | Copy | 1h | code-base/visualization/chart-config/ |
| WebGL large dataset rendering | Learn | 2h | Conceptual reference |
| react-plotly.js integration | Copy | 30min | Direct use in Next.js |

## Commercial Value

- **For天子**: react-plotly.js is the fastest way to add interactive charts to a Next.js SaaS. MIT license. Just `npm install react-plotly.js`.
- **Plotly pricing**: Open-source (MIT) → Dash Enterprise (commercial)

## Why It Might NOT Be Worth It

- Bundle size is large (~3MB minified) — impacts page load
- Styling/theming less flexible than D3
- For simple charts, Recharts (smaller, React-native) is often better
- For complex custom viz, D3 gives more control
- 811 open issues suggest limited maintenance bandwidth

## 天子点评

`npm install react-plotly.js` 是给Next.js加图表的最快路径。MIT许可，40+图表类型，够用就行，不纠结。
