# Project Output Spec Template

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`

## Canonical Output

- `docs/project-pipeline/01-output-spec.md`

## Stage Objective

Translate `00-project-brief.md` into a stack-agnostic output contract that is concrete enough for dependency mapping and later downstream design.

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

Use `## Interaction Contracts` to define the main product or service interactions in concrete terms without choosing a framework. Specify actors, primary operations, request and response behavior, identifiers, filter or selection semantics, pagination or continuation rules, sync versus async behavior, and error classes. For protocol-based systems such as MCP or APIs, make the exposed capabilities and response semantics explicit enough to drive downstream schema and test design.

Use `## Nonfunctional Requirements` for measurable expectations such as latency, freshness, throughput, concurrency, package size, data correctness, availability, recovery targets, scale assumptions, auditability, and cost or budget guardrails.

Use `## Security and Access Expectations` to define caller identity assumptions, authorization boundaries, content sensitivity, audit requirements, secret-handling expectations, and any trust-boundary constraints that downstream phases must preserve.

Use `Done: ready for $project-dependency-mapping` or `Blocked: <reason>` in `## Completion Decision`.

## Review Rubric

- The problem statement matches the project brief.
- Target users and operators are explicit and distinct.
- Core use cases describe user outcomes rather than implementation mechanics.
- Primary outputs are concrete enough to evaluate later.
- Interaction contracts are concrete enough to derive downstream interfaces and tests.
- Experience requirements are concrete, observable, and consistent with the brief.
- Nonfunctional requirements are measurable and relevant to the project's quality priorities.
- Security and access expectations are explicit enough to shape architecture and data flow.
- Acceptance criteria are testable.
- Non-goals prevent scope creep.
- The artifact stays stack-agnostic.

## Handoff Checklist

- Read the latest `00-project-brief.md` before drafting.
- Carry any explicit experience direction into `## Experience Requirements` instead of leaving it implicit.
- Carry stakeholder, ownership, and quality-priority signals from the brief into contracts and quality expectations instead of leaving them as future decisions.
- Preserve existing intent unless the brief changed.
- Call out unresolved questions instead of filling gaps with framework assumptions.
- If core interaction, quality, or security expectations remain too vague to drive later phases, block and point back to `00-project-brief.md`.
- If blocked, point back to `00-project-brief.md`.
- If done, ensure no placeholder text remains.

## Evaluation Gate

This stage is usable only when all of the following are true:

- The exact required headings are present.
- The artifact stays stack-agnostic and has no placeholder text.
- `## Interaction Contracts`, `## Experience Requirements`, `## Nonfunctional Requirements`, and `## Security and Access Expectations` are concrete enough to drive `02-dependency-map.md` without inventing first-order assumptions.
- First-order blockers are escalated through `## Upstream Changes Required` instead of being left implicit.
- `## Completion Decision` uses `Done: ready for $project-dependency-mapping` or `Blocked: <reason>`.
