# Project Implementation Planning Template

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- `docs/project-pipeline/02-dependency-map.md`
- `docs/project-pipeline/03-schema-data-model.md`
- `docs/project-pipeline/04-pipeline-design.md`

## Canonical Output

- `docs/project-pipeline/05-implementation-plan.md`

## Stage Objective

Translate `00-project-brief.md` through `04-pipeline-design.md` into a stack-agnostic, task-ready delivery plan with milestone, rollout, and evaluation gates that is concrete enough for detailed implementation work.

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
- Risks and mitigations are concrete and actionable.

## Handoff Checklist

- Read `00` through `04` before drafting.
- Keep the task graph aligned with the pipeline design and dependency map.
- For UI-heavy projects, schedule design system, UX review, and performance instrumentation work early rather than as cleanup.
- After this stage completes, use `$project-enhancement-iteration` for optional polish and roadmap work. If the user wants net-new feature-delta planning, stop and route that request to a separate feature-planning workflow rather than mutating the baseline artifacts.
- Use `## Open Questions` only for non-blocking sequencing or staffing assumptions.
- If unresolved contracts, runtime decisions, rollout steps, or validation criteria still block milestone decomposition, mark the artifact blocked and push the issue upstream.
- If blocked, point to the earliest upstream artifact that must change.
- If done, ensure no placeholder text remains.

## Evaluation Gate

This stage is usable only when all of the following are true:

- The exact required headings are present.
- The artifact stays stack-agnostic and has no placeholder text.
- Milestones, task graph, MVP cutline, reliability and operations work, and test and evaluation strategy are concrete enough to begin detailed implementation without inventing first-order delivery assumptions.
- `## Open Questions` contains only non-blocking follow-up rather than baseline blockers.
- `## Completion Decision` uses `Done: baseline workflow complete` or `Blocked: <reason>`.
