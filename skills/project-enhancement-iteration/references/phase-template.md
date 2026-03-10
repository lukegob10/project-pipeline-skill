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

- Baseline preconditions accurately summarize what must already be true.
- Enhancement themes extend the baseline instead of redefining it.
- The prioritized roadmap orders work by value, dependency, or risk.
- Complexity increments describe how the system grows over time.
- Dependencies and preconditions call out what must exist before each enhancement.
- Risk and impact explain cost, complexity, or operational effects.

## Handoff Checklist

- Read `00` through `05` before drafting.
- Keep the roadmap optional and post-baseline.
- Use `## Open Questions` for unresolved prioritization or sequencing choices.
- If blocked, point to the earliest upstream artifact that must change.
- If done, ensure no placeholder text remains.
