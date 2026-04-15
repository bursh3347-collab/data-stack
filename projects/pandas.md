# Pandas

> Powerful Python data analysis and manipulation library.

| Metric | Data |
|--------|------|
| GitHub | [pandas-dev/pandas](https://github.com/pandas-dev/pandas) |
| Stars | ~45,000 |
| Forks | ~18,000 |
| License | BSD-3-Clause |
| Language | Python (C/Cython core) |
| Last Update | 2026-04 (very active) |
| Contributors | 3,200+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 88 | DataFrame API gold standard. Rich I/O (CSV, Excel, SQL, Parquet, JSON). GroupBy, merge, pivot, time-series. |
| E Ecosystem | 92 | 45k stars, 3200+ contributors. Core of Python data science stack. NumPy Foundation steward. |
| M Market | 80 | Mature, universal adoption. Being challenged by Polars for performance but still dominant. |
| C Combo | 55 | Python-only. DataFrame patterns conceptually applicable. API design is a gold standard reference. |
| **Overall** | **79** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 78.9 |

## Core Value
The lingua franca of data analysis. DataFrame API is the mental model every data analyst uses. Rich I/O, powerful transformations, and seamless integration with the entire Python data stack.

## Architecture Highlights
- **DataFrame/Series Core**: 2D labeled data structure with rich indexing
- **Vectorized Operations**: NumPy-based for performance, avoid Python loops
- **GroupBy Engine**: Split-apply-combine pattern for aggregation
- **I/O System**: Read/write CSV, Excel, SQL, Parquet, JSON, HDF5, Feather
- **Extension Arrays**: Custom data types (categorical, nullable integers, string)

## Extractable Patterns
- DataFrame API design (method chaining, lazy evaluation concepts)
- Split-apply-combine aggregation pattern
- Data I/O abstraction layer
