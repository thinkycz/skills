---
name: spec-driven-development
description: Turn a written client specification, design input such as Figma or Google Stitch, or both into a traceable implementation workflow and delivered code. Use when the agent needs to implement backend/API work, admin panels, frontend screens, or mixed product slices from provided source artifacts while keeping markdown docs under `/docs`, splitting work into visible phases, routing to the right helper skills, and verifying the result against the specification and design before claiming completion.
---

# Spec Driven Development

Drive delivery from client-provided artifacts instead of starting from a blank slate.

Use this skill when the user already has a written specification, design files, or both, and wants implementation with visible progress, structured docs, and strict verification against the source materials.

## Core Promise

- Start from the source artifacts, not guesses.
- Keep progress visible through markdown docs in the project’s `/docs` folder.
- Split large work into small, traceable phases and bite-sized tasks.
- Route implementation to the right existing skills instead of handling every domain the same way.
- Do not claim completion until code, behavior, and design have been verified against the inputs.

## Workflow

### 1. Collect Artifacts And Ground In The Repo

- Ask the user for the written client specification, Figma or Google Stitch links/files, and any API contract or admin requirements that already exist.
- Accept partial inputs and keep moving with what exists.
- Apply `repo-convention-discovery` before locking plans or file structure so the work follows the local repo instead of inventing a new pattern.
- Explore the repo immediately to understand current architecture, conventions, feature boundaries, and likely implementation touchpoints.
- Record missing artifacts explicitly instead of silently filling gaps.

If the user has not provided a source file yet, ask for it directly. Typical asks:

- written client specification path or pasted content
- Figma URL, node link, Stitch project or screen ids, screenshots, or exported design files
- API contract, Swagger/OpenAPI link, backend docs, or admin requirements

### 2. Normalize Sources Before Planning

- Summarize the artifacts into a clear working understanding before implementation begins.
- Treat the written client specification and provided design materials as source inputs that may disagree.
- If the written specification and the design source conflict in a way that changes scope, UX, fields, flows, or acceptance criteria, stop and ask the user which source has priority before planning or implementation continues.
- If the inputs are too ambiguous to implement safely, route to `product-brainstorming` first to clarify the intended behavior.

Read these references when needed:

- [references/source-of-truth-and-conflicts.md](references/source-of-truth-and-conflicts.md)
- [references/docs-layout.md](references/docs-layout.md)

### 3. Create The Traceable Doc Set

Write markdown files under the project’s `/docs` folder only.

Default structure:

- `/docs/specs/` for normalized source summaries, clarified requirements, and decision records
- `/docs/plans/` for phased implementation plans
- `/docs/progress/` for live phase trackers, blockers, and current status
- `/docs/verification/` for verification evidence, spec/design compliance notes, and final readiness reports

Create a requirement traceability matrix that maps:

- source requirement or design input
- owning phase
- implementing tasks
- blocker or decision state
- verification evidence

Use [references/traceability-and-progress.md](references/traceability-and-progress.md) for the required templates and structure.

### 4. Plan In Small Visible Phases

- Split work into phases that are meaningful to the user and safe to verify.
- Keep phases narrow enough that progress is obvious and blockers are local.
- For each phase, create bite-sized tasks and checklists suitable for execution by a focused agent or subagent.
- Keep plans concrete enough that the next execution slice is obvious, testable, and easy to verify.

Each phase should be traceable from source artifact to implementation outcome. Avoid giant “do everything” phases.

### 5. Route To The Right Helper Skills

Do not treat all implementation work as the same kind of task.

Apply `custom-skill-routing` first to choose the right high-level owner and helper stack for the task.

Use [references/skill-routing.md](references/skill-routing.md) for the spec-driven delivery rules that layer on top of that shared routing.

Default routing:

- Use `figma` when Figma is the design source for frontend screens or components that must match closely.
- Use `google-stitch` when Google Stitch is the design source for frontend screens or components.
- Use `design-to-traversable-app` for multi-screen design-to-app implementation after the source adapter has normalized the input.
- When the target framework is known, read the matching framework reference inside `design-to-traversable-app`, including AdonisJS + Inertia when relevant.
- Use `design-fidelity-polish` when the remaining work is mostly design parity on an existing implementation.
- Use `integrating-backend-api-into-frontend` when frontend work depends on a published or partial backend API.
- Use `product-brainstorming` when the provided materials are too ambiguous or contradictory to implement safely.
- Apply `test-driven-development` during implementation.
- Apply `verification-before-completion` before any claim that something is complete, fixed, passing, or visually matched.

### 6. Execute With Visible Progress

- Keep `/docs/progress/` current as phases move from planned to active to verified.
- Mark blockers explicitly instead of hiding them in prose.
- Apply `docs-driven-execution` when moving from the written plan into active implementation so execution stays synced with the docs.
- If tasks are separable, execute them in clearly bounded slices and keep the docs synchronized after each slice.
- Keep implementation tied back to the traceability matrix so a reader can see what is done, blocked, deferred, or awaiting verification.

### 7. Verify Against The Right Source

Verification is required before any completion claim.

Always verify:

- implementation against the written client specification
- implementation against the design, when a design is part of the input
- test, build, lint, and runtime behavior as appropriate for the touched surfaces
- admin and API behavior against the real contract or backend support when relevant

Do not say work is complete because code was written. Require evidence.

Read [references/verification.md](references/verification.md) for the required verification layers and reporting expectations.

Before a final handoff or “done” claim on broader work, apply `release-readiness`.

## Delivery Rules

- Do not invent missing requirements when the source files are unclear.
- Do not silently choose between conflicting written and visual sources.
- Do not write non-markdown status artifacts outside `/docs`.
- Do not collapse the entire project into one monolithic plan if phases can be separated.
- Do not skip TDD, traceability, or verification because a phase seems small.
- Do not trust agent success reports without independent verification evidence.

## Output Expectations

At the end of a successful run, the project should have:

- a normalized spec summary under `/docs/specs/`
- a phased implementation plan under `/docs/plans/`
- a live progress tracker and requirement matrix under `/docs/progress/`
- verification evidence under `/docs/verification/`
- implementation routed through the right helper skills for the relevant domain
- explicit resolution of any source-of-truth conflicts
