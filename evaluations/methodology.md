# Evaluation Methodology

**Status**: DRAFT v0 — awaiting verification before any runs.

## 1. Research question

Does a constitutional multi-agent architecture grounded in Oxford MMPM doctrine (MMPM-COS) produce measurably better programme-decision judgment than (a) unprimed Claude Opus and (b) Claude Opus primed with a short outside-view / reference-class-forecasting preamble?

"Better" is operationalized by a 10-dimension rubric derived from the MMPM-COS constitution (see §4). The study is not a test of correctness — outcomes are unknowable at the decision moment — but of whether the output surfaces the analytical structures that, in hindsight, would have distinguished a robust decision process from a fragile one.

## 2. Design

Within-subjects, three-condition comparison across 8 megaproject decision cases (W1), 22 MMPM-concept vignettes (W2), one P3 Monte Carlo scenario (W3), and four Edmonton LRT decision points (W4).

### Conditions (W1, W2, W4)

- **A — Vanilla**: Claude Opus with only a generic "you are an advisor to the programme board" frame. No MMPM doctrine, no reference-class primer.
- **B — Flyvbjerg-primed**: Claude Opus with a short outside-view prompt grounded in reference-class forecasting and optimism-bias research. Represents "off-the-shelf best practice."
- **C — MMPM-COS Council**: Full `/council` invocation against the same input.

For W3 (P3 tail-risk), the comparison is single-condition — Council output against what mean-variance DCF analysis would surface — because the research question is about fat-tail risk surfacing, not comparative judgment quality.

### Input discipline

Every case brief describes the decision context **as known at the time of the go/no-go or scope-commitment moment**. Outcomes are documented separately in a sealed ground-truth appendix, opened only at scoring.

## 3. Ground-truth discipline

The fundamental methodological challenge: we know how these projects turned out, and that knowledge leaks into both (a) the way briefs are written and (b) the way outputs are scored.

Mitigations:

1. **Contemporaneous-source discipline for briefs.** Each brief is constructed from sources dated *before* the decision moment where possible (news, parliamentary inquiries filed before the decision, contemporaneous risk registers, cost estimates published at the time). Retrospective sources are used only to identify what information *was* available at the decision moment, not to import hindsight framing.
2. **Hindsight-stripped language.** No phrases like "as would later become clear," "the fatal flaw was," or "in retrospect." Claim-level audit: any sentence that couldn't have been written contemporaneously gets cut.
3. **Ground-truth sealed until scoring.** Outcomes, cost overruns, schedule slippage, and post-mortem risk classification live in `benchmark/briefs/{case}.ground-truth.md`, written last, not referenced during brief construction.
4. **Scorer blinding where feasible.** Scorer reads the three outputs for a case, scores them on all ten dimensions, THEN reads the ground-truth file. Rubric dimensions that require hindsight (D2: risk-class identification) are scored against markers that were *present in contemporaneous source material* — not against what later happened. The ground-truth file lists both.

This discipline will be imperfect. It is documented as a limitation in `limitations.md`.

## 4. Scoring rubric

Ten dimensions, each scored 0 / 1 / 2. Maximum 20 per output. Scorer justifies each score with a one-sentence reason quoted from the output or its absence.

### D1 — Optimism-bias markers identified

Whether the output flags signals of optimism bias visible in the source material (single-point cost estimates, unprecedented benefit uptake, schedule compression, novel-technology risk treated as manageable, absence of reference-class data).

- 0: no markers identified
- 1: generic caveats about "being realistic" without naming specific markers
- 2: named specific markers present in the brief, tied to specific decision claims

### D2 — Risk-class identification

Whether the output identifies the risk classes that the source material flagged or that were contemporaneously identifiable. **Scored against markers present in the brief**, not against known outcomes.

Risk classes tracked: scope creep, tight coupling, stakeholder fragmentation, political time-horizon mismatch, escalation of commitment, novel-technology integration risk, governance fragmentation, commercial misalignment, legitimacy erosion, fat-tail cost/schedule exposure.

- 0: missed the risk classes flagged by contemporaneous material
- 1: partial — identified some, missed major ones
- 2: identified the risk classes contemporaneously identifiable, with reasoning

### D3 — Cross-domain coupling surfaced

Whether the output identifies interaction effects across domains rather than treating each domain in isolation.

