---
name: traceable-delivery
description: Keep implementation work traceable through markdown docs, phased progress, requirement or screen mapping, blocker tracking, and verification evidence under a project’s `/docs` folder. Use when the agent is executing multi-step delivery work and the user needs visible progress, shared status artifacts, and a durable audit trail instead of chat-only updates.
---

# Traceable Delivery

Make delivery progress visible outside the chat.

Use this skill when implementation spans multiple steps, phases, screens, modules, or blockers and the work should leave a durable markdown trail under `/docs` so another engineer can see what is planned, active, blocked, verified, or deferred.

## Core Promise

- Keep delivery state in markdown, not only in chat.
- Separate source mapping, phase planning, progress tracking, blockers, and verification.
- Preserve a durable audit trail for humans and agents.
- Support domain-specific skills without replacing them.

## When To Apply

Apply this skill whenever the work:

- spans multiple phases or modules
- includes blockers or deferred scope
- needs a screen, requirement, or route mapping
- requires visible progress for handoff or collaboration
- should end with verification evidence, not just “done”

Do not use this skill for trivial one-file changes that do not benefit from durable tracking.

## Default Docs Layout

Write markdown files under the project’s `/docs` folder only.

Default structure:

- `/docs/specs/` for normalized source summaries, decisions, and requirement clarifications when inputs exist
- `/docs/plans/` for phased implementation plans
- `/docs/progress/` for trackers, matrices, blockers, and status snapshots
- `/docs/verification/` for verification evidence and closeout reports

Not every project needs every file, but broad delivery work should usually populate all four folders.

## Shared Workflow

### 1. Create The Minimum Traceability Set

For non-trivial delivery, create:

- one source or decision summary when inputs need normalization
- one implementation plan
- one active progress tracker
- one verification report target

### 2. Map The Work

Use a matrix when the source work needs explicit traceability, such as:

- requirements to phases and verification
- Figma frames to routes or parent-state interactions
- modules to backend support and blockers

Keep every mapped item in exactly one accountable state.

### 3. Track Phases Explicitly

Each phase should show:

- goal
- current state
- remaining work
- blockers
- next recommended slice

When visual fidelity matters, also track whether the phase is:

- extracted
- mapped
- traversable
- fidelity-polished
- verified

Avoid vague “in progress” notes with no actionable breakdown.

### 4. Update During Execution

After each meaningful slice:

- mark completed items
- update blockers
- reclassify deferred or cancelled work honestly
- link new verification evidence
- update route/state mapping and fidelity status when those are part of acceptance

### 5. Close With Evidence

Before calling the work complete:

- ensure the tracker reflects the final state
- ensure blockers are current
- ensure verification docs point to fresh evidence
- ensure route/state mappings and fidelity matrices are current when the work is design-driven

## Common Artifacts

Use the references in this skill for templates and rules:

- [references/docs-layout.md](references/docs-layout.md)
- [references/matrices-and-trackers.md](references/matrices-and-trackers.md)
- [references/blockers-and-status.md](references/blockers-and-status.md)
- [references/verification-closeout.md](references/verification-closeout.md)

## Delivery Rules

- Do not keep critical progress state only in chat.
- Do not hide blockers inside prose paragraphs.
- Do not blur blocked, deferred, cancelled, and verified work together.
- Do not leave mapped items in ambiguous ownership or status.
- Do not treat “implemented” as a single flat state when route/state coverage, traversability, and fidelity are materially different milestones.
- Do not claim completion without updated verification artifacts.
