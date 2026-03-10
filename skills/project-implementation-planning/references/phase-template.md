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
## Test Strategy
## Risks and Mitigations
## Open Questions
## Upstream Changes Required
## Completion Decision
```

Write `None` in `## Upstream Changes Required` when `00` through `04` are sufficient. Otherwise list the earliest upstream artifact that must change before this file can be marked done.

Use `Done: baseline workflow complete` or `Blocked: <reason>` in `## Completion Decision`.

## Review Rubric

- Delivery strategy matches the project goal and constraints.
- Milestones are sequenced and outcome-based.
- The task graph shows dependency ordering and critical path items.
- The MVP cutline clearly separates must-have from later work.
- Test strategy covers artifact-level acceptance and implementation validation.
- Risks and mitigations are concrete and actionable.

## Handoff Checklist

- Read `00` through `04` before drafting.
- Keep the task graph aligned with the pipeline design and dependency map.
- Use `## Open Questions` for unresolved sequencing or staffing assumptions.
- If blocked, point to the earliest upstream artifact that must change.
- If done, ensure no placeholder text remains.
