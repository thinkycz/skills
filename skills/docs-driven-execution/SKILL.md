---
name: docs-driven-execution
description: Execute multi-phase implementation work from markdown plans and progress docs while keeping `/docs` artifacts current as the source of truth. Use when the agent already has a plan or tracker and needs to carry work through phase-by-phase execution, status updates, blocker maintenance, and verification handoff without letting the docs drift from reality.
---

# Docs Driven Execution

Use docs as the execution control surface, not just as a kickoff artifact.

Apply this skill when a plan already exists under `/docs` and the work should proceed slice by slice while keeping plans, progress, blockers, and verification evidence in sync with reality.

## Core Workflow

1. Read the active plan and progress docs before changing code.
2. Pick the current phase or next actionable slice, not the whole roadmap at once.
3. Execute in small increments that can be verified independently.
4. After each meaningful slice:
   - update progress docs
   - reclassify blockers
   - link verification evidence
   - update fidelity and interaction status when those are part of acceptance
5. Do not mark a phase complete until its docs reflect the real state.
6. For broad design-driven delivery, prefer this execution order unless the user says otherwise:
   - source normalization or PRD alignment
   - roadmap and mappings
   - screen or page implementation
   - state consolidation
   - traversability wiring
   - asset localization
   - fidelity pass
   - final verification

## When To Use

- after `spec-driven-development` has produced a plan
- after `design-to-prd` has produced a PRD that is now driving implementation planning
- during `design-to-traversable-app` implementation
- during backend/frontend integration work with active phase trackers
- whenever `/docs/plans` and `/docs/progress` already exist and should drive execution

## Rules

- Treat `/docs/plans` and `/docs/progress` as live artifacts, not stale notes.
- Prefer one current phase and one next slice over broad parallel thrashing.
- Keep blockers explicit.
- Do not stop at first-pass screen delivery when known fidelity or interaction gaps are still part of the requested acceptance bar.
- Do not mark phases complete while known visual or interaction mismatches remain in docs as unresolved.
- Hand off to `release-readiness` when implementation is functionally done and needs final closeout.
