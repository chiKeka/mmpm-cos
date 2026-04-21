# Evidence Quality Gate — Implementation Reference

Added post-evaluation. The Evidence Quality Gate is a Chair sub-function (see `CLAUDE.md` §Evidence Quality Gate) that runs before synthesis. This document specifies the routines the Gate executes.

## Gate routines (in order)

### 1. Claim-Evidence Matching

For each key finding in the draft synthesis, verify that claim strength is proportionate to evidence quality. Strong claim ("the programme will fail") + weak evidence ("this feels risky") = downgrade or caveat.

### 2. Method Fit Check

Are the types of evidence appropriate for the types of claims being made? Reference-class base rates support directional cost/schedule/demand claims but not specific magnitude; technical-systems claims require technical-systems evidence which Council typically cannot provide from a brief alone.

### 3. Inference Chain Audit

Can the reasoning chain from evidence to conclusion be followed? Are there unsupported leaps? Each Council recommendation must trace back to specific evidence through named agent findings.

### 4. Confidence Calibration

Is the stated confidence consistent with the evidence quality, assumption stability, and cross-domain completeness? If >50% of consulted agents report low confidence, system confidence cannot exceed "low".

### 5. Fluency Trap Detection

Is any part of the synthesis polished and confident but actually resting on weak evidence or unexamined assumptions? The 13-section structure can produce fluent-sounding syntheses that obscure thin evidence.

### 6. Reference-Class Presence Check *(added post-eval)*

Per routing rule 9: if the decision has a nameable reference class, Risk Agent output must invoke it with base rates. If absent, Gate flags as an omission and either (a) requires Risk Agent to produce before synthesis proceeds, or (b) notes the absence explicitly in the Evidence Confidence section.

### 7. Financial-Model Structural Critique *(added post-eval)*

Per routing rule 10: if the input contains a quantified risk / VfM / BCR / financial-model analysis, Gate runs the four-point structural check before synthesis.

#### The four points

**(a) Fat-tail treatment of heavy-tailed risks.** Does the model average heavy-tailed distributions (PERT-mean, single-point EV) into numbers that understate the tail? Reference: Ansar, Flyvbjerg, Bun on heavy tails in infrastructure cost and force-majeure distributions. The canonical signal: force-majeure or cost-overrun P90s collapsed into EV via PERT-mean weighting (P50 weighted 4× the tails).

**(b) Independent-risk assumption.** Are risk line-items summed as if independent? Empirically, cost overruns correlate with schedule delays, operating cost with lifecycle underestimation, demand shocks with regulatory/force-majeure events, design deficiency with commissioning. Joint-tail stress produces aggregate exposure materially larger than sum-of-independent-EVs. Council should estimate comonotonic and moderate-correlation stress alongside the model's independent aggregation.

**(c) Binary risk allocation without return-of-risk.** Does the model treat risk allocation as 0% / 50% / 100% retention per risk per delivery model, with no line for return-of-risk under counterparty distress? Reference: post-Carillion P3 literature (Siemiatycki, Vining & Boardman). The canonical signal: SPV solvency treated as a binary that does not interact with the risk register. Council should propose a distress-haircut (20–30% typical) on Risk Transfer Value.

**(d) Absent legitimacy / community / public-value pricing.** Does the model price construction / operating / lifecycle / demand / regulatory / force-majeure risk but not community impact, legitimacy of long-horizon concessions, distributional consequences, or socio-material effects? Reference: Mazzucato on public-value framing; Beetham on legitimacy applied to programmes. Council surfaces these as dimensions the model definitionally excludes.

#### Gate action

If the structural critique identifies any of (a)–(d), Gate requires that:
1. The four-point critique is explicit in the Council synthesis (§4 Risk or §6.3 Public Value as appropriate).
2. The synthesis recommendation acknowledges sensitivity to the four points (e.g., "stress-test the Risk Transfer Value under (a)–(d) before ratification").
3. The Evidence Confidence section (§11) cites the structural-critique findings as load-bearing.

Not surfacing (a)–(d) on a financial-model input is a Gate failure, not an agent-level oversight.

## Gate failure handling

If any routine flags a problem, Gate requires one of:
- Downgrade confidence
- Add explicit caveats in synthesis
- Flag weakness in Unresolved Tensions (§12)
- Trigger escalation if severe

Gate must NEVER silently pass through weaknesses it has detected. The Chair cannot override Gate findings — only preserve them or escalate them.

## Provenance note

This document was drafted 2026-04-21 after the Evaluation Workstream surfaced consistent patterns across W1 / W3 that the Gate was not explicitly running. Codifying them converts ad-hoc findings into reliable system behaviour.
