---
name: project-pipeline-design
description: Produce or revise `docs/project-pipeline/04-pipeline-design.md` as stage `04` of the greenfield project-pipeline workflow using `docs/project-pipeline/00-project-brief.md` through `03-schema-data-model.md`. Use when Codex needs to define the end-to-end flow, control and data movement, failure handling, and observability points for a new project, or when the user explicitly invokes `$project-pipeline-design`. Redirect to the orchestrator or prior stage if earlier artifacts are missing or stale.
---

# Project Pipeline Design

## Overview

Produce the canonical pipeline design artifact for the current greenfield project. Treat this as stage `04` in a larger pipeline: convert the earlier planning artifacts into an explicit end-to-end operating flow and runtime view without choosing a framework or implementation stack, and without redefining upstream contracts.

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- `docs/project-pipeline/02-dependency-map.md`
- `docs/project-pipeline/03-schema-data-model.md`
- Any later project-pipeline artifacts that already exist, if revising
- [references/phase-template.md](references/phase-template.md)
- [../shared/references/implementation-readiness-quality-bar.md](../shared/references/implementation-readiness-quality-bar.md)
- [../shared/references/ui-ux-quality-bar.md](../shared/references/ui-ux-quality-bar.md) when the project includes user-facing UI

## Stage Contract

- Objective: define how the planned system operates end to end, including control flow, data flow, failures, observability, and runtime topology.
- Expected Output: `docs/project-pipeline/04-pipeline-design.md`
- Validation Gate: the artifact uses the exact template headings, stays stack-agnostic, makes runtime and recovery behavior concrete enough for implementation planning, and blocks upstream instead of leaving first-order flow or topology ambiguity unresolved.

## Workflow

1. Confirm the request remains inside the greenfield baseline workflow.
2. Validate that `00` through `03` exist, match the current request, and are usable for this stage. If any required input is missing, stale, or contradictory, stop and redirect to `$project-pipeline-orchestrator`.
3. Read `00` through `03`, the phase template, and the shared implementation-readiness reference before drafting. If the project includes user-facing surfaces, also read the shared UI/UX reference.
4. Create or revise `docs/project-pipeline/04-pipeline-design.md` using the exact headings from the template.
5. Describe how work moves through the system, where control decisions happen, how data flows, how failures are handled and observed, and how user-facing responsiveness is protected when the project includes UI.
6. Include runtime topology, deployment flow, trust boundaries, recovery paths, rollout or rollback expectations, and observability points that map back to the quality targets defined upstream.
7. If any upstream artifact is insufficient, contradictory, or too vague to support an implementation-ready runtime design, populate `## Upstream Changes Required`, mark the artifact blocked, and stop instead of compensating for missing stage inputs.
8. Before marking the stage done, validate the artifact against the phase template review rubric and confirm `05-implementation-plan.md` can be produced without inventing first-order orchestration, topology, failure, or observability assumptions.
9. If you revise `04-pipeline-design.md`, assume `05` and `06` may need revalidation by the orchestrator.

## Completion Behavior

- End the artifact with `## Completion Decision` using `Done: ready for $project-implementation-planning` or `Blocked: <reason>`.
- If blocked by an upstream issue, direct the user to `$project-pipeline-orchestrator`.
- If done, hand off only when the artifact is usable for `$project-implementation-planning`.
