# MMPM-COS Empirical Evaluation

**Status**: DRAFT v0 — methodology under review, no runs executed.

This directory contains the empirical evaluation of MMPM-COS. Its purpose is to test whether the constitutional multi-agent architecture produces materially better judgment on major programme decisions than (a) vanilla Claude and (b) Claude primed with a short outside-view / reference-class-forecasting prompt.

## Workstreams

| ID  | Workstream | Artifact | Status |
|-----|-----------|----------|--------|
| W1  | [Megaproject decision benchmark](benchmark/) | 8 case briefs × 3 conditions × 10-dimension rubric | scaffolded |
| W2  | [Blind-spots audit](blind-spots/) | 22 vignettes × 2 conditions, concept-coverage tabulation | scaffolded |
| W3  | [P3 tail-risk × adversarial layer](p3-tail-risk/) | Monte Carlo distribution → Council run → tail-risk surfacing score | awaiting VFM model |
| W4  | [Edmonton LRT deep case](deep-case/) | 4 decision points × Council run vs literature prediction | scaffolded |

## Cross-cutting docs

- [`methodology.md`](methodology.md) — conditions, rubric, scoring protocol, ground-truth discipline
- [`limitations.md`](limitations.md) — honest confounds across all workstreams

## Headline finding

*(To be written after W1 + W2 + W3 run. W4 is a narrative complement, not a primary finding source.)*

## Review order

If you're reviewing this cold, read in this order:
1. `methodology.md` — the rubric is the load-bearing artifact
2. `limitations.md` — confounds we name before they're used against us
3. `benchmark/cases.md` — which megaprojects and why
4. `benchmark/prompts/` — the three conditions, verbatim
5. `benchmark/brief-template.md` — what a decision brief must contain
6. `blind-spots/concepts.md` — the MMPM concept list
7. `p3-tail-risk/scenario.md` — the integration design (requires VFM model)
8. `deep-case/decision-points.md` — Edmonton LRT decision lifecycle
