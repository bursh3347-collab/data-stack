# Dagster

> The modern orchestration platform built for the whole development lifecycle — "an orchestrator that's also a development framework."

| Metric | Data |
|--------|------|
| GitHub | [dagster-io/dagster](https://github.com/dagster-io/dagster) |
| Stars | ~12,500+ |
| License | Apache-2.0 ✅ |
| Language | Python |
| Last Update | Active daily |
| Contributors | 450+ |

## TEMC Scoring

| Dimension | Score | Reasoning |
|-----------|-------|-----------|
| T Technology | 85 | Asset-centric paradigm is genuinely innovative. Software-defined assets, built-in IO managers, type system, and `materialize_to_memory` for testing. Dagster+ (cloud) offers branch deployments. Best developer experience in the category. |
| E Ecosystem | 78 | Growing rapidly from Airflow migration wave. 450+ contributors, active Slack community. Integrations for dbt, Spark, Snowflake, etc. Dagster Labs raised $94M Series C. Smaller ecosystem than Airflow but higher quality. |
| M Market | 80 | Positioned as "the modern Airflow replacement." Wins on developer experience and testing story. Asset-centric approach resonates with analytics engineers. Market timing excellent — teams actively migrating from Airflow. |
| C Combo | 76 | Python-only but excellent API design. REST API + GraphQL API for external integration. Lightweight local dev (single `dagster dev` command). Embedded mode possible for SaaS. Higher combo potential than Airflow for solo devs. |
| **Composite** | **80** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 21.25 + 15.6 + 24.0 + 19.0 = **79.85 → 80** |

## Architecture Highlights

```
dagster/
├── python_modules/dagster/dagster/
│   ├── _core/
│   │   ├── definitions/   ← Assets, Jobs, Schedules, Sensors, Resources
│   │   ├── execution/     ← Run coordination, step execution engine
│   │   ├── storage/       ← Event log, run storage, IO managers
│   │   ├── instance/      ← DagsterInstance — the central runtime state
│   │   └── launcher/      ← Run launchers (local, Docker, K8s, ECS)
│   ├── _config/           ← Pydantic-style config system
│   ├── _daemon/           ← Background scheduler, sensor, run monitoring
│   └── _grpc/             ← gRPC for multi-process code location serving
├── dagster-webserver/     ← React UI (Dagit) — asset lineage graph, run viewer
└── dagster-cloud/         ← Dagster+ cloud-specific modules
```

**Key patterns worth studying:**
- **Software-Defined Assets**: Declare what the data *should be* (like a dbt model), not just the computation steps. The system figures out what to run.
- **IO Managers**: Abstract storage layer — same asset code writes to local filesystem in dev, S3/GCS in prod, in-memory for tests
- **Resources pattern**: Dependency injection for external services — swap real APIs for mocks in testing
- **Type system**: Input/output types with validation, making pipeline interfaces explicit
- **`materialize_to_memory`**: Execute assets in tests without any external infrastructure

## Best Practices Extracted

1. **Asset-first > Task-first** — Define what data assets exist and their dependencies. Let the orchestrator figure out execution order.
2. **IO Manager abstraction** — Decouple compute from storage. Same code, different storage backends for dev/test/prod.
3. **Resource injection** — Dependency injection pattern for external services. Makes testing trivial.
4. **Type-safe pipelines** — Explicit input/output types catch integration errors at definition time, not runtime.
5. **Single-command local dev** — `dagster dev` runs everything locally. No docker-compose needed.

## Competitor Comparison

| | Dagster | Airflow | Prefect |
|--|---------|---------|--------|
| Core abstraction | Assets | Tasks/DAGs | Tasks/Flows |
| Testing | `materialize_to_memory` ✅ | Manual/custom | Built-in task tests |
| Local dev | `dagster dev` (single cmd) | docker-compose | `prefect server start` |
| UI | Asset lineage graph (excellent) | DAG/Gantt views | Flow run dashboard |
| Config | Pydantic-style typed config | Airflow Variables + Connections | Pydantic + blocks |
| Learning curve | Moderate (new concepts) | Steep (ops overhead) | Low (Pythonic) |
| Solo dev fit | ✅ Best testing + local dev | ❌ Too heavy | ✅ Easiest start |

## Solo Dev Verdict

**The best-designed orchestration framework today.** If you need to orchestrate data pipelines in a SaaS product, Dagster's asset-centric approach and IO Manager pattern are genuinely innovative. The `materialize_to_memory` testing pattern alone saves hours of debugging. For a solo dev, Dagster hits the sweet spot: powerful enough for production, but `dagster dev` makes local iteration instant. The Resource pattern (dependency injection) is a universal software design lesson worth extracting.

## Extracted for code-base

- ⭐ **IO Manager pattern** → `code-base/data/io-manager/` — Storage abstraction for dev/test/prod
- ⭐ **Resource injection pattern** → `code-base/architecture/dependency-injection/` — Testable external service access
- ⭐ **Software-Defined Assets paradigm** → `best-practices/data-pipeline.md` — Declarative data asset management
