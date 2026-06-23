# Intake and Clarification

Use this reference before creating or refreshing `docs/project-pipeline/00-project-brief.md`, especially when the user gives a long, informal, spoken, or mixed-priority prompt.

## Intake Objective

Convert the user's raw prompt into a stable planning baseline before downstream artifacts are written. The output of intake is not a separate canonical file; it becomes the content and assumptions of `00-project-brief.md`.

## Normalize the Prompt

Extract these signals before asking questions or drafting:

- Project idea and desired outcome
- Target users, operators, buyers, reviewers, and affected stakeholders
- Primary workflows and jobs to be done
- Expected outputs, decisions, reports, automations, or user-facing surfaces
- Current constraints, deadlines, tools, integrations, compliance needs, and budget or scale hints
- UX direction, information density, navigation model, visual constraints, accessibility needs, and performance expectations
- Data sensitivity, authentication, authorization, audit, retention, and trust-boundary hints
- Success criteria, acceptance expectations, quality priorities, and explicit non-goals
- Risks, contradictions, speculative ideas, and open choices

Separate confirmed facts from inferred assumptions. Record assumptions only when they are safe, local, and non-blocking.

## Ask Before Spec Generation

Ask focused clarifying questions before generating downstream specs when a missing or contradictory detail would materially affect:

- Product behavior, primary workflows, or acceptance criteria
- User roles, permissions, data visibility, or approval paths
- Data sensitivity, retention, auditability, or regulatory posture
- Authentication, authorization, secret handling, or trust boundaries
- Core integration scope, external systems, or transport assumptions
- UI model, navigation, density, content hierarchy, accessibility, or responsive behavior
- MVP cutline, rollout approach, operational ownership, or success metrics

Do not ask about details that can be safely inferred from the prompt and later changed without invalidating the architecture. Instead, record the inference in `## Explicit Assumptions`.

## Question Quality

Prefer short, grouped questions that close high-impact ambiguity. Each question must change the project brief, downstream contracts, UX model, security model, or delivery plan.

Avoid broad questions such as "What else should I know?" Replace them with concrete choices or missing facts, for example:

- "Who can view or change this data: only the creator, team admins, or all workspace members?"
- "Is the first version a private operator tool, a customer-facing app, or both?"
- "Should the MVP optimize for correctness and auditability over speed of delivery?"

## Contradiction Handling

Block intake and ask before drafting when the prompt contains contradictions such as:

- Different target users with incompatible workflows
- A request for no-login access and private or sensitive user data
- A "simple MVP" that also requires enterprise-grade workflow breadth
- A visual direction that conflicts with stated density, accessibility, or performance goals
- A fixed deadline that conflicts with required reliability, security, or compliance scope

When blocking, name the contradiction and ask only for the decision needed to unblock the brief.

## Brief Readiness Gate

Do not mark `00-project-brief.md` ready for stage `01` until:

- The desired outcome and primary users are clear.
- MVP scope and non-goals are explicit enough to prevent scope drift.
- User-facing experience direction is either concrete or explicitly not applicable.
- Security, access, and data sensitivity are sufficiently understood for output specification.
- Quality priorities are ranked or at least explicitly stated.
- Assumptions are documented and do not hide first-order product, UX, security, or delivery decisions.
