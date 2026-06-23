# Product Quality Gates

Use this reference when drafting or validating any project-pipeline artifact that defines product behavior, workflows, user experience, acceptance criteria, or quality targets.

## No Vague Spec Rule

Translate vague words into observable standards before downstream stages rely on them:

- "Good UX" -> concrete layout, navigation, hierarchy, feedback, accessibility, and responsiveness expectations.
- "Fast" -> latency, first paint, response time, throughput, freshness, or batch duration targets.
- "Secure" -> identity model, authorization boundary, data sensitivity, secret handling, audit, and least-privilege requirements.
- "Robust" -> expected failure modes, retries, recovery, rollback, degraded behavior, monitoring, and data integrity checks.
- "Simple" -> MVP cutline, reduced workflows, explicit non-goals, and minimized configuration surface.
- "High quality" -> measurable acceptance criteria, review gates, and test or evaluation coverage.

If a vague requirement materially changes product, UX, security, or delivery scope and cannot be safely converted into an assumption, ask before drafting.

## Product Completeness Gate

Every baseline plan must make these concrete by the end of the relevant stages:

- Actors: primary users, operators, admins, approvers, external systems, and automated jobs.
- Workflows: the happy path, common alternate paths, and key edge cases.
- Outputs: screens, records, reports, files, notifications, API responses, decisions, or automations.
- Inputs: source data, user-entered fields, imported files, events, credentials, and configuration.
- States: loading, empty, success, partial success, validation error, permission denied, upstream failure, and recovery.
- Service and data contracts: API operations, backend actions, persisted entities, integration events, worker jobs, database records, and ownership boundaries when applicable.
- Acceptance criteria: observable checks that prove the workflow works.
- Non-goals: explicit boundaries that protect the MVP and prevent accidental platform expansion.

## Edge Case and Error Gate

Require planning coverage for:

- Empty or missing input
- Invalid or conflicting input
- Duplicate records or repeated requests
- Partial failures across external systems
- Permission changes while work is in progress
- Slow, unavailable, or rate-limited dependencies
- Data drift, stale data, replay, rebuild, or import errors
- Duplicate API calls, retried jobs, idempotent writes, transaction conflicts, cache staleness, and migration failures
- User cancellation, rollback, and retry behavior where relevant

Do not push baseline failure behavior into post-baseline enhancement planning.

## Acceptance Criteria Gate

Acceptance criteria should be testable without reading the author's mind. Good criteria include:

- A specific actor or system condition
- The action or event
- The expected output or state change
- Any timing, accuracy, security, accessibility, or observability expectation that matters

Avoid acceptance criteria that only say the system is "easy", "clean", "works well", or "handles errors" without concrete evidence.

## Product-to-Implementation Trace

Before marking `05-implementation-plan.md` done, confirm:

- Every core use case has implementation tasks and tests.
- Every stated quality priority has a design response and validation path.
- Every security or access expectation appears in dependency, schema, pipeline, and implementation planning where relevant.
- Every applicable backend/API/data expectation appears in output spec, dependency map, schema/data model, pipeline design, and implementation planning.
- Every user-facing experience requirement appears in output spec, pipeline design, and experience quality planning.
- No major product promise exists only in the brief.
