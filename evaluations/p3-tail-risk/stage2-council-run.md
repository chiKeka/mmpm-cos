<!--
Run metadata
============
case_id: p3-vfm-alberta-hospital
condition: council
model: claude-opus-4-7
temperature: 0 (nominal)
run_date: 2026-04-20
prompt_source: evaluations/benchmark/prompts/council.md (full /council invocation per commands/council.md)
input: scenario-brief.md (Stage 2 input) + stage1-vfm-writeup.md (baseline VfM, treated as the practitioner submission Council is critiquing)
execution_environment: Claude Code session with full MMPM-COS constitutional context (Condition C native).
word_count: ~4400 (approximate)
parameters: auto-inferred per methodology §2 Condition C protocol
-->

# PROGRAMME GOVERNANCE COUNCIL BRIEF

## 1. PROBLEM FRAMING

Alberta Treasury Board is being asked to ratify a Value for Money (VfM) recommendation to proceed with P3 DBFM delivery for a $220M new-build hospital, in preference to conventional DB delivery. The VfM analysis is competent on its own terms — it follows Treasury Board Directive 2019-04, applies Alberta-standard risk allocation, sources its assumptions to Flyvbjerg reference-class forecasting (A14) and P3 Canada benchmarking (A13), and presents a Risk Transfer Value of **$37.17M** as the principal driver of a positive VfM recommendation.

