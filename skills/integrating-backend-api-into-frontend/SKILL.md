---
name: integrating-backend-api-into-frontend
description: Use when connecting an existing frontend app to a published or partially published backend API, especially when the work includes phased delivery, missing page or form functionality, blocker tracking, browser QA, runtime debugging, plan/doc updates during execution, and traceable progress under `/docs`.
---

# Integrating Backend API Into Frontend

## Overview

This skill is for production integration work in an existing frontend repository. The goal is not just to "add API calls"; it is to make the real backend-supported behavior fit the repo cleanly, finish missing pages and forms, keep unsupported behavior explicit, and leave a traceable implementation record.

Use this skill when the task sounds like:
- connect all pages or forms to the backend
- make an existing frontend fully functional
- finish missing backend-supported functionality
- integrate an OpenAPI or Swagger contract into an existing app
- deliver the work in phases and keep plans updated as progress changes

Do not use this skill for greenfield app creation.

## Required Workflow

1. Ground in repo conventions first.
   Apply `repo-convention-discovery`, then inspect route layout, feature folders, shared request helpers, form wrappers, validation, i18n, tables, and state before proposing changes.
2. Inspect the backend contract directly.
   Read the published OpenAPI or live API behavior before trusting stale docs or assumptions.
   If the product definition itself is still unclear or design-first artifacts need normalization, hand off to `spec-driven-development` or `design-to-prd` before broad integration work.
3. Map user-visible behaviors to exact backend support.
   For each list, detail page, create/edit form, archive action, relation view, download, or message flow, identify the real backend operation that supports it.
4. Slice delivery by module or workflow.
   Implement vertically, one domain at a time, so blockers and verification stay easy to reason about.
   Apply `traceable-delivery` so plans, trackers, blockers, and verification evidence remain durable under `docs/`.
   Apply `docs-driven-execution` when carrying those phases into active implementation.
5. Reuse existing repo patterns.
   Prefer the app's current routing, API helpers, serializers, response transformers, form patterns, and locale structure over introducing new architecture.
6. Treat unsupported behavior as explicit blockers.
   Do not invent frontend-only success paths, fake local mutations, or placeholder data that looks complete.
7. Verify in layers.
   Run lint, typecheck, and build, then manually exercise the touched routes and key mutations in the browser.
8. Keep progress traceable.
   Keep `traceable-delivery` active while implementation evolves.
   Update plans, phase docs, blocker notes, verification evidence, and locale parity as the implementation evolves.
9. Assess final readiness explicitly.
   Apply `release-readiness` before treating the integrated slice as fully ready for handoff or release.

## Unified Workflow Position

This skill usually sits after source normalization and written planning:

- `design-to-prd` when design needs to become a written product artifact
- `spec-driven-development` when implementation phases and delivery docs need to be set up
- `integrating-backend-api-into-frontend` during contract-backed frontend execution

## Read These References As Needed

- For phase-based planning and closeout criteria, read [references/planning.md](references/planning.md).
- For mapping OpenAPI and live payloads to frontend behavior, read [references/api-contract-mapping.md](references/api-contract-mapping.md).
- For browser-based validation and manual smoke testing, read [references/browser-and-manual-qa.md](references/browser-and-manual-qa.md).
- For blocker taxonomy, progress snapshots, and phase doc maintenance, read [references/blockers-and-phase-tracking.md](references/blockers-and-phase-tracking.md).
  Apply this after the shared `traceable-delivery` rules to keep the integration-specific blocker semantics consistent.
- For runtime regressions and framework-style debugging during integration, read [references/runtime-debugging.md](references/runtime-debugging.md).

## Default Delivery Rules

- Use the live API contract as the source of truth when written product specs and backend behavior disagree.
- Preserve the current route structure unless the task explicitly requires route changes.
- Add thin typed API modules and mapping helpers near the feature instead of inventing a new app-wide data framework.
- Keep shared enums and options aligned to backend-supported values.
- Sync locale keys across all supported languages whenever UI changes.
- Prefer relation-aware rendering when responses expose `relationships` and `included`.
- Validate real create/edit/archive/message flows in-browser, not just list rendering.

## Blocker Taxonomy

- `backend missing`: required endpoint, field, relationship, or file action is not supported
- `intentionally deferred`: valid follow-up work left out of the current slice
- `runtime/framework issue`: build, framework, cache, or library behavior interfering with delivery
- `cancelled`: previously planned area removed by product or scope decision

## Do Not Do This

- Do not invent unsupported backend flows.
- Do not hide missing endpoints behind fake success messages or mock data that looks real.
- Do not stop at passing static checks when the change affects runtime behavior.
- Do not skip locale parity or plan/doc updates.
- Do not integrate the whole product area in one blind pass when a phased approach is feasible.

## Output Expectations

A strong result from this skill usually includes:
- a phased or module-based plan when the scope is broad
- implementation aligned to existing frontend conventions
- explicit blocker documentation for unsupported backend behavior
- verification evidence from lint, typecheck, build, and browser/manual QA
- updated progress tracking so the next engineer can see what is complete, blocked, deferred, or cancelled
