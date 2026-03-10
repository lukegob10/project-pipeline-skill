---
name: project-enhancement-iteration
description: Produce or revise `docs/project-pipeline/06-enhancement-roadmap.md` for a greenfield project after `docs/project-pipeline/05-implementation-plan.md` is complete. Use when Codex needs to plan post-baseline enhancements, prioritization, complexity increments, prerequisites, and risk or impact for a new project, or when the user explicitly invokes `$project-enhancement-iteration`. Do not use until the baseline planning flow is complete.
---

# Project Enhancement Iteration

## Overview

Produce the canonical post-baseline enhancement roadmap for the current greenfield project. Treat this as an optional follow-on phase that starts only after the baseline implementation plan is complete.

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- `docs/project-pipeline/02-dependency-map.md`
- `docs/project-pipeline/03-schema-data-model.md`
- `docs/project-pipeline/04-pipeline-design.md`
- `docs/project-pipeline/05-implementation-plan.md`
- [references/phase-template.md](references/phase-template.md)

## Workflow

1. Confirm that `05-implementation-plan.md` exists and is complete before doing any enhancement planning.
2. Read `00` through `05` and the phase template before drafting.
3. Create or revise `docs/project-pipeline/06-enhancement-roadmap.md` using the exact headings from the template.
4. Organize enhancements as post-baseline increments rather than changes to the baseline definition.
5. If any upstream artifact is insufficient or contradictory, populate `## Upstream Changes Required`, mark the artifact blocked, and stop.
6. Keep the roadmap stack-agnostic unless the earlier artifacts explicitly constrain technology.

## Completion Behavior

- End the artifact with `## Completion Decision` set to `Done:` or `Blocked:`.
- If blocked by a missing or stale baseline artifact, direct the user to `$project-pipeline-orchestrator`.
- If done, keep the roadmap clearly separate from the baseline `00` through `05` artifacts.
