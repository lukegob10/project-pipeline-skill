# Project Pipeline Design Template

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- `docs/project-pipeline/02-dependency-map.md`
- `docs/project-pipeline/03-schema-data-model.md`

## Canonical Output

- `docs/project-pipeline/04-pipeline-design.md`

## Stage Objective

Translate `00-project-brief.md` through `03-schema-data-model.md` into a stack-agnostic end-to-end operating flow, failure model, observability plan, and runtime topology that are concrete enough for implementation planning.

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

Use `## User Experience and Responsiveness` to describe the user-facing or client-facing feedback loops that matter to the plan: loading, empty, error, and success states; perceived latency; progressive disclosure; and any performance-sensitive paths. If the project has no user-facing surface, focus this section on client and operator interaction semantics rather than writing `Not applicable`.

Use `Done: ready for $project-implementation-planning` or `Blocked: <reason>` in `## Completion Decision`.

## Review Rubric

- The end-to-end flow covers the full lifecycle implied by the output spec.
- Control flow identifies orchestration, branching, and decision points.
- Data flow matches the schema and dependency artifacts.
- Failure handling covers expected failure modes and recovery paths.
- Observability points show where monitoring, logging, audit signals, and service-level indicators matter.
- Runtime topology and deployment view make runtime boundaries and operational pathways concrete enough to plan rollout and recovery.
- User experience and responsiveness covers the main experience-critical feedback and performance paths when relevant.

## Handoff Checklist

- Read `00` through `03` before drafting.
- Keep the design consistent with the dependency map and data model.
- For UI-heavy projects, describe how the system preserves fast-feeling interactions rather than leaving responsiveness implicit.
- Make rollout, rebuild, migration, and degraded-mode behavior explicit when they affect delivery or recovery planning.
- Record unresolved design choices in `## Open Questions`.
- If runtime topology or recovery behavior remains too vague to drive implementation planning, block and point to the earliest upstream artifact that must change.
- If blocked, point to the earliest upstream artifact that must change.
- If done, ensure no placeholder text remains.

## Evaluation Gate

This stage is usable only when all of the following are true:

- The exact required headings are present.
- The artifact stays stack-agnostic and has no placeholder text.
- End-to-end flow, control flow, data flow, failure handling, observability, and runtime topology are concrete enough to drive `05-implementation-plan.md` without inventing first-order orchestration or recovery assumptions.
- First-order blockers are escalated through `## Upstream Changes Required` instead of being left implicit.
- `## Completion Decision` uses `Done: ready for $project-implementation-planning` or `Blocked: <reason>`.
