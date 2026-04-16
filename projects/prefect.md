# Prefect

> Modern workflow orchestration for Python — "the easiest way to automate your data workflows."

| Metric | Data |
|--------|------|
| GitHub | [PrefectHQ/prefect](https://github.com/PrefectHQ/prefect) |
| Stars | ~17,500+ |
| License | Apache-2.0 ✅ |
| Language | Python |
| Last Update | Active daily |
| Contributors | 300+ |

## TEMC Scoring

| Dimension | Score | Reasoning |
|-----------|-------|-----------|
| T Technology | 76 | Pythonic decorator-based API (`@flow`, `@task`) is the lowest-friction orchestration DX. Prefect 2/3 rewrite with Pydantic, async support, and flexible deployment. Built-in caching, retries, and concurrency limits. |
| E Ecosystem | 75 | Strong community (17K+ stars), 300+ contributors. Prefect Cloud is the primary commercial offering. Integration blocks for major services (AWS, GCP, Snowflake, dbt). Prefect raised $60M+ total. |
| M Market | 82 | Positioned as "the easy Airflow alternative." Lowest barrier to entry in the category. Prefect Cloud free tier is generous. Growing adoption among startups and small teams. Market timing: excellent for cloud-native teams. |
| C Combo | 78 | Pure Python with minimal overhead. Can run flows from any Python environment (Lambda, Cloud Functions, containers). REST API for TypeScript integration. Lightweight enough for SaaS embedding. |
| **Composite** | **78** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 19.0 + 15.0 + 24.6 + 19.5 = **78.1 → 78** |

## Architecture Highlights

```
prefect/
├── src/prefect/
│   ├── flows.py           ← @flow decorator — entry point for orchestrated workflows
│   ├── tasks.py           ← @task decorator — individual units of work with retry/cache
│   ├── states.py          ← State machine (Pending → Running → Completed/Failed/Cancelled)
│   ├── deployments/       ← Deployment specifications (schedule, infra, parameters)
│   ├── server/            ← Self-hosted Prefect server (FastAPI + SQLAlchemy)
│   ├── client/            ← API client for Prefect server/cloud
│   ├── blocks/            ← Configurable integration blocks (S3, GCS, Slack, etc.)
│   ├── concurrency/       ← Task-level and global concurrency limits
│   ├── cache_policies.py  ← Smart caching (by inputs, expiration, custom keys)
│   └── runner/            ← Work pool runners (Process, Docker, K8s)
├── ui/                    ← React dashboard
└── prefect.yaml           ← Deployment configuration
```

**Key patterns worth studying:**
- **Decorator-based orchestration**: `@flow` and `@task` decorators — wrap any Python function to add orchestration features. Zero boilerplate.
- **State machine for tasks**: Every task run goes through a well-defined state machine, making observability and retry logic clean.
- **Blocks system**: Pre-built integrations as typed, configurable objects stored server-side. Reusable across flows.
- **Smart caching**: `cache_key_fn` + `cache_expiration` — avoid recomputation based on input hashes.
- **Result persistence**: Task results optionally persisted to external storage for recovery and debugging.

## Best Practices Extracted

1. **Decorator-based orchestration** — The lowest-friction way to add retry, caching, logging, and observability to any Python function.
2. **State machine for workflow steps** — Explicit states (Pending/Running/Completed/Failed/Cancelled/Cancelling) enable precise control flow.
3. **Smart caching by input hash** — Cache task results based on input fingerprints. Avoid recomputation automatically.
4. **Blocks = typed config objects** — Store connection configs server-side with typed schemas. Better than environment variables.
5. **Progressive complexity** — Start with `@flow` on a script, scale to distributed workers. No architecture change needed.

## Competitor Comparison

| | Prefect | Dagster | Airflow |
|--|---------|---------|--------|
| DX friction | Lowest (decorators) | Medium (asset concepts) | Highest (ops overhead) |
| Testing | Flow/task unit tests | `materialize_to_memory` ✅ | Manual |
| Caching | Built-in input-based | Via IO managers | None built-in |
| Cloud offering | Generous free tier | Dagster+ | Astronomer (paid) |
| Observability | Good (state history) | Excellent (asset lineage) | Good (Gantt/tree views) |
| Best for | Quick automation, small teams | Complex data platforms | Enterprise batch |

## Solo Dev Verdict

**The fastest path from zero to orchestrated workflows.** If you're a solo dev who needs scheduled data pipelines tomorrow, Prefect is the answer. Wrap your existing Python scripts with `@flow` and `@task`, deploy with `prefect deploy`, and you have retries, caching, scheduling, and a dashboard. The decorator pattern is a masterclass in progressive complexity — start simple, scale later without rewrites. For a Micro SaaS data backend, Prefect's lightweight deployment model (runs anywhere Python runs) is ideal.

## Extracted for code-base

- ⭐ **Decorator-based orchestration** → `code-base/patterns/decorator-orchestration/` — Add retry/cache/logging to any function
- ⭐ **Smart caching pattern** → `code-base/caching/input-hash-cache/` — Cache by input fingerprint with expiration
- ⭐ **State machine pattern** → `code-base/patterns/state-machine/` — Explicit task state transitions
