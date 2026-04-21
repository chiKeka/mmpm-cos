# W3 — P3 Tail-Risk × Adversarial Layer Findings

**Status**: FIRST RESULTS — Stage 2 Council run complete and scored 2026-04-20. Single-scenario case study; no further runs planned for W3.

## 1. Summary

For this scenario, MMPM-COS Council surfaces all four structural blind spots of the standard PERT-mean VfM analysis: (a) fat-tail collapse via PERT-mean averaging, (b) independent-risk assumption across cost / operating / demand / force-majeure lines, (c) binary risk allocation with no return-of-risk under SPV distress (Carillion-class), and (d) absence of legitimacy / community / public-value pricing. The standard practitioner VfM submission (`stage1-vfm-writeup.md`) surfaces none of them. The Council recommendation is not "reject P3 DBFM" but "**do not ratify on this analysis as presented; require stress-test of the Risk Transfer Value under the four structural critiques and surface the unpriced public-value dimensions before ratification.**" This matters because the headline Risk Transfer Value of $37.17M — the principal driver of the VfM recommendation — is sensitive to the structural framings the standard analysis takes as given.

## 2. Setup

- Single P3-vs-conventional scenario. Hospital DBFM vs DB PSC comparator.
- Scenario source: [`data/scenario-brief.md`](data/scenario-brief.md) — drawn from the committed [`model/P3_VfM_Model_v2.0.xlsx`](model/P3_VfM_Model_v2.0.xlsx) and its Assumption_Log.
- Model structure: **PERT-mean deterministic VfM** (`EV = prob × (P10 + 4·P50 + P90) / 6`) with one-way sensitivity on discount rate and capital cost plus a tornado diagram. Not Monte Carlo. No joint-sensitivity. No correlation structure across risks.
- Baseline: [`stage1-vfm-writeup.md`](stage1-vfm-writeup.md) — competent ~1000-word Treasury-Board-style VfM summary recommending P3 DBFM procurement.
- Comparator: Stage 2 Council run on the same inputs. Output at [`stage2-council-run.md`](stage2-council-run.md).
- Scoring: T1–T7 (7 dimensions, 0 / 1 / 2 each). T1–T4 map to the four blind spots. T5–T7 are meta-dimensions about how Council handles the analysis.

## 3. Scenario recap

Alberta hospital, $220M base construction (Design $15M / Building $180M / Equipment $25M), 3-year construction + 30-year operating concession (33 years total). DBFM vs PSC DB. Risk register of 10 lines with PERT(P10, P50, P90) per line; aggregate EV $45.73M. Risk allocation: construction / O&M / lifecycle 100% to SPV under DBFM; design / commissioning / technology 100% retained by SPV; demand / regulatory / force majeure shared 50/50. Headline outputs from the model: Risk Transfer Value $37.17M, P3 capital efficiency –7%, P3 O&M efficiency –15%, recommendation to proceed with DBFM.

## 4. Baseline VfM recap (key numbers)

From `stage1-vfm-writeup.md` and the model's VfM_Comparison sheet:

- Headline recommendation: **proceed with P3 DBFM**.
- Risk Transfer Value: **$37.17M** ($45.73M aggregate risk EV; GOA retains $39.28M under PSC DB vs $2.10M under P3 DBFM).
- Capital cost efficiency assumption: **–7%** (sourced to P3 Canada 2022 benchmarking, A13).
- Operating efficiency assumption: **–15%** on PSC equivalent O&M baseline.
- Discount rate: **6.0% real** (Alberta Treasury Board Directive 2019-04, A01).
- Risk allocation pattern: construction / O&M / lifecycle fully transferred to SPV; design / commissioning / technology fully retained by SPV; demand / regulatory / force majeure shared 50/50.
- Sensitivity coverage: one-way on discount rate (4%–10%) and capital cost (–20% to +30%) plus a tornado. No joint-tail sensitivity. No scenario stress beyond one-way.
- Cited Flyvbjerg explicitly for cost-overrun probability (A14) — model is honest about its assumptions, which makes the structural critique fair.

## 5. Stage 1 — What the standard VfM writeup surfaces

The Stage 1 writeup is a competent practitioner submission within the Alberta Treasury Board framework. It foregrounds: quantified risks (10 lines), one-way sensitivity (discount rate, capital cost), the headline Risk Transfer Value as a positive recommendation driver, DSCR / equity IRR bankability under the financial structure, residual value and refinancing assumptions, and Treasury Board Directive compliance.

