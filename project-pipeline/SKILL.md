---
name: project-pipeline
description: Run the full greenfield project planning pipeline as one skill. Use when Codex needs to turn a new project idea into implementation-ready planning artifacts, create or refresh `docs/project-pipeline/00-project-brief.md`, resume from partial project-pipeline artifacts, regenerate stale stages, produce stages `01` through `05`, or optionally create `06-enhancement-roadmap.md` after the baseline is complete. Use for greenfield planning only; do not use for existing-repo rescue, modernization, refactor-only work, or implementation/scaffolding.
---

# Project Pipeline

## Core Role

Act as the single project-level planning pipeline for greenfield software projects. Infer the real objective, create or refresh the project brief, produce dependency-ordered planning artifacts, validate each stage before advancing, and preserve end-to-end coherence across the complete baseline.

Keep the workflow planning-first and stack-agnostic. Do not scaffold code, choose frameworks, or generate implementation files as part of this skill.

## Required References

Read these references when they are relevant to the next action:

- [references/pipeline-contract.md](references/pipeline-contract.md) before deciding the next stage, resuming, validating completion, or handling staleness.
- [references/intake-and-clarification.md](references/intake-and-clarification.md) before creating or refreshing `00-project-brief.md`, especially for long, informal, spoken, or contradictory prompts.
- [references/product-quality-gates.md](references/product-quality-gates.md) before drafting or validating any artifact that defines product behavior, user workflows, acceptance criteria, edge cases, or quality targets.
- [references/backend-api-data-quality-gate.md](references/backend-api-data-quality-gate.md) when the project includes a backend, API, persistence layer, SQL database, worker, queue, integration service, service-to-service contract, or frontend-backend interaction.
- [references/implementation-readiness-quality-bar.md](references/implementation-readiness-quality-bar.md) before drafting or validating any stage.
- [references/stage-review-checklists.md](references/stage-review-checklists.md) before marking any stage done and again after `05-implementation-plan.md`.
- [references/ui-ux-quality-bar.md](references/ui-ux-quality-bar.md) when the project includes a product UI, admin UI, dashboard, documentation site, marketing site, or any other user-facing surface.
- [references/01-output-spec.md](references/01-output-spec.md) when producing `01-output-spec.md`.
- [references/02-dependency-map.md](references/02-dependency-map.md) when producing `02-dependency-map.md`.
- [references/03-schema-data-model.md](references/03-schema-data-model.md) when producing `03-schema-data-model.md`.
- [references/04-pipeline-design.md](references/04-pipeline-design.md) when producing `04-pipeline-design.md`.
- [references/05-implementation-plan.md](references/05-implementation-plan.md) when producing `05-implementation-plan.md`.
- [references/06-enhancement-roadmap.md](references/06-enhancement-roadmap.md) only after `05-implementation-plan.md` is complete and the user asks for optional post-baseline enhancement planning.

## Operating Procedure

1. Confirm the request is for greenfield project planning. Reject existing-repo rescue, modernization, refactor-only, and implementation-only requests as out of scope.
2. Read the latest user request and run intake normalization before writing or refreshing `00-project-brief.md`: extract the real objective, target users, workflows, constraints, quality priorities, UX direction, risks, explicit facts, contradictions, and unknowns.
3. Determine whether backend/API/data quality gates are applicable. Treat them as applicable when the project includes backend services, APIs, persistence, SQL, workers, queues, integrations, service contracts, or frontend-backend interaction. Treat them as not applicable only when the project is clearly local/static/no-backend and record why.
4. Ask focused clarifying questions before generating specs when missing or contradictory details materially affect product behavior, UI model, backend/API/data contract, data sensitivity, authentication or authorization, deployment boundaries, integration scope, MVP cutline, or acceptance criteria. Do not ask about details that can be safely inferred and recorded as non-blocking assumptions.
5. Inspect `docs/project-pipeline/` if it exists. Compare existing artifacts to the latest request and the pipeline contract.
6. Create or refresh `docs/project-pipeline/00-project-brief.md` when it is missing, incomplete, or contradicted by the current request. Record confirmed choices and explicit assumptions in the brief.
7. Determine the earliest missing, incomplete, blocked, or stale stage using the pipeline contract.
8. For multi-stage or materially complex work, present a concise stage plan before major execution using the contract's stage planning format.
9. Produce the next required artifact using its phase reference. Run stages in order from `01` through `05`; use `06` only for optional post-baseline enhancement planning after `05` is complete.
10. Validate every artifact against its exact headings, completion phrase, stage objective, staleness rules, product quality gates, applicable backend/API/data gates, implementation-readiness quality bar, and stage review checklist before advancing.
11. If a stage is unusable, diagnose whether the failure is bad input, wrong stage choice, bad sequencing, insufficient validation, or conflicting requirements. Retry, restart from the earliest affected stage, or surface a clear blocker.
12. If an artifact lists upstream changes required, stop forward progress and regenerate from the earliest affected upstream artifact.

## Artifact Discipline

- Store every planning artifact in `docs/project-pipeline/`.
- Preserve the canonical stage order and filenames from the pipeline contract.
- Use exact headings from each phase reference.
- End every stage artifact with `## Completion Decision` using that phase's exact `Done:` phrase or `Blocked: <reason>`.
- Use `## Open Questions` only for non-blocking questions. Put first-order product, contract, security, runtime, delivery, or evaluation blockers in `## Upstream Changes Required` and mark the stage blocked.
- Treat vague requirements such as "good UX", "fast", "secure", "robust", "simple", or "high quality" as inputs that must become observable standards, measurable targets, or explicit questions before downstream stages rely on them.
- For applicable backend/API/data projects, make service contracts, data contracts, frontend-backend behavior, auth, performance, reliability, observability, migrations, and operational readiness explicit before marking the baseline complete.
- Mark downstream artifacts stale when an upstream artifact changes materially.
- By the end of `05`, ensure the baseline includes concrete interaction contracts, measurable nonfunctional expectations, deployment and trust boundaries, data lifecycle rules, recovery and rollout expectations, and task-ready milestone decomposition.

## Completion Behavior

Stop when the next stage needs user input, when a stage returns `Blocked:`, or when the requested scope is complete. Final delivery must synthesize the pipeline status rather than returning isolated stage fragments. Include completed artifacts, blocked or failed work, key assumptions, validation status, and remaining risks or gaps.

If the user asks for a net-new feature after `05` is complete, stop and tell them this skill does not include feature-delta planning; keep feature-delta planning separate from baseline refresh and optional enhancement roadmap work.
