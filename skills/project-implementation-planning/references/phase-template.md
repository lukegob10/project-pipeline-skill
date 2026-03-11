# Project Implementation Planning Template

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- `docs/project-pipeline/02-dependency-map.md`
- `docs/project-pipeline/03-schema-data-model.md`
- `docs/project-pipeline/04-pipeline-design.md`

## Canonical Output

- `docs/project-pipeline/05-implementation-plan.md`

## Required Sections

Use these exact headings:

```md
# Implementation Plan
## Delivery Strategy
## Milestones
## Task Graph
## MVP Cutline
## Experience Quality Plan
## Test Strategy
## Risks and Mitigations
## Open Questions
## Upstream Changes Required
## Completion Decision
```

Write `None` in `## Upstream Changes Required` when `00` through `04` are sufficient. Otherwise list the earliest upstream artifact that must change before this file can be marked done.

Use `## Experience Quality Plan` to show how the implementation will protect UX consistency and performance. Include design system or UI system setup, responsive QA, accessibility checks, user-facing state coverage, and frontend performance guardrails when relevant. If the project has no user-facing surface, write `Not applicable`.

Use `Done: baseline workflow complete` or `Blocked: <reason>` in `## Completion Decision`.

## Review Rubric

- Delivery strategy matches the project goal and constraints.
- Milestones are sequenced and outcome-based.
- The task graph shows dependency ordering and critical path items.
- The MVP cutline clearly separates must-have from later work.
- The experience quality plan covers UX consistency, accessibility, responsiveness, and performance guardrails when relevant.
- Test strategy covers artifact-level acceptance and implementation validation.
- Risks and mitigations are concrete and actionable.

## Handoff Checklist

- Read `00` through `04` before drafting.
- Keep the task graph aligned with the pipeline design and dependency map.
- For UI-heavy projects, schedule design system, UX review, and performance instrumentation work early rather than as cleanup.
- Use `## Open Questions` for unresolved sequencing or staffing assumptions.
- If blocked, point to the earliest upstream artifact that must change.
- If done, ensure no placeholder text remains.
