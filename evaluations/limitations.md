# Limitations and Confounds

**Status**: DRAFT v0 — limitations named in advance of runs, not retrofitted after.

This document is load-bearing. A reviewer screening for research sensibility will look here before they look at the findings. Honest naming of confounds is stronger than polished findings with hidden ones.

## 1. Designer is scorer

The scorer (Chike Egbuneke) is also the system designer. This is the single largest confound. Mitigations:

- Per-score justification is recorded per dimension per output, so scoring can be audited by any reader without access to the scorer.
- Rubric was locked before any runs executed (see git history of `methodology.md`).
- D2 is explicitly scored against contemporaneous markers listed in the ground-truth file, not against outcome knowledge.

Residual confound: scorer may unconsciously favor MMPM-COS outputs because they match the rubric's MMPM-derived structure. This is partially *expected* — the rubric is derived from the system's own constitution, which is a known feature of designer-driven evaluation — but it means a Council advantage on, say, D10 (traceability) is less surprising than a Council advantage on D4 (outside-view reasoning), which MMPM-COS does not explicitly optimize for. Findings should be reported per dimension so readers can discount the rubric-aligned ones.

## 2. No co-rater

No inter-rater reliability statistic is available. A κ or Krippendorff's α would be the standard. Its absence is a legitimate critique. Partial mitigation: per-score justifications support post hoc auditability.

## 3. Single-model, single-prompt-per-condition

Results may reflect Claude-Opus-specific behavior or prompt-specific framing. No prompt sensitivity analysis. No cross-model replication. Any finding could be an artifact of a specific prompt wording.

## 4. Small N (benchmark: 8; blind-spots: 22; P3: 1; deep-case: 1)

Wilcoxon on paired benchmark scores with N=8 has limited statistical power. The study is descriptive, not inferential. Claims will be framed accordingly.

## 5. Case selection bias

Publicly documented megaprojects overrepresent spectacular failures (Berlin Brandenburg, Sydney Opera House) relative to quiet successes. A system that flags optimism bias will appear to perform better on failure-weighted cases. Mitigation: the case list includes at least two relative successes (Crossrail before 2018, Channel Tunnel post-operational) to test whether the system also produces appropriately tempered analysis when warranted. Even so, the case distribution is not representative.

## 6. Brief construction leaks hindsight

Writing a "decision brief at time T" while knowing what happened after T is inherently contaminated. Mitigation: contemporaneous-source discipline documented in `methodology.md` §3. Residual: unavoidable.

## 7. Rubric is the system's own rubric

The 10 dimensions are derived from the MMPM-COS constitution. A study built around a system's own definition of "good" will tend to find that system performs well. This is acknowledged and mitigated by:

- Four of the ten dimensions (D1, D4, D6, D9) are drawn from Flyvbjerg / Kahneman reference-class literature, not MMPM-specific.
- Per-dimension reporting lets readers discount MMPM-aligned dimensions (D3, D5, D7, D8) if they wish.
- A reader can substitute their own rubric against the same raw outputs.

## 8. Council is more verbose

Council outputs will be longer than vanilla outputs by design. Longer outputs trivially contain more of almost everything. Mitigations:

- Word-count per output is recorded in the CSV.
- A "normalized" score variant (score ÷ word-count-100s) is reported alongside raw scores.
- D5 (dissent preservation), D6 (evidence–claim calibration), and D9 (insufficient-basis discipline) are *harder* with more words, not easier — verbosity can hurt these dimensions.

## 9. Scorer fatigue

Scoring 24 benchmark outputs (8 cases × 3 conditions) plus 44 blind-spot outputs (22 × 2) plus P3 and Edmonton LRT materials in a compressed timeframe introduces fatigue effects. Mitigation: scoring is done in a fixed order (all Condition A first, then B, then C) and case ordering is recorded, so a reader can check for drift.

Wait — that mitigation creates its own bias (order effects). Revised: scoring is done per-case (A, B, C for case 1, then A, B, C for case 2, etc.) in random case order, with the condition-label hidden during scoring where feasible. Scorer will be able to infer condition from output structure, so full blinding is not possible.

## 10. MMPM-COS is a specification, not a running system at scoring time

