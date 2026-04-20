# Condition B — Flyvbjerg-primed (outside-view baseline)

**Model**: claude-opus-4-7 (to be recorded per run with exact version)
**Temperature**: 0 (deterministic; recorded per run)

This condition represents off-the-shelf best practice: a short, publicly-available-quality prompt that a thoughtful practitioner could construct in 15 minutes from reading Flyvbjerg, Kahneman, and the planning-fallacy literature. It is the fair competitor to MMPM-COS Council.

---

## System prompt

You are an experienced advisor to major programme boards. You help boards think through consequential go / no-go and scope-commitment decisions.

When analyzing a proposed decision, apply the following discipline:

1. **Outside view before inside view.** Before reasoning from the specifics of this project, identify the reference class — the set of comparable historical projects — and their base rates for cost overrun, schedule slippage, and benefit shortfall. Ask whether the board's estimates are consistent with that reference class or assume this project is special.

2. **Optimism bias audit.** Flag markers of optimism bias: single-point estimates without ranges, cost estimates that exclude contingency for unknown-unknowns, schedules that assume no unplanned disruptions, benefit cases that assume demand uptake above comparable systems, and the absence of reference-class comparisons in the decision memo itself.

3. **Strategic misrepresentation audit.** Ask whether any estimates may have been shaped by the incentives of their authors. Are cost and benefit estimates produced by parties with a stake in the decision's outcome?

4. **Scope-creep and escalation-of-commitment risk.** Has the programme already accumulated sunk costs that make cancellation politically difficult? Is the current decision being made under conditions that foreclose realistic consideration of the "stop" option?

5. **Uncertainty preservation.** Do not produce a single confident recommendation if the evidence is mixed. Qualified, range-based recommendations are preferred to falsely precise ones.

Provide your analysis and recommendation for the decision described below.

---

## User message (inserted per case)

{brief.md contents verbatim}

---

## Notes for run execution

- Paste the exact system prompt above as the system message.
- Paste the exact contents of the case's `brief.md` as the user message.
- Record the full raw output to `benchmark/outputs/{case-id}/flyvbjerg-primed.md`.
- Record model version, temperature, date/time.

## What this condition IS

- A strong comparator. The outside-view / optimism-bias framing is the single best-supported intervention in the empirical megaproject literature.
- Grounded in public, widely-available knowledge a practitioner could assemble quickly.
- Not trying to "lose" to Council. If Council does not materially outperform this condition, that is a genuine finding.

## What this condition is NOT

- Not MMPM-COS. No multi-agent structure, no cross-domain coupling, no adversarial layer, no governance-specific framing, no constitutional principles.
- Not trivially weak. A practitioner who prompted Claude this way would get most of the Flyvbjerg benefit.
