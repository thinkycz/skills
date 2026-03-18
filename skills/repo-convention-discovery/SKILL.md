---
name: repo-convention-discovery
description: Discover the implementation conventions of the current repository before planning or coding. Use when the agent needs to inspect routing, feature structure, API helpers, forms, state, styling, i18n, docs, tests, or other local patterns so later work follows the repo instead of inventing a new architecture.
---

# Repo Convention Discovery

Start by learning how this repo already works.

Apply this skill before planning or implementation when matching existing conventions matters more than inventing a fresh pattern.

## What To Inspect

- route structure and navigation
- feature/module layout
- API clients, serializers, and request helpers
- form wrappers and validation
- state management and providers
- styling and design-system primitives
- i18n and content structure
- tests, fixtures, and QA helpers
- existing docs that define delivery or architecture rules
- shell-level ownership of global overlays, drawers, and slideovers
- whether overlays are viewport-level or mistakenly clipped to local containers
- current asset strategy such as remote URLs, `public/` assets, SVG registries, or icon libraries
- current font loading strategy and whether local or proprietary fonts can be added
- whether docs already track route/state/fidelity mappings
- whether navigation distinguishes true destinations from transient visual states

## Output

Produce a short working summary of:

- the key conventions that matter for the task
- the likely files or subsystems involved
- any strong repo patterns that should be reused
- any missing or conflicting patterns worth surfacing early
- any shell, overlay, asset, icon, or font constraints that could affect fidelity-sensitive work

## Rules

- Explore first, ask second.
- Prefer existing patterns over cleaner new abstractions unless the current task clearly justifies a change.
- Keep the summary short and actionable.
