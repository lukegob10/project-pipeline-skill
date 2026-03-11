# Project Dependency Mapping Template

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`

## Canonical Output

- `docs/project-pipeline/02-dependency-map.md`

## Required Sections

Use these exact headings:

```md
# Dependency Map
## System Components
## External Systems and Integrations
## Dependency Graph
## Coupling and Risk Notes
## Operational Dependencies
## Open Questions
## Upstream Changes Required
## Completion Decision
```

Write `None` in `## Upstream Changes Required` when `00` and `01` are sufficient. Otherwise list the earliest upstream artifact that must change before this file can be marked done.

Use `Done: ready for $project-schema-data-model` or `Blocked: <reason>` in `## Completion Decision`.

## Review Rubric

- System components cover the core solution surface implied by the output spec.
- System components include user-facing surfaces and performance-critical delivery pieces when relevant.
- External systems and integrations are explicit.
- The dependency graph shows critical relationships and sequencing.
- Coupling and risk notes surface fragile boundaries and likely bottlenecks.
- Operational dependencies identify deployment, runtime, or support needs at a planning level.
- The artifact stays stack-agnostic.

## Handoff Checklist

- Read `00-project-brief.md` and `01-output-spec.md` before drafting.
- Model only the dependencies needed to satisfy the output spec, including experience-critical delivery dependencies for UI-heavy projects.
- Identify unknown integrations in `## Open Questions`.
- If blocked, point to the earliest upstream artifact that must change.
- If done, ensure no placeholder text remains.
