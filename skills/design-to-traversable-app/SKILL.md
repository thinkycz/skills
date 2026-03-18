---
name: "design-to-traversable-app"
description: "Use when implementing multi-screen design source material into a real traversable application with screen inventory, route/state mapping, phased delivery, and traceable verification. Trigger when the source may come from Figma, Google Stitch, or another confirmed design handoff and the target stack may vary by framework."
---

# Design To Traversable App

Use this as the canonical shared implementation workflow for multi-screen, design-driven app delivery.

This skill is framework-neutral. It does not own source acquisition. Apply a source adapter such as `figma` or `google-stitch` first, then read the matching framework reference under `references/` when the target stack is known.

If the design exists but the written product document does not, prefer `design-to-prd` before broad implementation so the delivery work has a normalized written source.

## When To Use

Use this skill when the user:

- wants many screens implemented from a design source into a real app
- needs screen inventory, route/state mapping, and phased delivery docs
- expects a traversable product flow rather than a gallery of isolated exports
- wants implementation progress and fidelity verification tracked under `/docs`

Do not use this skill for source acquisition problems or framework-specific bootstrapping by itself.

## Core Workflow

1. Ground in the repo first.
   - Apply `repo-convention-discovery` before locking route/state structure, shared primitives, or framework assumptions.
   - Inspect routing, state, docs, feature boundaries, and current screen organization.
   - Identify whether the app already uses route-per-screen pages, parent-state interactions, or a mixed pattern.

2. Normalize the design source before broad implementation.
   - Start only after a source adapter such as `figma` or `google-stitch` has provided a usable screen summary, screenshots or comparable visual references, and source caveats.
   - Confirm the top-level screen inventory before implementation begins.
   - If the source changes materially, re-baseline inventory counts, route/state mapping, roadmap phases, and coverage tracking immediately.

3. Pair with the correct framework reference.
   - Use `references/nextjs-delivery.md`, `references/vuejs-delivery.md`, `references/laravel-inertia-delivery.md`, or `references/adonis-inertia-delivery.md` to translate the shared workflow into framework-specific page, route, state, and build conventions.
   - Keep platform-specific defaults and stack rules in those references, not in the shared workflow body.

4. Create traceable docs before large buildout.
   - Apply `traceable-delivery` so the roadmap, mappings, progress state, blockers, and verification evidence stay durable under `/docs`.
   - Create source-neutral docs:
     - `docs/specs/design-source-summary.md`
     - `docs/specs/screen-inventory.md`
     - `docs/plans/design-implementation-plan.md`
     - `docs/progress/design-delivery-status.md`
     - `docs/verification/design-fidelity-matrix.md`
   - Keep the docs useful during execution, not just at kickoff.
   - If a PRD already exists under `/docs/specs/`, align the buildout docs to that PRD instead of silently diverging from it.

5. Phase the work into real user-visible slices.
   - Split work into narrow phases with obvious completion boundaries.
   - Distinguish extraction, mapping, traversability, fidelity, and verification when the project is non-trivial.
   - Apply `docs-driven-execution` once the roadmap is ready and active implementation begins.

6. Consolidate state-only screens into parent routes or page interactions.
   - If a source screen is just a dialog, tab state, review state, overlay, or drawer, implement it as a named interaction on a parent route or page unless the user explicitly wants a separate URL.
   - Keep true destination routes only where they represent actual navigation destinations.
   - Implement viewport-level overlays and slideovers at viewport level when the source behaves that way.

7. Make the app traversable.
   - Ensure the user can move through the important product flow without manual URL edits.
   - Treat route/state coverage and real click-path traversal as separate milestones.
   - Do not stop after screens are merely mapped if the product flow is not actually usable.

8. Preserve fidelity while translating into repo conventions.
   - Match layout, spacing, typography, iconography, imagery, and state composition as closely as possible.
   - Prefer repo primitives when they preserve fidelity.
   - Localize unstable remote assets into stable project paths.
   - If the remaining work is mainly exactness and polish after route/state coverage exists, hand off to `design-fidelity-polish`.

9. Keep the mapping and progress artifacts honest.
   - Maintain a route/state matrix so every source screen maps to exactly one of:
     - a standalone route or page
     - a named interaction on a parent route or page
   - Update the docs whenever routes are consolidated, phases move, or blockers appear.

10. Verify before claiming completion.
   - Run formatter if configured.
   - Run linter.
   - Run production build or equivalent release check.
   - Update the fidelity matrix with current parity status and known constraints.
   - Apply `release-readiness` before treating a non-trivial slice as ready for handoff or release.

## Required Outputs

Produce these outputs unless the user explicitly narrows scope:

- `docs/specs/design-source-summary.md`
- `docs/specs/screen-inventory.md`
- `docs/plans/design-implementation-plan.md`
- `docs/progress/design-delivery-status.md`
- `docs/verification/design-fidelity-matrix.md`
- an in-code mapping of source screens to routes, pages, or parent-state interactions
- a coverage count that distinguishes extraction, mapping, traversability, fidelity, and verification for non-trivial projects

## Decision Defaults

Use these defaults unless the user overrides them:

- source adapter first, shared implementation workflow second, platform adapter third
- confirm the full top-level screen inventory before implementing subsets
- re-baseline inventory and coverage if the design source changes
- collapse state-only screens into parent-route or parent-page interactions
- overlays and slideovers default to viewport-level implementations when the source behaves that way
- preserve visual fidelity over architectural purity when the tradeoff is mild
- localize unstable remote assets
- document font or asset limitations honestly when exact parity is blocked

## References

Read these only as needed:

- `references/session-patterns.md`
  Use for the reusable workflow patterns behind the phased implementation flow.
- `references/deliverables.md`
  Use for the doc outputs and minimum content requirements.
- `references/fidelity-and-consolidation.md`
  Use when deciding route/state consolidation, asset localization, overlay ownership, and fidelity rules.
- `references/docs-and-traceability.md`
  Use for the source-neutral mapping and coverage rules that layer on top of `traceable-delivery`.
- `references/nextjs-delivery.md`
  Use when the target stack is Next.js.
- `references/vuejs-delivery.md`
  Use when the target stack is Vue.js.
- `references/laravel-inertia-delivery.md`
  Use when the target stack is Laravel with Inertia.
- `references/adonis-inertia-delivery.md`
  Use when the target stack is AdonisJS with Inertia.
- `../design-fidelity-polish/SKILL.md`
  Use when the work has moved from broad implementation into a dedicated fidelity-polish phase.
