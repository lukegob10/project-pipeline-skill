---
name: project-enhancement-iteration
description: Produce or revise `docs/project-pipeline/06-enhancement-roadmap.md` as stage `06` of the greenfield project-pipeline workflow after `docs/project-pipeline/05-implementation-plan.md` is complete. Use when Codex needs to plan optional post-baseline enhancements, prioritization, complexity increments, prerequisites, and risk or impact for a new project, or when the user explicitly invokes `$project-enhancement-iteration`. Do not use until the baseline planning flow is complete, and do not use it for net-new feature-delta planning.
---

# Project Enhancement Iteration

## Overview

Produce the canonical post-baseline enhancement roadmap for the current greenfield project. Treat this as stage `06` in a larger pipeline: an optional follow-on phase that starts only after the baseline implementation plan is complete and implementation-ready, extends rather than redefines the baseline, and stays separate from net-new feature-delta planning.

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- `docs/project-pipeline/02-dependency-map.md`
- `docs/project-pipeline/03-schema-data-model.md`
- `docs/project-pipeline/04-pipeline-design.md`
- `docs/project-pipeline/05-implementation-plan.md`
- [references/phase-template.md](references/phase-template.md)
- [../shared/references/implementation-readiness-quality-bar.md](../shared/references/implementation-readiness-quality-bar.md)
- [../shared/references/ui-ux-quality-bar.md](../shared/references/ui-ux-quality-bar.md) when the project includes user-facing UI

## Stage Contract

- Objective: plan optional post-baseline enhancements without moving required baseline work out of stages `00` through `05`.
- Expected Output: `docs/project-pipeline/06-enhancement-roadmap.md`
- Validation Gate: the artifact uses the exact template headings, stays stack-agnostic, preserves the completed baseline as the prerequisite, and blocks upstream instead of treating deferred baseline work as enhancement scope.

## Workflow

1. Confirm that `05-implementation-plan.md` exists, matches the current request, and is complete before doing any enhancement planning. If the baseline is missing, stale, or blocked, stop and redirect to `$project-pipeline-orchestrator`.
2. Confirm the request is optional enhancement, polish, prioritization, or iteration work rather than a net-new feature delta. If it is a new feature request, stop and tell the user this suite does not currently ship a net-new feature-delta worker; they need a separate feature-planning workflow.
3. Read `00` through `05`, the phase template, and the shared implementation-readiness reference before drafting. If the project includes user-facing surfaces, also read the shared UI/UX reference.
4. Create or revise `docs/project-pipeline/06-enhancement-roadmap.md` using the exact headings from the template.
5. Organize enhancements as post-baseline increments rather than changes to the baseline definition. For UI-heavy projects, treat higher-order polish, richer workflows, and deeper performance optimization as enhancement themes only after the baseline quality bar is already covered upstream.
6. If baseline artifacts still defer required contract, security, reliability, or delivery-readiness work, do not treat that work as an enhancement. Push the issue upstream and block this stage.
7. If any upstream artifact is insufficient or contradictory, populate `## Upstream Changes Required`, mark the artifact blocked, and stop instead of collapsing baseline fixes into roadmap items.
8. Keep the roadmap stack-agnostic unless the earlier artifacts explicitly constrain technology.
9. Before marking the stage done, validate the artifact against the phase template review rubric and confirm the roadmap remains clearly optional, post-baseline, dependency-aware, and distinct from new feature work.

## Completion Behavior

- End the artifact with `## Completion Decision` using `Done: enhancement roadmap ready` or `Blocked: <reason>`.
- If blocked by a missing or stale baseline artifact, direct the user to `$project-pipeline-orchestrator`.
- If the request is really a net-new feature delta, stop and tell the user this suite does not currently ship a net-new feature-delta worker.
- If done, keep the roadmap clearly separate from the baseline `00` through `05` artifacts, do not present it as a replacement for baseline readiness, and do not use it to plan net-new features.
