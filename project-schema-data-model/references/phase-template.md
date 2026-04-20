# Project Schema Data Model Template

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- `docs/project-pipeline/02-dependency-map.md`

## Canonical Output

- `docs/project-pipeline/03-schema-data-model.md`

## Stage Objective

Translate `00-project-brief.md`, `01-output-spec.md`, and `02-dependency-map.md` into stack-agnostic entities, contracts, validation rules, and lifecycle behavior that are concrete enough for pipeline design.

## Required Sections

Use these exact headings:

```md
# Schema and Data Model
## Core Entities
## Data Structures and Fields
## Contracts and Interfaces
## State Transitions
## Validation Rules
## Data Lifecycle and Retention
## Open Questions
## Upstream Changes Required
## Completion Decision
```

Write `None` in `## Upstream Changes Required` when `00` through `02` are sufficient. Otherwise list the earliest upstream artifact that must change before this file can be marked done.

Use `Done: ready for $project-pipeline-design` or `Blocked: <reason>` in `## Completion Decision`.

## Review Rubric

- Core entities cover the important nouns implied by the output spec and dependency map.
- Data structures and fields are specific enough to guide later design work.
- Contracts and interfaces describe boundaries between components or actors and are concrete enough to derive request, response, event, or resource schemas where relevant.
- State transitions capture lifecycle changes that matter to the project.
- Validation rules prevent invalid or incomplete data movement.
- Data lifecycle and retention covers versioning, provenance, retention, deletion, rebuild or replay, and compatibility concerns that matter to the project.
- The artifact stays stack-agnostic.

## Handoff Checklist

- Read `00`, `01`, and `02` before drafting.
- Keep schemas aligned with the dependency map rather than inventing new subsystems.
- Make identifier, provenance, authorization, and compatibility fields explicit when they shape interfaces or operational behavior.
- Record unknowns in `## Open Questions`.
- If contracts or lifecycle rules remain too vague to drive pipeline and implementation planning, block and point to the earliest upstream artifact that must change.
- If blocked, point to the earliest upstream artifact that must change.
- If done, ensure no placeholder text remains.

## Evaluation Gate

This stage is usable only when all of the following are true:

- The exact required headings are present.
- The artifact stays stack-agnostic and has no placeholder text.
- Entities, data structures, contracts, validation rules, and lifecycle behavior are concrete enough to drive `04-pipeline-design.md` without inventing first-order interface or identifier assumptions.
- First-order blockers are escalated through `## Upstream Changes Required` instead of being left implicit.
- `## Completion Decision` uses `Done: ready for $project-pipeline-design` or `Blocked: <reason>`.
