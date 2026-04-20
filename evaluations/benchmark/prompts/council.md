# Condition C — MMPM-COS Council

**Model**: claude-opus-4-7 (to be recorded per run with exact version)
**Temperature**: 0 (deterministic; recorded per run)

This condition invokes the full MMPM-COS architecture via the `/council` slash command.

---

## Invocation

The case's `brief.md` is passed as the argument to `/council`:

```
/council {brief.md contents verbatim}
```

The Council orchestration proceeds per `commands/council.md`:

1. INTAKE — Chair receives the brief as the programme question.
2. CLASSIFICATION — Chair classifies as GOVERNANCE_DECISION.
3. PARAMETER INFERENCE — Chair infers parameters. **For benchmark runs, the Chair's proposed parameters are accepted as-is without user override** to keep the condition reproducible. Parameters are recorded in the output.
4. AGENT SELECTION — per routing rules in `configs/routing/routing-rules.md`.
5. DOMAIN ASSESSMENT — parallel.
6. COUPLING REVIEW.
7. CHALLENGE ROUND.
8. REBUTTAL ROUND.
9. ADVERSARIAL REVIEW.
10. EVIDENCE QUALITY GATE.
11. SYNTHESIS — 13-section Council brief.
12. MEMORY WRITE — to `memory/decisions/` per normal operation.

---

## Run-execution protocol

- Start a fresh session for each case to avoid cross-case memory contamination.
- Invoke `/council` with the brief.
- Accept the Chair's parameter inference without user correction. Record inferred parameters in the output header.
- Allow the full 12-step orchestration to run without user intervention. Do not answer clarifying questions from the Chair during the run — if the Chair proceeds without clarification, that is the Council's native behavior and is scorable.
- Record the full raw output to `benchmark/outputs/{case-id}/council.md`.
- Record the memory write-back file path alongside.

## What this condition IS

- The full system as specified. Not a stripped-down variant.
- Tested under its documented operating assumptions, not under ad-hoc modifications per case.

## What this condition is NOT

- Not augmented with case-specific practitioner annotations. This is a clean test of the architecture, not of the architecture-plus-expert-user.
- Not run with user parameter overrides. Chair's inference is the condition.

## Reproducibility note

Because `/council` spawns multiple agent sessions and relies on Claude's stochastic reasoning, two runs of the same case will not produce identical outputs even at temperature 0 (orchestration paths can diverge). For each case, Council is run **once** and that output is scored. This is a deliberate choice — multiple runs would shift the study into "best-of-N" territory, which is not a fair comparison to single-shot Vanilla and Flyvbjerg-primed runs. Single-run fragility is acknowledged in `limitations.md`.

## Accepted output format (post-pilot)

Following the BER pilot (`outputs/ber/council.md`), the 13-section structure defined in `commands/council.md` is the **accepted Council output format** for all benchmark runs. No tightening or word-budget cap is applied. Rationale:

- The 13 sections are the system's native output contract. Truncating or compressing them would produce a Council-shaped-but-not-Council artifact and weaken the comparison.
- The verbosity confound is already named (`limitations.md §8`) and reported via the normalised score column in `scores/scored-rubric.csv`. Readers can weight raw vs normalised.
- Later cases may produce shorter synthesis naturally where agent dissent is lower or the decision is less multi-domain; no floor is imposed.

## Fallback if `/council` orchestration is infeasible to run automated

If mid-study it becomes clear that end-to-end `/council` runs per case are too expensive or too slow to complete within the study window, the fallback is:

- Run `/council` manually on a subset (minimum 4 of 8 cases).
- For the remaining cases, run a compressed-Council variant (Chair + 3 mandatory domain agents + 1 coupling agent + 1 adversarial agent) and **flag the change in the output file and in findings.md**.
- Do not silently substitute. Any deviation from full Council is disclosed.
