# UI / UX Quality Bar

Use this reference when the project includes a product UI, admin UI, dashboard, documentation site, marketing site, or any other user-facing surface. Apply only the parts that fit the surface.

## Primary Reference Models

- Product and system UI: Linear
- Documentation, information-heavy, and marketing clarity: Stripe Docs
- Structured information presentation: Airtable as a secondary reference

## Experience Goals

- Crisp
- Dense without clutter
- Clean
- Intuitive
- Purpose-built
- High-signal
- Uncluttered

Favor strong structure, tight spacing, clear hierarchy, and fast scanning. Fill space with useful information and controls instead of decorative emptiness.

## Required Experience Decisions

For user-facing projects, capture these decisions in the brief and carry them through later stages:

- Surface type: product app, admin tool, dashboard, workflow tool, documentation, marketing site, or hybrid.
- Primary navigation model: sidebar, top nav, tabs, command palette, list-detail, wizard, canvas, search-first, or another explicit model.
- Information density: compact operational, balanced product, editorial, or intentionally sparse.
- Hierarchy: what must be visible above the fold, what can be progressively disclosed, and what should never compete visually.
- State model: loading, empty, partial, success, validation error, permission denied, upstream failure, offline or degraded, and completion states.
- Responsiveness: desktop, tablet, mobile, keyboard, screen reader, and reduced-motion expectations where relevant.
- Visual constraints: palette direction, contrast, typography tone, icon use, imagery needs, and brand constraints.
- Performance expectations: first paint, interaction latency, filtering/search responsiveness, bundle weight, and layout stability where relevant.

## Positive Patterns

- Compact but readable layouts
- Clear hierarchy and obvious next actions
- Strong list, detail, sidebar, and command-oriented workflows where they fit
- Clean lines driven by alignment, typography, spacing, and layout
- Progressive disclosure for advanced power without a noisy default state
- Responsive layouts that stay useful on desktop and coherent on mobile
- Motion only when it improves orientation or feedback
- Stable dimensions for fixed-format controls, grids, boards, tables, and toolbars so labels, loading states, and dynamic content do not shift layout.
- Clear affordances for destructive actions, bulk actions, filters, sorting, undo, and recovery where the workflow needs them.

## Anti-Patterns

- Oversized cards
- Excessive padding
- Large empty sections with low information value
- Generic SaaS dashboard aesthetics
- Loose or under-resolved layouts
- Decoration that weakens hierarchy
- Trend-driven choices with no usability benefit
- Muted tan, beige, parchment, or "old newspaper" palettes unless explicitly requested
- Hero or marketing composition for operational tools that need dense scanning and repeated use.
- Ambiguous icons without labels or tooltips when the action is not universally recognizable.
- Text that can overflow buttons, cards, tables, tabs, or mobile containers.
- UI quality requirements that appear only in `06-enhancement-roadmap.md` even though they are necessary for baseline usability.

## Color and Visual Direction

- Use a deliberate, solid palette with strong contrast and one or two clear accent colors.
- Avoid washed-out neutral-heavy palettes that make the interface feel stale.
- Use color to reinforce hierarchy, state, and readability first.
- Default toward crisp neutrals plus a decisive accent, not sepia or tan surfaces.

## Performance and Responsiveness

- Treat perceived speed as a core UX requirement.
- Design for fast first paint, quick feedback, low layout shift, and low input latency.
- Prefer progressive disclosure, incremental loading, meaningful loading states, and optimistic UI where safe.
- Avoid heavy animation, oversized bundles, blocking third-party scripts, and unnecessary client-side work.
- For dense data surfaces, plan pagination, virtualization, and filtering so density does not degrade responsiveness.
- Record measurable performance expectations when the project brief supports them.

## Accessibility and Interaction

- Plan keyboard navigation, focus states, labels, semantic structure, contrast, reduced motion, and screen-reader behavior for baseline workflows.
- Include error recovery, validation messages, save states, undo or confirmation behavior, and clear status feedback.
- For data-heavy tools, plan filtering, sorting, search, pagination or virtualization, saved views, and bulk selection when they are core to the workflow.
- For forms and multi-step flows, plan field grouping, progressive disclosure, autosave or draft behavior, and clear completion states.
- For mobile, preserve task completion rather than only making the layout shrink.

## Planning Expectations

- Put the experience bar into the project brief and output spec, not only in open questions.
- Translate UX goals into observable behaviors and acceptance criteria.
- Carry frontend performance and responsiveness concerns into dependency mapping, pipeline design, and implementation planning.
- Keep baseline quality requirements separate from post-baseline polish ideas.
- In `02-dependency-map.md`, include experience-critical dependencies such as design system, asset delivery, search/indexing, telemetry, content pipeline, and client runtime boundaries when relevant.
- In `04-pipeline-design.md`, describe user-visible feedback loops for loading, errors, partial results, retries, optimistic actions, and stale data.
- In `05-implementation-plan.md`, schedule UX review, accessibility validation, responsive QA, state coverage, and frontend performance checks as baseline work.
