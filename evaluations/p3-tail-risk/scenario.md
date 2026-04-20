# P3 Tail-Risk × Adversarial Layer — Scenario Design

**Status**: DRAFT v0 — interface-first design. Awaiting VFM model input (commit to repo, paste outputs, or describe structure).

## Research question

When a Monte Carlo VFM model produces a distribution of cost/NPV outcomes for a P3 vs conventional delivery comparison, does the MMPM-COS adversarial layer (Contrarian, Red Team, Emergence & Fragility, Public Value) surface the tail risks that mean-variance DCF analysis systematically understates?

This is the distinctive workstream. It sits at the intersection of Flyvbjerg (infrastructure cost distributions are fat-tailed), Taleb (mean-variance analysis misreads fat-tail exposure), and human-AI decision-making (does multi-agent deliberation change how fat-tail risk is weighted?).

## Hypothesis

H1: Given the same Monte Carlo output distribution, a Council-reviewed decision brief surfaces materially more of the following than a standard VFM summary:
- Fat-tail cost exposure (>P90)
- Risk-transfer illusions (risks formally transferred to private partner but that return under distress)
- Fragility-driving correlations (e.g., project-specific risk × systemic demand risk)
- Legitimacy risks not priced in DCF (community impact, equity effects)
- Path dependence (once P3 signed, exit costs shape future decisions)

## Study design

Single P3-vs-conventional scenario. Monte Carlo produces N simulated outcomes. Study proceeds in three stages:

### Stage 1 — Standard VFM write-up (baseline)

A conventional VFM comparison as a practitioner would produce: expected NPV under each delivery model, P50 / P90 cost, qualitative risk-transfer commentary, recommendation. Drawn from the model output without Council involvement.

Length: ~1000 words. This is what a board would typically see.

### Stage 2 — Monte Carlo output → Council input

The Council receives a structured brief containing:
- The scenario (scope, delivery model options, cost envelope)
- The Monte Carlo output summary (distribution shape, P50/P90/P99, tail examples, correlation structure)
- The Stage 1 VFM write-up for context
- Question: "The board is deciding between P3 DBFOM and conventional D-B-B delivery. The VFM analysis above recommends P3. What is your analysis?"

Council runs the full orchestration.

### Stage 3 — Differential analysis

Compare what Council surfaces against the Stage 1 VFM write-up. Scored on seven dimensions:

| Dimension | What it tests |
|-----------|---------------|
| T1 — Tail framing | Does the output treat >P90 outcomes as material, not residual? |
| T2 — Risk-transfer audit | Does the output question whether transferred risks stay transferred under distress? |
| T3 — Correlation surfacing | Does the output identify correlated exposures that inflate joint tail? |
| T4 — Legitimacy dimensions not in model | Does the output raise effects the Monte Carlo does not capture? |
| T5 — Path dependence | Does the output surface exit-cost asymmetry? |
| T6 — Insufficient-basis discipline | Does the output decline to endorse P3 if the evidence is mixed? |
| T7 — Recommendation robustness | Is the recommendation framed as robust to tail realizations, or only to the mean? |

Each scored 0/1/2, max 14.

## Interface to VFM model

The study does not need the full model, only the interface — what the model produces that becomes Council input.

### Minimum viable input

If you commit the VFM model to `evaluations/p3-tail-risk/model/`, or paste outputs into `evaluations/p3-tail-risk/data/monte-carlo-output.md`, the study needs:

1. **Scenario description** — scope, schedule envelope, capex envelope, opex envelope, delivery models compared.
2. **Monte Carlo structure** — which variables are parameterized, which distributions, which correlations.
3. **Output distribution** — either:
   - (a) the full simulation output as CSV (N rows × variables), OR
   - (b) summary statistics: mean, P10, P25, P50, P75, P90, P95, P99, max; plus tail exemplars (e.g., three worst realizations with scenario descriptions).
4. **Recommendation produced by the model** — which delivery option dominates on expected NPV, and by how much.
5. **What the model does NOT capture** — explicitly named (e.g., political risk, legitimacy, technology obsolescence).

Item 5 is particularly important — it is the boundary of the DCF paradigm the Council is testing against.

### Preferred format

```
evaluations/p3-tail-risk/
├── model/                             # the VFM model itself, if committable
│   └── {model files}
├── data/
│   ├── scenario.md                    # items 1, 2, 5 above
│   ├── monte-carlo-output.csv         # item 3a
│   └── monte-carlo-summary.md         # item 3b (if full CSV not feasible)
├── stage1-vfm-writeup.md              # baseline
├── stage2-council-run.md              # Council output
├── stage3-scoring.md                  # T1-T7 scored
└── findings.md                        # writeup
```

## What to paste if not committing the model

If you paste summary rather than commit:

```
## Scenario
{1-2 paragraphs describing the project and the two delivery options}

## Monte Carlo structure
- Variables parameterized: {list}
- Distributions assumed: {list}
- Correlations modeled: {list}
- Number of simulations: {N}

## Output summary (NPV, $M, P3 minus conventional; negative = P3 cheaper)
- Mean: {value}
- P10: {value}
- P25: {value}
- P50: {value}
- P75: {value}
- P90: {value}
- P95: {value}
- P99: {value}

## Tail exemplars (worst 3 realizations)
1. {description}
2. {description}
3. {description}

## Model recommendation
{one paragraph}

## Known model limitations
{bullets — what the model cannot price}
```

## What this workstream does not claim

- Not a claim that the specific P3 scenario generalizes.
- Not a claim that Council-surfaced risks are *correct* — they may also be phantom risks.
- Not a claim that mean-variance DCF is wrong; the claim is narrower — it systematically understates certain classes of exposure, and multi-agent deliberation surfaces some of them.
- Not a claim that Council > human expert. The baseline is the VFM write-up, not a human reviewer.
