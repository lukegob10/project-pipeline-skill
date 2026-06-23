# Stage 01: Output Spec

## Stage Contract

- Required input: `docs/project-pipeline/00-project-brief.md`
- Canonical output: `docs/project-pipeline/01-output-spec.md`
- Objective: translate the approved project brief into a concrete product, interaction, quality, and access contract for downstream design.
- Validation gate: the artifact uses the exact template headings, stays stack-agnostic, makes interaction, experience, nonfunctional, and security expectations concrete enough for dependency mapping, and blocks upstream instead of leaving first-order ambiguity unresolved.

## Workflow

1. Confirm the request remains inside the greenfield baseline workflow.
2. Validate that `00-project-brief.md` exists, matches the current request, and is usable for this stage. If it is missing, stale, or contradictory, stop and return to the pipeline contract's resume algorithm.
3. Read the project brief, this phase reference, `product-quality-gates.md`, `implementation-readiness-quality-bar.md`, and `stage-review-checklists.md` before drafting. If the project includes backend, API, persistence, SQL, workers, integrations, service contracts, or frontend-backend interaction, also read `backend-api-data-quality-gate.md`. If the project includes user-facing surfaces, also read `ui-ux-quality-bar.md`.
4. Create or revise `docs/project-pipeline/01-output-spec.md` using the exact headings below.
5. Define behavior and deliverables without choosing frameworks or implementation details. Convert any UI direction from the brief into concrete experience requirements and observable quality expectations.
6. Make interaction contracts, nonfunctional requirements, and security or access expectations concrete enough to drive downstream architecture. For backend/API/service projects, require explicit operations, request and response semantics, error behavior, auth expectations, continuation or pagination rules, filtering/sorting semantics, idempotency, versioning, compatibility, rate limits, and budget or size limits at a planning level.
7. If the brief is insufficient, contradictory, or too vague to support implementation-ready downstream design, populate `## Upstream Changes Required`, mark the artifact blocked, and stop instead of guessing or skipping ahead.
8. Before marking the stage done, validate the artifact against the review rubric, product quality gates, applicable backend/API/data quality gate, and stage review checklist. Confirm `02-dependency-map.md` can be produced without inventing first-order product, UX, backend/API/data contract, quality, or security assumptions.

## Required Sections

Use these exact headings:

```md
# Output Spec
## Problem Statement
## Target Users and Operators
## Core Use Cases
## Primary Outputs
## Interaction Contracts
## Experience Requirements
## Nonfunctional Requirements
## Security and Access Expectations
## Acceptance Criteria
## Non-Goals
## Open Questions
## Upstream Changes Required
## Completion Decision
```

Write `None` in `## Upstream Changes Required` when the project brief is sufficient. Otherwise list the earliest upstream artifact that must change before this file can be marked done.

Use `## Experience Requirements` to translate any briefed UI or UX direction into concrete expectations for information density, hierarchy, navigation model, responsive behavior, accessibility, state feedback, and performance. If the project has no user-facing surface, write `Not applicable`.

Use `## Interaction Contracts` to define the main product or service interactions in concrete terms without choosing a framework. Specify actors, primary operations, request and response behavior, identifiers, filter or selection semantics, pagination or continuation rules, sync versus async behavior, error classes, idempotency, compatibility, and versioning expectations. For protocol-based systems such as MCP or APIs, make the exposed capabilities and response semantics explicit enough to drive downstream schema and test design.

Use `## Nonfunctional Requirements` for measurable expectations such as latency, freshness, throughput, concurrency, package size, data correctness, availability, recovery targets, scale assumptions, auditability, and cost or budget guardrails.

Use `## Security and Access Expectations` to define caller identity assumptions, authorization boundaries, content sensitivity, audit requirements, secret-handling expectations, and any trust-boundary constraints that downstream phases must preserve.

Use `Done: ready for $project-dependency-mapping` or `Blocked: <reason>` in `## Completion Decision`.

## Review Rubric

- The problem statement matches the project brief.
- Target users and operators are explicit and distinct.
- Core use cases describe user outcomes rather than implementation mechanics.
- Primary outputs are concrete enough to evaluate later.
- Interaction contracts are concrete enough to derive downstream interfaces and tests.
- Backend/API/service contracts are explicit when applicable, including operations, request/response semantics, errors, pagination/filtering, auth, idempotency, rate or size limits, and compatibility expectations.
- Experience requirements are concrete, observable, and consistent with the brief.
- Nonfunctional requirements are measurable and relevant to the project's quality priorities.
- Security and access expectations are explicit enough to shape architecture and data flow.
- Acceptance criteria are testable.
- Non-goals prevent scope creep.
- The artifact stays stack-agnostic.

## Handoff Checklist

- Read the latest `00-project-brief.md` before drafting.
- Carry explicit experience direction into `## Experience Requirements` instead of leaving it implicit.
- Carry stakeholder, ownership, and quality-priority signals from the brief into contracts and quality expectations instead of leaving them as future decisions.
- Preserve existing intent unless the brief changed.
- Call out unresolved questions instead of filling gaps with framework assumptions.
- Convert vague requirements such as "good UX", "fast", "secure", "robust", "simple", and "high quality" into observable standards or focused questions.
- Cover happy paths, important alternate paths, edge cases, error states, empty states, permission failures, and acceptance criteria.
- For clients backed by services, define frontend-backend interaction semantics: validation ownership, loading/error/empty states, optimistic or pessimistic updates, cache freshness, retry behavior, and auth/session flow.
- If core interaction, quality, or security expectations remain too vague to drive later phases, block and point back to `00-project-brief.md`.
- Ensure no placeholder text remains.

## Evaluation Gate

This stage is usable only when all of the following are true:

- The exact required headings are present.
- The artifact stays stack-agnostic and has no placeholder text.
- `## Interaction Contracts`, `## Experience Requirements`, `## Nonfunctional Requirements`, and `## Security and Access Expectations` are concrete enough to drive `02-dependency-map.md` without inventing first-order assumptions.
- Applicable backend/API/data requirements are concrete enough to drive component, persistence, trust-boundary, and service-contract planning.
- Core workflows, outputs, edge cases, error states, and acceptance criteria are testable.
- First-order blockers are escalated through `## Upstream Changes Required` instead of being left implicit.
- `## Completion Decision` uses `Done: ready for $project-dependency-mapping` or `Blocked: <reason>`.
