# W3 — P3 Tail-Risk × Adversarial Layer Findings

**Status**: SKELETON — to be populated after the Stage 2 Council run completes.

## 1. Summary

One paragraph: does multi-agent deliberation surface the four structural blind spots of a sophisticated PERT-mean VfM analysis — (a) fat-tail collapse through PERT-mean averaging, (b) independent-risk assumption across cost/operating/demand/force-majeure lines, (c) binarized risk allocation with no return-of-risk under distress, (d) absent legitimacy and public-value pricing? For this specific scenario, the answer is — and matters because —.

## 2. Setup

- Single P3-vs-conventional scenario. Hospital DBFM vs DB/DBB PSC comparators.
- Scenario source: [`data/scenario-brief.md`](data/scenario-brief.md) — drawn from the committed [`model/P3_VfM_Model_v2.0.xlsx`](model/P3_VfM_Model_v2.0.xlsx) and its Assumption_Log.
- Model structure: **PERT-mean deterministic VfM** (`EV = prob × (P10 + 4·P50 + P90) / 6`) with one-way sensitivity on discount rate and capital cost plus a tornado diagram. Not Monte Carlo. No joint-sensitivity. No correlation structure across risks.
- Baseline: [`stage1-vfm-writeup.md`](stage1-vfm-writeup.md) — competent ~1000-word Treasury-Board-style VfM summary recommending P3 DBFM procurement.
- Comparator: Stage 2 Council run on the same inputs. Output at `stage2-council-run.md`.
- Scoring: T1–T7 (7 dimensions, 0 / 1 / 2 each). T1–T4 map to the four blind spots. T5–T7 are meta-dimensions about how Council handles the analysis.

## 3. Scenario recap

Short description of the Alberta hospital scenario, the model structure (PERT-mean, 30-year DBFM concession, 10 risk lines, binary/50-50 risk allocation), and the baseline recommendation (proceed with P3 DBFM, $37.2M Risk Transfer Value, –7% capital efficiency, –15% operating efficiency).

## 4. Baseline VfM recap (key numbers)

From `stage1-vfm-writeup.md` and the model's VfM_Comparison sheet:

- Headline recommendation: **proceed with P3 DBFM**.
- Risk Transfer Value: **$37.2M** ($45.7M aggregate risk EV; GOA retains $39.3M under PSC DB vs $2.1M under P3 DBFM).
- Capital cost efficiency assumption: **–7%** (sourced to P3 Canada 2022 benchmarking).
- Operating efficiency assumption: **–15%** on PSC equivalent O&M baseline.
- Discount rate: **6.0% real** (Alberta Treasury Board Directive 2019-04).
- Risk allocation pattern: construction / O&M / lifecycle fully transferred to SPV; design / commissioning / technology fully retained by SPV; demand / regulatory / force majeure shared 50/50.
- Sensitivity coverage: one-way on discount rate (4%–10%) and capital cost (–20% to +30%) plus a tornado. No joint-tail sensitivity. No scenario stress beyond one-way.

These are the numbers Council sees. The test is what it does with them.

## 5. Stage 1 — What the standard VfM writeup surfaces

Summary of the baseline. Which dimensions of risk are foregrounded (quantified risks, sensitivity on discount rate and capital cost, headline VfM number, DSCR / equity IRR bankability). Which are backgrounded or absent (joint-tail exposure, return-of-risk under SPV distress, legitimacy / community effects, path dependence of 33-year concession commitment).

## 6. Stage 2 — What Council surfaces

Summary of Council output. Particular attention to:

- Did the adversarial layer (Contrarian, Red Team, Emergence & Fragility) flag fat-tail collapse and the independence assumption?
- Did Commercial & Contracting interrogate binary risk allocation and flag return-of-risk pathways under SPV distress (Carillion-analogue scenarios)?
- Did Public Value & Ethics surface legitimacy, community, and distributional effects that the model does not price?
- Did Temporal Dynamics flag the 33-year concession horizon and sponsor-term clock mismatch?
- Did the Evidence Quality Gate challenge the model's PERT-mean framing given its own fat-tail exposure?

## 7. T-scoring table

| T | Dimension | Blind spot | Stage 1 | Stage 2 (Council) |
|---|-----------|------------|---------|--------------------|
| T1 | PERT-mean / fat-tail collapse surfaced | (a) | — | — |
| T2 | Binary risk-allocation & return-of-risk under distress audited | (c) | — | — |
| T3 | Risk-correlation / joint-tail dependence surfaced | (b) | — | — |
| T4 | Legitimacy, community, and public-value dimensions not priced | (d) | — | — |
| T5 | Path dependence and 33-year lock-in | — | — | — |
| T6 | Insufficient-basis / escalation discipline | — | — | — |
| T7 | Recommendation robustness under adversarial stress | — | — | — |

Scored 0 / 1 / 2 per dimension per output. Scorer records one-sentence justification per score, quoting the output or its absence.

## 8. Where Council departs from the VfM recommendation

If Council agrees with the VfM recommendation, that is a finding. If Council disagrees, the grounds for disagreement are the substantive output — in particular whether the four structural blind spots materially change the decision, or merely qualify it.

## 9. Significance

- For the Flyvbjerg question (does deliberation surface optimism / reference-class considerations better than a formal VfM analysis): —
- For the Taleb / Ansar question (does deliberation weight fat-tail exposure that PERT-mean analysis definitionally averages away): —
- For the P3 literature (Siemiatycki; Vining & Boardman): does Council's Commercial & Contracting agent reproduce the "risk-transfer illusion" critique that the post-Carillion literature has established?
- For the human-AI decision-making question (do constitutional multi-agent structures change how fat-tail infrastructure risk gets surfaced in a Treasury-Board-style analysis): —

## 10. Limitations

- Single scenario, not a benchmark. Case-study, not population-level, claim.
- The VfM model is an *example scenario*, not a live Treasury Board submission. Inputs are illustrative.
- Model outputs depend on input distributional assumptions (P10 / P50 / P90 per risk line), which are themselves judgment calls.
- Council's tail-risk framing is not independently validated against actual Canadian hospital P3 outcomes.
- Single-condition comparison (Council vs standard VfM writeup). Flyvbjerg-primed comparator is not run here; the research question is structural-critique coverage, not relative judgment quality. Cross-reference `methodology.md` §2 for why.
