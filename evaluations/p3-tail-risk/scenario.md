# P3 VfM × Adversarial Layer — Scenario Design

**Status**: DRAFT v1 — redesigned to reflect the actual VfM model artifact (`model/P3_VfM_Model_v2.0.xlsx`).

## Research question (refined)

A sophisticated, risk-quantified, sensitivity-aware VfM model — the kind a Canadian Treasury Board review would actually use — systematically:

- (a) collapses fat-tail risk exposure (P90s) into PERT means via `EV = prob × (P10 + 4·P50 + P90)/6`
- (b) treats risks as independent (no joint-tail modelling across cost, operating, demand, and force majeure lines)
- (c) binarizes risk allocation between PSC and P3 counterparties (0 / 50 / 100% retention, no return-of-risk under distress)
- (d) prices no legitimacy, community, or public-value risk

Does MMPM-COS Council, presented with this model's scenario and outputs and a competent VfM writeup of the recommendation, surface these four structural blind spots?

This is sharper than the original "Monte Carlo fat tails" framing because the model is not a Monte Carlo — it is a deterministic PERT-mean VfM comparison with one-way sensitivity analysis. The structural critiques above are specific and testable.

## What the model actually is

- 11 sheets: Cover, Quick_Start, Dashboard, Inputs_Master (82 rows), Delivery_Params, Risk_Register (10 risks), Calc_PSC, Calc_P3, VfM_Comparison, Sensitivity, Assumption_Log.
- Example scenario: Alberta hospital, 3-year construction, 30-year operating period, $220M base construction ($180M building + $25M equipment + $15M design), DBFM structure compared against DBB / DB / CM PSC comparators.
- Risks specified as probability × PERT(P10, P50, P90) per line. Correlations across risks: none modelled.
- Risk transfer point-estimated per risk: PSC fully retains construction/operating risks; P3 fully retains design/commissioning/technology; demand, regulatory, and force majeure shared 50/50.
- Sensitivity: one-way on discount rate (4% to 10%) and capital cost (-20% to +30%), plus a tornado diagram. No joint sensitivity.
- Assumption Log cites Flyvbjerg (A14-A15 for cost overrun parameters) and market benchmarking studies (A13 for P3 capital efficiency) — the model is honest about its assumptions, which strengthens the fairness of the Council critique.

The model has known calculation artifacts when opened in openpyxl data-only mode (several cells show `#NUM!` / `#N/A` because the Active PSC Method selector recomputes in Excel but not in openpyxl's cached values). This does not affect the structural analysis; numbers flowing into Council input are drawn from cells that are independently calculable (Risk Register EVs and derived totals).

## Study design — three stages

### Stage 1 — Practitioner VfM write-up (baseline)

A competent ~1000-word VfM summary as would be presented to an Alberta Treasury Board review. Drawn from the model's own outputs and assumption log. Positive framing consistent with typical Treasury submissions: headline VfM number, risk transfer analysis, sensitivity test results, recommendation to proceed with P3.

Artifact: `stage1-vfm-writeup.md`.

This is the baseline — the comparator that Council is measured against.

### Stage 2 — Council input and run

Council receives:

1. The scenario description (hospital, delivery comparison, key assumptions).
2. The risk register structure and outputs (probability, P10/P50/P90, EV, allocation).
3. The model's Assumption_Log (so Council sees what is sourced and what is inferred).
4. The Stage 1 write-up.
5. The question: *"The Treasury Board is deciding whether to proceed with the P3 DBFM structure recommended by the Value for Money analysis above, or to use a conventional DB delivery. What is your analysis? What would you recommend, with what confidence, and why?"*

Full `/council` orchestration runs. Output is the Council's 13-section brief.

Artifacts: `data/scenario-brief.md` (Council input), `stage2-council-run.md` (Council output).

### Stage 3 — Differential scoring

Score Stage 2 against the Stage 1 baseline on seven dimensions, each 0/1/2, max 14.

| T | Dimension | What a 2 looks like |
|---|-----------|---------------------|
| T1 | PERT-mean fat-tail collapse | Council names that P90 exposures are aggregated into PERT means and the tail realization is not scoped |
| T2 | Joint-tail / correlation surfacing | Council identifies that construction overrun, O&M variance, and force majeure are likely correlated under distress and the model treats them independently |
| T3 | Risk-transfer realism under distress | Council interrogates whether formally transferred risks return to the sponsor under consortium insolvency, counterparty credit distress, or contract disputes |
| T4 | Legitimacy / public-value dimensions not priced | Council raises community impact, distributional effects on service access, political legitimacy, or other dimensions the VfM does not price |
| T5 | P3 capital-efficiency claim interrogation | Council questions the -7% capital efficiency assumption — its source, its realism, whether it reflects true efficiency or strategic misrepresentation in benchmarking studies |
| T6 | Path dependence / exit asymmetry | Council identifies that signing a 33-year DBFM concession foreclosures realistic exit and reshapes all subsequent governance decisions |
| T7 | Insufficient-basis discipline | Council qualifies, defers, or conditions its recommendation where the evidence is weak — does not rubber-stamp the VfM |

Scoring rationale captured in `stage3-scoring.md`.

## What this workstream does not claim

- Not a claim that the specific hospital scenario generalizes.
- Not a claim the VfM model is wrong — the structural critique is that *any* PERT-mean VfM exhibits these blind spots, and the question is whether Council surfaces them.
- Not a claim that Council-surfaced risks are correct — they may include phantom risks as well as genuine ones.
- Not a claim about Council > human expert reviewer. The baseline is the Stage 1 VfM write-up, not a human reviewer.

## What successful completion looks like

- `data/scenario-brief.md` finalised and treated as the canonical Council input.
- `stage1-vfm-writeup.md` finalised — competent practitioner-grade baseline.
- Single Council run executed (temperature 0, one run, single-shot per the benchmark discipline — not best-of-N).
- T1–T7 scored with one-sentence justifications each.
- `findings.md` populated — where Council adds signal vs Stage 1, where it does not, and one paragraph explicitly asking whether the Council-surfaced risks are genuine or phantom.