- 0: single-domain reasoning or domains treated independently
- 1: coupling acknowledged abstractly ("these are related")
- 2: specific cross-domain interaction named (e.g., "the D-B-F-M contract model reduces governance agility because…")

### D4 — Outside-view / reference-class reasoning

Whether the output invokes reference-class forecasting, base rates, or historical analogues rather than reasoning purely from the project's own narrative.

- 0: pure inside view — reasoning from the project's own optimism
- 1: acknowledged relevance of outside view without applying it
- 2: applied — specific reference class invoked, base-rate implication drawn

### D5 — Dissent preservation

Whether the output surfaces genuine disagreement or tension, or converges to a smooth consensus narrative.

- 0: single confident narrative, no dissent
- 1: gestures at "some considerations" but ultimately converges
- 2: preserves named tension with explicit unresolved questions

### D6 — Evidence–claim calibration

Whether claim strength is proportionate to evidence strength. Strong recommendations on weak evidence = 0. Qualified recommendations with explicit uncertainty = 2.

- 0: confident assertions unsupported by stated evidence
- 1: mixed — some calibrated, some not
- 2: claim strength matches evidence throughout; uncertainty explicit

### D7 — Stakeholder legitimacy / public value

Whether the output surfaces affected populations, legitimacy risks, and exclusions beyond internal programme metrics.

- 0: success framed only in programme-delivery terms
- 1: stakeholders noted narrowly (opposition, regulators)
- 2: affected populations named, legitimacy risks surfaced, distributional effects considered

### D8 — Temporal mismatch identification

Whether the output identifies clock mismatches between political, delivery, benefit-realization, and community timescales.

- 0: single-timeline reasoning
- 1: timing mentioned abstractly
- 2: specific clock mismatch identified (e.g., "benefit case assumes 30-year horizon; sponsor term is 4 years")

### D9 — Escalation / insufficient-basis discipline

Whether the output recommends escalation or says "insufficient basis" when the evidence warrants it, rather than producing a confident recommendation regardless.

- 0: produces confident recommendation regardless of evidence state
- 1: recommendation made with caveats
- 2: explicitly flags escalation conditions, insufficient-basis signals, or hard-stop criteria

### D10 — Traceability

Whether the reasoning chain is inspectable — sources cited, assumptions typed, confidence justified.

- 0: opaque reasoning, no assumptions flagged, no confidence stated
- 1: partial transparency
- 2: assumptions named, evidence basis stated per claim, confidence level justified

## 5. Scoring protocol

1. Read the three outputs for the case cold.
2. Score each output on all ten dimensions with a one-sentence reason per score.
3. Open the ground-truth file.
4. Audit D2 scores against the contemporaneous-markers list in the ground-truth file. Adjust if you had imported hindsight.
5. Record final scores in `benchmark/scores/scored-rubric.csv` (schema in `benchmark/scoring-schema.md`).
6. After all cases scored, compute:
   - Mean score per condition per dimension
   - Delta: Council − Vanilla, Council − Flyvbjerg-primed, per dimension
   - Non-parametric test (Wilcoxon signed-rank) on paired per-case totals; report test statistic and p-value but do not over-claim with N=8.

## 6. Inter-rater reliability

No co-rater. This is a single-scorer study. Consequences documented in `limitations.md`. Partial mitigation: scorer's reasoning is recorded per dimension per output, so scoring can be re-audited post hoc by any reader.

## 7. Prompt hygiene

- Single prompt per condition. No prompt ensembling, no best-of-N.
- Same Claude model version across all runs (recorded in CSV).
- Temperature recorded.
- Full prompts stored verbatim in `benchmark/prompts/`.
- Full raw outputs stored in `benchmark/outputs/{case}/{condition}.md` with no editing.

## 8. Model / version control

All runs executed within a single working session window. Model ID, date, and any system prompt context recorded per output file. If the model version changes mid-study, the study is re-run from scratch — no mixing versions.

## 9. What this study does not claim

- **Not a claim that Council is "correct."** Correctness is unknowable at the decision moment.
- **Not a claim of generalization.** N=8 on a curated case list is descriptive, not inferential.
- **Not a claim that the rubric is the right rubric.** It is one rubric, derived from the system's own constitution. A reader could disagree with the dimensions and the paper would still hold as a descriptive artifact.
- **Not a claim about human-plus-AI performance.** The comparison is AI-alone under three conditions, not AI-augmented human judgment.
