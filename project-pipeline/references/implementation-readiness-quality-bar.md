# Implementation-Ready Planning Quality Bar

Use this reference for every project-pipeline phase. The goal is not just a coherent architecture note set. The baseline `00` through `05` artifacts must be concrete enough that an engineer can begin detailed coding without reopening first-order questions about scope, contracts, security, deployment, or delivery sequencing.

## Core Principle

Stack-agnostic does not mean vague. Avoid naming frameworks or vendors unless the user already constrained them, but still force concrete behavior, interfaces, budgets, runtime boundaries, and delivery gates.

## External Baselines

This quality bar aligns the planning workflow with high-signal architecture and operations guidance:

- arc42: architecture documentation should cover context, building blocks, runtime behavior, deployment, cross-cutting concerns, quality goals, and architectural decisions.
- MCP specification: protocol-based projects need explicit capability, transport, authorization, lifecycle, request and response, and error semantics.
- Google SRE: service planning should define measurable service expectations, readiness criteria, and observability that maps to those expectations.
- AWS Well-Architected: plans should make security, operational excellence, reliability, and recovery first-class concerns rather than late hardening work.

## What Implementation-Ready Means By Phase 05

By the end of `05-implementation-plan.md`, all of the following should be true unless the user explicitly asked for a looser artifact:

- The functional scope is closed enough to implement an MVP without inventing behavior mid-build.
- The main interaction contracts are explicit enough to derive concrete schemas, handlers, and tests.
- Applicable backend/API/service contracts are explicit enough to derive handlers, schemas, persistence behavior, integration behavior, and contract tests.
- The top nonfunctional requirements are measurable, not qualitative placeholders.
- Security and access expectations are clear enough to shape interfaces and data flow.
- Runtime topology, trust boundaries, and operational dependencies are explicit enough to plan deployment and failure handling.
- Data lifecycle rules cover versioning, retention, deletion, replay or rebuild, and compatibility where relevant.
- Database or persistent storage contracts cover constraints, relationships, indexes, transaction boundaries, migrations, backup/restore, and data integrity where relevant.
- Recovery, rollback, migration, and change-management expectations are planned before implementation starts.
- The implementation plan decomposes work enough to assign tasks and define milestone exit criteria.
- Observability, alerting, audit, and operational ownership are planned where the project needs sustained operation.
- Evaluation criteria exist for qualitative outputs, ranking, retrieval, AI behavior, recommendations, or any workflow where correctness cannot be checked by a single deterministic assertion.
- The MVP cutline is explicit enough that optional polish, advanced features, and platform expansion cannot slip into baseline scope by accident.

## First-Order Questions That Must Not Stay Implicit

- Product or service contract: exact operations, actors, payload shapes, identifiers, filters, pagination or continuation semantics, sync versus async behavior, error categories, and response completeness rules.
- Protocol details for API, MCP, or other integration surfaces: tool versus resource behavior when relevant, transport assumptions, capability boundaries, auth flow, versioning, rate or budget limits, and retry or idempotency expectations.
- Backend/API/data design: API or service contract artifact, frontend-backend interaction semantics, database constraints and indexes, transaction/concurrency assumptions, migrations, cache/freshness behavior, worker/queue behavior, SLOs, and operational ownership.
- Quality targets: latency, freshness, throughput, concurrency, correctness, package size, scale assumptions, availability or recovery expectations, and auditability.
- Security and access: caller identity model, authorization point, trust boundaries, data sensitivity, secret flow, audit requirements, and least-privilege expectations.
- Runtime and deployment: execution units, stateful versus stateless boundaries, background jobs, storage boundaries, network paths, blast radius, backup and restore expectations, and rollout model.
- Delivery readiness: milestone entry and exit criteria, dependencies, evaluation datasets or scenarios when retrieval or ML is involved, rollout and rollback approach, and operational ownership.

## Security, Trust, and Compliance Expectations

Every baseline plan must identify:

