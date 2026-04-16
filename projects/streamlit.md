# Streamlit

> The fastest way to build Python data apps — write a script, get a web app

| Metric | Value |
|--------|-------|
| GitHub | [streamlit/streamlit](https://github.com/streamlit/streamlit) |
| Stars | ~38,000 |
| License | Apache-2.0 ✅ |
| Language | Python + TypeScript (frontend) |
| Last Update | Active (daily commits) |
| Owner | Snowflake (acquired 2022) |

## TEMC Scores

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 82 | Mature codebase, React frontend + Python backend, protobuf comm, extensive widget system. Well-architected but monolithic |
| E (Eco) | 92 | 38k stars, Snowflake backing, massive community, 1000+ community components, Streamlit Cloud hosting |
| M (Market) | 78 | De facto standard for Python data apps. But market saturating with Gradio, Mesop, Panel |
| C (Combo) | 55 | Python-only backend — doesn't match天子's TS/Next.js stack. Value is in studying patterns, not direct code reuse |
| **Composite** | **76** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value

Streamlit invented the "script → web app" paradigm. `st.write()`, `st.chart()`, `st.button()` — every line of Python becomes a UI widget. No frontend knowledge needed. Snowflake acquisition validated the model ($800M+).

## Architecture Highlights

- **Reactive scripting model** — re-runs entire script on interaction
- **Protobuf** communication between Python backend and React frontend
- **Session state** management for stateful apps
- **Custom components** via React/iframe bridge
- **Streamlit Cloud** — one-click deploy from GitHub

## Key Modules

1. `lib/streamlit/` — core Python library (widgets, caching, state)
2. `frontend/` — React TypeScript app (Material UI based)
3. `proto/` — Protobuf definitions for Python↔JS communication
4. `e2e_playwright/` — comprehensive E2E test suite

## Solo Dev Verdict

**🟡 STUDY PATTERN** — Don't use Streamlit code in your Next.js stack. Instead, study how they solved: reactive data binding, session state, widget composition. These patterns transfer to any data app. If you need a quick Python data prototype, Streamlit is unbeatable.

## Why It Might NOT Be Worth It

- Python-only = zero code reuse for TS/Next.js projects
- Snowflake ownership means priorities may shift to enterprise/cloud
- Reactive re-run model can be slow for complex apps
- Not embeddable as components in other frameworks