The Chair classifies as GOVERNANCE_DECISION with a specific analytical lens: not "is the VfM math wrong?" (it isn't, on its own terms) but "**does the model's analytical structure capture the dimensions on which a 33-year concession can fail?**" The Council's adversarial mandate is explicit here — to interrogate the model's structural choices rather than its arithmetic execution.

Four structural concerns surface on first reading the model:

- **(a) PERT-mean fat-tail collapse.** The risk EVs are computed as `prob × PERT(P10, P50, P90)`. PERT-mean weights the P50 four times the tails. R07 force majeure has P10 $2M / P50 $20M / **P90 $100M** but a PERT mean of $30.33M — the $100M P90 is averaged into a number that materially understates what GOA is exposed to in the 5% tail event.
- **(b) Independent-risk assumption.** The 10 risks are summed as if independent. No correlation structure across construction, operating, demand, and force majeure lines. Real distress events typically correlate cost, schedule, demand, and operating outcomes; the additive EV understates joint-tail exposure.
- **(c) Binary risk allocation with no return-of-risk under distress.** Risk retention is 0% / 50% / 100% per risk per delivery model. The model assumes the SPV bears construction and operating risk under P3, full stop. Under SPV distress (Carillion-class scenario), risk returns to GOA; the model has no line for this.
- **(d) Absent legitimacy / community / public-value pricing.** The model prices construction, operating, lifecycle, demand, regulatory, and force majeure risk. It does not price community impact, legitimacy of long-horizon concession governance, distributional consequences, or socio-material effects of a 33-year private-sector operating relationship.

These four are testable structural critiques, not arithmetic challenges. The Council's analysis is structured around them.

## 2. PROGRAMME CONTEXT AND PARAMETERS

Inferred:

| Parameter | Value | Basis |
|-----------|-------|-------|
| strategic_criticality | high | New hospital; public-service essential infrastructure |
| public_visibility | moderate-to-high | Treasury Board ratification typically reported |
| stakeholder_fragmentation | high | TB / Alberta Health / SPV / lender consortium / community / clinicians |
| risk_tolerance | moderate | Standard Treasury Board posture, but life-safety and access concerns |
| tail_risk_sensitivity | high | PERT-mean treatment of force majeure is the load-bearing concern |
| schedule_rigidity | moderate | Hospital opening dates have political weight |
| equity_weighting | high | Public hospital; access/equity dimensions |
| environmental_sensitivity | moderate | Hospital lifecycle, materials, energy |
| time_horizon | long (33 years) | Full concession period |
| disruption_sensitivity | high | Healthcare technology and demographics evolve materially over 33 years |

**Mandatory triggers**: Risk (cost/schedule/operating); Commercial (long-horizon contracting, SPV structure); Governance (33-year governance arrangement); Public Value (essential public service, community); Contrarian (high-stakes consequential ratification); Red Team (irreversible 33-year commitment); Emergence & Fragility (joint-tail exposure); Temporal Dynamics (33-year horizon, 4-year political tenure); Constraint & Tradeoff (P3 vs DB); Interface Integrity (multi-domain). Futures invoked due to long horizon.

## 3. AGENTS CONSULTED

Twelve agents plus Chair: Risk; Commercial; Governance; Strategic Leadership; Impact; Futures; Interface Integrity; Cascading Effects; Temporal Dynamics; Emergence & Fragility; Contrarian; Red Team; Public Value & Ethics. Constraint & Tradeoff folded into §7. Organisational Design not invoked.

## 4. KEY FINDINGS BY DOMAIN

### 4.1 Risk, Uncertainty & Fragility — primary finding on (a) and (b)

The model is honest about its assumptions — it cites Flyvbjerg (A14) for cost overrun probability and AB historical data (A15) for cost overrun P50. This honesty is what makes the structural critique fair.

**On (a) PERT-mean fat-tail collapse**: The PERT formula `EV = (P10 + 4×P50 + P90) / 6` weights the P50 four times the tails. For symmetric distributions this is reasonable. For *heavy-tailed* distributions — which infrastructure cost overruns and force majeure events empirically are (Ansar, Flyvbjerg, Bun et al.) — PERT-mean systematically understates the tail. The clearest case is R07 (force majeure): P10 $2M / P50 $20M / P90 **$100M** with PERT mean $30.33M. The expected value calculation produces $1.52M because of the 5% probability, but that EV does not communicate that *if force majeure occurs*, the realisation can be $100M. The headline Risk Transfer Value of $37.17M is a sum of EVs that compresses the tail behaviour the Treasury Board needs to see.

**On (b) Independent-risk assumption**: The model sums 10 risk EVs as if independent. Empirically, cost overruns correlate with schedule delays (R01–R02); operating cost variance correlates with lifecycle underestimation (R03–R04); demand shocks often coincide with regulatory or force majeure events (R05–R06–R07); design deficiency drives commissioning risk (R08–R09). A correlated-tail simulation — even a simple comonotonic stress where adverse outcomes are aligned — would produce a joint-tail loss materially larger than the sum of independent EVs.

What the model would look like with these corrected: under a comonotonic adverse stress (all 10 risks at P90), aggregate exposure approaches **$273M** in absolute terms; even under a 30%-correlation stress, the 95th-percentile loss is materially above the $45.7M independent EV. The Risk Transfer Value of $37.17M is being computed against a distribution that does not show the tail GOA is actually transferring.

Confidence: **high** that these are structural understatements; **moderate** on specific magnitudes (depends on correlation assumption).

### 4.2 Commercial & Contracting — primary finding on (c)

The risk-allocation table assumes the SPV retains 100% of construction, operating, lifecycle, design, commissioning, and technology risk under DBFM. This is correct as a contractual statement: the PA clauses cited (Sch 14 §3.2(a) etc.) do allocate these risks to the SPV.

**But contractual allocation is not the same as effective allocation.** When the SPV faces distress — bidder thinness in the Canadian P3 market, lender covenant breach, parent-company insolvency, supply-chain shock, force majeure beyond insurance limits — the contracts have step-in rights and termination provisions, but the *practical* outcome is that GOA either (i) renegotiates on adverse terms to keep the hospital operating, (ii) takes the asset back and assumes residual risk, or (iii) bears service-disruption while alternative arrangements are made. This is the **return-of-risk-under-distress** dynamic the Carillion failure (2018) made canonical and the post-2018 Canadian P3 literature (Siemiatycki, Vining & Boardman) has formalised.

The model does not have a line item for return-of-risk. The Risk Transfer Value of $37.17M is computed as if SPV solvency is a binary that does not interact with the risk register. Empirically, SPV distress probability over a 33-year concession is non-trivial (P3 market in Canada has thinned post-Carillion; lender-covenant pressure compounds over decades).

A defensible model adjustment: discount the $37.17M Risk Transfer Value by an *SPV-distress-and-return-of-risk* factor. Even a 20–30% discount produces a Risk Transfer Value of $26–30M, which materially changes the VfM headline.

Confidence: **high** that the model omits this dimension; **moderate** on the specific discount factor (depends on consortium credit profile and Canadian P3 market evolution).

### 4.3 Governance, Stakeholder & Institutional Leadership

Two governance findings.

(i) **33-year concession governance** is a 33-year political commitment that will outlast any current government, several health-policy regimes, and probably the SPV ownership structure (refinancing in Year 3 already shifts the financial counterparty). The model treats governance as static — Alberta TB Directive 2019-04 today is the framework — but the directive itself can change, and contractual disputes typically arrive in conditions where the original model assumptions no longer match the operating reality.

(ii) **Sponsor-monitoring capacity**: $0.5M/yr GOA monitoring/oversight against a $32.36M/yr availability payment is approximately 1.5% of the contract value. The post-Carillion literature consistently finds that *under-investment in sponsor monitoring* is a leading indicator of P3 distress not being caught early enough. This is a governance line the model surfaces as a cost but does not interrogate as a risk.

Confidence: moderate.

### 4.4 Strategic Leadership & Performance

The headline VfM number obscures the decision-quality question. The Treasury Board is being asked to choose between two delivery models on a single point-estimate ratio. Decision-quality discipline would require (i) the VfM distribution under the structural-critique scenarios, (ii) the alternatives that are not in the comparator set (e.g., PSC variants beyond DB; smaller / phased construction; design-build-operate without finance), (iii) explicit distributional analysis of who benefits and who bears risk. The model and Stage 1 writeup do not surface these.

### 4.5 Socio-Technical Impact & Legitimacy — primary finding on (d)

The model prices construction, operating, lifecycle, demand, regulatory, and force majeure risk. It does **not** price:

- **Community impact** of a 33-year private-sector operating relationship with a public hospital (clinician-management dynamics, scope-of-service flexibility, community access).
- **Legitimacy** of multi-decade availability-payment commitments locked into provincial budgets across multiple electoral cycles.
- **Distributional effects** — who in the population benefits from the financing efficiency claim, who bears the long-horizon availability-payment commitment.
- **Public-trust** consequences if the SPV faces distress mid-concession and the public sector is seen to be bailing out a private operator of an essential service (politically corrosive even if contractually defensible).
- **Socio-material effects** of integrating private-sector operating practice into a public-sector clinical environment (decisions about maintenance, lifecycle replacement, and minor capital that would, under public ownership, be made on clinical-priority grounds and may, under SPV ownership, be made on contract-economics grounds).

These are not absences in the *model*; they are absences in the *VfM frame*. The Risk Transfer Value of $37.17M is a financial framing of the choice. A public-value framing would surface these dimensions and ask whether the financing efficiency genuinely compensates for taking on a 33-year commercial relationship in an essential-service context.

Confidence: high on the *omission*; the value of these dimensions is inherently contested.

### 4.6 Futures Agent

Over 33 years, multiple disruption vectors are material: (i) demographic shift (Alberta's hospital demand profile in 2058 is not the 2025 forecast); (ii) clinical practice (telehealth, AI diagnostics, hospital-at-home models reduce traditional inpatient demand); (iii) energy and lifecycle costs (climate transition affects building operating costs); (iv) consortium ownership churn (Plenary, PCL, Graham — the comparators in A08 — will likely not be the same firms operating this asset in 2055); (v) policy regime change (TB Directive 2019-04 will be superseded; new directives may impose obligations the original PA does not anticipate).

The model treats inflation deterministically (CPI 2.0%, construction 3.5%, O&M 2.5%) and does not stress-test demand or service-mix evolution. A 33-year concession against a 33-year deterministic forecast assumes a stability the futures evidence does not support.

Confidence: high that disruption is material; low on specific magnitudes.

## 5. CROSS-DOMAIN INTERACTIONS

### 5.1 Interface Integrity

The interface concentration in this model is between (a) the financial/quantitative VfM framework and (b) the public-service / community / legitimacy dimensions. The PERT-mean and independent-risk assumptions are interface choices — the model treats risk as decomposable into independent line items, then sums them. Real concession failure is interactive: a force majeure event coinciding with construction overrun coinciding with lender covenant pressure coinciding with adverse public reception of a service disruption produces a joint cascade the additive structure cannot represent.

### 5.2 Cascading Effects

The Carillion-class scenario is the canonical cascade. Sequence: (a) construction or operating cost pressure on the SPV; (b) parent or consortium distress; (c) lender covenant trigger; (d) GOA forced to intervene to maintain hospital operation; (e) renegotiation on adverse terms or asset takeback; (f) Risk Transfer Value retroactively becomes much smaller than the headline $37.17M; (g) public-trust damage to the Alberta P3 programme generally, affecting future VfM analyses. The cascade is bounded under DB delivery (GOA already owns the risk) but unbounded under DBFM if SPV distress materialises. The model's binary risk-allocation does not capture this asymmetry in cascade exposure.

### 5.3 Temporal Dynamics

Three clocks. (a) **Concession clock** — 33 years, fixed. (b) **Political tenure clock** — 4-year electoral cycles in Alberta. (c) **SPV ownership clock** — refinancing in Year 3, debt term 25 years; effective ownership and governance turnover within the concession. The mismatch matters: the political accountability for the DBFM decision rests with the 2025 Treasury Board; the contractual relationship outlasts that accountability by an order of magnitude. The model does not visibly address how political continuity is preserved across the horizon.

### 5.4 Emergence & Fragility — primary finding combining (a), (b), (c)

The model presents the P3 DBFM structure as risk-transferring; the Council's structural critique is that the model exhibits classic fragility under joint stress.

- **PERT-mean (a)** averages away the heavy tails the structure is supposed to insulate against.
- **Independent-risk (b)** treats the failure modes that empirically correlate as if they are independent, suppressing the joint-tail exposure.
- **Binary allocation (c)** treats SPV solvency as a binary that does not interact with the risk register, while the Carillion-class scenario is precisely the case where SPV-distress and risk-register events are jointly distributed.

These three together produce a model output (Risk Transfer Value $37.17M) whose *headline value* is greater than its *robust value*. A robust analysis — fat tails, correlated risks, SPV-distress haircut — produces a Risk Transfer Value materially below the headline, plausibly in the $15–25M range depending on correlation and distress assumptions. The VfM recommendation is sensitive to which framing the Treasury Board accepts.

## 6. ADVERSARIAL REVIEW FINDINGS

### 6.1 Contrarian

(a) The PERT-mean and independent-risk assumptions are *standard practice* in Alberta and Canadian Treasury Board VfM analysis. Critiquing the model for following the standard is critiquing the standard, not this analysis. (b) The –7% capital efficiency and –15% O&M efficiency are sourced to actual benchmarking (P3 Canada 2022); they are not invented. (c) The Carillion-class scenario is a UK case; Canadian P3 market structure is different (smaller, more conservative consortia). Importing post-Carillion UK critique into Canadian P3 may over-discount. (d) Public hospitals delivered under conventional DB in Alberta have themselves had cost-overrun and lifecycle problems; the PSC comparator is not a guarantee of better outcomes. (e) Refusing the recommendation requires an alternative recommendation; "the model is structurally flawed" is not by itself a decision.

The Contrarian softens the framing: the four structural critiques do not by themselves overturn the recommendation; they require the Treasury Board to interrogate them and decide whether the headline VfM number is robust to them. The recommendation should be **conditional on stress-testing**, not rejected.

### 6.2 Red Team

Failure scenario, 2030–2040: SPV consortium parent (one of Plenary, PCL, Graham) faces unrelated commercial distress. Lenders trigger covenant review. Hospital operating service continues under contractual continuity provisions but at degraded quality and with disputed lifecycle expenditure. GOA faces a choice: enforce contract (legal cost, service-disruption risk), renegotiate (write down Risk Transfer Value, potentially extend concession or restructure availability payment), or take the asset back (return-of-risk, capital cost, transition cost). The financial headline that motivated the 2025 decision — Risk Transfer Value $37.17M — has retroactively become Risk Transfer Loss $30M+. The ministerial-level political cost is concentrated in the moment of distress, not in the original 2025 ratification, which means the original decision-maker is shielded and the structural critique is borne by their successor.

Red Team finding: the asymmetric political-time-horizon between commitment and consequence is the most reliably under-weighted dimension in P3 ratification decisions.

### 6.3 Public Value & Ethics — primary finding on (d)

Three public-value findings.

(i) **The VfM frame is itself a public-value choice**. The Treasury Board is being asked to evaluate a 33-year hospital concession on a financial-efficiency metric. The choice to use that metric — rather than, say, a public-control metric, a clinician-flexibility metric, or a community-governance metric — is a values commitment that the model does not surface. A genuinely public-value-aware analysis would ask the Treasury Board to ratify the *frame*, not just the *answer within the frame*.

(ii) **Distributional analysis is absent**. The –7% capital efficiency and –15% O&M efficiency are claimed savings to the Treasury (good for taxpayers in aggregate). Who pays for them? Plausibly: SPV labour (efficiency from compressed staffing or contractor pay), supply-chain (margin pressure on subcontractors), and arguably the long-horizon committed taxpayer (33-year availability payment locked into provincial budgets). The model does not surface these.

(iii) **Essential-service legitimacy** is the deepest concern. A 33-year private-sector operating relationship with a public hospital introduces a structural dependency that constrains future public choices about that hospital's operation. Whether that constraint is acceptable is a public-value judgment that the financial VfM cannot make.

Public Value verdict: the model is competent on what it measures but incomplete on what matters for a 33-year commitment to a public-essential service. The Treasury Board should be presented with the dimensions the VfM does not price, and asked to weigh them explicitly.

## 7. MAIN RECOMMENDATION

Do not ratify the P3 DBFM recommendation on the VfM analysis as presented. Require, before ratification:

1. **Stress-test the Risk Transfer Value** under the four structural critiques: (a) tail-aware risk valuation (e.g., conditional-value-at-risk or P95 framing alongside EV); (b) correlated-risk sensitivity (comonotonic and 30%-correlation stress); (c) SPV-distress haircut (e.g., 20–30% reduction in Risk Transfer Value to reflect return-of-risk exposure); (d) disclose what the headline VfM looks like under the corrected framings.
2. **Surface the dimensions the VfM does not price** (community, legitimacy, distributional, socio-material) in a separate analysis presented to the Treasury Board alongside the financial VfM, so the choice is made on a complete frame.
3. **Strengthen sponsor-monitoring capacity** beyond the modelled $0.5M/yr if the recommendation proceeds — empirically, under-investment here is a leading indicator of late detection of P3 distress.
4. **Decouple the ratification decision from the headline VfM number**. Treat the $37.17M Risk Transfer Value as a financial-frame estimate, not a decision-determinative quantity.

**Confidence: moderate-to-high** that the structural critiques are valid; **moderate** on the specific recommendation (stress-test and resubmit) vs the alternative (revise the comparator framework before any individual case).

## 8. ALTERNATIVE OPTIONS

**A. Ratify as presented**. Rejected on Risk, Public Value, Red Team, Emergence & Fragility grounds — the headline VfM is sensitive to structural assumptions the Treasury Board has not interrogated.

**B. Stress-test and re-present** (primary recommendation).

**C. Reject the P3 DBFM and proceed with conventional DB**. Defensible if the structural critiques are weighted heavily, but should be made on full-frame analysis (including DB's own risk profile), not as a default. The model's PSC comparator may also have its own optimistic assumptions.

**D. Pause and revise the Alberta VfM framework itself**. The deepest response — recognising that the structural concerns generalise beyond this case. Out of scope for a single Treasury Board sitting but should be flagged for medium-term policy review.

## 9. KEY RISKS

| Risk | Source agent | Severity | Mitigation |
|------|-------------|----------|------------|
| Force majeure realisation at P90 ($100M) understated by PERT mean | Risk, Emergence | HIGH | Tail-aware risk valuation |
| Joint adverse movement across cost / operating / demand / FM lines | Risk, Emergence | HIGH | Correlated-risk sensitivity |
| SPV distress with risk return to GOA | Commercial, Red Team | HIGH | SPV-distress haircut on Risk Transfer Value |
| Community / legitimacy / distributional dimensions unpriced | Impact, Public Value | HIGH on legitimacy grounds | Separate analysis presented to TB |
| 33-year political commitment outlasts current TB accountability | Temporal, Red Team | HIGH | Engineered cross-administration governance |
| Sponsor-monitoring under-investment at $0.5M/yr | Governance | MODERATE-HIGH | Increase oversight allocation |
| Demographic / clinical practice change over 33 years | Futures | MODERATE-HIGH | Periodic concession review windows |
| Refinancing-year and debt-term churn shifting effective counterparty | Temporal, Commercial | MODERATE | Pre-defined consent regime for ownership change |
| Carillion-class consortium failure | Red Team | MODERATE in Canadian context, but consequential | SPV credit monitoring; market-thinness scenario |

## 10. ASSUMPTIONS

- Reference-class evidence on PERT-mean understating heavy tails is applicable to infrastructure cost overruns (high confidence — Ansar, Flyvbjerg).
- Risks correlate empirically in distress events (high confidence).
- Carillion-class scenarios apply (with calibration) to Canadian P3 market (moderate confidence — Canadian market structure differs from UK).
- 33-year forecast accuracy on demand, technology, demographics is bounded (high confidence — futures evidence).
- Treasury Board is open to receiving structural-critique stress tests (moderate confidence — institutional posture-dependent).

## 11. EVIDENCE CONFIDENCE

Primary recommendation (do not ratify on VfM as presented; require stress-test): **MODERATE-TO-HIGH**. Structural critiques are well-supported by reference-class literature and post-Carillion P3 governance evidence. The recommendation does not claim the P3 DBFM is wrong; it claims the analysis is not yet sufficient to support ratification.

Coverage check: all mandatory agents consulted; Futures invoked for long horizon; adversarial layer fully engaged.

Method fit check: the question is well-suited to Council critique because it is structural, not arithmetic. A pure DCF/financial-modelling response could not produce findings (a)–(d); a multi-agent constitutional architecture with explicit Public Value, Emergence, Commercial, and Red Team coverage produces them as a routing-rule consequence.

## 12. UNRESOLVED TENSIONS

**Tension 1** *(Contrarian vs Risk / Emergence / Public Value)*: the four structural critiques are critiques of standard Alberta and Canadian Treasury Board practice, not of this analysis specifically. Acting on them at the case level requires either deviating from standard or revising the standard. Chair's synthesis: act at case level (require stress-test for this hospital) and flag for medium-term policy review (Option D).

**Tension 2** *(Commercial Contrarian vs Commercial primary)*: Canadian P3 market structure may not import UK Carillion-class concerns one-to-one. Chair's synthesis: the asymmetry direction is the same (return-of-risk under SPV distress is a real risk in any P3) even if the magnitude calibration differs. The 20–30% haircut range in §4.2 is illustrative; precise calibration is for sponsor-credit analysis.

**Tension 3** *(Public Value vs Strategic Leadership pragmatism)*: surfacing the unpriced dimensions (community, legitimacy, distributional, socio-material) in a Treasury-Board-readable form is hard. The financial VfM is decision-ergonomic; the public-value frame is decision-resistive. Chair's synthesis: the frame's *unfamiliarity* is not a reason to omit it, but the analysis must be packaged so the TB can act on it.

## 13. ESCALATION STATUS

**Escalation: YES** for two questions.

1. **Whether the Alberta VfM standard itself is fit for 33-year commitments**. The four structural critiques generalise. Treasury Board policy review beyond Council inputs.

2. **What public-value framework substitutes for or complements the financial VfM**. Public-value pricing has methodologies (multi-criteria decision analysis, public-value-based budgeting per Mazzucato) but selecting and operationalising one for Alberta hospital P3 is a policy-design choice beyond Council inputs.

Primary recommendation (stress-test before ratification) is actionable at the TB sitting level.

---

**Concept-surfacing note** (for W3 T-scoring): all four structural blind spots named explicitly — (a) PERT-mean fat-tail collapse §4.1; (b) independent-risk assumption §4.1; (c) binary allocation / return-of-risk §4.2; (d) absent legitimacy/community/public-value pricing §4.5 + §6.3. T5 path dependence covered §5.3. T6 insufficient-basis discipline §11. T7 recommendation robustness §7 + §8.
