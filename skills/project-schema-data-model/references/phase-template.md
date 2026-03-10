# Project Schema Data Model Template

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- `docs/project-pipeline/02-dependency-map.md`

## Canonical Output

- `docs/project-pipeline/03-schema-data-model.md`

## Required Sections

Use these exact headings:

```md
# Schema and Data Model
## Core Entities
## Data Structures and Fields
## Contracts and Interfaces
## State Transitions
## Validation Rules
## Open Questions
## Upstream Changes Required
## Completion Decision
```

Write `None` in `## Upstream Changes Required` when `00` through `02` are sufficient. Otherwise list the earliest upstream artifact that must change before this file can be marked done.

Use `Done: ready for $project-pipeline-design` or `Blocked: <reason>` in `## Completion Decision`.

## Review Rubric

- Core entities cover the important nouns implied by the output spec and dependency map.
- Data structures and fields are specific enough to guide later design work.
- Contracts and interfaces describe boundaries between components or actors.
- State transitions capture lifecycle changes that matter to the project.
- Validation rules prevent invalid or incomplete data movement.
- The artifact stays stack-agnostic.

## Handoff Checklist

- Read `00`, `01`, and `02` before drafting.
- Keep schemas aligned with the dependency map rather than inventing new subsystems.
- Record unknowns in `## Open Questions`.
- If blocked, point to the earliest upstream artifact that must change.
- If done, ensure no placeholder text remains.
