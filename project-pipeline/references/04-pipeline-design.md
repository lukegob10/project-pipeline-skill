# Stage 04: Pipeline Design

## Stage Contract

- Required inputs: `docs/project-pipeline/00-project-brief.md`, `docs/project-pipeline/01-output-spec.md`, `docs/project-pipeline/02-dependency-map.md`, `docs/project-pipeline/03-schema-data-model.md`
- Canonical output: `docs/project-pipeline/04-pipeline-design.md`
- Objective: define how the planned system operates end to end, including control flow, data flow, failures, observability, and runtime topology.
- Validation gate: the artifact uses the exact template headings, stays stack-agnostic, makes runtime and recovery behavior concrete enough for implementation planning, and blocks upstream instead of leaving first-order flow or topology ambiguity unresolved.

## Workflow

1. Confirm the request remains inside the greenfield baseline workflow.
2. Validate that `00` through `03` exist, match the current request, and are usable for this stage. If any required input is missing, stale, or contradictory, stop and return to the pipeline contract's resume algorithm.
3. Read `00` through `03`, this phase reference, `product-quality-gates.md`, `implementation-readiness-quality-bar.md`, and `stage-review-checklists.md` before drafting. If the project includes backend, API, persistence, SQL, workers, integrations, service contracts, or frontend-backend interaction, also read `backend-api-data-quality-gate.md`. If the project includes user-facing surfaces, also read `ui-ux-quality-bar.md`.
4. Create or revise `docs/project-pipeline/04-pipeline-design.md` using the exact headings below.
5. Describe how work moves through the system, where control decisions happen, how data flows, how failures are handled and observed, and how user-facing responsiveness is protected when the project includes UI.
6. For backend systems, cover request flow, async or worker flow, persistence flow, cache or freshness behavior, timeouts, retries, idempotency, consistency, degradation, and dependency failure handling.
7. Include runtime topology, deployment flow, trust boundaries, recovery paths, rollout or rollback expectations, and observability points that map back to the quality targets defined upstream.
8. If any upstream artifact is insufficient, contradictory, or too vague to support an implementation-ready runtime design, populate `## Upstream Changes Required`, mark the artifact blocked, and stop instead of compensating for missing stage inputs.
9. Before marking the stage done, validate the artifact against the review rubric, product quality gates, applicable backend/API/data quality gate, and stage review checklist. Confirm `05-implementation-plan.md` can be produced without inventing first-order orchestration, topology, backend flow, failure, UX feedback, security, recovery, consistency, or observability assumptions.

## Required Sections

Use these exact headings:

```md
# Pipeline Design
## End-to-End Flow
## Control Flow
## Data Flow
## Failure Handling
## Observability Points
## Runtime Topology and Deployment View
## User Experience and Responsiveness
## Open Questions
## Upstream Changes Required
## Completion Decision
```

Write `None` in `## Upstream Changes Required` when `00` through `03` are sufficient. Otherwise list the earliest upstream artifact that must change before this file can be marked done.

Use `## Runtime Topology and Deployment View` to describe execution units, synchronous and background paths, storage boundaries, transport paths, stateful and stateless separation, rollout topology, recovery paths, backup or rebuild expectations, and major trust boundaries without locking into a vendor or framework.

Use `## User Experience and Responsiveness` to describe the user-facing or client-facing feedback loops that matter to the plan: loading, empty, error, and success states; perceived latency; progressive disclosure; and performance-sensitive paths. If the project has no user-facing surface, focus this section on client and operator interaction semantics rather than writing `Not applicable`.

Use `Done: ready for $project-implementation-planning` or `Blocked: <reason>` in `## Completion Decision`.

## Review Rubric

- The end-to-end flow covers the full lifecycle implied by the output spec.
- Control flow identifies orchestration, branching, and decision points.
- Data flow matches the schema and dependency artifacts.
- Failure handling covers expected failure modes and recovery paths.
- Backend/API/data flows cover sync request paths, async jobs, retries/timeouts, idempotency, consistency, persistence, cache freshness, dependency failures, and degraded behavior when relevant.
- Observability points show where monitoring, logging, audit signals, and service-level indicators matter.
- Runtime topology and deployment view make runtime boundaries and operational pathways concrete enough to plan rollout and recovery.
- User experience and responsiveness covers the main experience-critical feedback and performance paths when relevant.

## Handoff Checklist

- Read `00` through `03` before drafting.
- Keep the design consistent with the dependency map and data model.
- For UI-heavy projects, describe how the system preserves fast-feeling interactions rather than leaving responsiveness implicit.
- Cover loading, empty, partial success, validation error, permission denied, upstream failure, retry, stale data, and completion feedback when user or operator workflows depend on them.
- For backend systems, describe where auth checks, object-level access checks, validation, transactions, writes, events, retries, and audit logs occur.
- Make rollout, rebuild, migration, and degraded-mode behavior explicit when they affect delivery or recovery planning.
- Record unresolved design choices in `## Open Questions`.
- If runtime topology or recovery behavior remains too vague to drive implementation planning, block and point to the earliest upstream artifact that must change.
- Ensure no placeholder text remains.

## Evaluation Gate

This stage is usable only when all of the following are true:

- The exact required headings are present.
- The artifact stays stack-agnostic and has no placeholder text.
- End-to-end flow, control flow, data flow, failure handling, observability, and runtime topology are concrete enough to drive `05-implementation-plan.md` without inventing first-order orchestration or recovery assumptions.
- User or operator feedback loops, security-relevant control points, recovery paths, and observability points map back to upstream quality targets.
- Applicable backend/API/data runtime behavior covers request/worker flows, persistence, cache/freshness, timeout/retry/idempotency behavior, consistency model, and observability.
- First-order blockers are escalated through `## Upstream Changes Required` instead of being left implicit.
- `## Completion Decision` uses `Done: ready for $project-implementation-planning` or `Blocked: <reason>`.
