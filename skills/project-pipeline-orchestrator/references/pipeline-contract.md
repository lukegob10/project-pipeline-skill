# Project Pipeline Contract

## Artifact Root

Store every planning artifact in `docs/project-pipeline/`. Create the directory before writing the first file.

## Canonical Files

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- `docs/project-pipeline/02-dependency-map.md`
- `docs/project-pipeline/03-schema-data-model.md`
- `docs/project-pipeline/04-pipeline-design.md`
- `docs/project-pipeline/05-implementation-plan.md`
- `docs/project-pipeline/06-enhancement-roadmap.md` (optional, post-baseline only)

## Stage Order

1. `00-project-brief.md`
2. `01-output-spec.md`
3. `02-dependency-map.md`
4. `03-schema-data-model.md`
5. `04-pipeline-design.md`
6. `05-implementation-plan.md`
7. `06-enhancement-roadmap.md` only after `05` is complete and the user asks for enhancements

## 00 Project Brief Template

Use these exact headings:

```md
# Project Brief
## Project Idea
## Desired Outcome
## Target Users
## Constraints
## Success Criteria
## Non-Goals
## Explicit Assumptions
```

Refresh `00-project-brief.md` whenever the user changes the core goal, target users, constraints, or success criteria.

## Worker Map

- `01-output-spec.md` -> `$project-output-spec`
- `02-dependency-map.md` -> `$project-dependency-mapping`
- `03-schema-data-model.md` -> `$project-schema-data-model`
- `04-pipeline-design.md` -> `$project-pipeline-design`
- `05-implementation-plan.md` -> `$project-implementation-planning`
- `06-enhancement-roadmap.md` -> `$project-enhancement-iteration`

## Required Heading Checks

Use these minimum heading checks when resuming:

- `01-output-spec.md`: `Problem Statement`, `Target Users and Operators`, `Core Use Cases`, `Primary Outputs`, `Acceptance Criteria`, `Non-Goals`, `Open Questions`, `Upstream Changes Required`, `Completion Decision`
- `02-dependency-map.md`: `System Components`, `External Systems and Integrations`, `Dependency Graph`, `Coupling and Risk Notes`, `Operational Dependencies`, `Open Questions`, `Upstream Changes Required`, `Completion Decision`
- `03-schema-data-model.md`: `Core Entities`, `Data Structures and Fields`, `Contracts and Interfaces`, `State Transitions`, `Validation Rules`, `Open Questions`, `Upstream Changes Required`, `Completion Decision`
- `04-pipeline-design.md`: `End-to-End Flow`, `Control Flow`, `Data Flow`, `Failure Handling`, `Observability Points`, `Operational Assumptions`, `Open Questions`, `Upstream Changes Required`, `Completion Decision`
- `05-implementation-plan.md`: `Delivery Strategy`, `Milestones`, `Task Graph`, `MVP Cutline`, `Test Strategy`, `Risks and Mitigations`, `Open Questions`, `Upstream Changes Required`, `Completion Decision`
- `06-enhancement-roadmap.md`: `Baseline Preconditions`, `Enhancement Themes`, `Prioritized Roadmap`, `Complexity Increments`, `Dependencies and Preconditions`, `Risk and Impact`, `Open Questions`, `Upstream Changes Required`, `Completion Decision`

## Completion Rules

A stage counts as complete only when all of the following are true:

- The file exists at the canonical path.
- The required headings are present.
- The artifact has no placeholder text such as `[TODO]` or `TBD`.
- `## Completion Decision` starts with `Done:`.

Treat `00-project-brief.md` as complete when all required headings are present and the contents match the latest user request.

## Stale Rules

Treat an artifact as stale when any of the following is true:

- The current request changes project goal, users, constraints, success criteria, or scope.
- The artifact conflicts with an earlier artifact.
- The artifact depends on assumptions that were removed or changed upstream.
- A later artifact lists this file in `## Upstream Changes Required`.

When an artifact is stale, restart from the earliest stale stage and regenerate every later stage in order.

## Resume Algorithm

1. Read `00-project-brief.md` if it exists and compare it to the latest request.
2. Refresh `00-project-brief.md` if it is missing or stale.
3. Evaluate `01` through `05` in order and stop at the first missing, incomplete, or stale stage.
4. Invoke the mapped worker skill for that stage.
5. After the worker completes, re-check all later stages for staleness before proceeding.
6. Allow `06` only when `05` is complete and the user requests post-baseline enhancement planning.
