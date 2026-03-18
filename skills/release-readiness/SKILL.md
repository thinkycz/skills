---
name: release-readiness
description: Decide whether a feature or fix is truly ready for handoff, review, or release by checking verification evidence, blocker state, docs freshness, and remaining gaps. Use when implementation is mostly done and the agent needs to produce a final readiness assessment instead of assuming “done”.
---

# Release Readiness

Turn “it seems done” into an explicit readiness decision.

Apply this skill near the end of delivery or debugging when code exists, checks have run, and you need to decide whether the work is actually ready for handoff, review, or release.

## Checkpoints

- fresh verification evidence exists
- blockers and deferred items are current
- plans and progress docs match the actual delivered state
- any PRD, design doc, or written source of truth still matches the delivered behavior
- known gaps are explicit
- user-facing flows affected by the change were exercised appropriately
- source-of-truth requirements or design expectations were checked when relevant

## Output

Produce a concise readiness summary covering:

- what is ready
- what is not ready
- known risks
- required follow-ups before release, if any

## Rules

- Do not confuse “code written” with “release ready”.
- If docs, blockers, or verification are stale, call that out directly.
- If the build drifted from the PRD, design doc, or design source, call that out directly.
- Prefer an honest “not ready yet because…” over a soft-complete summary.
