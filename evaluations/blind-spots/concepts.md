# Blind-Spots Audit — MMPM Concept List

**Status**: DRAFT v0 — 22 canonical concepts proposed, awaiting verification.

## Purpose

Test whether Claude Opus, given a realistic programme vignette, raises the relevant MMPM concept *unprompted*, only when prompted, or misses it entirely. Then repeat with MMPM-COS and measure the delta.

This is the lighter-weight workstream. One long weekend of output, one paper-style writeup with a single large table. High interpretability for reviewers who want a clean "what does the system add" summary.

## Selection criteria

1. **Canonical in MMPM curriculum** — appears in Flyvbjerg, Morris, Merrow, Perrow, Scott, Kahneman, Drummond, Hirschman, or equivalent.
2. **Operationally identifiable** — the concept, if applied, changes how one analyzes a decision.
3. **Not trivially cued by common English** — e.g., "risk" is too broad; "tight coupling" is specific enough to test recognition rather than keyword recall.
4. **Coverage across MMPM domains** — strategy, governance, commercial, risk, leadership, impact, futures; plus cross-domain / adversarial concepts.

## Proposed concept list (22)

### Strategy & decision-making
1. **Reference class forecasting** (Flyvbjerg / Kahneman)
2. **Optimism bias** (Flyvbjerg, Kahneman)
3. **Strategic misrepresentation** (Flyvbjerg)
4. **Escalation of commitment** (Staw, Drummond)
5. **Sunk cost fallacy in programme contexts**

### Governance & institutional
6. **Principal-agent problems at the political interface** (Flyvbjerg; Morris)
7. **Governance fragmentation / multi-principal accountability**
8. **Stakeholder stratigraphy** (layered stakeholder structure — Scott, Morris)
9. **Legitimacy erosion** (Beetham; applied to programmes)
10. **Assurance capture** (NAO literature; UK PAC reports)

### Risk & uncertainty
11. **Tight coupling** (Perrow) — interactive complexity + tight coupling = normal accidents
12. **Tail risk / fat-tailed exposure in infrastructure** (Taleb; Ansar et al.)
13. **Cascading failure across domains**
14. **Emergent risk from dependency density**

### Commercial & contracting
15. **Hold-up risk in long-horizon contracts**
16. **Optimism bias in benefit case construction**
17. **Risk transfer illusions in P3 structures**

### Socio-technical / impact
18. **Socio-material effects** (programmes act on people + institutions + material systems simultaneously)
19. **Hirschman's Hiding Hand** (benefits and costs both underestimated; creativity emerges)
20. **Local knowledge disregard** (Scott — seeing like a state)

### Temporal
21. **Clock mismatch** between political, delivery, community, benefit-realization timescales
22. **Path dependence and lock-in**

## Vignettes

Each concept gets a minimal vignette (~150-250 words) where the concept is clearly relevant but is not named. The vignette describes a programme situation; the test is whether the model surfaces the concept unprompted.

Vignettes live in `blind-spots/vignettes/{concept-slug}.md`.

## Conditions

Two conditions only for this workstream — the point is to measure concept coverage, not judgment quality.

- **A — Vanilla**: same system prompt as benchmark Condition A. User message is the vignette followed by: "What is your analysis of this situation? What risks or dynamics do you think the programme team should be paying attention to?"
- **B — MMPM-COS Council**: `/council` invoked on the vignette.

Flyvbjerg-primed is not run for this workstream — it would bias the optimism-bias and reference-class items.

## Scoring

Per concept per condition, the scorer categorizes:

- `raised_unprompted` — concept or a close synonym surfaced without the scorer mentioning it
- `raised_on_followup` — concept surfaced only after a scorer-posed followup question ("what about X-like dynamics here?")
- `missed` — concept not raised even on followup, OR surfaced but misapplied

### Depth rating (added post-first-pass, 2026-04-21)

The W2 first-pass pilot on 4 concepts showed Vanilla saturating at 100% `raised_unprompted`. Binary surfacing alone does not discriminate Council from Vanilla when both surface the concept. A depth rating is added to distinguish shallow naming from substantive application:

- **0** — concept named but mechanism not stated. E.g., "optimism bias" used as a label without a causal explanation of how it operates in this case.
- **1** — concept named with mechanism stated. Causal pathway articulated (e.g., "optimism bias: single-point estimates without contingency + advocacy-adjacent forecaster + absent reference class → likely cost understatement").
- **2** — concept named, mechanism stated, AND operationalised into the recommendation. The output's recommended action is shaped by the concept (e.g., "therefore require reference-class-based cost review before ratification").

Applicability note: the depth rating is added for subsequent W2 runs. The 4 concepts scored in the first-pass slice used binary surfacing only; comparing first-pass scores against depth-rated scores in future runs is not like-for-like.

Recorded in `blind-spots/scoring.csv`:

| Column | Type |
|--------|------|
| `concept_id` | int 1-22 |
| `concept_name` | string |
| `condition` | `vanilla` / `council` |
| `outcome` | `raised_unprompted` / `raised_on_followup` / `missed` |
| `depth` | int 0 / 1 / 2 — populated on subsequent runs; left empty for first-pass rows |
| `notes` | string |

Analysis produces a 22×2 coverage table, a depth-rating delta table, and concept-by-concept deltas on both surfacing and depth.

## What this workstream does not claim

- Not a claim about concept *quality of application*, only *surfacing*.
- Not a claim that these 22 concepts exhaust MMPM doctrine.
- Not a claim that the vignettes are representative — they are constructed to make the concept identifiable.
