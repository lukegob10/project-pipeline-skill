# Stage 03: Schema and Data Model

## Stage Contract

- Required inputs: `docs/project-pipeline/00-project-brief.md`, `docs/project-pipeline/01-output-spec.md`, `docs/project-pipeline/02-dependency-map.md`
- Canonical output: `docs/project-pipeline/03-schema-data-model.md`
- Objective: define the entities, contracts, validation rules, and lifecycle behavior required by the upstream output and dependency decisions.
- Validation gate: the artifact uses the exact template headings, stays stack-agnostic, makes contracts and lifecycle behavior concrete enough for pipeline design, and blocks upstream instead of leaving first-order interface or data ambiguity unresolved.

## Workflow

1. Confirm the request remains inside the greenfield baseline workflow.
2. Validate that `00` through `02` exist, match the current request, and are usable for this stage. If any required input is missing, stale, or contradictory, stop and return to the pipeline contract's resume algorithm.
3. Read `00` through `02`, this phase reference, `product-quality-gates.md`, `implementation-readiness-quality-bar.md`, and `stage-review-checklists.md` before drafting. If the project includes backend, API, persistence, SQL, workers, integrations, service contracts, or frontend-backend interaction, also read `backend-api-data-quality-gate.md`.
4. Create or revise `docs/project-pipeline/03-schema-data-model.md` using the exact headings below.
5. Define entities, fields, contracts, state transitions, validation rules, and data lifecycle behavior at the planning level.
6. For persistence or SQL scope, define keys, relationships, uniqueness, nullability, constraints, indexes, transaction boundaries, concurrency expectations, migration/backfill approach, and retention/deletion behavior at the planning level.
7. Make contracts specific enough to derive later interface schemas, identifiers, filters, payload shapes, compatibility rules, and authorization or provenance fields where relevant.
8. If any upstream artifact is insufficient, contradictory, or too vague to support interface- and lifecycle-ready modeling, populate `## Upstream Changes Required`, mark the artifact blocked, and stop instead of inventing missing contracts.
9. Before marking the stage done, validate the artifact against the review rubric, product quality gates, applicable backend/API/data quality gate, and stage review checklist. Confirm `04-pipeline-design.md` can be produced without inventing first-order schema, SQL/data contract, identifier, lifecycle, authorization, validation, transaction, migration, or interface assumptions.

## Required Sections

Use these exact headings:

```md
# Schema and Data Model
## Core Entities
## Data Structures and Fields
## Contracts and Interfaces
## State Transitions
## Validation Rules
## Data Lifecycle and Retention
## Open Questions
## Upstream Changes Required
## Completion Decision
```

Write `None` in `## Upstream Changes Required` when `00` through `02` are sufficient. Otherwise list the earliest upstream artifact that must change before this file can be marked done.

Use `Done: ready for $project-pipeline-design` or `Blocked: <reason>` in `## Completion Decision`.

## Review Rubric

- Core entities cover the important nouns implied by the output spec and dependency map.
- Data structures and fields are specific enough to guide later design work.
- Contracts and interfaces describe boundaries between components or actors and are concrete enough to derive request, response, event, or resource schemas where relevant.
- Persistence contracts cover keys, relationships, constraints, indexes, transaction/concurrency expectations, and migration/lifecycle behavior when relevant.
- State transitions capture lifecycle changes that matter to the project.
- Validation rules prevent invalid or incomplete data movement.
- Data lifecycle and retention covers versioning, provenance, retention, deletion, rebuild or replay, and compatibility concerns that matter to the project.
- The artifact stays stack-agnostic.

## Handoff Checklist

- Read `00`, `01`, and `02` before drafting.
- Keep schemas aligned with the dependency map rather than inventing new subsystems.
- Make identifier, provenance, authorization, and compatibility fields explicit when they shape interfaces or operational behavior.
- Include data needed for validation, empty states, error recovery, audit, observability, permissions, retention, deletion, rebuild, replay, and evaluation when relevant.
- For SQL-backed projects, make primary keys, foreign keys, unique constraints, check constraints, nullable fields, indexing needs, and transaction boundaries explicit enough for implementation planning.
- Record unknowns in `## Open Questions`.
- If contracts or lifecycle rules remain too vague to drive pipeline and implementation planning, block and point to the earliest upstream artifact that must change.
- Ensure no placeholder text remains.

## Evaluation Gate

This stage is usable only when all of the following are true:

- The exact required headings are present.
- The artifact stays stack-agnostic and has no placeholder text.
- Entities, data structures, contracts, validation rules, and lifecycle behavior are concrete enough to drive `04-pipeline-design.md` without inventing first-order interface or identifier assumptions.
- Data sensitivity, authorization-relevant fields, lifecycle behavior, and recovery or evaluation data needs are explicit when relevant.
- Applicable SQL/data contracts include constraints, indexes, relationships, migrations, seed/backfill needs, retention/deletion, and transaction/concurrency assumptions.
- First-order blockers are escalated through `## Upstream Changes Required` instead of being left implicit.
- `## Completion Decision` uses `Done: ready for $project-pipeline-design` or `Blocked: <reason>`.
