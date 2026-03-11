---
name: project-output-spec
description: Produce or revise `docs/project-pipeline/01-output-spec.md` for a greenfield project from `docs/project-pipeline/00-project-brief.md`. Use when Codex needs to define the problem, audience, use cases, outputs, acceptance criteria, and non-goals for a new project, or when the user explicitly invokes `$project-output-spec`. Redirect to the orchestrator or prior stage if the project brief is missing or stale.
---

# Project Output Spec

## Overview

Produce the canonical output specification artifact for the current greenfield project. Keep the result stack-agnostic and trace every section back to the project brief.

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- Any later project-pipeline artifacts that already exist, if revising, so contradictions can be detected
- [references/phase-template.md](references/phase-template.md)
- [../shared/references/ui-ux-quality-bar.md](../shared/references/ui-ux-quality-bar.md) when the project includes user-facing UI

## Workflow

1. Confirm the request is for a greenfield project. Refuse existing-repo rescue or modernization work.
2. Read the project brief and the phase template before drafting. If the project includes user-facing surfaces, also read the shared UI/UX reference.
3. Create or revise `docs/project-pipeline/01-output-spec.md` using the exact headings from the template.
4. Define behavior and deliverables without choosing frameworks or implementation details. Convert any UI direction from the brief into concrete experience requirements and observable quality expectations.
5. If the brief is insufficient or contradictory, populate `## Upstream Changes Required`, mark the artifact blocked, and stop.
6. If you revise `01-output-spec.md`, assume all downstream artifacts may need revalidation by the orchestrator.

## Completion Behavior

- End the artifact with `## Completion Decision` set to `Done:` or `Blocked:`.
- If blocked by the brief, direct the user to `$project-pipeline-orchestrator`.
- If done, the next baseline skill is `$project-dependency-mapping`.
