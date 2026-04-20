---
name: project-output-spec
description: Produce or revise `docs/project-pipeline/01-output-spec.md` as stage `01` of the greenfield project-pipeline workflow from `docs/project-pipeline/00-project-brief.md`. Use when Codex needs to define the problem, audience, use cases, outputs, acceptance criteria, and non-goals for a new project, or when the user explicitly invokes `$project-output-spec`. Redirect to the orchestrator or prior stage if the project brief is missing or stale.
---

# Project Output Spec

## Overview

Produce the canonical output specification artifact for the current greenfield project. Treat this as stage `01` in a larger pipeline: convert the project brief into a usable downstream contract, keep the result stack-agnostic and implementation-ready, and trace every section back to the brief rather than trying to solve the whole project in one pass.

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- Any later project-pipeline artifacts that already exist, if revising, so contradictions can be detected
- [references/phase-template.md](references/phase-template.md)
- [../shared/references/implementation-readiness-quality-bar.md](../shared/references/implementation-readiness-quality-bar.md)
- [../shared/references/ui-ux-quality-bar.md](../shared/references/ui-ux-quality-bar.md) when the project includes user-facing UI

## Stage Contract

- Objective: translate the approved project brief into a concrete product, interaction, quality, and access contract for downstream design.
- Expected Output: `docs/project-pipeline/01-output-spec.md`
- Validation Gate: the artifact uses the exact template headings, stays stack-agnostic, makes interaction, experience, nonfunctional, and security expectations concrete enough for dependency mapping, and blocks upstream instead of leaving first-order ambiguity unresolved.

## Workflow

1. Confirm the request is for a greenfield project. Refuse existing-repo rescue or modernization work.
2. Validate that `00-project-brief.md` exists, matches the current request, and is usable for this stage. If it is missing, stale, or contradictory, stop and redirect to `$project-pipeline-orchestrator`.
3. Read the project brief, the phase template, and the shared implementation-readiness reference before drafting. If the project includes user-facing surfaces, also read the shared UI/UX reference.
4. Create or revise `docs/project-pipeline/01-output-spec.md` using the exact headings from the template.
5. Define behavior and deliverables without choosing frameworks or implementation details. Convert any UI direction from the brief into concrete experience requirements and observable quality expectations.
6. Make interaction contracts, nonfunctional requirements, and security or access expectations concrete enough to drive downstream architecture. For protocol or API projects, require explicit operations, request and response semantics, error behavior, auth expectations, continuation or pagination rules, and budget or size limits at a planning level.
7. If the brief is insufficient, contradictory, or too vague to support implementation-ready downstream design, populate `## Upstream Changes Required`, mark the artifact blocked, and stop instead of guessing or skipping ahead.
8. Before marking the stage done, validate the artifact against the phase template review rubric and confirm `02-dependency-map.md` can be produced without inventing first-order product, contract, quality, or security assumptions.
9. If you revise `01-output-spec.md`, assume all downstream artifacts may need revalidation by the orchestrator.

## Completion Behavior

- End the artifact with `## Completion Decision` using `Done: ready for $project-dependency-mapping` or `Blocked: <reason>`.
- If blocked by the brief, direct the user to `$project-pipeline-orchestrator`.
- If done, hand off only when the artifact is usable for `$project-dependency-mapping`.
