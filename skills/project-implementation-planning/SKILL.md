---
name: project-implementation-planning
description: Produce or revise `docs/project-pipeline/05-implementation-plan.md` for a greenfield project using `docs/project-pipeline/00-project-brief.md` through `04-pipeline-design.md`. Use when Codex needs to define milestones, task sequencing, MVP scope, test strategy, and delivery risks for a new project, or when the user explicitly invokes `$project-implementation-planning`. Redirect to the orchestrator or prior stage if earlier artifacts are missing or stale.
---

# Project Implementation Planning

## Overview

Produce the canonical implementation plan for the current greenfield project. Convert the earlier planning artifacts into a phased delivery strategy with an explicit MVP cutline and validation approach.

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- `docs/project-pipeline/02-dependency-map.md`
- `docs/project-pipeline/03-schema-data-model.md`
- `docs/project-pipeline/04-pipeline-design.md`
- Any later project-pipeline artifacts that already exist, if revising
- [references/phase-template.md](references/phase-template.md)
- [../shared/references/ui-ux-quality-bar.md](../shared/references/ui-ux-quality-bar.md) when the project includes user-facing UI

## Workflow

1. Confirm the request remains inside the greenfield baseline workflow.
2. Read `00` through `04` and the phase template before drafting. If the project includes user-facing surfaces, also read the shared UI/UX reference.
3. Create or revise `docs/project-pipeline/05-implementation-plan.md` using the exact headings from the template.
4. Define milestones, task dependencies, MVP boundaries, experience quality workstreams, test strategy, and key delivery risks. For UI-heavy projects, plan the design system, responsive QA, accessibility, and frontend performance validation as first-class work.
5. If any upstream artifact is insufficient or contradictory, populate `## Upstream Changes Required`, mark the artifact blocked, and stop.
6. If you revise `05-implementation-plan.md`, require enhancement planning to be revisited before `06` can be considered current.

## Completion Behavior

- End the artifact with `## Completion Decision` set to `Done:` or `Blocked:`.
- If blocked by an upstream issue, direct the user to `$project-pipeline-orchestrator`.
- If done, the baseline workflow is complete and `$project-enhancement-iteration` becomes available on request.
