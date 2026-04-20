# W1 — Benchmark Findings

**Status**: SKELETON — to be populated after scoring.

*Every section below is a placeholder. Numerical claims will be filled from `scored-rubric.csv`. Nothing in this document should read as finalized.*

## 1. Summary

One paragraph. Headline finding. Where Council adds signal, where it does not.

## 2. Setup

- N = 8 cases (list)
- 3 conditions
- 10-dimension rubric
- Model version: {claude-opus-4-7}
- Temperature: 0
- Scorer: single scorer, no co-rater (see `limitations.md` §1-2)

## 3. Aggregate results

### 3.1 Totals by condition

| Condition | Mean total (max 20) | SD | Mean normalized (÷ words/100) |
|-----------|---------------------|-----|-------------------------------|
| Vanilla | — | — | — |
| Flyvbjerg-primed | — | — | — |
| Council | — | — | — |

### 3.2 Per-dimension means

| Dim | Vanilla | Flyvbjerg | Council | Δ(C-V) | Δ(C-F) |
|-----|---------|-----------|---------|--------|--------|
| D1 Optimism markers | | | | | |
| D2 Risk-class ID | | | | | |
| D3 Coupling | | | | | |
| D4 Outside view | | | | | |
| D5 Dissent | | | | | |
| D6 Evidence calibration | | | | | |
| D7 Legitimacy | | | | | |
| D8 Temporal | | | | | |
| D9 Insufficient basis | | | | | |
| D10 Traceability | | | | | |

### 3.3 Paired tests

Wilcoxon signed-rank on case totals:

- Council vs Vanilla: W = —, p = —
- Council vs Flyvbjerg: W = —, p = —

N=8. Descriptive, not inferential. See `limitations.md` §4.

## 4. Where Council adds signal

Dimensions where Council meaningfully outperforms both comparators, with per-case examples. Honest about whether the advantage is structural (system produces these sections by design) or substantive (system raises points the comparators miss).

## 5. Where Council does not add signal

Dimensions where Council matches or underperforms Flyvbjerg-primed. This section is load-bearing for credibility.

## 6. Case-level observations

Brief note per case on what each condition surfaced vs missed, and any anomalous results (e.g., Vanilla outperforming Council on a specific dimension on a specific case — what happened?).

## 7. Limitations specific to this workstream

Cross-reference `limitations.md`. Add anything that emerged during scoring that was not anticipated.

## 8. What next

If this study were extended: what would be the highest-value next step? (Co-rater replication? Larger N? Cross-model replication? Human-augmented condition?)
