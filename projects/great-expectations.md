# Great Expectations

> The leading open-source data quality framework — "always know what to expect from your data."

| Metric | Data |
|--------|------|
| GitHub | [great-expectations/great_expectations](https://github.com/great-expectations/great_expectations) |
| Stars | ~10,000+ |
| License | Apache-2.0 ✅ |
| Language | Python |
| Last Update | Active (GX 1.0 released 2024) |
| Contributors | 400+ |

## TEMC Scoring

| Dimension | Score | Reasoning |
|-----------|-------|-----------|
| T Technology | 75 | Comprehensive expectation library (300+ built-in expectations). GX 1.0 simplified the API significantly. Fluent datasource config. Auto-generating data docs. Supports Pandas, Spark, SQL backends. |
| E Ecosystem | 72 | 400+ contributors, 10K+ stars. GX Cloud (commercial) launched. dbt integration via dbt-expectations package. Smaller community than orchestration tools but dominant in data quality niche. |
| M Market | 78 | Data quality is a growing concern (Gartner: poor data quality costs $12.9M/year avg). GX is the default open-source answer. Competitors: Soda, Elementary, Monte Carlo (commercial). EU AI Act compliance driving demand. |
| C Combo | 74 | Python library — can embed in any Python pipeline. REST API via GX Cloud. Expectations are JSON-serializable — can store/share/version. Integration with dbt, Airflow, Dagster, Prefect for pipeline-embedded quality checks. |
| **Composite** | **75** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 18.75 + 14.4 + 23.4 + 18.5 = **75.05 → 75** |

## Architecture Highlights

```
great_expectations/
├── core/                  ← GX 1.0 core — simplified fluent API
│   ├── expectation.py     ← Base Expectation class
│   ├── batch.py           ← Batch — unit of data to validate
│   ├── suite.py           ← ExpectationSuite — collection of expectations
│   ├── checkpoint.py      ← Checkpoint — run suites + actions (notify, store, etc.)
│   └── validation_result.py ← Structured validation output
├── datasource/            ← Fluent datasource configuration
│   ├── pandas/            ← Pandas DataFrame validation
│   ├── spark/             ← Spark DataFrame validation
│   └── sql/               ← SQL database validation
├── expectations/          ← 300+ built-in expectations
│   ├── core/              ← expect_column_values_to_not_be_null, etc.
│   └── contrib/           ← Community-contributed expectations
├── data_docs/             ← Auto-generated HTML documentation
│   ├── renderers/         ← Expectation → HTML rendering
│   └── site_builder.py    ← Static site generation from validation results
├── checkpoint/            ← Validation orchestration + actions
│   └── actions/           ← Slack notify, store results, update docs, etc.
└── plugins/               ← Custom expectation development
```

**Key patterns worth studying:**
- **Expectation as declarative assertion**: Each expectation is a self-documenting, JSON-serializable validation rule. `expect_column_values_to_be_between(column="age", min_value=0, max_value=150)`
- **Data Docs auto-generation**: Every validation run automatically generates browsable HTML docs showing pass/fail status, statistics, and sample failures.
- **Checkpoint + Actions**: Validation results trigger configurable actions (Slack alert, S3 upload, pipeline halt). Separation of validation from reaction.
- **Multi-backend execution**: Same expectations run on Pandas (small data), Spark (big data), or SQL (warehouse) via backend-specific execution engines.
- **Profiler**: Automatically generates expectations from existing data patterns. "Data-driven testing."

## Best Practices Extracted

1. **Declarative data quality assertions** — Define what data *should* look like, not how to check it. JSON-serializable for storage/sharing.
2. **Auto-generated data documentation** — Every validation produces human-readable docs. Zero extra effort for documentation.
3. **Checkpoint-Action separation** — Validate data → trigger actions based on results. Clean separation of concerns.
4. **Data profiling → auto-expectations** — Generate baseline expectations from existing data. Useful for legacy data onboarding.
5. **Multi-backend same-API** — Write once, validate on Pandas/Spark/SQL. Decouple logic from engine.

## Competitor Comparison

| | Great Expectations | Soda | Elementary | dbt tests |
|--|-------------------|------|-----------|----------|
| Approach | Expectation library | SodaCL (YAML-based) | dbt-native | SQL assertions |
| Backend support | Pandas/Spark/SQL | SQL + Spark | SQL (dbt) | SQL (dbt) |
| Auto-docs | ✅ Data Docs (HTML) | ✅ Soda Cloud | ✅ Elementary Cloud | ❌ |
| Auto-profiling | ✅ Built-in | ✅ Built-in | ❌ | ❌ |
| Learning curve | Medium (many concepts) | Low (YAML) | Low (dbt-native) | Lowest |
| Standalone use | ✅ Any Python pipeline | ✅ CLI + Cloud | ❌ Requires dbt | ❌ Requires dbt |
| Solo dev fit | ✅ Embeddable library | ⚠️ Cloud-first pricing | ⚠️ dbt-only | ✅ If using dbt |

## Solo Dev Verdict

**The data quality library to embed in your SaaS.** If your product handles customer data (CSV uploads, API integrations, analytics), Great Expectations lets you validate data on ingest with zero infrastructure. The auto-generated Data Docs pattern is brilliant — gives your users a data quality dashboard with almost no extra code. The JSON-serializable expectations model means you can let users *define their own data quality rules* in a UI and store them as JSON. That's a SaaS feature waiting to be built.

## Extracted for code-base

- ⭐ **Declarative assertion pattern** → `code-base/testing/data-quality/` — JSON-serializable validation rules
- ⭐ **Data Docs auto-generation** → `code-base/documentation/auto-docs/` — Validation → browsable HTML
- ⭐ **Checkpoint-Action pattern** → `code-base/patterns/checkpoint-action/` — Validate then react
- ⭐ **Data Profiler** → `best-practices/data-pipeline.md` — Auto-generate quality rules from existing data
