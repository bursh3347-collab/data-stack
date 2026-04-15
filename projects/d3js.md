# D3.js

> The most powerful data visualization library for the web.

| Metric | Data |
|--------|------|
| GitHub | [d3/d3](https://github.com/d3/d3) |
| Stars | ~110,000 |
| Forks | ~23,000 |
| License | ISC |
| Language | JavaScript |
| Last Update | 2026 (active) |
| Contributors | 100+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 90 | Unmatched flexibility. SVG/Canvas/WebGL rendering. Modular architecture (30+ sub-packages). Functional composition. |
| E Ecosystem | 95 | 110k stars = most starred viz library. Observable notebooks. Massive plugin ecosystem. Industry standard for custom viz. |
| M Market | 78 | Mature, stable demand. Not growing but irreplaceable for custom visualizations. High learning curve limits adoption. |
| C Combo | 65 | JavaScript (not TypeScript-native, but TS types available). High learning curve. Better as reference than direct use for Tianzi. |
| **Overall** | **80** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 80.2 |

## Core Value
The foundation of web data visualization. Direct DOM manipulation with data binding. Unmatched flexibility for custom charts, maps, network graphs, and interactive dashboards. Every other viz library is built on top of or inspired by D3.

## Architecture Highlights
- **Data Binding (Enter-Update-Exit)**: The core paradigm — bind data to DOM elements, handle create/update/remove
- **Modular Sub-packages**: d3-scale, d3-axis, d3-shape, d3-geo, d3-transition, d3-force, etc.
- **Functional Composition**: Scales, axes, layouts are composable functions
- **SVG-First**: Native SVG manipulation with Canvas/WebGL for performance
- **Observable Integration**: Live notebooks for prototyping and sharing

## Key Modules
1. **d3-selection + d3-transition** (Core) — DOM manipulation and animation
2. **d3-scale** (Core) — Linear, log, time, ordinal, color scales
3. **d3-shape** (Medium) — Lines, areas, arcs, pies, stacks
4. **d3-geo** (Medium) — Map projections and geographic rendering
5. **d3-force** (Small) — Force-directed graph layouts

## Extractable Patterns
- **⭐ Universal Code Candidate: Scale Functions** → code-base/visualization/scales/
- Data binding paradigm (enter-update-exit)
- Force-directed graph layout algorithm
- Geographic projection patterns

## Competitors
| | D3.js | Plotly | Chart.js | ECharts |
|---|-------|--------|----------|--------|
| Flexibility | ★★★★★ | ★★★ | ★★ | ★★★ |
| Learning Curve | Hard | Easy | Easy | Medium |
| Out-of-box Charts | None | Many | Many | Many |
| Custom Viz | Unlimited | Limited | Limited | Good |
| Performance | Excellent | Good | Good | Excellent |
