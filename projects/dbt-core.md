# dbt (data build tool)

> The standard for analytics engineering — "transform data in your warehouse using SQL SELECT statements."

| Metric | Data |
|--------|------|
| GitHub | [dbt-labs/dbt-core](https://github.com/dbt-labs/dbt-core) |
| Stars | ~10,500+ |
| License | Apache-2.0 ✅ |
| Language | Python (core), SQL + Jinja (user-facing) |
| Last Update | Active daily |
| Contributors | 500+ |

## TEMC Scoring

| Dimension | Score | Reasoning |
|-----------|-------|-----------|
| T Technology | 82 | Elegant "SQL + Jinja + YAML" paradigm. Compiles models to warehouse-native SQL. Built-in testing, documentation, lineage. dbt Mesh for multi-project at scale. Adapters for 30+ warehouses. |
| E Ecosystem | 90 | Created the "analytics engineering" discipline. 50K+ companies use dbt. dbt Community with 80K+ members. Massive package hub (dbt-utils, dbt-expectations, elementary). dbt Labs raised $414M. |
| M Market | 85 | Dominates the T in ELT. Every modern data stack includes dbt. dbt Cloud (commercial) growing rapidly. SQL-first approach means near-zero learning curve for analysts. Market timing: perfect — cloud warehouse adoption at all-time high. |
| C Combo | 78 | SQL-first makes it accessible but limits programmatic use. dbt Cloud API enables triggering from TypeScript apps. dbt-core is fully open source. Excellent for building analytics layers in SaaS products. |
| **Composite** | **84** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 20.5 + 18.0 + 25.5 + 19.5 = **83.5 → 84** |

## Architecture Highlights

```
dbt-core/
├── core/dbt/
│   ├── parser/            ← SQL + Jinja → parsed node graph
│   ├── compilation/       ← Resolve refs, apply macros → executable SQL
│   ├── runner/            ← Execute compiled SQL against warehouse
│   ├── contracts/         ← Data contracts (model-level schema enforcement)
│   ├── graph/             ← DAG of model dependencies via ref() and source()
│   ├── adapters/          ← Database-specific SQL generation (Postgres, BigQuery, etc.)
│   ├── tests/             ← Built-in schema tests (unique, not_null, relationships)
│   └── docs/              ← Auto-generated documentation + lineage graph
├── plugins/               ← Adapter plugins for each warehouse
└── dbt_project.yml        ← Project configuration
```

**Key patterns worth studying:**
- **ref() function**: The genius of dbt — `SELECT * FROM  ref('orders') ` creates implicit DAG edges. No manual dependency declaration needed.
- **Adapter pattern**: Each warehouse gets a plugin that generates warehouse-specific DDL/DML from a common interface
- **Test-as-YAML**: Schema tests declared in YAML, compiled to SQL assertions — `unique`, `not_null`, `accepted_values`, `relationships`
- **Jinja-powered SQL**: Macros enable DRY SQL with loops, conditionals, and reusable patterns
- **Materialization strategies**: `table`, `view`, `incremental`, `ephemeral` — same SQL, different physical output

## Best Practices Extracted

1. **ref() as implicit DAG** — Let function calls define dependencies instead of explicit declarations. Reduces human error.
2. **SQL-first transformation** — Analysts write SELECT statements; the tool handles DDL/DML, dependencies, and execution order.
3. **Data testing as first-class citizen** — Every model should have schema tests. dbt makes testing as easy as writing YAML.
4. **Materialization abstraction** — Same transformation logic, different physical storage strategies. Decouple "what" from "how."
5. **Lineage from code** — Auto-generated dependency graphs from `ref()` calls. No manual documentation needed.

## Competitor Comparison

| | dbt | SQLMesh | Dataform (Google) |
|--|-----|---------|-------------------|
| Paradigm | SQL + Jinja + YAML | SQL + Python, incremental-first | SQL + SQLX (JS) |
| Testing | Built-in YAML schema tests | Built-in + audit framework | Assertions in SQLX |
| Lineage | Auto from ref() | Auto + column-level | Auto within BigQuery |
| Cloud lock-in | None (30+ adapters) | None | BigQuery only |
| Incremental | Supported but verbose | First-class, automatic | Supported |
| Pricing | Core=free, Cloud=paid | Fully open source | Free (Google) |
| Solo dev fit | ✅ dbt-core is perfect | ✅ Lighter alternative | ⚠️ BigQuery only |

## Solo Dev Verdict

**Essential knowledge for any data-touching SaaS.** Even if you never use dbt directly, the mental model — SQL transformations as versioned, tested, documented code — is the gold standard. For a Micro SaaS with analytics features, dbt-core can power your data transformation layer with zero licensing cost. The `ref()` pattern alone is worth studying for any DAG-based system design.

## Extracted for code-base

- ⭐ **ref()-as-implicit-DAG pattern** → `best-practices/data-pipeline.md` — Function-call-based dependency declaration
- ⭐ **Schema test YAML pattern** → `code-base/testing/data-quality/` — Declarative data quality assertions
- ⭐ **Materialization abstraction** → `best-practices/data-pipeline.md` — Same logic, different physical outputs
- ⭐ **Adapter plugin pattern** → `code-base/integrations/adapter-pattern/` — Database-agnostic SQL generation
