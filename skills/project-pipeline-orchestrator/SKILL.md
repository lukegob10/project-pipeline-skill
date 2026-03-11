---
name: project-pipeline-orchestrator
description: Orchestrate a staged, artifact-driven planning workflow for greenfield software projects. Use when Codex needs to turn a new product or application idea into a complete project pipeline, create or refresh `docs/project-pipeline/00-project-brief.md`, resume from partial planning artifacts, choose the correct next planning stage, or enforce prerequisite handoffs between the project-pipeline worker skills. Do not use for existing-repo rescue, refactors of an in-flight codebase, or implementation work.
---

# Project Pipeline Orchestrator

## Overview

Use this skill as the default entrypoint for the project creation suite. Drive the workflow through explicit planning artifacts in `docs/project-pipeline/`, keep the process stack-agnostic, and resume from the earliest missing, incomplete, or stale stage.

## Core Rules

- Support only greenfield projects. Reject existing-repo rescue, modernization, or refactor-only requests as out of scope for v1.
- Persist all planning artifacts in `docs/project-pipeline/`.
- Read [references/pipeline-contract.md](references/pipeline-contract.md) before deciding what to do next.
- If the project includes user-facing surfaces, read [../shared/references/ui-ux-quality-bar.md](../shared/references/ui-ux-quality-bar.md) before refreshing the brief.
- Treat the suite as planning-first. Do not scaffold code, choose frameworks, or generate implementation files as part of this workflow.
- Drive the baseline sequence through `00` to `05`. Use `06` only after `05` is complete and only when the user asks for post-baseline enhancement planning.

## Operating Procedure

1. Inspect `docs/project-pipeline/` and compare any existing artifacts with the latest user request.
2. Create or refresh `docs/project-pipeline/00-project-brief.md` when it is missing, incomplete, or contradicted by the current request.
   - For user-facing projects, record the visual direction, density and hierarchy preferences, palette constraints, and frontend performance expectations under `## Experience Direction`.
3. Determine the highest completed non-stale stage using the contract reference.
4. Route to the next required worker skill:
   - `01` -> `$project-output-spec`
   - `02` -> `$project-dependency-mapping`
   - `03` -> `$project-schema-data-model`
   - `04` -> `$project-pipeline-design`
   - `05` -> `$project-implementation-planning`
   - `06` -> `$project-enhancement-iteration`
5. Tell the user which artifact is being created or revised before invoking the next stage.
6. After each worker finishes, re-check downstream artifacts for staleness before moving forward.
7. Continue through the remaining baseline stages unless the user asks to stop or a worker returns a blocked result.

## Output Discipline

- Require each worker artifact to use the exact headings from its phase template reference.
- Require every worker artifact to end with `## Completion Decision` set to `Done:` or `Blocked:`.
- If a worker identifies an upstream problem, require it to populate `## Upstream Changes Required` and stop forward progress.
- If an earlier artifact changes materially, mark all downstream artifacts stale and restart from the earliest affected stage.

## Worker Handoff Map

- `$project-output-spec` produces `docs/project-pipeline/01-output-spec.md`
- `$project-dependency-mapping` produces `docs/project-pipeline/02-dependency-map.md`
- `$project-schema-data-model` produces `docs/project-pipeline/03-schema-data-model.md`
- `$project-pipeline-design` produces `docs/project-pipeline/04-pipeline-design.md`
- `$project-implementation-planning` produces `docs/project-pipeline/05-implementation-plan.md`
- `$project-enhancement-iteration` produces `docs/project-pipeline/06-enhancement-roadmap.md`

## Completion Behavior

- Stop when the next stage needs new user input or when a worker returns `Blocked:`.
- If the user requests only one phase, run only that phase and preserve the artifact contract.
- If the user asks for post-baseline enhancements and `05` is complete, route directly to `$project-enhancement-iteration`.
