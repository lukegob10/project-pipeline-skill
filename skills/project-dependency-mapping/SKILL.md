---
name: project-dependency-mapping
description: Produce or revise `docs/project-pipeline/02-dependency-map.md` for a greenfield project using `docs/project-pipeline/00-project-brief.md` and `docs/project-pipeline/01-output-spec.md`. Use when Codex needs to map system components, external systems, integrations, dependency relationships, and coupling or risk notes for a new project, or when the user explicitly invokes `$project-dependency-mapping`. Redirect to the orchestrator or prior stage if the brief or output spec is missing or stale.
---

# Project Dependency Mapping

## Overview

Produce the canonical dependency map for the current greenfield project. Translate the brief and output spec into an explicit component and integration graph without locking in a framework choice.

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- Any later project-pipeline artifacts that already exist, if revising
- [references/phase-template.md](references/phase-template.md)

## Workflow

1. Confirm the request is still greenfield-only.
2. Read `00-project-brief.md`, `01-output-spec.md`, and the phase template before drafting.
3. Create or revise `docs/project-pipeline/02-dependency-map.md` using the exact headings from the template.
4. Model internal components, external systems, operational dependencies, and major coupling risks.
5. If `00` or `01` is insufficient or contradictory, populate `## Upstream Changes Required`, mark the artifact blocked, and stop.
6. If you revise `02-dependency-map.md`, assume `03` and later artifacts may need revalidation by the orchestrator.

## Completion Behavior

- End the artifact with `## Completion Decision` set to `Done:` or `Blocked:`.
- If blocked by an upstream issue, direct the user to `$project-pipeline-orchestrator`.
- If done, the next baseline skill is `$project-schema-data-model`.
