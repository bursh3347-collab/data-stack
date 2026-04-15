# Data Pipeline Best Practices

> Patterns extracted from DuckDB, Polars, Pandas, and modern data engineering.

## Pattern 1: ELT over ETL

```
Old (ETL): Extract → Transform → Load
New (ELT): Extract → Load → Transform (in-place)
```

**Why ELT wins**: Modern analytical databases (DuckDB, BigQuery, Snowflake) can transform data faster than external tools. Load raw data first, transform with SQL.

## Pattern 2: File-First Architecture (from DuckDB)

Skip the database for small-medium data:

```
Source → Parquet files → DuckDB SQL queries → Results
```

**Benefits**:
- No database infrastructure to manage
- Parquet files are compressed, columnar, fast
- DuckDB queries Parquet directly (no import step)
- Files are easy to version, backup, share

```sql
-- Query Parquet file directly with DuckDB
SELECT category, SUM(revenue) as total
FROM 'data/sales_2026.parquet'
GROUP BY category
ORDER BY total DESC;
```

## Pattern 3: Lazy Evaluation Pipeline (from Polars)

```python
# Build pipeline (no execution yet)
result = (
    pl.scan_parquet("data/*.parquet")  # Lazy scan
    .filter(pl.col("date") > "2026-01-01")
    .group_by("category")
    .agg(pl.col("revenue").sum())
    .sort("revenue", descending=True)
    .collect()  # Execute optimized plan
)
```

**Optimization applied automatically**:
- Predicate pushdown (filter early)
- Projection pushdown (read only needed columns)
- Join reordering
- Parallel execution

## Pattern 4: Incremental Processing

```
Full refresh (bad):  Process ALL data every run
Incremental (good):  Process only NEW/CHANGED data
```

```typescript
async function incrementalLoad(lastRunTimestamp: string) {
  // Only fetch records modified since last run
  const newRecords = await source.query(
    `SELECT * FROM events WHERE updated_at > ?`,
    [lastRunTimestamp]
  );
  
  // Upsert into target
  await target.upsert(newRecords, { conflictKey: 'id' });
  
  // Update checkpoint
  await saveCheckpoint(new Date().toISOString());
}
```

## Pattern 5: Data Quality Checks

Run these after every pipeline step:

```typescript
const qualityChecks = [
  { name: 'not_null', check: (df) => df.filter(col('id').isNull()).count() === 0 },
  { name: 'unique', check: (df) => df.select('id').unique().count() === df.count() },
  { name: 'range', check: (df) => df.filter(col('age').gt(150)).count() === 0 },
  { name: 'freshness', check: (df) => df.select(col('updated_at').max()).gt(yesterday()) },
];
```

## Anti-Patterns

1. **Processing everything in Python loops** — Use vectorized operations (Polars/Pandas)
2. **Storing data as CSV** — Use Parquet (10x smaller, 100x faster queries)
3. **No schema validation** — Validate data types on ingestion
4. **No idempotency** — Pipelines should be safely re-runnable
5. **Ignoring data freshness** — Monitor when data was last updated