- The caller, user, operator, service, or job identity model.
- Authorization boundaries and who can view, create, edit, approve, export, delete, or administer data.
- Data sensitivity, privacy expectations, retention, deletion, auditability, and export behavior.
- Secret handling, credential storage, token flow, and least-privilege expectations.
- Trust boundaries between client, server, background jobs, storage, third-party systems, and operators.
- Abuse, misuse, or accidental data exposure paths that should be prevented or detected.

If these cannot be defined from the prompt, block intake or the earliest affected stage instead of assuming a permissive model.

## Observability and Operations Expectations

Plans for any durable service, automation, integration, or user-facing product should cover:

- Health signals, logs, metrics, traces, audit events, and user-visible status indicators.
- Ownership for operations, support, incident response, and release decisions.
- Backup, restore, rebuild, replay, and rollback expectations.
- Degraded-mode behavior when dependencies fail or data is stale.
- Rate limits, quotas, cost guardrails, and capacity assumptions where relevant.
- Launch readiness checks and post-launch monitoring.

Do not defer basic observability, rollback, or support ownership into optional enhancements.

## Backend / API / Data Expectations

When a project includes backend, API, persistence, SQL, workers, queues, integrations, service contracts, or frontend-backend interaction, the baseline must include:

- Applicability decision: `Applicable` or `Not applicable`, with a short reason.
- API or service contracts: operations, request/response shapes, errors, pagination/filtering/sorting, idempotency, versioning, compatibility, rate limits, and size limits.
- Frontend-backend behavior: validation ownership, loading/error/empty states, optimistic or pessimistic updates, cache freshness, retry behavior, and auth/session behavior.
- Data contracts: entities, keys, relationships, constraints, indexes, retention, deletion, migrations, transaction boundaries, seed/backfill, and backup/restore.
- Security: authentication, authorization, object-level access checks, secrets, audit logs, data sensitivity, rate limits, and abuse prevention.
- Reliability and performance: latency budgets, throughput, concurrency, timeouts, retries, SLOs, degraded modes, connection/cache/queue behavior, and N+1 or fan-out risks.
- Operations and tests: logs, metrics, traces, alerts, runbooks, contract tests, migration tests, authorization tests, load tests, resilience tests, and rollout/rollback checks.

If any of these are applicable but unresolved in a way that changes architecture or implementation sequencing, block the earliest affected stage.

## Evaluation Expectations

When quality depends on judgment, AI output, retrieval, classification, ranking, recommendations, generated content, or business rules, require:

- Representative scenarios or evaluation datasets.
- Acceptance thresholds or review criteria.
- Regression checks for critical workflows.
- Human review points where automation confidence is insufficient.
- Failure examples and escalation behavior.

## Phase-Specific Expectations

- `00-project-brief.md` captures stakeholders or owners and explicit quality attribute priorities, not just the idea and audience.
- `01-output-spec.md` defines interaction contracts, nonfunctional requirements, and security or access expectations in addition to use cases and outputs.
- `02-dependency-map.md` includes deployment and trust boundaries, not just logical components.
- `03-schema-data-model.md` defines interface-relevant schemas, invariants, and data lifecycle or retention rules.
- `04-pipeline-design.md` includes runtime topology, operational flows, recovery paths, and observability points that map to the chosen quality targets.
- `05-implementation-plan.md` closes or explicitly gates major architectural decisions, defines milestone exit criteria, and decomposes work to a task-ready level with validation and rollout plans.
- Backend/API/data scope is carried through `01` to `05` when applicable rather than appearing only as a generic backend task.
- `06-enhancement-roadmap.md` keeps enhancements separate from baseline obligations; do not move required reliability, security, or delivery readiness work out of the baseline.

## Blocking Guidance

- If a missing decision prevents the next phase from being concrete, do not bury it in `## Open Questions`.
- Put the issue in `## Upstream Changes Required`.
- Mark the artifact `Blocked:` and stop forward progress.
- By `05`, `## Open Questions` should contain only non-blocking or follow-on items.
- Treat unresolved product behavior, UX model, data sensitivity, auth, trust boundary, rollout, or MVP cutline choices as blockers when they would materially change downstream implementation.
