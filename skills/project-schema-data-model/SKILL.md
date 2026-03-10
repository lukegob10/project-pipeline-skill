---
name: project-schema-data-model
description: Produce or revise `docs/project-pipeline/03-schema-data-model.md` for a greenfield project using `docs/project-pipeline/00-project-brief.md`, `01-output-spec.md`, and `02-dependency-map.md`. Use when Codex needs to define core entities, data structures, contracts, state transitions, and validation rules for a new project, or when the user explicitly invokes `$project-schema-data-model`. Redirect to the orchestrator or prior stage if earlier artifacts are missing or stale.
---

# Project Schema Data Model

## Overview

Produce the canonical schema and data model artifact for the current greenfield project. Convert earlier planning artifacts into stable data shapes and interface contracts without choosing a concrete implementation stack.

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- `docs/project-pipeline/02-dependency-map.md`
- Any later project-pipeline artifacts that already exist, if revising
- [references/phase-template.md](references/phase-template.md)

## Workflow

1. Confirm the request remains within the greenfield baseline workflow.
2. Read `00` through `02` and the phase template before drafting.
3. Create or revise `docs/project-pipeline/03-schema-data-model.md` using the exact headings from the template.
4. Define entities, fields, contracts, state transitions, and validation rules at the planning level.
5. If any upstream artifact is insufficient or contradictory, populate `## Upstream Changes Required`, mark the artifact blocked, and stop.
6. If you revise `03-schema-data-model.md`, assume `04` and later artifacts may need revalidation by the orchestrator.

## Completion Behavior

- End the artifact with `## Completion Decision` set to `Done:` or `Blocked:`.
- If blocked by an upstream issue, direct the user to `$project-pipeline-orchestrator`.
- If done, the next baseline skill is `$project-pipeline-design`.
