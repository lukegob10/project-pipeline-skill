# Project Pipeline Contract

## Artifact Root

Store every planning artifact in `docs/project-pipeline/`. Create the directory before writing the first file.

Treat the baseline workflow as implementation-ready planning. The artifacts must stay stack-agnostic, but they must still close product, contract, quality, security, runtime, and delivery questions enough to support detailed coding.

## Orchestration Role

Treat the orchestrator as a project-level execution layer, not as a narrow local helper. Its job is to infer the real project objective, decompose the work into dependency-ordered stages, delegate each stage to the correct downstream skill or tool, validate outputs before advancing, and preserve end-to-end coherence across the full pipeline.

## Stage Planning Contract

Before major execution when the work is complex or spans multiple stages, present a concise stage plan. Use the following pattern when relevant:

```md
<Project Objective>
Brief statement of the real desired outcome.

<Pipeline Stages>
1. Stage name
   - Goal
   - Skill/tool
   - Inputs
   - Outputs
   - Eval/check

<Execution>
Run stages in dependency order. Re-plan if needed.

<Final Delivery>
Provide:
- final output
- key assumptions
- validation status
- remaining risks/gaps
```

For every stage, the orchestrator must identify:

- The stage objective.
- The required inputs.
- The downstream skill or tool to invoke.
- The expected output artifact or decision.
- The validation or evaluation criteria that determine whether the output is usable.

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
## Stakeholders and Owners
## Experience Direction
## Constraints
## Quality Attribute Priorities
## Success Criteria
## Non-Goals
## Explicit Assumptions
```

For projects with user-facing surfaces, use `## Experience Direction` to record the primary UI reference model, layout density and hierarchy preferences, navigation or information architecture assumptions, palette constraints, and any explicit frontend performance expectations. For non-UI projects, write `Not applicable`.

Use `## Stakeholders and Owners` to identify who consumes, operates, approves, or funds the work at a planning level. Use `## Quality Attribute Priorities` to rank the most important qualities such as latency, correctness, availability, freshness, auditability, security, operability, cost control, or maintainability.

Refresh `00-project-brief.md` whenever the user changes the core goal, target users, stakeholders, experience direction, constraints, quality priorities, or success criteria.

## Worker Map

- `01-output-spec.md` -> `$project-output-spec`
- `02-dependency-map.md` -> `$project-dependency-mapping`
- `03-schema-data-model.md` -> `$project-schema-data-model`
- `04-pipeline-design.md` -> `$project-pipeline-design`
- `05-implementation-plan.md` -> `$project-implementation-planning`
- `06-enhancement-roadmap.md` -> `$project-enhancement-iteration`

## Post-Baseline Follow-On Skills

After baseline `05` is complete:

- Use `$project-enhancement-iteration` for optional polish, prioritization, and roadmap-style post-baseline enhancement planning.
- This suite does not currently ship a net-new feature-delta worker. Route those requests to a separate feature-planning workflow rather than mutating the baseline docs.

## Required Heading Checks

Use these minimum heading checks when resuming:

- `01-output-spec.md`: `Problem Statement`, `Target Users and Operators`, `Core Use Cases`, `Primary Outputs`, `Interaction Contracts`, `Experience Requirements`, `Nonfunctional Requirements`, `Security and Access Expectations`, `Acceptance Criteria`, `Non-Goals`, `Open Questions`, `Upstream Changes Required`, `Completion Decision`
- `02-dependency-map.md`: `System Components`, `External Systems and Integrations`, `Dependency Graph`, `Deployment and Trust Boundaries`, `Coupling and Risk Notes`, `Operational Dependencies`, `Open Questions`, `Upstream Changes Required`, `Completion Decision`
- `03-schema-data-model.md`: `Core Entities`, `Data Structures and Fields`, `Contracts and Interfaces`, `State Transitions`, `Validation Rules`, `Data Lifecycle and Retention`, `Open Questions`, `Upstream Changes Required`, `Completion Decision`
- `04-pipeline-design.md`: `End-to-End Flow`, `Control Flow`, `Data Flow`, `Failure Handling`, `Observability Points`, `Runtime Topology and Deployment View`, `User Experience and Responsiveness`, `Open Questions`, `Upstream Changes Required`, `Completion Decision`
- `05-implementation-plan.md`: `Delivery Strategy`, `Architectural Decisions and Decision Gates`, `Milestones`, `Task Graph`, `MVP Cutline`, `Reliability, Security, and Operations Plan`, `Experience Quality Plan`, `Test and Evaluation Strategy`, `Risks and Mitigations`, `Open Questions`, `Upstream Changes Required`, `Completion Decision`
- `06-enhancement-roadmap.md`: `Baseline Preconditions`, `Enhancement Themes`, `Prioritized Roadmap`, `Complexity Increments`, `Dependencies and Preconditions`, `Risk and Impact`, `Open Questions`, `Upstream Changes Required`, `Completion Decision`

