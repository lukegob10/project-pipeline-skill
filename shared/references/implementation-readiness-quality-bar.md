# Implementation-Ready Planning Quality Bar

Use this reference for every project-pipeline phase. The goal is not just a coherent architecture note set. The baseline `00` through `05` artifacts must be concrete enough that an engineer can begin detailed coding without reopening first-order questions about scope, contracts, security, deployment, or delivery sequencing.

## Core Principle

Stack-agnostic does not mean vague. Avoid naming frameworks or vendors unless the user already constrained them, but still force concrete behavior, interfaces, budgets, runtime boundaries, and delivery gates.

## External Baselines

This quality bar aligns the planning workflow with high-signal architecture and operations guidance:

- arc42: architecture documentation should cover context, building blocks, runtime behavior, deployment, cross-cutting concerns, quality goals, and architectural decisions.
- MCP specification: protocol-based projects need explicit capability, transport, authorization, lifecycle, request and response, and error semantics.
- Google SRE: service planning should define measurable service expectations, readiness criteria, and observability that maps to those expectations.
- AWS Well-Architected: plans should make security, operational excellence, reliability, and recovery first-class concerns rather than late hardening work.

## What "Implementation-Ready" Means By Phase 05

By the end of `05-implementation-plan.md`, all of the following should be true unless the user explicitly asked for a looser artifact:

- The functional scope is closed enough to implement an MVP without inventing behavior mid-build.
- The main interaction contracts are explicit enough to derive concrete schemas, handlers, and tests.
- The top nonfunctional requirements are measurable, not qualitative placeholders.
- Security and access expectations are clear enough to shape interfaces and data flow.
- Runtime topology, trust boundaries, and operational dependencies are explicit enough to plan deployment and failure handling.
- Data lifecycle rules cover versioning, retention, deletion, replay or rebuild, and compatibility where relevant.
- Recovery, rollback, migration, and change-management expectations are planned before implementation starts.
- The implementation plan decomposes work enough to assign tasks and define milestone exit criteria.

## First-Order Questions That Must Not Stay Implicit

- Product or service contract:
  exact operations, actors, payload shapes, identifiers, filters, pagination or continuation semantics, sync versus async behavior, error categories, and response completeness rules.
- Protocol details for API, MCP, or other integration surfaces:
  tool versus resource behavior when relevant, transport assumptions, capability boundaries, auth flow, versioning, rate or budget limits, and retry or idempotency expectations.
- Quality targets:
  latency, freshness, throughput, concurrency, correctness, package size, scale assumptions, availability or recovery expectations, and auditability.
- Security and access:
  caller identity model, authorization point, trust boundaries, data sensitivity, secret flow, audit requirements, and least-privilege expectations.
- Runtime and deployment:
  execution units, stateful versus stateless boundaries, background jobs, storage boundaries, network paths, blast radius, backup and restore expectations, and rollout model.
- Delivery readiness:
  milestone entry and exit criteria, dependencies, evaluation datasets or scenarios when retrieval or ML is involved, rollout and rollback approach, and operational ownership.

## Phase-Specific Expectations

- `00-project-brief.md`
  capture stakeholders or owners and explicit quality attribute priorities, not just the idea and audience.
- `01-output-spec.md`
  define interaction contracts, nonfunctional requirements, and security or access expectations in addition to use cases and outputs.
- `02-dependency-map.md`
  include deployment and trust boundaries, not just logical components.
- `03-schema-data-model.md`
  define interface-relevant schemas, invariants, and data lifecycle or retention rules.
- `04-pipeline-design.md`
  include runtime topology, operational flows, recovery paths, and observability points that map to the chosen quality targets.
- `05-implementation-plan.md`
  close or explicitly gate major architectural decisions, define milestone exit criteria, and decompose work to a task-ready level with validation and rollout plans.
- `06-enhancement-roadmap.md`
  keep enhancements separate from baseline obligations; do not move required reliability, security, or delivery readiness work out of the baseline.

## Blocking Guidance

- If a missing decision prevents the next phase from being concrete, do not bury it in `## Open Questions`.
- Put the issue in `## Upstream Changes Required`.
- Mark the artifact `Blocked:` and stop forward progress.
- By `05`, `## Open Questions` should contain only non-blocking or follow-on items.