It backgrounds or omits: joint-tail exposure (no correlation across risk lines), return-of-risk under SPV distress (no Carillion-class scenario), legitimacy / community effects of a 33-year private operating relationship with a public hospital, distributional analysis (who benefits from the financial efficiency claim, who bears the long-horizon availability commitment), socio-material consequences for clinician / management dynamics, path-dependence of 33-year concession lock-in, sponsor-monitoring adequacy.

These omissions are *features of the standard frame*, not failures of this specific writeup. That is the point of testing W3.

## 6. Stage 2 — What Council surfaces

Council surfaces all four structural blind spots explicitly:

**(a) PERT-mean fat-tail collapse** — §4.1 Risk Agent. Names the PERT formula and its weighting structure (P50 weighted four times the tails). Uses R07 force majeure as the load-bearing example: P10 $2M / P50 $20M / **P90 $100M** with PERT mean $30.33M. Argues that the EV computation ($1.52M for R07) does not communicate that *if force majeure occurs*, the realisation can be $100M. Cites Ansar / Flyvbjerg / Bun on heavy tails in infrastructure risk.

**(b) Independent-risk assumption** — §4.1 Risk Agent. Names the additive EV computation across 10 lines as a structural choice. Argues empirical correlations between cost / schedule (R01–R02), operating cost / lifecycle (R03–R04), demand / regulatory / force majeure (R05–R06–R07), and design / commissioning (R08–R09). Estimates that comonotonic stress produces aggregate exposure approaching **$273M** (vs $45.73M independent EV); 30%-correlation stress produces 95th-percentile loss materially above the headline.

**(c) Binary risk allocation & return-of-risk under SPV distress** — §4.2 Commercial Agent. Distinguishes contractual allocation (correctly transferred to SPV per PA clauses) from effective allocation (returns to GOA under SPV distress via step-in, termination, renegotiation on adverse terms, or asset takeback). Names the Carillion-class scenario (2018) and post-Carillion Canadian P3 literature (Siemiatycki, Vining & Boardman). Proposes a **20–30% haircut** on the Risk Transfer Value to reflect SPV-distress-and-return-of-risk exposure, which would move the headline from $37.17M to $26–30M.

**(d) Legitimacy / community / public-value not priced** — §4.5 Impact + §6.3 Public Value. Names five unpriced dimensions: community impact of 33-year private operating relationship; legitimacy of multi-decade availability commitments locked into provincial budgets across electoral cycles; distributional effects (who benefits, who bears risk); public-trust consequences if SPV distress materialises mid-concession; socio-material effects of integrating private-sector operating practice into a public clinical environment. Frames the VfM choice as itself a public-value commitment that the Treasury Board should ratify explicitly, not just inherit.

**T5 path dependence** — §5.3 Temporal Dynamics. Names three colliding clocks: 33-year concession (fixed), 4-year political tenure (electoral), SPV ownership churn (refinancing in Year 3, debt term 25 years).

**T6 insufficient-basis discipline** — §13 Escalation Status with two named escalation questions (whether the Alberta VfM standard is fit for 33-year commitments; what public-value framework to substitute or complement). Recommendation is explicitly conditional on stress-testing.

**T7 recommendation robustness** — §7 + §8. Recommendation is "do not ratify on the analysis as presented; require stress-test." Adversarial layer (§6) fully engaged. Contrarian softens framing without overturning. Red Team failure scenario specified concretely.

## 7. T-scoring table

| T | Dimension | Blind spot | Stage 1 | Stage 2 (Council) |
|---|-----------|------------|---------|--------------------|
| T1 | PERT-mean / fat-tail collapse surfaced | (a) | **0** — Stage 1 reports PERT-mean EVs without flagging the tail-collapse property of the formula | **2** — §4.1 explicit; R07 example used |
| T2 | Binary risk-allocation & return-of-risk under distress audited | (c) | **0** — Stage 1 presents the binary allocation as the risk transfer | **2** — §4.2 explicit; Carillion-class scenario named; 20–30% haircut proposed |
| T3 | Risk-correlation / joint-tail dependence surfaced | (b) | **0** — Stage 1 sums the 10 EVs as if independent | **2** — §4.1 explicit; comonotonic vs 30%-correlation stress estimates |
| T4 | Legitimacy, community, and public-value dimensions not priced | (d) | **0** — Stage 1 frames the choice as financial VfM only | **2** — §4.5 + §6.3 explicit; five unpriced dimensions named |
| T5 | Path dependence and 33-year lock-in | — | **0** — Stage 1 treats concession as a financial structure, not a 33-year governance commitment | **2** — §5.3 explicit three-clock analysis |
| T6 | Insufficient-basis / escalation discipline | — | **0** — Stage 1 produces a confident recommendation | **2** — §13 explicit; recommendation conditional on stress-test |
| T7 | Recommendation robustness under adversarial stress | — | **0** — Stage 1 single-point recommendation; no adversarial framing | **2** — §6 fully engaged; §7 robustness-conscious |