## Completion Rules

A stage counts as complete only when all of the following are true:

- The file exists at the canonical path.
- The required headings are present.
- The artifact has no placeholder text such as `[TODO]` or `TBD`.
- `## Completion Decision` starts with `Done:`.

Treat `00-project-brief.md` as complete when all required headings are present and the contents match the latest user request, including any explicit experience direction.

Treat a baseline stage as incomplete when it leaves first-order implementation blockers unresolved in `## Open Questions` instead of escalating them through `## Upstream Changes Required`.

Only advance when the current stage output is usable. A usable result is complete, non-stale, aligned with the latest request, and sufficient to satisfy the stage objective without leaving first-order product, contract, runtime, security, delivery, or evaluation ambiguity.

## Stale Rules

Treat an artifact as stale when any of the following is true:

- The current request changes project goal, users, constraints, success criteria, or scope.
- The current request changes stakeholders, owners, or quality attribute priorities.
- The current request changes explicit UI or UX direction, palette constraints, or frontend performance expectations.
- The artifact conflicts with an earlier artifact.
- The artifact depends on assumptions that were removed or changed upstream.
- A later artifact lists this file in `## Upstream Changes Required`.

When an artifact is stale, restart from the earliest stale stage and regenerate every later stage in order.

## Failure Diagnosis and Re-Plan

If a stage output is missing, ambiguous, blocked, or unusable, diagnose the problem before continuing. Use these failure categories:

- Bad input
- Wrong skill choice
- Bad sequencing
- Insufficient validation
- Conflicting requirements

Then take the corresponding action:

- Retry the same stage with corrected inputs when the stage choice is still correct.
- Reroute to a different worker when the prior skill choice was wrong.
- Restart from the earliest affected stage when sequencing or upstream artifacts were wrong.
- Tighten the validation gate and re-check the result when the issue was insufficient evaluation.
- Surface a clear blocker when the requirement conflict cannot be resolved inside the current stage.

## Resume Algorithm

1. Read the latest request and infer the real project objective.
2. Read `00-project-brief.md` if it exists and compare it to the latest request.
3. Refresh `00-project-brief.md` if it is missing or stale.
4. Evaluate `01` through `05` in order and stop at the first missing, incomplete, or stale stage.
5. When the work spans multiple stages or requires a substantial refresh, present a concise stage plan using the stage planning contract.
6. Invoke the mapped worker skill for the next required stage.
7. Validate the stage output against heading checks, completion rules, staleness rules, and the stage objective before advancing.
8. If the output is unusable, run failure diagnosis and re-plan from the earliest affected point.
9. After a usable stage completes, re-check all later stages for staleness and implementation-readiness gaps before proceeding.
10. Allow `06` only when `05` is complete and the user requests post-baseline enhancement planning.
11. When `05` is complete and the user requests a net-new feature, stop and direct them to a separate feature-planning workflow instead of treating the work as baseline refresh or optional enhancement polish.

## Final Delivery

The final response should reflect the full pipeline result rather than isolated worker outputs. Keep it structured, execution-oriented, and concise. Include:

- The final output produced or refreshed.
- Key assumptions that remained in force.
- Validation status for the completed stages.
- Any failed or blocked stages.
- Remaining risks, gaps, or follow-up needed.
