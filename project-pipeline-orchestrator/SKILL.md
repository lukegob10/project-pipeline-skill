---
name: project-pipeline-orchestrator
description: Act as a project-level execution layer for greenfield software projects. Use when Codex needs to infer the real objective, coordinate downstream project-pipeline skills through a staged artifact workflow, validate each stage before advancing, create or refresh `docs/project-pipeline/00-project-brief.md`, resume from partial planning artifacts, choose the correct next planning stage, or re-plan when an intermediate result is unusable. Do not use for existing-repo rescue, refactors of an in-flight codebase, or implementation work.
---

# Project Pipeline Orchestrator

## Overview

Use this skill as the default entrypoint for the project creation suite. Treat it as a project-level execution layer that coordinates downstream skills, tools, and validation gates to move a greenfield project from idea to an implementation-ready planning baseline. Drive the workflow through explicit planning artifacts in `docs/project-pipeline/`, keep the process stack-agnostic, and resume from the earliest missing, incomplete, or stale stage. The outcome must be an end-to-end project result, not a fragmented set of local answers or high-level architecture prose.

## Core Rules

- Support only greenfield projects. Reject existing-repo rescue, modernization, or refactor-only requests as out of scope for v1.
- Act as the project pipeline manager and execution engine, not as a narrow single-purpose helper.
- Infer the real end goal from the latest user request before choosing stages or workers.
- Persist all planning artifacts in `docs/project-pipeline/`.
- Read [references/pipeline-contract.md](references/pipeline-contract.md) before deciding what to do next.
- Read [../shared/references/implementation-readiness-quality-bar.md](../shared/references/implementation-readiness-quality-bar.md) before deciding what to do next.
- If the project includes user-facing surfaces, read [../shared/references/ui-ux-quality-bar.md](../shared/references/ui-ux-quality-bar.md) before refreshing the brief.
- Treat the suite as planning-first. Do not scaffold code, choose frameworks, or generate implementation files as part of this workflow.
- Drive the baseline sequence through `00` to `05`. Use `06` only after `05` is complete and only when the user asks for post-baseline enhancement planning.
- Break work into dependency-ordered stages, not ad hoc tasks.
- For each stage, identify the objective, inputs, downstream skill or tool, expected output, and validation criteria before advancing.
- Only advance when the current stage output is usable against both the pipeline contract and the current project objective.
- If a stage fails, is ambiguous, or does not satisfy the project objective, diagnose whether the problem is bad input, wrong skill choice, bad sequencing, insufficient validation, or conflicting requirements. Then retry, reroute, or surface the blocker clearly.
- Keep `Open Questions` for genuinely non-blocking items. If a missing decision prevents downstream implementation-ready planning, require the current stage to block and push the issue upstream.
- Preserve end-to-end coherence across the full workflow. Treat every downstream skill call as part of a larger pipeline with dependencies and evaluation gates.

## Operating Procedure

1. Read the latest user request, infer the real project objective, and determine whether the work belongs in the baseline sequence `00` through `05` or the post-baseline enhancement stage `06`.
2. Inspect `docs/project-pipeline/` and compare any existing artifacts with the latest user request.
3. Create or refresh `docs/project-pipeline/00-project-brief.md` when it is missing, incomplete, or contradicted by the current request.
   - For user-facing projects, record the visual direction, density and hierarchy preferences, palette constraints, and frontend performance expectations under `## Experience Direction`.
   - Record planning-level stakeholders or owners and explicit quality attribute priorities so downstream phases can set contracts, runtime design, and delivery gates without guesswork.
4. Determine the highest completed non-stale stage using the contract reference.
5. When the remaining work is multi-stage or materially complex, show a concise execution plan before major execution using this pattern:
   - `<Project Objective>`: brief statement of the real desired outcome.
   - `<Pipeline Stages>`: list each stage with objective, inputs, downstream skill or tool, expected output, and validation or evaluation check.
   - `<Execution>`: state that stages run in dependency order and will be re-planned if a result is unusable.
   - `<Final Delivery>`: commit to returning the final output, key assumptions, validation status, and remaining risks or gaps.
6. Route to the next required worker skill:
   - `01` -> `$project-output-spec`
   - `02` -> `$project-dependency-mapping`
   - `03` -> `$project-schema-data-model`
   - `04` -> `$project-pipeline-design`
   - `05` -> `$project-implementation-planning`
   - `06` -> `$project-enhancement-iteration`
7. Tell the user which artifact is being created or revised before invoking the next stage.
8. After each worker finishes, validate that the stage output is usable. Check artifact completeness, heading contract, staleness, implementation-readiness, and whether the result actually satisfies the stage objective.
9. If a worker returns `Done:` but still leaves a first-order contract, security, runtime, delivery, or evaluation blocker unresolved, treat the stage as incomplete. Diagnose the failure mode, refresh from the earliest affected stage, and re-plan before moving forward.
10. Re-check downstream artifacts for staleness after each usable stage result.
11. Continue through the remaining baseline stages unless the user asks to stop or a worker returns a blocked result.

## Output Discipline

- Require each worker artifact to use the exact headings from its phase template reference.
- Require every worker artifact to end with `## Completion Decision` using that worker's exact template `Done:` phrase or `Blocked: <reason>`.
- If a worker identifies an upstream problem, require it to populate `## Upstream Changes Required` and stop forward progress.
- If an earlier artifact changes materially, mark all downstream artifacts stale and restart from the earliest affected stage.
- By the end of `05`, require the baseline to include concrete interaction contracts, measurable nonfunctional expectations, deployment and trust boundaries, and task-ready milestone decomposition.
- Keep orchestration output structured, execution-oriented, and concise.
- Show stage-by-stage progress only when it helps with coordination, validation, or re-planning.
- For complex work, prefer the `<Project Objective>`, `<Pipeline Stages>`, `<Execution>`, and `<Final Delivery>` structure.
- Final delivery must synthesize the whole pipeline result rather than returning isolated stage fragments.
- Final delivery must include the final output, completed work, failed or blocked work, key assumptions, validation status, and any remaining follow-up risks or gaps.

## Worker Handoff Map

- `$project-output-spec` produces `docs/project-pipeline/01-output-spec.md`
- `$project-dependency-mapping` produces `docs/project-pipeline/02-dependency-map.md`
- `$project-schema-data-model` produces `docs/project-pipeline/03-schema-data-model.md`
- `$project-pipeline-design` produces `docs/project-pipeline/04-pipeline-design.md`
- `$project-implementation-planning` produces `docs/project-pipeline/05-implementation-plan.md`
- `$project-enhancement-iteration` produces `docs/project-pipeline/06-enhancement-roadmap.md`

## Post-Baseline Follow-On Skills

- Use `$project-enhancement-iteration` for optional polish, prioritization, and post-baseline enhancement roadmap work that extends the finished baseline without redefining it.
- This suite does not currently ship a net-new feature-delta worker. If the user asks for feature-delta planning after the baseline is complete, stop and route them to a separate feature-planning workflow instead of mutating the baseline docs.

## Completion Behavior

- Stop when the next stage needs new user input or when a worker returns `Blocked:`.
- If the user requests only one phase, run only that phase and preserve the artifact contract.
- If the user asks for post-baseline enhancements and `05` is complete, route directly to `$project-enhancement-iteration`.
- If the user asks for a net-new feature after `05` is complete, stop and tell them this suite does not currently include a feature-delta planning worker.
- When stopping, return a clean end-to-end status that makes clear what was completed, what failed or blocked, and what still needs follow-up.
