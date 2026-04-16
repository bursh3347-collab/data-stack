# Apache Airflow

> The industry-standard platform for programmatic workflow orchestration — "author, schedule, and monitor workflows."

| Metric | Data |
|--------|------|
| GitHub | [apache/airflow](https://github.com/apache/airflow) |
| Stars | ~38,000+ |
| License | Apache-2.0 ✅ |
| Language | Python |
| Last Update | Active daily |
| Contributors | 3,000+ |

## TEMC Scoring

| Dimension | Score | Reasoning |
|-----------|-------|-----------|
| T Technology | 78 | Mature DAG-based scheduler, extensible operator/hook system, but monolithic core showing age vs newer competitors. TaskFlow API (2.0+) modernizes Python-native authoring. Celery/Kubernetes executors for scale. |
| E Ecosystem | 92 | Apache top-level project, 3000+ contributors, 1000+ community-maintained providers (AWS, GCP, Azure, Snowflake, dbt). Massive job market demand. Astronomer (commercial) drives enterprise adoption. |
| M Market | 82 | De facto standard for batch orchestration. 80%+ of data teams use or have used Airflow. Facing pressure from Dagster/Prefect for modern use cases, but installed base is enormous. |
| C Combo | 70 | Python-only limits TypeScript-native SaaS integration. However, Airflow REST API enables triggering from any stack. Heavy operational overhead for solo dev (needs scheduler + webserver + DB + worker). |
| **Composite** | **81** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 19.5 + 18.4 + 24.6 + 17.5 = **80.0 → 81** |

## Architecture Highlights

```
airflow/
├── dags/                  ← User DAG definitions (Python files)
├── airflow/
│   ├── models/            ← Core DAG, Task, DagRun, TaskInstance ORM models
│   ├── executors/         ← LocalExecutor, CeleryExecutor, KubernetesExecutor
│   ├── operators/         ← BashOperator, PythonOperator, etc.
│   ├── hooks/             ← Connection abstractions (S3Hook, PostgresHook)
│   ├── providers/         ← 1000+ integrations as installable packages
│   ├── api/               ← REST API for external triggering
│   └── www/               ← Flask-based web UI (React rewrite underway)
├── scheduler/             ← DAG parsing + task scheduling engine
└── triggerer/             ← Async deferrable operator support (2.4+)
```

**Key patterns worth studying:**
- **Provider architecture**: Each external integration is a separate pip-installable package with standardized hook/operator/sensor pattern
- **Executor abstraction**: Same DAGs run on local, Celery, or Kubernetes with zero code changes
- **XCom for inter-task communication**: Small data passing between tasks via metadata DB
- **Deferrable operators (2.4+)**: Async waiting that frees worker slots — critical for cost efficiency

## Best Practices Extracted

1. **DAG-as-Code > GUI-based workflows** — Version control, code review, testing all work naturally
2. **Provider isolation pattern** — 1000+ integrations without bloating core. Each provider independently versioned.
3. **Idempotent task design** — Tasks should be safely re-runnable. Airflow's retry/backfill assumes idempotency.
4. **Scheduler heartbeat architecture** — Periodic scanning for new DAG runs + task state transitions

## Competitor Comparison

| | Airflow | Dagster | Prefect |
|--|---------|---------|--------|
| Paradigm | DAG-first (imperative) | Asset-first (declarative) | Flow-first (Pythonic) |
| Learning curve | Steep | Moderate | Low |
| UI/UX | Functional but dated | Modern, asset-centric | Modern, cloud-native |
| Testing | Manual/custom | Built-in `materialize_to_memory` | Built-in task unit tests |
| Scale | Battle-tested at PB scale | Growing enterprise adoption | Cloud-managed scaling |
| Solo dev fit | ❌ Heavy ops overhead | ✅ Local dev friendly | ✅ Easiest to start |

## Solo Dev Verdict

**Study, don't deploy.** Airflow's provider pattern and DAG-as-code philosophy are brilliant design lessons, but the operational overhead (scheduler + webserver + metadata DB + workers) makes it impractical for solo devs. Use Dagster or Prefect instead for actual work, but study Airflow's provider architecture for building extensible systems.

## Extracted for code-base

- ⭐ **Provider pattern** → `code-base/integrations/provider-pattern/` — Standardized hook/operator/sensor abstraction for external services
- ⭐ **Idempotent task design** → `best-practices/data-pipeline.md` — Retry-safe task patterns
