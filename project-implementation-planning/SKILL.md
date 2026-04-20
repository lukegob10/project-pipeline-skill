---
name: project-implementation-planning
description: Produce or revise `docs/project-pipeline/05-implementation-plan.md` as stage `05` of the greenfield project-pipeline workflow using `docs/project-pipeline/00-project-brief.md` through `04-pipeline-design.md`. Use when Codex needs to define milestones, task sequencing, MVP scope, test strategy, and delivery risks for a new project, or when the user explicitly invokes `$project-implementation-planning`. Redirect to the orchestrator or prior stage if earlier artifacts are missing or stale.
---

# Project Implementation Planning

## Overview

Produce the canonical implementation plan for the current greenfield project. Treat this as stage `05` in a larger pipeline: convert the earlier planning artifacts into a phased delivery strategy with an explicit MVP cutline, decision gates, and validation approach that is ready for detailed coding without re-opening upstream planning decisions.

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- `docs/project-pipeline/02-dependency-map.md`
- `docs/project-pipeline/03-schema-data-model.md`
- `docs/project-pipeline/04-pipeline-design.md`
- Any later project-pipeline artifacts that already exist, if revising
- [references/phase-template.md](references/phase-template.md)
- [../shared/references/implementation-readiness-quality-bar.md](../shared/references/implementation-readiness-quality-bar.md)
- [../shared/references/ui-ux-quality-bar.md](../shared/references/ui-ux-quality-bar.md) when the project includes user-facing UI

## Stage Contract

- Objective: turn the approved product, dependency, schema, and runtime design artifacts into a task-ready delivery plan with milestone, risk, and evaluation gates.
- Expected Output: `docs/project-pipeline/05-implementation-plan.md`
- Validation Gate: the artifact uses the exact template headings, stays stack-agnostic, makes milestone and validation sequencing concrete enough for detailed coding, and blocks upstream instead of leaving first-order delivery ambiguity unresolved.

## Workflow

1. Confirm the request remains inside the greenfield baseline workflow.
2. Validate that `00` through `04` exist, match the current request, and are usable for this stage. If any required input is missing, stale, or contradictory, stop and redirect to `$project-pipeline-orchestrator`.
3. Read `00` through `04`, the phase template, and the shared implementation-readiness reference before drafting. If the project includes user-facing surfaces, also read the shared UI/UX reference.
4. Create or revise `docs/project-pipeline/05-implementation-plan.md` using the exact headings from the template.
5. Define milestones, task dependencies, MVP boundaries, decision gates, reliability and operations workstreams, experience quality workstreams, evaluation strategy, and key delivery risks. For UI-heavy projects, plan the design system, responsive QA, accessibility, and frontend performance validation as first-class work.
6. Decompose the work enough that an engineer could begin detailed implementation planning without inventing missing contracts, runtime assumptions, rollout steps, or validation criteria.
7. If any upstream artifact is insufficient, contradictory, or too vague to support task-ready planning, populate `## Upstream Changes Required`, mark the artifact blocked, and stop instead of flattening unresolved dependencies into the task plan.
8. Before marking the stage done, validate the artifact against the phase template review rubric and confirm the baseline workflow is implementation-ready without inventing first-order milestone, rollout, or evaluation assumptions.
9. If you revise `05-implementation-plan.md`, require enhancement planning to be revisited before `06` can be considered current.

## Completion Behavior

- End the artifact with `## Completion Decision` using `Done: baseline workflow complete` or `Blocked: <reason>`.
- If blocked by an upstream issue, direct the user to `$project-pipeline-orchestrator`.
- If done, treat the baseline workflow as complete and keep post-baseline follow-ons separate: use `$project-enhancement-iteration` for optional polish and roadmap work. This suite does not currently ship a net-new feature-delta worker, so route those requests to a separate feature-planning workflow instead of mutating the baseline artifacts.
