---
name: "verification-before-completion"
description: "Require fresh evidence before claiming work is done, fixed, passing, or matched. Use when implementation, debugging, or fidelity work is mostly complete and the agent needs to verify the relevant tests, runtime behavior, design expectations, docs, and blockers before making a success claim."
---

# Verification Before Completion

Do not let a success claim outrun the evidence.

Use this skill near the end of implementation, debugging, or design-fidelity work when the next step is to prove the result rather than continue coding.

## Core Promise

- Verify the thing that was actually requested, not just the easiest green check.
- Prefer fresh evidence over assumptions, stale logs, or “should be fixed now”.
- Check the most relevant technical and product-facing surfaces before claiming success.
- Leave a clear record of what was verified and what remains unverified.

## Core Workflow

### 1. Restate The Completion Claim

Before verifying, state what is being claimed:

- fixed
- implemented
- passing
- visually matched
- ready for review

Tie the claim to the user request, spec, PRD, bug report, or design source rather than to a vague notion of progress.

### 2. Choose The Right Verification Layers

Select only the layers that actually matter for the touched surface:

- targeted automated tests
- nearest related suite
- lint or typecheck
- build or release check
- runtime/manual behavior
- API contract compliance
- design or fidelity comparison
- docs, blockers, and tracker freshness

Do not stop at static checks when the claim is about runtime behavior or visual parity.

### 3. Run Fresh Evidence

- Prefer running the exact command or test that proves the changed behavior.
- Then run the smallest broader confidence pass that makes regressions less likely.
- If a claim depends on browser or manual behavior, exercise the real flow.
- If a claim depends on a design or spec, verify against that source explicitly.

### 4. Compare Evidence To The Claim

- Confirm whether the evidence fully supports the claim, partially supports it, or contradicts it.
- Call out gaps directly:
  - tests passed but runtime not checked
  - build passed but fidelity not checked
  - local flow worked but docs or blockers are stale
  - bug no longer reproduces but no regression test was added

### 5. Close Honestly

- If the evidence is sufficient, say exactly what was verified.
- If the evidence is incomplete, say what is still missing.
- If the evidence fails, do not soften the result into a near-success.

## Verification Rules

- Do not claim success from code inspection alone.
- Do not rely on stale command output from before the latest changes.
- Do not collapse “implemented”, “verified”, and “ready” into the same status.
- Do not ignore docs or blocker state when the workflow is traceable and multi-phase.

## Handoffs

- Use `release-readiness` when broader go/no-go judgment is needed after verification.
- Use `systematic-debugging` when the verification fails and the result is not actually explained yet.
- Use `design-fidelity-polish` when the remaining failure is mostly visual parity.

## References

Read these only as needed:

- `references/verification-layers.md`
  Use for choosing the right mix of checks for the claim.
- `references/closeout-language.md`
  Use for reporting verified, partially verified, and not verified outcomes clearly.