The `/council` command invokes Claude with the MMPM-COS constitutional frame. It is not a separately trained model. Its performance is therefore bounded by what Claude can do when given the MMPM-COS prompt scaffold — not by an independent model architecture. This is relevant for reviewers who might misread Council as a fine-tuned system.

## 11. P3 workstream is a single-scenario case study

The P3 VfM model (`p3-tail-risk/model/P3_VfM_Model_v2.0.xlsx`) is committed to the repo, so reproducibility is intact. However: the model is an *illustrative* Alberta hospital DBFM scenario, not a live Treasury Board submission. Inputs (P10/P50/P90 per risk line, –7% capital efficiency, –15% operating efficiency) are judgment calls drawn from benchmarking literature. The W3 finding should be framed as a case study of what Council surfaces against a standard Treasury-Board-style writeup — not a benchmark claim about P3s generally.

Note that the model is **PERT-mean deterministic VfM with one-way sensitivity**, not Monte Carlo. An earlier version of the scenario design framed the W3 question as "Monte Carlo fat-tail surfacing"; this was revised (commit 43124a2) to "four structural blind spots of a PERT-mean VfM" — which is sharper and empirically testable against the actual artifact. Reviewers reading git history will see this pivot; it is documented in `p3-tail-risk/scenario.md`.

## 12. Timeboxing

The study was produced in a compressed timeframe before a submission deadline. Nothing about that timeframe is visible in the findings, but it affected depth of source review per case. Each brief was timeboxed at 45 minutes of source work; deeper readings would likely improve brief quality and could change scores.

## 13. Sources are canonically named, not URL-verified

All 8 benchmark `sources.md` files and the 4 deep-case briefs cite sources by canonical name (e.g., "Bundesrechnungshof reports on BER cost and schedule development", "NAO report *Completing Crossrail* (May 2019)", "Flyvbjerg case library") rather than by verified URL and exact page. The sandbox in which briefs were constructed had no outbound web access, so citations reflect canonical references present in training-knowledge synthesis rather than source-by-source reconstruction from live documents.

Consequences:
- A reviewer cannot click through to verify any individual source claim.
- Minor citation errors (wrong year, wrong report name within a family) cannot be caught by the construction process alone.
- D2 scoring (risk-class identification against contemporaneous markers) is the dimension most exposed: the contemporaneous markers in each `ground-truth.md` are drawn from training-knowledge about what was visible before the decision moment, and any marker that is in fact retrospective would bias D2 scores.

Mitigations:
- Each `sources.md` explicitly flags the no-web-access limitation.
- `ground-truth.md` files separate "Outcome summary" from "Contemporaneous markers" so a reader can audit each marker for hindsight leakage.
- Before publication, sources should be passed through a URL-verification sweep by the designer-scorer. Sources that cannot be verified should be replaced, removed, or kept with an explicit "canonical reference, URL not located" tag.

This is a material limitation. It does not invalidate the comparative study design — the same briefs are shown to all three conditions, so any residual hindsight contamination affects conditions symmetrically — but it does constrain how strongly any individual case-level finding can be interpreted.

## 14. Condition A/B execution environment

Conditions A (Vanilla) and B (Flyvbjerg-primed) are designed to represent "Claude without MMPM-COS priming" and "Claude with a Flyvbjerg outside-view preamble" respectively. Where these conditions are executed inside a Claude session or sub-agent that has the MMPM-COS constitutional `CLAUDE.md` in its working-directory context, residual contamination is possible even if the system prompt for A/B contains none of that doctrine — the model may still draw on the MMPM-COS frame it has read.

Mitigations:
- Conditions A and B should be executed in a Claude session or API call where `CLAUDE.md` and the `configs/`, `agents/`, `commands/` trees are not present in context. A clean Claude.ai conversation or an API call from outside the repo is preferred.
- Where A/B runs are executed via sub-agent tooling inside an MMPM-loaded session, the residual-contamination risk should be recorded in the output file header and factored into interpretation.
- If any A/B output exhibits telltale MMPM-COS structure (explicit "Chair", "Public Value Agent", "Evidence Quality Gate" sections) that output is re-run in a cleaner environment.

This is an operational limitation of the evaluation pipeline, not of the system under test. It is called out here so a reviewer auditing the output files can check each one for the contamination signature directly.
