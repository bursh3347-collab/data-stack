# Evidence

> Code-driven BI: Write SQL + Markdown, get a beautiful data app

| Metric | Value |
|--------|-------|
| GitHub | [evidence-dev/evidence](https://github.com/evidence-dev/evidence) |
| Stars | ~5,000 |
| License | MIT ✅ |
| Language | JavaScript/Svelte |
| Last Update | Active (daily commits) |
| Architecture | Monorepo (pnpm workspace) |

## TEMC Scores

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 78 | Svelte-based, SQL+Markdown paradigm, built-in DuckDB, clean component system. Excellent DX but Svelte ecosystem smaller than React |
| E (Eco) | 68 | ~5k stars, growing niche community. YC-backed company (Evidence Inc). Active Discord, regular releases |
| M (Market) | 80 | Code-driven BI is the 2026 trend — data teams hate drag-and-drop. Competes with Hex, Mode, but open-source + self-hosted |
| C (Combo) | 82 | JS ecosystem, deploys to Vercel/Netlify, works with DuckDB (already in data-stack). SQL-first = easy for天子 to adopt |
| **Composite** | **78** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value

Evidence turns SQL queries into polished data reports using Markdown. No Python, no notebooks, no drag-and-drop. Write `.md` files with SQL code blocks → get interactive charts and tables. It's "BI as Code" — version-controlled, git-deployable, CI/CD compatible.

## Architecture Highlights

- **Svelte + SvelteKit** under the hood (SSG/SSR)
- **Universal SQL** — connects to Postgres, BigQuery, Snowflake, DuckDB, CSV, Parquet
- **Component library** — charts, tables, maps, KPIs built-in
- **Templating engine** — `{#each}` loops, `{#if}` conditionals in Markdown
- Ships with **DuckDB** embedded for local/CSV data

## Key Modules

1. `@evidence-dev/evidence` — core framework
2. `@evidence-dev/component-utilities` — chart/table components
3. `@evidence-dev/db-commons` — database connectors
4. `@evidence-dev/duckdb` — embedded DuckDB connector
5. `@evidence-dev/preprocess` — SQL preprocessing pipeline

## Solo Dev Verdict

**🟢 HIGH VALUE** — If天子 builds any data-focused SaaS, Evidence is the fastest path to beautiful analytics pages. Write SQL, deploy to Vercel. MIT license, zero infra. Study the component patterns for your own data viz features.

## Why It Might NOT Be Worth It

- Svelte, not React — can't directly reuse in Next.js projects
- Smaller ecosystem than Superset/Metabase
- Company-backed open-source (Evidence Inc) — risk of future license change
