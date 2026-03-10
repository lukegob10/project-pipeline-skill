# Project Pipeline Design Template

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- `docs/project-pipeline/02-dependency-map.md`
- `docs/project-pipeline/03-schema-data-model.md`

## Canonical Output

- `docs/project-pipeline/04-pipeline-design.md`

## Required Sections

Use these exact headings:

```md
# Pipeline Design
## End-to-End Flow
## Control Flow
## Data Flow
## Failure Handling
## Observability Points
## Operational Assumptions
## Open Questions
## Upstream Changes Required
## Completion Decision
```

Write `None` in `## Upstream Changes Required` when `00` through `03` are sufficient. Otherwise list the earliest upstream artifact that must change before this file can be marked done.

Use `Done: ready for $project-implementation-planning` or `Blocked: <reason>` in `## Completion Decision`.

## Review Rubric

- The end-to-end flow covers the full lifecycle implied by the output spec.
- Control flow identifies orchestration, branching, and decision points.
- Data flow matches the schema and dependency artifacts.
- Failure handling covers expected failure modes and recovery paths.
- Observability points show where monitoring, logging, or audit signals matter.
- Operational assumptions remain implementation-agnostic.

## Handoff Checklist

- Read `00` through `03` before drafting.
- Keep the design consistent with the dependency map and data model.
- Record unresolved design choices in `## Open Questions`.
- If blocked, point to the earliest upstream artifact that must change.
- If done, ensure no placeholder text remains.
