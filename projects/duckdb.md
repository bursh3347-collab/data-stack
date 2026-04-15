# DuckDB

> The SQLite for analytics — fast in-process analytical database.

| Metric | Data |
|--------|------|
| GitHub | [duckdb/duckdb](https://github.com/duckdb/duckdb) |
| Stars | ~30,000 |
| Forks | ~2,500 |
| License | MIT |
| Language | C++ (Python/Node.js/Rust/Java bindings) |
| Last Update | 2026-04 (very active) |
| Contributors | 300+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 92 | Vectorized execution engine. Column-oriented. Query Parquet/CSV/JSON directly. Zero-copy Arrow integration. |
| E Ecosystem | 82 | 30k stars, rapidly growing. MotherDuck (cloud version). DuckDB Foundation. Replacing SQLite for analytics. |
| M Market | 88 | Embedded analytics exploding. Edge computing needs. "SQLite for OLAP" positioning is brilliant. |
| C Combo | 78 | Node.js bindings (duckdb-node). SQL interface = universal. MIT license. Embed in any app for local analytics. |
| **Overall** | **86** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 85.7 |

## Core Value
Embed a full analytical database in your application with zero infrastructure. Query Parquet files, CSV, JSON directly with SQL. Columnar storage + vectorized execution = fast analytics without a server.

## Architecture Highlights
- **In-Process**: No server, runs inside your application process
- **Vectorized Execution**: Process data in batches (vectors) for CPU cache efficiency
- **Direct File Querying**: SQL directly on Parquet, CSV, JSON without importing
- **Apache Arrow Integration**: Zero-copy data exchange with other tools
- **Extension System**: Spatial, JSON, FTS, httpfs extensions
- **Multi-Language**: C/C++, Python, Node.js, Rust, Java, Go, R

## Key Modules
1. **Query Engine** (Large) — Parser, planner, optimizer, vectorized executor
2. **Storage Engine** (Large) — Columnar storage, compression, buffer management
3. **I/O Layer** (Medium) — Parquet, CSV, JSON readers/writers
4. **Extension System** (Medium) — Loadable extensions for extra functionality
5. **Language Bindings** (Medium) — Multi-language client libraries

## Extractable Patterns
- **⭐ Universal Code Candidate: Embedded SQL Analytics** → code-base/database/embedded-analytics/
- In-process database pattern (vs client-server)
- Direct file querying without ETL
- Vectorized query execution concepts

## Why #1 Data Tool for Tianzi
- MIT license, Node.js bindings = embed analytics in Next.js app
- No infrastructure needed = perfect for Micro SaaS
- SQL interface = universal, low learning curve
- Query files directly = simplify data pipelines
