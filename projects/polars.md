# Polars

> Lightning-fast DataFrame library — Rust engine, Python/Node.js API.

| Metric | Data |
|--------|------|
| GitHub | [pola-rs/polars](https://github.com/pola-rs/polars) |
| Stars | ~33,000 |
| Forks | ~2,200 |
| License | MIT |
| Language | Rust (Python/Node.js/R bindings) |
| Last Update | 2026-04 (very active) |
| Contributors | 500+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 92 | 10-100x faster than Pandas. Lazy evaluation, query optimization, multi-threaded. Rust core = memory safe. |
| E Ecosystem | 80 | 33k stars, rapidly growing. Replacing Pandas in performance-critical pipelines. Node.js bindings available. |
| M Market | 85 | Pandas replacement wave underway. Performance demands growing with larger datasets. |
| C Combo | 72 | Node.js bindings exist! Rust engine patterns valuable. MIT license = fully commercial. |
| **Overall** | **83** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 82.7 |

## Core Value
The next generation DataFrame library. 10-100x faster than Pandas by leveraging Rust, Apache Arrow, lazy evaluation, and automatic multi-threading. Same DataFrame paradigm, dramatically better performance.

## Architecture Highlights
- **Lazy Evaluation**: Build query plan → optimize → execute (like SQL query planner)
- **Apache Arrow Backend**: Columnar memory format for zero-copy operations
- **Multi-threaded Engine**: Automatic parallelization of operations
- **Expression API**: Composable, chainable data transformations
- **Streaming Mode**: Process larger-than-memory datasets
- **Node.js Bindings**: `nodejs-polars` package for TypeScript/JavaScript

## Key Modules
1. **Expression Engine** (Core) — Lazy expressions, query optimization
2. **I/O Layer** (Medium) — CSV, Parquet, JSON, IPC, database connectors
3. **GroupBy/Join** (Medium) — Parallel aggregation and join operations
4. **Streaming** (Medium) — Out-of-core processing for large datasets
5. **Language Bindings** (Medium) — Python, Node.js, R, Rust native

## Extractable Patterns
- **⭐ Universal Code Candidate: Lazy Evaluation Pattern** → code-base/patterns/lazy-eval/
- Query optimization (predicate pushdown, projection pushdown)
- Apache Arrow columnar format integration
- Rust-to-Node.js FFI binding pattern

## Why This Matters for Tianzi
- Node.js bindings = usable in TypeScript backend
- MIT license = fully commercial
- Performance patterns applicable to any data-heavy SaaS
