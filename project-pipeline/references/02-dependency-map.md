# Stage 02: Dependency Map

## Stage Contract

- Required inputs: `docs/project-pipeline/00-project-brief.md`, `docs/project-pipeline/01-output-spec.md`
- Canonical output: `docs/project-pipeline/02-dependency-map.md`
- Objective: map the concrete components, integrations, runtime boundaries, and trust zones required to satisfy the output spec.
- Validation gate: the artifact uses the exact template headings, stays stack-agnostic, makes deployment and trust boundaries explicit enough for schema and pipeline work, and blocks upstream instead of leaving first-order runtime ambiguity unresolved.

## Workflow

1. Confirm the request remains inside the greenfield baseline workflow.
2. Validate that `00-project-brief.md` and `01-output-spec.md` exist, match the current request, and are usable for this stage. If either is missing, stale, or contradictory, stop and return to the pipeline contract's resume algorithm.
3. Read `00-project-brief.md`, `01-output-spec.md`, this phase reference, `product-quality-gates.md`, `implementation-readiness-quality-bar.md`, and `stage-review-checklists.md` before drafting. If the project includes backend, API, persistence, SQL, workers, integrations, service contracts, or frontend-backend interaction, also read `backend-api-data-quality-gate.md`. If the project includes user-facing surfaces, also read `ui-ux-quality-bar.md`.
4. Create or revise `docs/project-pipeline/02-dependency-map.md` using the exact headings below.
5. Model internal components, external systems, deployment and trust boundaries, operational dependencies, and major coupling risks. For backend projects, include API/service layer, persistence, queues or workers, caches, secrets, auth providers, third-party services, telemetry, migration path, and runtime ownership. For UI-heavy projects, include the client runtime, design system, asset delivery, search, telemetry, or other experience-critical dependencies needed to satisfy the output spec.
6. Make runtime boundaries, secret and auth boundaries, network paths, and blast-radius-sensitive dependencies explicit enough to drive later schema, pipeline, and rollout planning.
7. If `00` or `01` is insufficient, contradictory, or too vague to establish a concrete runtime view, populate `## Upstream Changes Required`, mark the artifact blocked, and stop instead of patching around missing inputs.
8. Before marking the stage done, validate the artifact against the review rubric, product quality gates, applicable backend/API/data quality gate, and stage review checklist. Confirm `03-schema-data-model.md` can be produced without inventing first-order component, integration, runtime, persistence, worker, UX-delivery, or trust-boundary assumptions.

## Required Sections

Use these exact headings:

```md
# Dependency Map
## System Components
## External Systems and Integrations
## Dependency Graph
## Deployment and Trust Boundaries
## Coupling and Risk Notes
## Operational Dependencies
## Open Questions
## Upstream Changes Required
## Completion Decision
```

Write `None` in `## Upstream Changes Required` when `00` and `01` are sufficient. Otherwise list the earliest upstream artifact that must change before this file can be marked done.

Use `Done: ready for $project-schema-data-model` or `Blocked: <reason>` in `## Completion Decision`.

## Review Rubric

- System components cover the core solution surface implied by the output spec.
- System components include user-facing surfaces and performance-critical delivery pieces when relevant.
- Backend components include API or service layer, persistence, queues or workers, caches, auth, secrets, third-party integrations, telemetry, and migration/support surfaces when relevant.
- External systems and integrations are explicit.
- The dependency graph shows critical relationships and sequencing.
- Deployment and trust boundaries identify runtime nodes, network or transport paths, auth or secret boundaries, and blast-radius-sensitive edges at a planning level.
- Coupling and risk notes surface fragile boundaries and likely bottlenecks.
- Operational dependencies identify deployment, runtime, or support needs at a planning level.
- The artifact stays stack-agnostic.

## Handoff Checklist

- Read `00-project-brief.md` and `01-output-spec.md` before drafting.
- Model only the dependencies needed to satisfy the output spec, including experience-critical delivery dependencies for UI-heavy projects.
- Make runtime topology, trust zones, and external dependency boundaries explicit enough to support later security, recovery, and rollout planning.
- Include dependencies that protect baseline product quality, such as design system, search/indexing, telemetry, asset delivery, notifications, content pipeline, evaluation data, or operator tooling when relevant.
- For backend systems, make trust boundaries explicit between client, API/service layer, workers, storage, external services, operators, and observability systems.
- Identify unknown integrations in `## Open Questions`.
- If deployment or trust boundaries remain too vague to drive later phases, block and point to the earliest upstream artifact that must change.
- Ensure no placeholder text remains.

## Evaluation Gate

This stage is usable only when all of the following are true:

- The exact required headings are present.
- The artifact stays stack-agnostic and has no placeholder text.
- Component boundaries, external integrations, deployment paths, and trust boundaries are concrete enough to drive `03-schema-data-model.md` without inventing first-order runtime assumptions.
- Experience-critical and operations-critical dependencies are represented when they are needed to satisfy the output spec.
- Applicable backend/API/data dependencies cover persistence, async processing, cache, auth, secrets, integrations, migrations, observability, and runtime ownership.
- First-order blockers are escalated through `## Upstream Changes Required` instead of being left implicit.
- `## Completion Decision` uses `Done: ready for $project-schema-data-model` or `Blocked: <reason>`.
