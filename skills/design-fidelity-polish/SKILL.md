---
name: "design-fidelity-polish"
description: "Use when a design-driven app already has screen coverage and now needs a dedicated visual parity pass for exact assets, typography, spacing, overlays, states, and browser QA. Trigger when the source may come from Figma, Google Stitch, or another confirmed design handoff."
---

# Design Fidelity Polish

Use this as the canonical fidelity workflow after the main routes or parent-state interactions already exist.

This skill is design-platform-agnostic. Apply a source adapter such as `figma` or `google-stitch` first when you need fresh screenshots, source notes, or source-specific asset guidance.

## When To Use

Use this skill when the user:

- says the screens are implemented but the visuals still do not match the design source
- wants 1:1 parity for icons, fonts, logos, images, spacing, overlays, or active states
- needs route/state coverage refined into true design fidelity
- wants a final browser QA pass driven by the design source

Do not use this skill for first-pass route creation or broad app planning. Use `design-to-traversable-app` for that.

## Core Workflow

1. Confirm the current implementation shape first.
   - Apply `repo-convention-discovery` before changing visual primitives or shell behavior.
   - Identify which screens are already routes versus parent-state interactions.
   - Identify whether current mismatches are asset problems, layout problems, state or interaction problems, or shell ownership problems.

2. Re-ground in the source design.
   - Use the relevant source adapter first for screenshots, structure, asset guidance, and source caveats.
   - Prefer the user-confirmed source canvas, screen, or project scope rather than an arbitrary child view.

3. Build a fidelity checklist before broad edits.
   - Track every relevant screen or interaction in a fidelity matrix.
   - Separate exactness work into:
     - icons
     - fonts
     - images and logos
     - spacing and sizing
     - active and inactive states
     - overlays and slideovers
     - browser QA notes

4. Fix exact assets before tweaking CSS by hand.
   - If icon fidelity matters, export or generate the correct assets from the source system and replace placeholder icon libraries.
   - If the user provides proprietary fonts, ingest them into the project instead of continuing with fallbacks.
   - Localize unstable remote assets into stable project paths.
   - Track exact active and inactive asset variants separately when the design uses different states.

5. Fix ownership and behavior mismatches.
   - Move state-only routes into parent interactions if the design implies a dialog, drawer, tab state, or slideover.
   - Make overlays viewport-level when the design visually covers the viewport.
   - Put shell-owned panels such as notification drawers in the shell rather than behind separate pages when the design implies that ownership.

6. Fix layout and type mismatches after assets are correct.
   - Align spacing, sizing, content widths, card heights, text scale, and state variants to the design screenshots.
   - Reuse repo primitives only if they preserve fidelity.
   - Prefer editing shared primitives and shells when that resolves a mismatch across multiple screens.

7. Verify before claiming fidelity is done.
   - Run formatter if configured.
   - Run linter.
   - Run production build.
   - Update the fidelity matrix with what is exact, what is still approximate, and any remaining constraints.
   - Do not claim 1:1 parity while known mismatches or unresolved font or asset gaps remain.
   - Apply `release-readiness` when the polish work is part of a broader handoff or release decision.

## Required Outputs

Produce or update these when the work is non-trivial:

- `docs/verification/design-fidelity-matrix.md`
- any route/state matrix entries affected by consolidation
- localized icon, font, or image assets under stable project paths
- a clear closeout note that distinguishes:
  - exact parity achieved
  - close approximation
  - known remaining constraints

## Decision Defaults

Use these defaults unless the user overrides them:

- treat screen coverage and fidelity polish as separate completion stages
- replace generic icon libraries with source-correct assets when icon fidelity is requested
- ingest provided proprietary fonts instead of continuing with approximations
- localize brittle remote assets
- treat dialogs, drawers, and slideovers as parent-state interactions unless the user explicitly wants standalone URLs
- implement full-screen overlays at viewport level when the design behaves that way
- keep docs honest about remaining mismatches

## References

Read these only as needed:

- `references/exact-assets.md`
  Use for icon, logo, image, and font handling rules.
- `references/overlays-and-shells.md`
  Use when fixing dialogs, slideovers, shell-owned panels, and viewport overlays.
- `references/browser-qa.md`
  Use for the fidelity checklist structure and closeout expectations.
