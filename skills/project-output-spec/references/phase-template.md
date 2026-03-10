# Project Output Spec Template

## Required Inputs

- `docs/project-pipeline/00-project-brief.md`

## Canonical Output

- `docs/project-pipeline/01-output-spec.md`

## Required Sections

Use these exact headings:

```md
# Output Spec
## Problem Statement
## Target Users and Operators
## Core Use Cases
## Primary Outputs
## Acceptance Criteria
## Non-Goals
## Open Questions
## Upstream Changes Required
## Completion Decision
```

Write `None` in `## Upstream Changes Required` when the project brief is sufficient. Otherwise list the earliest upstream artifact that must change before this file can be marked done.

Use `Done: ready for $project-dependency-mapping` or `Blocked: <reason>` in `## Completion Decision`.

## Review Rubric

- The problem statement matches the project brief.
- Target users and operators are explicit and distinct.
- Core use cases describe user outcomes rather than implementation mechanics.
- Primary outputs are concrete enough to evaluate later.
- Acceptance criteria are testable.
- Non-goals prevent scope creep.
- The artifact stays stack-agnostic.

## Handoff Checklist

- Read the latest `00-project-brief.md` before drafting.
- Preserve existing intent unless the brief changed.
- Call out unresolved questions instead of filling gaps with framework assumptions.
- If blocked, point back to `00-project-brief.md`.
- If done, ensure no placeholder text remains.
