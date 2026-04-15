# Data Pipeline Best Practices

> Extracted from DuckDB, Polars, Pandas, and Superset — the world's top data processing tools.

## 1. Lazy Evaluation Pattern (from Polars)

The single most important pattern in modern data processing.

**Principle**: Don't execute operations immediately. Build a computation graph, optimize it, then execute.

```python
# ❌ Eager (Pandas-style) — executes each step immediately
df = pd.read_csv('large.csv')          # Load ALL data
df = df[df['amount'] > 100]            # Filter (full scan)
df = df.groupby('category').sum()       # Aggregate
df = df.sort_values('amount')           # Sort

# ✅ Lazy (Polars-style) — builds plan, optimizes, then executes
result = (
    pl.scan_csv('large.csv')            # Just scan schema
    .filter(pl.col('amount') > 100)     # Plan: filter
    .group_by('category').agg(pl.sum('amount'))  # Plan: aggregate
    .sort('amount')                     # Plan: sort
    .collect()                          # NOW execute optimized plan
)
```

**Why it matters**: The optimizer can push filters before aggregations, eliminate unused columns, and parallelize automatically. Real-world speedup: 10-100x.

**Applicable to**: Any data processing pipeline, ETL system, or analytics backend.

## 2. SQL-Over-Files Pattern (from DuckDB)

Query files directly with SQL without loading into a database.

```sql
-- Query Parquet files directly
SELECT category, SUM(amount) as total
FROM 'data/*.parquet'
WHERE date > '2026-01-01'
GROUP BY category
ORDER BY total DESC;

-- Query CSV from S3
SELECT * FROM read_csv('s3://bucket/data.csv')
WHERE amount > 100;

-- Join Parquet with JSON
SELECT a.*, b.metadata
FROM 'orders.parquet' a
JOIN 'metadata.json' b ON a.id = b.order_id;
```

**Why it matters**: Eliminates the ETL step for analytical queries. No database setup, no data loading, just query.

**Applicable to**: Ad-hoc analytics, data exploration, SaaS analytics features.

## 3. I/O Abstraction Pattern (from Pandas)

Unified interface for reading/writing multiple formats.

```python
# Same pattern, different formats
df = pd.read_csv('data.csv')
df = pd.read_parquet('data.parquet')
df = pd.read_json('data.json')
df = pd.read_sql('SELECT * FROM table', conn)
df = pd.read_excel('data.xlsx')

# Symmetric write
df.to_csv('output.csv')
df.to_parquet('output.parquet')
df.to_json('output.json')
```

**Design principle**: `read_FORMAT()` and `to_FORMAT()` methods with consistent parameters (sep, header, encoding, etc.).

**Applicable to**: Any data product that needs to import/export multiple formats.

## 4. Vectorized Execution Pattern (from DuckDB)

Process data in batches (vectors) instead of row-by-row.

**Principle**: CPU cache lines are ~64 bytes. Processing 1024 values at once keeps data in L1/L2 cache. Row-by-row processing causes constant cache misses.

```
Row-by-row:  row1 → filter → aggregate → output
             row2 → filter → aggregate → output
             row3 → filter → aggregate → output
             ... (cache miss per row)

Vectorized:  [row1, row2, ... row1024] → filter_batch → aggregate_batch → output_batch
             (data stays in CPU cache)
```

**Result**: 10-50x speedup for analytical queries.

**Applicable to**: Any system processing >10K rows. Consider batch processing in APIs.

## 5. Data Source Connector Pattern (from Superset)

Pluggable database driver system.

```python
# Abstract interface
class DatabaseEngine:
    def get_connection(self, uri): ...
    def execute_query(self, sql): ...
    def get_schema(self, table): ...
    def get_tables(self): ...

# Concrete implementations
class PostgresEngine(DatabaseEngine): ...
class MySQLEngine(DatabaseEngine): ...
class BigQueryEngine(DatabaseEngine): ...
class DuckDBEngine(DatabaseEngine): ...
```

**Design principle**: Each database has its own quirks (SQL dialect, connection params, type mapping). Encapsulate these behind a unified interface.

**Applicable to**: Any SaaS that connects to customer databases.

## 6. Apache Arrow as Universal Data Format

Used by: DuckDB, Polars, Pandas (2.0+), Superset

**Why Arrow**: Zero-copy data sharing between systems. A DataFrame in Polars can be passed to DuckDB without serialization.

```python
# Polars → DuckDB (zero copy via Arrow)
import polars as pl
import duckdb

df = pl.DataFrame({'a': [1,2,3], 'b': ['x','y','z']})
result = duckdb.sql('SELECT * FROM df WHERE a > 1')  # Direct query!
```

**Applicable to**: Any system passing data between components. Use Arrow IPC for inter-process communication.
