# Limitations and Confounds

**Status**: DRAFT v0 — limitations named in advance of runs, not retrofitted after.

This document is load-bearing. A reviewer screening for research sensibility will look here before they look at the findings. Honest naming of confounds is stronger than polished findings with hidden ones.

## 1. Designer is scorer

The scorer (Chike Egbuneke) is also the system designer. This is the single largest confound. Mitigations:

- Per-score justification is recorded per dimension per output, so scoring can be audited by any reader without access to the scorer.
- Rubric was locked before any runs executed (see git history of `methodology.md`).
- D2 is explicitly scored against contemporaneous markers listed in the ground-truth file, not against outcome knowledge.

Residual confound: scorer may unconsciously favor MMPM-COS outputs because they match the rubric's MMPM-derived structure. This is partially *expected* — the rubric is derived from the system's own constitution, which is a known feature of designer-driven evaluation — but it means a Council advantage on, say, D10 (traceability) is less surprising than a Council advantage on D4 (outside-view reasoning), which MMPM-COS does not explicitly optimize for. Findings should be reported per dimension so readers can discount the rubric-aligned ones.

## 2. No co-rater

No inter-rater reliability statistic is available. A κ or Krippendorff's α would be the standard. Its absence is a legitimate critique. Partial mitigation: per-score justifications support post hoc auditability.

## 3. Single-model, single-prompt-per-condition

Results may reflect Claude-Opus-specific behavior or prompt-specific framing. No prompt sensitivity analysis. No cross-model replication. Any finding could be an artifact of a specific prompt wording.

## 4. Small N (benchmark: 8; blind-spots: 22; P3: 1; deep-case: 1)

Wilcoxon on paired benchmark scores with N=8 has limited statistical power. The study is descriptive, not inferential. Claims will be framed accordingly.

## 5. Case selection bias

Publicly documented megaprojects overrepresent spectacular failures (Berlin Brandenburg, Sydney Opera House) relative to quiet successes. A system that flags optimism bias will appear to perform better on failure-weighted cases. Mitigation: the case list includes at least two relative successes (Crossrail before 2018, Channel Tunnel post-operational) to test whether the system also produces appropriately tempered analysis when warranted. Even so, the case distribution is not representative.

## 6. Brief construction leaks hindsight

Writing a "decision brief at time T" while knowing what happened after T is inherently contaminated. Mitigation: contemporaneous-source discipline documented in `methodology.md` §3. Residual: unavoidable.

## 7. Rubric is the system's own rubric

The 10 dimensions are derived from the MMPM-COS constitution. A study built around a system's own definition of "good" will tend to find that system performs well. This is acknowledged and mitigated by:

- Four of the ten dimensions (D1, D4, D6, D9) are drawn from Flyvbjerg / Kahneman reference-class literature, not MMPM-specific.
- Per-dimension reporting lets readers discount MMPM-aligned dimensions (D3, D5, D7, D8) if they wish.
- A reader can substitute their own rubric against the same raw outputs.

## 8. Council is more verbose

Council outputs will be longer than vanilla outputs by design. Longer outputs trivially contain more of almost everything. Mitigations:

- Word-count per output is recorded in the CSV.
- A "normalized" score variant (score ÷ word-count-100s) is reported alongside raw scores.
- D5 (dissent preservation), D6 (evidence–claim calibration), and D9 (insufficient-basis discipline) are *harder* with more words, not easier — verbosity can hurt these dimensions.

## 9. Scorer fatigue

Scoring 24 benchmark outputs (8 cases × 3 conditions) plus 44 blind-spot outputs (22 × 2) plus P3 and Edmonton LRT materials in a compressed timeframe introduces fatigue effects. Mitigation: scoring is done in a fixed order (all Condition A first, then B, then C) and case ordering is recorded, so a reader can check for drift.

Wait — that mitigation creates its own bias (order effects). Revised: scoring is done per-case (A, B, C for case 1, then A, B, C for case 2, etc.) in random case order, with the condition-label hidden during scoring where feasible. Scorer will be able to infer condition from output structure, so full blinding is not possible.

## 10. MMPM-COS is a specification, not a running system at scoring time

The `/council` command invokes Claude with the MMPM-COS constitutional frame. It is not a separately trained model. Its performance is therefore bounded by what Claude can do when given the MMPM-COS prompt scaffold — not by an independent model architecture. This is relevant for reviewers who might misread Council as a fine-tuned system.

## 11. P3 workstream depends on an external artifact

The P3 VFM Monte Carlo model is maintained outside this repo. Reproducibility depends on that artifact being accessible. If not published alongside, the P3 finding is the weakest on reproducibility grounds and should be framed as a case study, not a benchmark.

## 12. Timeboxing

The study was produced in a compressed timeframe before a submission deadline. Nothing about that timeframe is visible in the findings, but it affected depth of source review per case. Each brief was timeboxed at 45 minutes of source work; deeper readings would likely improve brief quality and could change scores.
