# Stage 05: Implementation Plan

## Stage Contract

- Required inputs: `docs/project-pipeline/00-project-brief.md`, `docs/project-pipeline/01-output-spec.md`, `docs/project-pipeline/02-dependency-map.md`, `docs/project-pipeline/03-schema-data-model.md`, `docs/project-pipeline/04-pipeline-design.md`
- Canonical output: `docs/project-pipeline/05-implementation-plan.md`
- Objective: turn the approved product, dependency, schema, and runtime design artifacts into a task-ready delivery plan with milestone, risk, and evaluation gates.
- Validation gate: the artifact uses the exact template headings, stays stack-agnostic, makes milestone and validation sequencing concrete enough for detailed coding, and blocks upstream instead of leaving first-order delivery ambiguity unresolved.

## Workflow

1. Confirm the request remains inside the greenfield baseline workflow.
2. Validate that `00` through `04` exist, match the current request, and are usable for this stage. If any required input is missing, stale, or contradictory, stop and return to the pipeline contract's resume algorithm.
3. Read `00` through `04`, this phase reference, `product-quality-gates.md`, `implementation-readiness-quality-bar.md`, and `stage-review-checklists.md` before drafting. If the project includes backend, API, persistence, SQL, workers, integrations, service contracts, or frontend-backend interaction, also read `backend-api-data-quality-gate.md`. If the project includes user-facing surfaces, also read `ui-ux-quality-bar.md`.
4. Create or revise `docs/project-pipeline/05-implementation-plan.md` using the exact headings below.
5. Define milestones, task dependencies, MVP boundaries, decision gates, reliability and operations workstreams, experience quality workstreams, evaluation strategy, and key delivery risks. For backend/API/data projects, plan contract tests, data migrations, authorization validation, load/resilience testing, observability, rollout/rollback, and operational readiness as first-class work. For UI-heavy projects, plan the design system, responsive QA, accessibility, and frontend performance validation as first-class work.
6. Decompose the work enough that an engineer could begin detailed implementation planning without inventing missing contracts, runtime assumptions, rollout steps, or validation criteria.
7. If any upstream artifact is insufficient, contradictory, or too vague to support task-ready planning, populate `## Upstream Changes Required`, mark the artifact blocked, and stop instead of flattening unresolved dependencies into the task plan.
8. Before marking the stage done, validate the artifact against the review rubric, product quality gates, applicable backend/API/data quality gate, stage review checklist, and baseline review. Confirm the baseline workflow is implementation-ready without inventing first-order milestone, backend/API/data contract, UX, security, rollout, operations, migration, or evaluation assumptions.

## Required Sections

Use these exact headings:

```md
# Implementation Plan
## Delivery Strategy
## Architectural Decisions and Decision Gates
## Milestones
## Task Graph
## MVP Cutline
## Reliability, Security, and Operations Plan
## Experience Quality Plan
## Test and Evaluation Strategy
## Risks and Mitigations
## Open Questions
## Upstream Changes Required
## Completion Decision
```

Write `None` in `## Upstream Changes Required` when `00` through `04` are sufficient. Otherwise list the earliest upstream artifact that must change before this file can be marked done.

Use `## Architectural Decisions and Decision Gates` to close or explicitly gate the high-impact decisions that still shape implementation. Record the decision, why it matters, what must be true before coding can proceed, and whether it is already resolved or must be completed by a specific milestone.

Use `## Reliability, Security, and Operations Plan` to define rollout and rollback expectations, migration or reindex strategy, recovery and incident readiness, secret and access-control work, backup or rebuild expectations, and the operational ownership or observability work needed for launch.

Use `## Experience Quality Plan` to show how the implementation will protect UX consistency and performance. Include design system or UI system setup, responsive QA, accessibility checks, user-facing state coverage, and frontend performance guardrails when relevant. If the project has no user-facing surface, focus on client and operator interaction quality instead of writing `Not applicable`.

Use `## Test and Evaluation Strategy` to cover unit, integration, contract, end-to-end, load, resilience, security, and acceptance validation as appropriate. When retrieval, ranking, or ML quality matters, include the evaluation set, representative scenarios, and acceptance thresholds.

Use `Done: baseline workflow complete` or `Blocked: <reason>` in `## Completion Decision`.

## Review Rubric

- Delivery strategy matches the project goal and constraints.
- Architectural decisions and decision gates close or isolate the choices that would otherwise block coding.
- Milestones are sequenced and outcome-based.
- The task graph shows dependency ordering, critical path items, and enough decomposition to assign implementation work.
- The MVP cutline clearly separates must-have from later work.
- Reliability, security, and operations planning is baseline work rather than post-launch cleanup.
- The experience quality plan covers UX consistency, accessibility, responsiveness, and performance guardrails when relevant.
- Test and evaluation strategy covers artifact-level acceptance, implementation validation, and quality evaluation where relevant.
- Backend/API/data work includes contract tests, integration tests, migration tests, authorization tests, load/resilience tests, rollout/rollback readiness, and observability validation when applicable.
- Risks and mitigations are concrete and actionable.

## Handoff Checklist

- Read `00` through `04` before drafting.
- Keep the task graph aligned with the pipeline design and dependency map.
- For UI-heavy projects, schedule design system, UX review, and performance instrumentation work early rather than as cleanup.
- Include tasks for security review, access-control validation, observability, rollout and rollback readiness, data lifecycle checks, edge-case coverage, and acceptance evaluation when relevant.
- For backend/API/data projects, include tasks for API schema/contract definition, database constraints and indexes, migrations/backfills, service integration, async jobs, rate limits, idempotency, performance budgets, SLOs, logs/metrics/traces, backups, and incident readiness where relevant.
- After this stage completes, use `06-enhancement-roadmap.md` for optional polish and roadmap work. If the user wants net-new feature-delta planning, stop and route that request to a separate feature-planning workflow rather than mutating the baseline artifacts.
- Use `## Open Questions` only for non-blocking sequencing or staffing assumptions.
- If unresolved contracts, runtime decisions, rollout steps, or validation criteria still block milestone decomposition, mark the artifact blocked and push the issue upstream.
- Ensure no placeholder text remains.

## Evaluation Gate

This stage is usable only when all of the following are true:

- The exact required headings are present.
- The artifact stays stack-agnostic and has no placeholder text.
- Milestones, task graph, MVP cutline, reliability and operations work, and test and evaluation strategy are concrete enough to begin detailed implementation without inventing first-order delivery assumptions.
- Each core use case, quality priority, UX requirement, security expectation, and operational requirement has a corresponding implementation and validation path.
- Applicable backend/API/data scope has implementation and validation paths for contracts, persistence, auth/object-level access, migrations, performance, resilience, observability, and operations.
- `## Open Questions` contains only non-blocking follow-up rather than baseline blockers.
- `## Completion Decision` uses `Done: baseline workflow complete` or `Blocked: <reason>`.
