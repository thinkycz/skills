---
name: custom-skill-routing
description: Choose between the custom skills in this workspace and compose them cleanly when a task spans brainstorming, traceable delivery, design implementation, API integration, debugging, or verification. Use when the agent needs to decide which local custom skill or combination of skills should own a task.
---

# Custom Skill Routing

Use the local custom skills as a coordinated system, not as isolated islands.

Apply this skill when a task could reasonably fit more than one custom skill and you need to choose the right owner or handoff path.

## Core Rule

Route by dominant risk first, then layer supporting skills only where they materially help.

Do not invoke multiple high-level skills in parallel just because they all seem relevant.

## Unified Workflow

Prefer this lifecycle when the work spans multiple stages:

1. source or product shaping:
   - `product-brainstorming` for ambiguous product direction
   - `design-to-prd` when the design exists but the written product doc does not
2. delivery specification:
   - `spec-driven-development` when the work is heading toward implementation with traceable docs
3. source normalization:
   - `figma` or `google-stitch`
4. shared implementation flow:
   - `design-to-traversable-app`
5. platform-specific delivery:
   - use the matching framework reference inside `design-to-traversable-app`, including Next.js, Vue.js, Laravel + Inertia, or AdonisJS + Inertia
6. execution and traceability:
   - `traceable-delivery`, `docs-driven-execution`, and `test-driven-development` when behavior is testable
7. polish, debugging, and closeout:
   - `design-fidelity-polish`, `systematic-debugging`, and `release-readiness`

Skip stages that do not add value, but keep the handoff direction consistent.

## Primary Routing

### Clarify the product or UX before implementation

Use:

- `product-brainstorming`
- `design-to-prd`

Choose this when:

- the user-facing behavior is still ambiguous
- tradeoffs need design or product discussion
- the source materials are incomplete enough that implementation would be guesswork

Use `design-to-prd` instead of `product-brainstorming` when the primary need is to convert an existing design source into a written PRD rather than exploring solution directions from scratch.

### Deliver implementation from written specs and design artifacts

Use:

- `spec-driven-development`

Choose this when:

- the user already has a written client spec, Figma/design, or both
- the task spans planning, implementation, progress tracking, and verification
- source-of-truth conflicts may need explicit resolution

### Turn an existing design into a written PRD

Use:

- `design-to-prd`

Choose this when:

- the design exists, but the written product document does not
- the user wants a PRD derived from Figma, Google Stitch, screenshots, or exported screens
- implementation should be preceded by a polished markdown spec under `/docs/specs`

### Keep multi-step delivery traceable

Use:

- `traceable-delivery`

Choose this when:

- the work spans phases, modules, screens, blockers, or deferred scope
- progress should remain visible in markdown under `/docs`
- another skill is doing the domain work but needs durable status artifacts

### Discover repo conventions before planning or coding

Use:

- `repo-convention-discovery`

Choose this when:

- the repo’s local patterns need to be understood before choosing an implementation shape
- later work should follow existing routing, forms, state, API, styling, or test conventions

### Execute from existing plans and trackers

Use:

- `docs-driven-execution`

Choose this when:

- `/docs/plans` and `/docs/progress` already exist
- the main challenge is carrying work through the next slices without docs drifting
- execution needs to stay tightly synced with phase status and blockers

### Drive a change from failing tests first

Use:

- `test-driven-development`

Choose this when:

- the intended behavior can be captured well as an automated test
- a bug should become a regression test before the fix
- implementation risk is high enough that red-green-refactor is the safest path

### Gather design-source context from Figma

Use:

- `figma`

Choose this when:

- the user provides Figma URLs, node IDs, or design-driven implementation work
- Figma is the source system for implementation or fidelity work

Boundary:

- `figma` owns only the Figma-specific source acquisition workflow: MCP setup, node fetching, screenshots, assets, and handoff into shared delivery or polish skills

### Gather design-source context from Google Stitch

Use:

- `google-stitch`

Choose this when:

- the user provides Stitch projects, screen ids, or wants Stitch-generated screens used as the design source
- Stitch is the source system for implementation or fidelity work

