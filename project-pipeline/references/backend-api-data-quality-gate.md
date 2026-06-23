# Backend / API / Data Quality Gate

Use this reference when a project includes a backend, API, persistence layer, SQL database, worker, queue, integration service, service-to-service contract, or frontend-backend interaction. Do not force API or database assumptions onto static sites, local-only tools, or projects that explicitly have no backend or persistence; mark the gate `Not applicable` and explain why.

## Research Baselines

Use these standards as planning anchors:

- OpenAPI Specification: API contracts should be explicit enough for humans and machines to understand operations, schemas, responses, and errors.
- RFC 9110 HTTP Semantics: HTTP designs should respect safe and idempotent method behavior.
- Google API Improvement Proposals and Microsoft REST API guidelines: resource-oriented APIs need stable resource models, pagination, filtering, errors, versioning, and compatibility rules.
- OWASP API Security and REST Security Cheat Sheet: APIs must account for object-level authorization, authentication, resource limits, sensitive data exposure, and abuse prevention.
- Google SRE and AWS Well-Architected: backend services need measurable reliability, observability, rollback, operations, and performance expectations.
- PostgreSQL documentation: durable data contracts should use constraints, keys, indexes, transaction boundaries, isolation expectations, and migration planning.

## Applicability Gate

For every project, decide and record one of:

- `Applicable`: The project has backend, API, persistence, SQL, async worker, queue, integration, service contract, or frontend-backend interaction scope.
- `Not applicable`: The project is static, local-only, prototype-only, or otherwise has no backend/data/service contract scope. State why.

If applicability is unclear and the answer changes architecture, ask before drafting downstream artifacts.

## API and Service Contract Gate

When applicable, require planning coverage for:

- Public, internal, or service-to-service operations.
- Resource model or command model, including resource identifiers and ownership.
- Request and response shapes, required and optional fields, validation behavior, and error classes.
- Status or result model, including partial success, async job status, retries, and cancellation where relevant.
- Pagination, filtering, sorting, search, continuation tokens, and response size limits.
- Safe and idempotent behavior for reads, creates, updates, deletes, retries, and duplicate requests.
- Versioning, backward compatibility, deprecation, and contract evolution.
- OpenAPI or equivalent schema/contract artifact when the project exposes HTTP APIs.

Do not mark the output spec complete when API/service behavior is implied but not contractually described.

## Frontend-Backend Interaction Gate

For projects with any user-facing client backed by a service, define:

- Which layer owns validation, normalization, authorization checks, and business rules.
- Loading, empty, optimistic update, pessimistic update, partial success, error, retry, stale data, and offline or degraded states.
- Client cache, server cache, invalidation, freshness, polling, subscription, or revalidation behavior.
- Auth/session flow, token refresh, logout, permission changes, and forbidden states.
- Form submission semantics, duplicate submit protection, idempotency keys, and conflict resolution.
- Latency budgets for user-visible interactions and fallback behavior when the backend is slow.

Carry these expectations into output spec, pipeline design, and implementation planning.

## Database and SQL Contract Gate

When persistence or SQL is in scope, define:

- Core entities, primary keys, foreign keys, ownership, uniqueness, nullable fields, and required constraints.
- Relationship cardinality, referential integrity, cascade or restrict behavior, and deletion semantics.
- Indexing strategy for expected lookup, filtering, sorting, join, uniqueness, and pagination paths.
- Transaction boundaries, isolation expectations, concurrency conflicts, locking risks, and idempotent writes.
- Retention, deletion, archive, export, backup, restore, replay, rebuild, and audit expectations.
- Migration strategy, rollback strategy, seed/backfill plan, compatibility windows, and data validation.
- Data volume, growth, hot paths, query performance risks, and N+1 or fan-out risks.

If the project uses non-SQL storage, apply the same contract intent to keys, indexes, consistency, lifecycle, migrations, and query/access patterns.

## Security Gate

Backend/API/data plans must define:

- Authentication model for users, services, jobs, and operators.
- Authorization model, including object-level access checks and admin/operator privileges.
- Data sensitivity, privacy, encryption expectations, secret handling, and credential storage.
- Audit events, security logs, export controls, and privileged action tracking.
- Rate limits, quotas, payload limits, abuse prevention, and denial-of-service controls.
- Cross-origin, webhook, callback, file upload, and third-party integration trust boundaries when relevant.

Do not assume "authenticated means authorized"; object-level authorization must be explicit when users can access scoped resources.

## Performance and Reliability Gate

Backend plans must define:

- Latency budgets for critical API calls, background jobs, imports, exports, and user-visible workflows.
- Throughput, concurrency, data volume, request size, response size, and freshness targets.
- Timeouts, retries, backoff, circuit breaking, idempotency, and duplicate-event handling.
- Connection pooling, cache strategy, queue behavior, worker concurrency, and backpressure where relevant.
- SLOs or service expectations for availability, correctness, durability, and recovery.
- Degraded-mode behavior and dependency failure behavior.

When targets are unknown but material, ask or record explicit assumptions before implementation planning.

## Operations and Observability Gate

Backend/API/data plans must include:

- Structured logs, metrics, traces, audit events, health checks, and service-level indicators.
- Alerting thresholds, dashboards, incident ownership, support flow, and runbook expectations.
- Deployment, migration, rollback, backup/restore, replay/rebuild, and disaster recovery expectations.
- Environment boundaries, configuration, secrets, feature flags, and release gates.
- Cost, quota, capacity, rate-limit, and dependency monitoring where relevant.

Operations readiness is baseline work, not an enhancement, for durable backends and integrations.

## Testing Gate

Require planned validation for:

- API or service contract tests.
- Schema, migration, seed, backfill, rollback, and data integrity tests.
- Authorization and object-level access-control tests.
- Integration tests across external systems, workers, queues, and persistence.
- Load, concurrency, timeout, retry, and resilience tests for critical paths.
- Observability and audit checks for security-sensitive or operationally important flows.
- Acceptance scenarios that prove frontend-backend behavior, error states, and recovery paths.

## Baseline Completion Gate

Before marking `05-implementation-plan.md` done for applicable projects, confirm:

- Backend/API/data applicability is explicit.
- Service contracts and data contracts are concrete enough to implement and test.
- Security, performance, reliability, operations, and migration expectations have implementation tasks and validation paths.
- Frontend-backend behavior is specified when a client talks to a backend.
- Open questions are non-blocking; unresolved first-order backend/API/data decisions are blockers.