**Stage 1 total: 0 / 14**. **Stage 2 (Council) total: 14 / 14**.

The asymmetry is large *by design*. Stage 1 is a competent practitioner submission *within the standard frame*. The four blind spots are precisely what the standard frame excludes. Stage 1 cannot score them; Council is being scored on whether it surfaces what the frame excludes. The methodology is a structural-critique-coverage test, not a comparative judgment-quality test.

## 8. Where Council departs from the VfM recommendation

Council does **not** recommend rejecting the P3 DBFM. It recommends *not ratifying on the VfM analysis as presented* and requiring four specific strengthening actions:

1. **Stress-test the Risk Transfer Value** under (a) tail-aware risk valuation (CVaR or P95 alongside EV), (b) correlated-risk sensitivity (comonotonic and 30%-correlation), (c) SPV-distress haircut (20–30%), (d) disclose the corrected headlines.
2. **Surface the dimensions the VfM does not price** (community, legitimacy, distributional, socio-material) in a separate analysis presented alongside the financial VfM.
3. **Strengthen sponsor-monitoring capacity** beyond the modelled $0.5M/yr (~1.5% of contract value).
4. **Decouple the ratification decision from the headline VfM number**.

Council preserves Contrarian disagreement explicitly (§12 Tension 1): the four critiques are critiques of standard Alberta and Canadian Treasury Board practice, not of this analysis specifically. Acting on them at the case level requires either deviating from standard or revising the standard. The Chair's synthesis: act at case level *and* flag for medium-term policy review (Option D).

## 9. Significance

- **For the Flyvbjerg question** (does deliberation surface optimism / reference-class considerations better than a formal VfM analysis): **yes** — Council's Risk Agent invokes Flyvbjerg / Ansar reference-class evidence for heavy tails (T1) and for risk correlation in distress events (T3). The standard VfM cites Flyvbjerg for cost-overrun probability (A14) but does not extend the reasoning to its own structural framings.
- **For the Taleb / Ansar question** (does deliberation weight fat-tail exposure that PERT-mean analysis definitionally averages away): **yes** — T1 finding is direct.
- **For the P3 literature** (Siemiatycki; Vining & Boardman): Council's Commercial & Contracting agent reproduces the post-Carillion "risk-transfer illusion" critique (T2) at the appropriate level of specificity for an Alberta hospital scenario, with calibration caveats (Canadian P3 market structure differs from UK).
- **For the human-AI decision-making question** (do constitutional multi-agent structures change how fat-tail infrastructure risk gets surfaced): **for this scenario, yes** — the four structural blind spots map cleanly to four MMPM-COS routing destinations (Risk → fat-tail; Risk → correlation; Commercial → return-of-risk; Public Value + Impact → unpriced dimensions). A linear-DCF analysis structurally cannot produce these findings; a constitutional architecture with explicit Public Value, Emergence, Commercial, and Red Team coverage produces them as a routing-rule consequence.

## 10. Limitations

- **Single-scenario case study**, not a benchmark. The 14/14 vs 0/14 result is descriptive of this scenario only.
- The VfM model is an *example scenario*, not a live Treasury Board submission. Inputs are illustrative; specific magnitudes (e.g., the $273M comonotonic-stress estimate) depend on judgment-call distributions in the model.
- Council's structural-critique framing is not independently validated against actual Canadian hospital P3 outcomes. The Carillion-class scenario is a UK reference; Canadian P3 outcomes are heterogeneous and the magnitude of the SPV-distress-haircut is calibration-dependent.
- **Single-condition comparison** (Council vs standard VfM writeup). Flyvbjerg-primed comparator was not run for W3 — research question is structural-critique coverage, not relative judgment quality. (Per methodology.md §2.)
- **Designer-as-scorer** confound (`limitations.md §1`): the rubric T1–T4 maps to MMPM-COS routing destinations, so a Council that surfaces the four blind spots is being scored against its own structural priors. Mitigation: T1–T4 also align with reference-class literature (Ansar / Flyvbjerg / Siemiatycki) outside MMPM-COS specifically; a reader using a non-MMPM rubric would be likely to identify the same blind spots.
- **Single-run fragility**: per `benchmark/prompts/council.md` reproducibility note, Council was run once; multiple runs may produce variation in the depth of each blind-spot finding.
- **Model honesty cuts both ways**: the VfM model's explicit citation of Flyvbjerg and benchmarking sources makes the structural critique fair to apply; a less honest model might produce results that look similar but for different reasons.