Boundary:

- `google-stitch` owns only the Stitch-specific source acquisition and handoff workflow

### Turn a design source into a real traversable app flow

Use:

- `design-to-traversable-app`

Choose this when:

- the work spans many design-source screens
- route/state consolidation matters
- the goal is a traversable app, not an isolated component
- the user wants all screens implemented
- close fidelity, exact assets, or implementation tracking are part of acceptance

Do not down-route to a lighter single-screen Figma workflow when the user expects:

- full-canvas extraction
- route/state consolidation
- coherent click-path traversal
- exact icon or font fidelity
- durable roadmap and coverage tracking

### Polish an already-built design-driven app to exact visual parity

Use:

- `design-fidelity-polish`

Choose this when:

- route or state coverage already exists
- the remaining work is mainly visual fidelity and interaction parity
- exact icons, fonts, overlays, slideovers, or active-state parity are part of acceptance
- the user is asking for 1:1 cleanup rather than new screen implementation

### Integrate real backend support into an existing frontend

Use:

- `integrating-backend-api-into-frontend`

Choose this when:

- the frontend must align with a published or partial backend API
- blockers must be tracked against real backend support
- browser/runtime QA matters

This also covers admin-panel style CRUD and backoffice flows when they are part of the same frontend integration surface.

### Investigate bugs before fixing them

Use:

- `systematic-debugging`

Choose this when:

- there is a bug, flake, regression, integration failure, or unexpected runtime behavior
- the problem needs evidence gathering and root-cause analysis before any fix

### Decide if work is actually ready to hand off or release

Use:

- `release-readiness`

Choose this when:

- implementation is mostly done
- verification exists but readiness is still uncertain
- you need an explicit final go/no-go style summary

### Maintain or validate the skill set itself

Use:

- `skill-maintenance-and-validation`

Choose this when:

- the user wants to create, refine, lint, or validate skills
- the task is about stale skill metadata, broken references, overlap, or maintenance quality
- validator or environment issues need an honest fallback validation pass

## Supporting Skills

These are not primary owners, but should be layered in where appropriate:

- `test-driven-development` during implementation or bug fixing
- `verification-before-completion` before any success claim
- `traceable-delivery` for durable docs when the primary skill does not already fully own traceability
- `repo-convention-discovery` at the start of unfamiliar repos or features
- `docs-driven-execution` during the plan-to-code phase
- `release-readiness` near the end of delivery

## Combination Patterns

### Ambiguous feature request

Use:

- `product-brainstorming` → `spec-driven-development`

### Existing design that needs a written PRD

Use:

- `figma` or `google-stitch` → `design-to-prd`

### Planned delivery already underway

Use:

- `docs-driven-execution`

### Figma multi-screen app build

Use:

- `figma` + `design-to-traversable-app`

### Stitch multi-screen app build

Use:

- `google-stitch` + `design-to-traversable-app`

Add:

- `docs-driven-execution` once roadmap execution is underway

### Single Figma component or screen

Use:

- `figma`

### Single Stitch screen or source handoff

Use:

- `google-stitch`

### Fidelity follow-up after screen coverage

Use:

- `design-fidelity-polish`

### Existing frontend + backend contract

Use:

- `integrating-backend-api-into-frontend` + `traceable-delivery`

### Final closeout before handoff

Use:

- `release-readiness`

### Skill quality follow-up

Use:

- `skill-maintenance-and-validation`

### Bug discovered during delivery

Use:

- `systematic-debugging`

Escalate to:

- `spec-driven-development` if the issue is really a spec/design mismatch
- `product-brainstorming` if the issue is unclear intended behavior

## Routing Rules

- Pick one primary skill to own the task.
- Add supporting skills only when their specialized rules are actually needed.
- Prefer handoffs over blended mega-workflows when one phase is clearly complete.
- If the task shape changes midstream, re-route explicitly instead of quietly switching mental models.
- Treat screen implementation and screen fidelity as separate completion stages when design accuracy is part of acceptance.
