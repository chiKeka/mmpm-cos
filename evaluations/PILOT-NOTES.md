# Pilot Notes — BER across three conditions

**Date**: 2026-04-20
**Pilot case**: Berlin Brandenburg Airport, Q1 2012 opening commitment
**Purpose**: Validate the evaluation pipeline before scaling to the remaining 23 W1 runs + 44 W2 runs + 1 W3 run + 3 W4 runs.

## What was validated

1. **Pipeline works end-to-end**. Brief → three conditions produced → all three are scorable against D1–D10 → CSV populated with scores and per-dimension reasons.
2. **Sub-agent role-isolation for A/B is acceptable**. Vanilla and Flyvbjerg-primed outputs were reviewed for MMPM-COS signatures (Chair / Public Value Agent / Evidence Quality Gate / Contrarian / multi-agent structure). None detected. Output-file headers record the execution environment and the contamination-review result per `limitations.md §14`.
3. **Council orchestration produces the 13-section structure** with per-domain attribution, cross-domain coupling §5, adversarial review §6, evidence quality gate §11, preserved tensions §12, and escalation section §13.

## What the pilot scores look like

| Dim | Vanilla | Flyvbjerg | Council | Δ(C-V) | Δ(C-F) |
|-----|---------|-----------|---------|--------|--------|
| D1 Optimism markers | 2 | 2 | 2 | 0 | 0 |
| D2 Risk-class ID | 2 | 2 | 2 | 0 | 0 |
| D3 Coupling | 2 | 2 | 2 | 0 | 0 |
| D4 Outside view | 1 | 2 | 1 | 0 | **−1** |
| D5 Dissent | 1 | 2 | 2 | +1 | 0 |
| D6 Evidence calibration | 2 | 2 | 2 | 0 | 0 |
| D7 Legitimacy | 1 | 1 | 2 | +1 | +1 |
| D8 Temporal | 1 | 1 | 2 | +1 | +1 |
| D9 Insufficient basis | 2 | 2 | 2 | 0 | 0 |
| D10 Traceability | 2 | 2 | 2 | 0 | 0 |
| **Total /20** | **16** | **18** | **19** | **+3** | **+1** |
| Word count | 1150 | 1700 | 4100 | | |
| Normalised (total / words/100) | 1.39 | 1.06 | 0.46 | | |

## Observations (one case, do not generalise yet)

**Vanilla is a strong baseline.** Claude 4.7 produces competent programme-board advice without MMPM priming — 16/20 on this case, hitting D1, D2, D3, D6, D9, D10. The unprimed-baseline floor is higher than a study designed against older models would assume.

**Flyvbjerg-primed is the genuine comparator the design intended.** It wins on D4 against Council (explicit reference class of named airport openings with quantitative base rates — T5, Madrid-Barajas, Denver). Methodology §4.4 says D4 is the dimension where Council advantage would be *less* surprising if the rubric is aligned with MMPM. The fact that Council loses D4 here is a real finding, not a noise.

**Council wins on the structural dimensions where MMPM-COS is designed to add value**: D5 (dissent preservation, +1 vs Vanilla, 0 vs Flyvbjerg), D7 (legitimacy / public value, +1 over both), D8 (temporal clock-mismatch, +1 over both). These are the dimensions the constitution explicitly foregrounds (Principles 5, 7, 8, 9).

**Verbosity confound is real.** Council normalised (0.46 per 100 words) is a third of Vanilla (1.39). The 13-section structure carries overhead that a shorter output does not. Reporting raw and normalised is the right discipline.

**Design feedback for Council**: the Risk Agent and Futures Agent did not invoke a named reference class or base rates on this case, even though airport-opening reference classes are readily available in MMPM doctrine. The routing rules do not currently *mandate* reference-class invocation. Consider adding a routing rule: "if the decision has a nameable reference class, Risk Agent + Futures Agent MUST produce base-rate framing." This would have closed the D4 gap on BER.

## Pipeline concerns before scaling

1. **Output-file header discipline**. The three BER output files use an inline HTML comment block for metadata. This is fine for reading but does not machine-extract cleanly. Consider a YAML frontmatter format for future runs if a reproducibility script is planned.

2. **Council run length**. 4100 words per Council output × 24 W1 runs = ~100k words of Council output alone. Plus W2 (22 vignettes × Council = shorter but still substantial) plus W3 and W4. Multi-session execution is required.

3. **A/B sub-agent contamination check protocol**. The review for MMPM signatures was done visually and informally. For scale, a simple grep-list (`Chair`, `Public Value Agent`, `Evidence Quality Gate`, `Contrarian Agent`, `Red Team`, `Programme Cognitive`, `constitutional principle`) would give a mechanical check before acceptance of an A or B output.

4. **D2 marker-crediting consistency**. The BER ground-truth file lists 8 contemporaneous markers; scoring credited "7/8" for all three conditions. If the rubric wants to distinguish between outputs that name markers with *mechanism* ("subcontractor fragmentation creates an integrated-responsibility gap") vs those that name them flatly ("subcontractor structure is fragmented"), the scoring schema should specify that. For this pilot we accepted "names the marker" as sufficient.

## Decision requested before scaling

1. Accept the sub-agent A/B execution protocol (acceptable per §14 with the headers and visual contamination check), OR require you to run A/B in a clean Claude.ai session yourself. The sub-agent protocol has worked for BER but your review of the output files before batch-running is the right gate.

2. Accept the Council output format / depth, OR request tightening (shorter synthesis, fewer sections, strict word budget).

3. Pick the next 1–3 cases to batch. Recommendation: **HS2 and Crossrail** next — HS2 has a strong reference-class story that will probe the D4 gap more rigorously, and Crossrail's assurance-capture dynamic is where Council's Governance and Contrarian agents should differentiate most cleanly from Flyvbjerg-primed. Save the Edmonton Valley Line for last since DP1 of W4 reuses that Council output.

4. Confirm the `SIGN-OFF.md` items. The pilot has produced usable outputs without formal sign-off, but scaling to 8 cases without sign-off risks re-work if any case-list or rubric change comes later.
