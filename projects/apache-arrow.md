# Apache Arrow

> The universal columnar memory format — the backbone of modern data tools

| Metric | Value |
|--------|-------|
| GitHub | [apache/arrow](https://github.com/apache/arrow) |
| Stars | ~15,000 |
| License | Apache-2.0 ✅ |
| Language | C++, Python, Java, Rust, Go, JS, R, C# |
| Last Update | Active (daily commits) |
| Foundation | Apache Software Foundation |

## TEMC Scores

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 95 | Industry-defining columnar format. Zero-copy reads, SIMD acceleration, IPC, Flight RPC. Engineering excellence |
| E (Eco) | 90 | 15k stars, Apache Foundation, used by DuckDB/Polars/Pandas/Spark/DataFusion. Foundational infrastructure |
| M (Market) | 70 | Foundation technology — invisible to end users. Value is indirect through tools built on it |
| C (Combo) | 65 | JS bindings exist (apache-arrow npm), but primary value is understanding why DuckDB/Polars are fast |
| **Composite** | **79** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value

Apache Arrow is **why modern data tools are fast**. It defines a standard columnar memory format that enables zero-copy data exchange between systems. DuckDB reads Arrow. Polars is built on Arrow (via Rust). Pandas 2.0 uses Arrow backends. Understanding Arrow = understanding the entire modern data stack.

## Architecture Highlights

- **Columnar memory format** — cache-friendly, SIMD-optimized
- **Zero-copy** — share data between processes without serialization
- **Arrow Flight** — gRPC-based high-performance data transport
- **Multi-language** — same format across C++/Python/Java/Rust/JS/Go/R/C#
- **Parquet integration** — Arrow ↔ Parquet is the standard data pipeline
- **JS implementation** — `apache-arrow` npm package for browser/Node.js

## Key Subprojects

1. `cpp/` — Core C++ implementation (reference)
2. `python/` — PyArrow (most-used binding)
3. `js/` — JavaScript/TypeScript Arrow implementation
4. `rust/` — DataFusion query engine (now separate repo)
5. `format/` — Specification documents

## Solo Dev Verdict

**🟢 FOUNDATION KNOWLEDGE** — You don't use Arrow directly in most SaaS products. But understanding it explains why DuckDB is fast, why Polars beats Pandas, and how modern data pipelines work. The JS bindings (`apache-arrow` npm) are useful if you need to handle columnar data in Next.js API routes.

## Why It Might NOT Be Worth It

- Infrastructure layer, not application layer — no direct SaaS value
- JS implementation less mature than C++/Python/Rust
- Overkill for small datasets (< 1M rows)
- Complex specification — deep learning curve
