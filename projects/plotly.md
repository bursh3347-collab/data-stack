# Plotly

> Interactive, open-source charting library for Python, R, and JavaScript.

| Metric | Data |
|--------|------|
| GitHub | [plotly/plotly.js](https://github.com/plotly/plotly.js) + [plotly/plotly.py](https://github.com/plotly/plotly.py) |
| Stars | ~17,000 (JS) + ~16,000 (Python) |
| License | MIT |
| Language | JavaScript + Python |
| Last Update | 2026 (active) |
| Contributors | 200+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 82 | Declarative API (JSON spec). 40+ chart types. WebGL for large datasets. Dash framework for full apps. |
| E Ecosystem | 78 | 33k combined stars. Plotly company behind it. Dash enterprise. Good but not dominant. |
| M Market | 75 | Strong in data science/analytics. Competes with Matplotlib, Seaborn, Altair in Python world. |
| C Combo | 70 | plotly.js usable in React/Next.js. Declarative spec = good for API-driven charts. Not TypeScript-native. |
| **Overall** | **76** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 75.7 |

## Core Value
Declarative charting that works across Python, R, and JavaScript. JSON-based chart specification means charts can be defined as data and rendered anywhere. Dash framework builds full data apps.

## Architecture Highlights
- **Declarative JSON Spec**: Charts defined as JSON objects → render in any language
- **plotly.js Core**: JavaScript rendering engine with WebGL for 3D/large data
- **Dash Framework**: Python framework for building data apps (React under the hood)
- **Chart Types**: 40+ including statistical, scientific, financial, geographic, 3D

## Extractable Patterns
- Declarative chart specification pattern (JSON → rendering)
- WebGL rendering for large datasets
- Python-to-JS bridge architecture (Dash)
