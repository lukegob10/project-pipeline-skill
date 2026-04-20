---
name: project-dependency-mapping
description: Produce or revise `docs/project-pipeline/02-dependency-map.md` as stage `02` of the greenfield project-pipeline workflow using `docs/project-pipeline/00-project-brief.md` and `docs/project-pipeline/01-output-spec.md`. Use when Codex needs to map system components, external systems, integrations, dependency relationships, and coupling or risk notes for a new project, or when the user explicitly invokes `$project-dependency-mapping`. Redirect to the orchestrator or prior stage if the brief or output spec is missing or stale.
---

# Project Dependency Mapping

## Overview

Produce the canonical dependency map for the current greenfield project. Treat this as stage `02` in a larger pipeline: translate the brief and output spec into an explicit component, deployment, and integration graph without locking in a framework choice or rewriting upstream product intent.

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- Any later project-pipeline artifacts that already exist, if revising
- [references/phase-template.md](references/phase-template.md)
- [../shared/references/implementation-readiness-quality-bar.md](../shared/references/implementation-readiness-quality-bar.md)
- [../shared/references/ui-ux-quality-bar.md](../shared/references/ui-ux-quality-bar.md) when the project includes user-facing UI

## Stage Contract

- Objective: map the concrete components, integrations, runtime boundaries, and trust zones required to satisfy the output spec.
- Expected Output: `docs/project-pipeline/02-dependency-map.md`
- Validation Gate: the artifact uses the exact template headings, stays stack-agnostic, makes deployment and trust boundaries explicit enough for schema and pipeline work, and blocks upstream instead of leaving first-order runtime ambiguity unresolved.

## Workflow

1. Confirm the request is still greenfield-only.
2. Validate that `00-project-brief.md` and `01-output-spec.md` both exist, match the current request, and are usable for this stage. If either is missing, stale, or contradictory, stop and redirect to `$project-pipeline-orchestrator`.
3. Read `00-project-brief.md`, `01-output-spec.md`, the phase template, and the shared implementation-readiness reference before drafting. If the project includes user-facing surfaces, also read the shared UI/UX reference.
4. Create or revise `docs/project-pipeline/02-dependency-map.md` using the exact headings from the template.
5. Model internal components, external systems, deployment and trust boundaries, operational dependencies, and major coupling risks. For UI-heavy projects, include the client runtime, design system, asset delivery, search, telemetry, or other experience-critical dependencies needed to satisfy the output spec.
6. Make runtime boundaries, secret and auth boundaries, network paths, and blast-radius-sensitive dependencies explicit enough to drive later schema, pipeline, and rollout planning.
7. If `00` or `01` is insufficient, contradictory, or too vague to establish a concrete runtime view, populate `## Upstream Changes Required`, mark the artifact blocked, and stop instead of patching around missing inputs.
8. Before marking the stage done, validate the artifact against the phase template review rubric and confirm `03-schema-data-model.md` can be produced without inventing first-order component, integration, or trust-boundary assumptions.
9. If you revise `02-dependency-map.md`, assume `03` and later artifacts may need revalidation by the orchestrator.

## Completion Behavior

- End the artifact with `## Completion Decision` using `Done: ready for $project-schema-data-model` or `Blocked: <reason>`.
- If blocked by an upstream issue, direct the user to `$project-pipeline-orchestrator`.
- If done, hand off only when the artifact is usable for `$project-schema-data-model`.
