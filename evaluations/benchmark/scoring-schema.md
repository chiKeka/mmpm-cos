# Scoring Schema

**Status**: DRAFT v0 — awaiting verification.

Raw scores are recorded in `benchmark/scores/scored-rubric.csv`. One row per (case × condition) pair. 24 rows total (8 cases × 3 conditions).

## CSV columns

| Column | Type | Notes |
|--------|------|-------|
| `case_id` | string | e.g., `ber`, `cahsr`, `hs2`, `sydney-opera`, `big-dig`, `crossrail`, `kashagan`, `edm-valley-line` |
| `condition` | enum | `vanilla` / `flyvbjerg` / `council` |
| `model_version` | string | e.g., `claude-opus-4-7` |
| `run_date` | ISO-8601 date | |
| `temperature` | float | recorded per run |
| `output_word_count` | int | word count of the raw output |
| `output_path` | string | path to raw output file, e.g., `benchmark/outputs/ber/council.md` |
| `d1_optimism_markers` | int 0/1/2 | |
| `d1_reason` | string | one-sentence justification, cites output quote or its absence |
| `d2_risk_class` | int 0/1/2 | scored against contemporaneous-markers list in ground-truth |
| `d2_reason` | string | |
| `d3_coupling` | int 0/1/2 | |
| `d3_reason` | string | |
| `d4_outside_view` | int 0/1/2 | |
| `d4_reason` | string | |
| `d5_dissent` | int 0/1/2 | |
| `d5_reason` | string | |
| `d6_evidence_calibration` | int 0/1/2 | |
| `d6_reason` | string | |
| `d7_legitimacy` | int 0/1/2 | |
| `d7_reason` | string | |
| `d8_temporal` | int 0/1/2 | |
| `d8_reason` | string | |
| `d9_insufficient_basis` | int 0/1/2 | |
| `d9_reason` | string | |
| `d10_traceability` | int 0/1/2 | |
| `d10_reason` | string | |
| `total` | int 0–20 | computed |
| `total_normalized` | float | `total / (output_word_count / 100)` — penalizes verbosity |
| `scorer_notes` | string | free text, any post-scoring observations |

## Derived tables produced by analysis script

After all 24 rows are scored:

- `results/condition-dimension-means.csv` — mean score per condition per dimension
- `results/case-condition-totals.csv` — 8×3 matrix of totals
- `results/deltas.csv` — Council − Vanilla, Council − Flyvbjerg, per dimension and total
- `results/wilcoxon.csv` — Wilcoxon signed-rank test on paired per-case totals (Council vs Vanilla, Council vs Flyvbjerg), reporting statistic and p-value with explicit N=8 caveat

## Scoring order (to manage order effects)

Per methodology §9, scoring proceeds per-case with all three conditions scored in the same sitting, but case order is randomized. The randomized case order is recorded at the top of `scored-rubric.csv` as a comment for auditability.

## Audit trail

Every cell with a non-zero score has a justification in the adjacent `_reason` column. A reader with access to the raw outputs can re-audit any score without contacting the scorer.
