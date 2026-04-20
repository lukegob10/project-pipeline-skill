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

## Positive Patterns

- Compact but readable layouts
- Clear hierarchy and obvious next actions
- Strong list, detail, sidebar, and command-oriented workflows where they fit
- Clean lines driven by alignment, typography, spacing, and layout
- Progressive disclosure for advanced power without a noisy default state
- Responsive layouts that stay useful on desktop and coherent on mobile
- Motion only when it improves orientation or feedback

## Anti-Patterns

- Oversized cards
- Excessive padding
- Large empty sections with low information value
- Generic SaaS dashboard aesthetics
- Loose or under-resolved layouts
- Decoration that weakens hierarchy
- Trend-driven choices with no usability benefit
- Muted tan, beige, parchment, or "old newspaper" palettes unless explicitly requested

## Color and Visual Direction

- Use a deliberate, solid palette with strong contrast and one or two clear accent colors
- Avoid washed-out neutral-heavy palettes that make the interface feel stale
- Use color to reinforce hierarchy, state, and readability first
- Default toward crisp neutrals plus a decisive accent, not sepia or tan surfaces

## Performance and Responsiveness

- Treat perceived speed as a core UX requirement
- Design for fast first paint, quick feedback, low layout shift, and low input latency
- Prefer progressive disclosure, incremental loading, meaningful loading states, and optimistic UI where safe
- Avoid heavy animation, oversized bundles, blocking third-party scripts, and unnecessary client-side work
- For dense data surfaces, plan pagination, virtualization, and filtering so density does not degrade responsiveness
- Record measurable performance expectations when the project brief supports them

## Planning Expectations

When turning this direction into project artifacts:

- Put the experience bar into the project brief and output spec, not only in open questions
- Translate UX goals into observable behaviors and acceptance criteria
- Carry frontend performance and responsiveness concerns into dependency mapping, pipeline design, and implementation planning
- Keep baseline quality requirements separate from post-baseline polish ideas
