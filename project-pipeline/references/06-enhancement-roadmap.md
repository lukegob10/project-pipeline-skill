# Stage 06: Enhancement Roadmap

## Stage Contract

- Required inputs: `docs/project-pipeline/00-project-brief.md`, `docs/project-pipeline/01-output-spec.md`, `docs/project-pipeline/02-dependency-map.md`, `docs/project-pipeline/03-schema-data-model.md`, `docs/project-pipeline/04-pipeline-design.md`, `docs/project-pipeline/05-implementation-plan.md`
- Canonical output: `docs/project-pipeline/06-enhancement-roadmap.md`
- Objective: plan optional post-baseline enhancements without moving required baseline work out of stages `00` through `05`.
- Validation gate: the artifact uses the exact template headings, stays stack-agnostic, preserves the completed baseline as the prerequisite, and blocks upstream instead of treating deferred baseline work as enhancement scope.

## Workflow

1. Confirm that `05-implementation-plan.md` exists, matches the current request, and is complete before doing any enhancement planning. If the baseline is missing, stale, or blocked, stop and return to the pipeline contract's resume algorithm.
2. Confirm the request is optional enhancement, polish, prioritization, or iteration work rather than a net-new feature delta. If it is a new feature request, stop and tell the user this skill does not include net-new feature-delta planning.
3. Read `00` through `05`, this phase reference, `product-quality-gates.md`, `implementation-readiness-quality-bar.md`, and `stage-review-checklists.md` before drafting. If the project includes user-facing surfaces, also read `ui-ux-quality-bar.md`.
4. Create or revise `docs/project-pipeline/06-enhancement-roadmap.md` using the exact headings below.
5. Organize enhancements as post-baseline increments rather than changes to the baseline definition. For UI-heavy projects, treat higher-order polish, richer workflows, and deeper performance optimization as enhancement themes only after the baseline quality bar is already covered upstream.
6. If baseline artifacts still defer required contract, security, reliability, or delivery-readiness work, do not treat that work as an enhancement. Push the issue upstream and block this stage.
7. If any upstream artifact is insufficient or contradictory, populate `## Upstream Changes Required`, mark the artifact blocked, and stop instead of collapsing baseline fixes into roadmap items.
8. Keep the roadmap stack-agnostic unless the earlier artifacts explicitly constrain technology.
9. Before marking the stage done, validate the artifact against the review rubric, product quality gates, and stage review checklist. Confirm the roadmap remains clearly optional, post-baseline, dependency-aware, and distinct from new feature work.

## Required Sections

Use these exact headings:

```md
# Enhancement Roadmap
## Baseline Preconditions
## Enhancement Themes
## Prioritized Roadmap
## Complexity Increments
## Dependencies and Preconditions
## Risk and Impact
## Open Questions
## Upstream Changes Required
## Completion Decision
```

Write `None` in `## Upstream Changes Required` when `00` through `05` are sufficient. Otherwise list the earliest upstream artifact that must change before this file can be marked done.

Use `Done: enhancement roadmap ready` or `Blocked: <reason>` in `## Completion Decision`.

## Review Rubric

- Baseline preconditions accurately summarize what must already be true and confirm that required baseline reliability, security, and delivery-readiness work was not deferred improperly.
- Enhancement themes extend the baseline instead of redefining it.
- The prioritized roadmap orders work by value, dependency, or risk.
- Complexity increments describe how the system grows over time.
- Dependencies and preconditions call out what must exist before each enhancement.
- Risk and impact accounts for experience polish and performance work without treating baseline UX quality as optional.
- Risk and impact explain cost, complexity, operational effects, and user-facing tradeoffs.

## Handoff Checklist

- Read `00` through `05` before drafting.
- Keep the roadmap optional and post-baseline.
- If the request is a net-new feature delta rather than optional enhancement or polish work, stop and route it to a separate feature-planning workflow instead of forcing it into this roadmap.
- For UI-heavy projects, keep baseline quality work in `05` and reserve this roadmap for follow-on polish, advanced interactions, and deeper optimization.
- Do not move required contract closure, security hardening, recovery readiness, or rollout safety work out of the baseline just to make `05` look smaller.
- Do not move required UX usability, accessibility, performance, error-state coverage, or operator readiness work out of the baseline.
- Use `## Open Questions` for unresolved prioritization or sequencing choices.
- Ensure no placeholder text remains.

## Evaluation Gate

This stage is usable only when all of the following are true:

- The exact required headings are present.
- The artifact stays stack-agnostic and has no placeholder text.
- `## Baseline Preconditions` clearly shows that baseline readiness was achieved before enhancement planning.
- Enhancement items remain optional, post-baseline, and dependency-aware instead of carrying deferred baseline work.
- Enhancement items do not introduce net-new feature planning that belongs in a separate feature-planning workflow.
- `## Completion Decision` uses `Done: enhancement roadmap ready` or `Blocked: <reason>`.
