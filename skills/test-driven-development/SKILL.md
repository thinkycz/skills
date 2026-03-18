---
name: "test-driven-development"
description: "Drive implementation or bug fixing from failing tests instead of code-first changes. Use when the work can be expressed as automated checks, when regressions need protection, or when the safest path is to write or update a failing test first, make the smallest passing change, and verify the result before broader refactoring."
---

# Test Driven Development

Use tests as the control surface for behavior changes.

This skill is for work where the intended behavior can be captured as an automated test and the safest way to move is to prove failure first, then make the minimum change that turns the test green.

## Core Promise

- Turn expected behavior into an executable failing test before relying on implementation changes.
- Keep the change loop tight: red, green, refactor.
- Prefer the smallest justified code change that satisfies the test.
- Leave behind regression protection, not just passing chat claims.

## When To Use

Use this skill when the user:

- wants behavior implemented safely with regression protection
- has a bug that can be reproduced as a test
- needs confidence while changing risky logic, state transitions, serializers, parsers, or domain rules
- is working in a codebase that already has a viable test harness for the touched surface

Do not force TDD when the behavior cannot yet be expressed meaningfully as an automated test. In those cases, use the best adjacent workflow first, then return to tests as soon as the behavior becomes testable.

## Core Workflow

### 1. Ground In The Current Test Surface

- Inspect the existing test framework, naming conventions, fixtures, helpers, and nearby test patterns before writing anything new.
- Prefer extending the closest existing test style over inventing a new harness.
- If no realistic automated test surface exists yet, note that explicitly and choose the smallest viable test boundary.

### 2. Write Or Update A Failing Test First

- Capture the intended behavior in a test before broad implementation changes.
- Make the failure meaningful:
  - the assertion should describe real behavior, not internal trivia
  - the failure should be specific enough to guide the fix
  - the test should fail for the right reason
- When fixing a bug, reproduce the bug in a failing test if the harness makes that practical.

### 3. Make The Smallest Passing Change

- Change as little production code as possible to satisfy the failing test.
- Avoid bundling refactors, cleanup, or architecture work into the red-to-green step unless they are required for correctness.
- If multiple behaviors are changing, add tests incrementally instead of jumping to a large implementation pass.

### 4. Refactor Only After Green

- Once the new or updated test passes, improve structure if needed without changing behavior.
- Keep the tests green while refactoring.
- Prefer follow-up cleanups that improve readability, duplication, naming, or shared helpers when they reduce future risk.

### 5. Verify Beyond One Test

- Run the most relevant targeted test first.
- Then run the surrounding suite or the smallest broader scope that gives useful confidence.
- If lint, typecheck, or build are materially affected by the change, run them too.
- Do not stop at a single green test if nearby behavior could have regressed.

## TDD Rules

- Do not write broad implementation first and backfill tests afterward unless the harness makes true TDD impossible.
- Do not keep a test that passes for the wrong reason.
- Do not over-mock behavior that should be exercised more directly.
- Do not turn tests into snapshots of unstable implementation details unless that is the accepted repo pattern.
- Do not skip the refactor step when the green implementation is obviously messy or duplicated.

## Handoffs

- Use `systematic-debugging` when you cannot yet explain or reproduce the failure well enough to write the right test.
- Use `spec-driven-development` when the expected behavior itself is still unclear and needs source-of-truth normalization.
- Use `release-readiness` near the end when passing tests are only one part of the readiness decision.

## References

Read these only as needed:

- `references/red-green-refactor.md`
  Use for the default TDD loop and pacing rules.
- `references/test-selection.md`
  Use for choosing the right test boundary and confidence level.
