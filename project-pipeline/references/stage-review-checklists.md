# Stage Review Checklists

Use these checklists before marking any stage `Done:` and again after `05-implementation-plan.md`.

## Universal Stage Review

Before advancing from any stage, confirm:

- The canonical file exists in `docs/project-pipeline/`.
- All required headings are present exactly as specified.
- No placeholder text such as `[TODO]`, `TBD`, "nice to have later" for baseline work, or unresolved author notes remains.
- `## Completion Decision` uses the exact allowed `Done:` phrase or `Blocked: <reason>`.
- The artifact aligns with the latest user request and all earlier artifacts.
- The artifact stays stack-agnostic unless the user explicitly constrained the stack.
- `## Open Questions` contains only non-blocking questions.
- First-order blockers are in `## Upstream Changes Required`, with the earliest upstream artifact named.
- Product, UX, security, runtime, and delivery claims are concrete enough for the next stage.
- Backend/API/data applicability is marked `Applicable` or `Not applicable` when the project could plausibly include backend, API, persistence, workers, integrations, service contracts, or frontend-backend interaction.

## Stage-Specific Review

- `00-project-brief.md`: Confirms the real goal, users, stakeholders, constraints, quality priorities, UX direction, success criteria, non-goals, and explicit assumptions. Blocks if product behavior, UI model, security posture, data sensitivity, or MVP scope is too ambiguous.
- `01-output-spec.md`: Converts the brief into concrete actors, workflows, outputs, interaction contracts, experience requirements, nonfunctional requirements, security expectations, and acceptance criteria.
- `02-dependency-map.md`: Identifies internal components, external systems, runtime boundaries, trust boundaries, operational dependencies, and coupling risks needed to satisfy the output spec.
- `03-schema-data-model.md`: Defines entities, fields, contracts, lifecycle rules, validation, identifiers, provenance, authorization-relevant fields, and retention behavior.
- `04-pipeline-design.md`: Explains end-to-end behavior, control flow, data flow, failure handling, observability, runtime topology, recovery paths, and user or operator responsiveness.
- `05-implementation-plan.md`: Produces a task-ready delivery strategy with milestone exits, MVP cutline, decision gates, reliability/security/operations work, experience quality work, tests, evaluation, and concrete risk mitigations.
- `06-enhancement-roadmap.md`: Keeps enhancements optional and post-baseline; does not hide required reliability, security, UX, or delivery-readiness work.

## Backend / API / Data Review

Use this review when backend/API/data quality is `Applicable`:

- `01-output-spec.md`: Defines API or service operations, request/response behavior, error classes, auth expectations, pagination/filtering/sorting, idempotency, rate or size limits, versioning, compatibility, and frontend-backend interaction semantics when relevant.
- `02-dependency-map.md`: Includes API/service layer, persistence, queues or workers, caches, auth, secrets, third-party services, observability, migrations, runtime ownership, and trust boundaries.
- `03-schema-data-model.md`: Defines keys, relationships, constraints, indexes, uniqueness, nullable fields, transaction/concurrency expectations, retention/deletion, migrations, seed/backfill, and data integrity behavior when relevant.
- `04-pipeline-design.md`: Covers request flow, async flow, persistence flow, cache or freshness behavior, timeouts, retries, idempotency, consistency, degraded behavior, failure handling, and observability.
- `05-implementation-plan.md`: Includes contract tests, integration tests, migration tests, authorization and object-level access tests, load/resilience tests, rollout/rollback, observability validation, backup/restore, and operational readiness.

If backend/API/data quality is `Not applicable`, confirm the project is genuinely static, local-only, prototype-only, or otherwise has no backend, persistence, service, worker, integration, or frontend-backend contract scope.

## Baseline Review After Stage 05

Before final delivery after `05`, confirm the full baseline is implementation-ready:

- The MVP can be implemented without reopening first-order scope, contract, security, runtime, or delivery questions.
- Interaction contracts, data contracts, failure behavior, and acceptance criteria trace across artifacts.
- UX requirements are carried through output specification, dependency choices, pipeline design, and implementation planning for user-facing projects.
- Security, access, audit, and trust boundaries are reflected in dependencies, schemas, runtime flow, operations, and tests.
- For applicable backend/API/data projects, service contracts, data contracts, migrations, auth/object-level authorization, performance budgets, reliability targets, observability, and operations trace across artifacts.
- Nonfunctional targets are measurable and have validation paths.
- Rollout, rollback, observability, ownership, and recovery are planned before implementation starts.
- Remaining open questions are genuinely non-blocking.

## Dry Forward-Test Scenarios

Use these scenarios to reason about whether the skill will behave correctly:

- A long messy spoken prompt with missing UX and security details should trigger focused clarification before spec generation.
- A long prompt with enough detail should create `00` through `05` with explicit assumptions and no hidden blockers.
- A UI-heavy app should carry UX quality through all relevant stages.
- A non-UI service should avoid irrelevant visual guidance but still define client and operator experience quality.
- Contradictions in the prompt should block intake rather than producing a confused spec.
- A post-`05` enhancement request should use `06`; net-new feature planning after `05` should remain out of scope.
- A web app with API and SQL backend should require backend, API, SQL, auth, and frontend-backend contract planning.
- A CLI-only local tool with no backend should mark backend/API/data quality not applicable.
- An API-only service should apply backend/API guidance without UI assumptions.
- A data pipeline with SQL but no HTTP API should apply database, worker, observability, and operations guidance.
- A prompt with vague "secure and fast backend" should force measurable security and performance expectations or clarification.
