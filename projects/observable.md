# Observable Framework

> Data apps in JavaScript/TypeScript — from the creators of D3.js

| Metric | Value |
|--------|-------|
| GitHub | [observablehq/framework](https://github.com/observablehq/framework) |
| Stars | ~3,000 |
| License | ISC ✅ |
| Language | TypeScript |
| Last Update | Active |
| Creator | Mike Bostock (D3.js creator) |

## TEMC Scores

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 80 | TypeScript native, built-in data loaders (any language), static site output, D3/Plot first-class. Excellent architecture |
| E (Eco) | 55 | ~3k stars, smaller community. But Observable brand + D3 creator = high credibility. Company pivoted from notebooks to framework |
| M (Market) | 72 | Data app frameworks growing. Competes with Evidence, Streamlit but JS-native niche is underserved |
| C (Combo) | 78 | TypeScript native, outputs static HTML (deploy anywhere), works with DuckDB WASM. Near-perfect stack alignment |
| **Composite** | **72** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value

Built by Mike Bostock (D3.js, 112k⭐), Observable Framework brings the "data app as static site" concept to JS/TS. Data loaders can be Python, SQL, R, or JS — they run at build time. Output is static HTML with reactive JavaScript. Zero runtime server needed.

## Architecture Highlights

- **Data loaders** — polyglot (Python/SQL/JS/R), run at build time, output cached
- **Reactive JavaScript** — Observable's reactive runtime for live interactions
- **Markdown pages** — write `.md` with embedded JS code blocks
- **Built-in Plot/D3** — first-class visualization integration
- **DuckDB WASM** — in-browser SQL analytics
- **Static output** — deploy to any CDN/Vercel/Netlify

## Solo Dev Verdict

**🟢 HIGH VALUE for data features** — If you need dashboards or data pages in a SaaS product, Observable Framework's patterns (build-time data loading, static output, DuckDB WASM) are directly transferable to Next.js. Study the data loader architecture.

## Why It Might NOT Be Worth It

- Smaller community than Evidence or Streamlit
- Observable Inc pivoted multiple times (notebooks → framework) — stability risk
- Not a React framework — can't drop components into Next.js directly
- Markdown-centric may not fit all SaaS use cases
