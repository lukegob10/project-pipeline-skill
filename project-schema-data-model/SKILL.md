---
name: project-schema-data-model
description: Produce or revise `docs/project-pipeline/03-schema-data-model.md` as stage `03` of the greenfield project-pipeline workflow using `docs/project-pipeline/00-project-brief.md`, `01-output-spec.md`, and `02-dependency-map.md`. Use when Codex needs to define core entities, data structures, contracts, state transitions, and validation rules for a new project, or when the user explicitly invokes `$project-schema-data-model`. Redirect to the orchestrator or prior stage if earlier artifacts are missing or stale.
---

# Project Schema Data Model

## Overview

Produce the canonical schema and data model artifact for the current greenfield project. Treat this as stage `03` in a larger pipeline: convert earlier planning artifacts into stable data shapes, lifecycle rules, and interface contracts without choosing a concrete implementation stack or inventing new product scope.

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- `docs/project-pipeline/02-dependency-map.md`
- Any later project-pipeline artifacts that already exist, if revising
- [references/phase-template.md](references/phase-template.md)
- [../shared/references/implementation-readiness-quality-bar.md](../shared/references/implementation-readiness-quality-bar.md)

## Stage Contract

- Objective: define the entities, contracts, validation rules, and lifecycle behavior required by the upstream output and dependency decisions.
- Expected Output: `docs/project-pipeline/03-schema-data-model.md`
- Validation Gate: the artifact uses the exact template headings, stays stack-agnostic, makes contracts and lifecycle behavior concrete enough for pipeline design, and blocks upstream instead of leaving first-order interface or data ambiguity unresolved.

## Workflow

1. Confirm the request remains within the greenfield baseline workflow.
2. Validate that `00` through `02` exist, match the current request, and are usable for this stage. If any required input is missing, stale, or contradictory, stop and redirect to `$project-pipeline-orchestrator`.
3. Read `00` through `02`, the phase template, and the shared implementation-readiness reference before drafting.
4. Create or revise `docs/project-pipeline/03-schema-data-model.md` using the exact headings from the template.
5. Define entities, fields, contracts, state transitions, validation rules, and data lifecycle behavior at the planning level.
6. Make contracts specific enough to derive later interface schemas, identifiers, filters, payload shapes, compatibility rules, and authorization or provenance fields where relevant.
7. If any upstream artifact is insufficient, contradictory, or too vague to support interface- and lifecycle-ready modeling, populate `## Upstream Changes Required`, mark the artifact blocked, and stop instead of inventing missing contracts.
8. Before marking the stage done, validate the artifact against the phase template review rubric and confirm `04-pipeline-design.md` can be produced without inventing first-order schema, identifier, lifecycle, or interface assumptions.
9. If you revise `03-schema-data-model.md`, assume `04` and later artifacts may need revalidation by the orchestrator.

## Completion Behavior

- End the artifact with `## Completion Decision` using `Done: ready for $project-pipeline-design` or `Blocked: <reason>`.
- If blocked by an upstream issue, direct the user to `$project-pipeline-orchestrator`.
- If done, hand off only when the artifact is usable for `$project-pipeline-design`.
