---
name: project-pipeline-design
description: Produce or revise `docs/project-pipeline/04-pipeline-design.md` for a greenfield project using `docs/project-pipeline/00-project-brief.md` through `03-schema-data-model.md`. Use when Codex needs to define the end-to-end flow, control and data movement, failure handling, and observability points for a new project, or when the user explicitly invokes `$project-pipeline-design`. Redirect to the orchestrator or prior stage if earlier artifacts are missing or stale.
---

# Project Pipeline Design

## Overview

Produce the canonical pipeline design artifact for the current greenfield project. Convert the earlier planning artifacts into an explicit end-to-end operating flow without choosing a framework or implementation stack.

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- `docs/project-pipeline/02-dependency-map.md`
- `docs/project-pipeline/03-schema-data-model.md`
- Any later project-pipeline artifacts that already exist, if revising
- [references/phase-template.md](references/phase-template.md)

## Workflow

1. Confirm the request remains inside the greenfield baseline workflow.
2. Read `00` through `03` and the phase template before drafting.
3. Create or revise `docs/project-pipeline/04-pipeline-design.md` using the exact headings from the template.
4. Describe how work moves through the system, where control decisions happen, how data flows, and how failures are handled and observed.
5. If any upstream artifact is insufficient or contradictory, populate `## Upstream Changes Required`, mark the artifact blocked, and stop.
6. If you revise `04-pipeline-design.md`, assume `05` and `06` may need revalidation by the orchestrator.

## Completion Behavior

- End the artifact with `## Completion Decision` set to `Done:` or `Blocked:`.
- If blocked by an upstream issue, direct the user to `$project-pipeline-orchestrator`.
- If done, the next baseline skill is `$project-implementation-planning`.
