# Project Enhancement Iteration Template

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`
- `docs/project-pipeline/01-output-spec.md`
- `docs/project-pipeline/02-dependency-map.md`
- `docs/project-pipeline/03-schema-data-model.md`
- `docs/project-pipeline/04-pipeline-design.md`
- `docs/project-pipeline/05-implementation-plan.md`

## Canonical Output

- `docs/project-pipeline/06-enhancement-roadmap.md`

## Stage Objective

Translate the completed baseline artifacts into a stack-agnostic, post-baseline enhancement roadmap without moving required baseline work out of stages `00` through `05`.

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
- Use `## Open Questions` for unresolved prioritization or sequencing choices.
- If blocked, point to the earliest upstream artifact that must change.
- If done, ensure no placeholder text remains.

## Evaluation Gate

This stage is usable only when all of the following are true:

- The exact required headings are present.
- The artifact stays stack-agnostic and has no placeholder text.
- `## Baseline Preconditions` clearly shows that baseline readiness was achieved before enhancement planning.
- Enhancement items remain optional, post-baseline, and dependency-aware instead of carrying deferred baseline work.
- Enhancement items do not introduce net-new feature planning that belongs in a separate feature-planning workflow.
- `## Completion Decision` uses `Done: enhancement roadmap ready` or `Blocked: <reason>`.
