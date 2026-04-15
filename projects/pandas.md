# Pandas

> The de facto standard for data analysis and manipulation in Python.

| Metric | Data |
|--------|------|
| GitHub | [pandas-dev/pandas](https://github.com/pandas-dev/pandas) |
| Stars | 48,508 |
| Forks | 19,868 |
| License | BSD-3-Clause ✅ |
| Language | Python + Cython |
| Last Update | 2026-04-15 (today!) |
| Open Issues | 3,460 |
| Contributors | 3,500+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 80 | Mature, comprehensive API (DataFrame, Series, GroupBy, Merge, Pivot). Well-tested. Cython optimizations. Type annotations improving. |
| E (Ecosystem) | 92 | 48k⭐, 20k forks, 3.5k contributors = most contributed-to data library. De facto Python data standard. 150M+ monthly pip installs. |
| M (Market) | 65 | Mature tool, established position. Being challenged by Polars for performance-critical workloads. |
| C (Combo) | 60 | Python — useful for backend data processing, scripts, ETL. Not directly in TypeScript stack but essential Python skill. |
| **Composite** | **73** | 80×0.25 + 92×0.20 + 65×0.30 + 60×0.25 |

## Core Value

Pandas is the **lingua franca of data manipulation**. Any data pipeline, ML workflow, or analysis script in Python starts with Pandas. Its DataFrame API is so influential that Polars, Spark, and DuckDB all reference it.

## Architecture Highlights

```
pandas-dev/pandas/
├── pandas/
│   ├── core/           ← Core data structures
│   │   ├── frame.py    — DataFrame (the star)
│   │   ├── series.py   — Series
│   │   ├── groupby/    — GroupBy operations
│   │   └── reshape.py  — Pivot, melt, stack
│   ├── io/             ← I/O layer
│   │   ├── parsers/    — CSV, JSON, Excel, Parquet
│   │   ├── sql.py      — SQL read/write
│   │   └── api.py      — Public I/O API
│   ├── plotting/       ← Visualization
│   └── tests/          ← Massive test suite
```

**Key Patterns**:
- **Method chaining API**: `df.groupby('col').agg('sum').reset_index().sort_values('col')`
- **I/O abstraction**: `pd.read_csv()`, `pd.read_sql()`, `pd.read_parquet()` — unified interface
- **Copy-on-Write (new)**: Memory-efficient data operations

## Extractable Patterns

| Pattern | Value | Target |
|---------|-------|--------|
| I/O abstraction (read_*/to_*) | 🔥 High | best-practices/data-pipeline.md |
| Method chaining API design | Medium | Conceptual reference |
| GroupBy-Agg-Transform pattern | Medium | Data processing scripts |

⭐ **Universal Code Candidate**: The read_*/to_* I/O abstraction pattern — universally applicable for any data product.

## Commercial Value

- **Pain point**: Data manipulation foundation → 基础设施级
- **Not directly monetizable** — it's a library, not a product
- **For天子**: Essential Python skill for data processing backends. Use Pandas for ETL/analysis scripts in SaaS products.

## Why It Might NOT Be Worth It

- Performance ceiling: single-threaded, memory-hungry for large datasets
- Being disrupted by Polars (10-100x faster for many operations)
- Python-only — doesn't run in browser or Node.js
- For new projects, consider Polars first, Pandas as fallback

## Pandas vs Polars

| | Pandas | Polars |
|---|---|---|
| Speed | 1x (baseline) | 10-100x faster |
| Memory | High (copies) | Low (Arrow-native) |
| Threading | Single | Multi-threaded |
| API | Imperative | Lazy + Eager |
| Ecosystem | Massive | Growing fast |
| When to use | Prototyping, small data, ecosystem compat | Production, large data, performance |
