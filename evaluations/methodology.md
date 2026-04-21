# Evaluation Methodology

**Status**: v1 — first-pass runs complete (2026-04-20). Revised 2026-04-21 to document methodology-level findings from the first-pass runs. Any subsequent study should incorporate §11 and §12.

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

---

## 10. Post-first-pass addenda

The sections below were added 2026-04-21 after the first-pass runs completed and exposed methodology-level issues that any subsequent study must address. Section numbers continue from §9.

## 11. Actor separation requirement (addresses designer-as-scorer confound)

**Finding from first-pass**: the single operator (one Claude session) produced the Council outputs, authored `deep-case/literature-expected.md`, and scored the rubric. Information flowed between these steps — for example, the operator read the BER W1 pilot score before producing HS2/Crossrail/Edmonton/CAHSR Council outputs, which plausibly nudged later Council outputs toward closing the D4 routing gap identified in BER. The W4 30/30 surfacing rate is similarly discounted because the operator authored both the literature-expected list and the Council outputs being scored against it.

**Requirement for any subsequent study**: three distinct actors, with no information flow between them during the study window:

1. **Runner**: produces Council, Vanilla, and Flyvbjerg outputs from briefs. Does not see the rubric dimensions in advance; does not see scoring; does not see `literature-expected.md`. Records outputs verbatim.
2. **Scorer**: produces scores from outputs against the rubric. Does not produce outputs; does not see the literature-expected list until D2 audit (per §3 ground-truth discipline).
3. **Methodology author**: authors the rubric, the literature-expected list, and the methodology document. Does not run outputs; does not score. Authorship of these documents must precede the study window.

If three actors are not available, a single-actor protocol is still defensible IF the artifacts are produced in a strictly sequenced order with dated commits and no post-hoc revision: (a) methodology + rubric + literature-expected → (b) runner outputs → (c) scoring. The first-pass of this study did not meet this bar; findings should be weighted accordingly.

## 12. Condition A/B clean-session requirement

**Finding from first-pass**: Conditions A (Vanilla) and B (Flyvbjerg-primed) were run via sub-agents spawned from a Claude Code session with full MMPM-COS constitutional context (CLAUDE.md, configs/, agents/, commands/) in the parent. Mechanical contamination-check per `benchmark/prompts/contamination-check.md` passed on all runs, but residual context-bleed cannot be ruled out.

**Requirement for any subsequent study**: Conditions A and B MUST be run in a Claude session that does NOT have the MMPM-COS project in context. Options:

1. **Claude.ai web session** outside the repo. Paste the system prompt and user message verbatim. Copy the raw output into `benchmark/outputs/{case}/{condition}.md` with no editing.
2. **Claude API** call from outside the repo with only the specified system prompt. Store response verbatim.
3. **Claude Code session in an empty directory** with no CLAUDE.md and no project files.

Sub-agent role-isolation (as used in the first-pass) is acceptable ONLY if the three cleaner options are operationally impossible, and must be flagged explicitly in the output file header and in `limitations.md §14`.

## 13. Scoring instrument depth for W2

**Finding from first-pass**: the W2 pilot (4 of 22 concepts) showed Vanilla saturating at 100% concept-surfacing on the selected concepts. The binary scoring schema (`raised_unprompted` / `raised_on_followup` / `missed`) cannot distinguish Council from Vanilla when both surface the concept. For the W2 instrument to produce discriminating data, the schema must augment the binary with depth:

**Revised W2 scoring schema (for subsequent studies)**:

- **Surfacing level** (existing binary): `raised_unprompted` / `raised_on_followup` / `missed`.
- **Depth rating** (0/1/2, added post-first-pass):
  - **0** — concept named but mechanism not stated (e.g., "optimism bias" as label without causal explanation)
  - **1** — concept named with mechanism stated (causal pathway articulated)
  - **2** — concept named, mechanism stated, AND operationalised into recommendation (the output's action-recommendation is shaped by the concept)

Combined outcome is `{surfacing level, depth rating}`. This allows the instrument to distinguish "Vanilla names the concept but does not act on it" from "Council names the concept, explains the mechanism, and rewrites the recommendation".

Note on applicability: the depth rating adds scorer workload and should not be added mid-study. Apply to subsequent W2 runs, not to the 4 completed in the first-pass slice.

## 14. Sign-off as a hard gate

**Finding from first-pass**: the operator signed off on methodology defaults on the user's behalf (see `SIGN-OFF.md` dated 2026-04-20). Items marked `[?]` — case substitutions, concept list adjustments, rubric dimension confirmations — were deferred. This produced a study that ran without user confirmation of the case list and the concept list, and therefore any post-study user objection to those choices would invalidate the affected runs.

**Requirement for any subsequent study**: `SIGN-OFF.md` is a literal gating mechanism, not advisory:

1. **No runs committed to the benchmark, vignette, or deep-case directories until SIGN-OFF.md has all `[?]` items resolved by the designated user** (typically the designer-scorer, but see §11 — ideally three distinct actors).
2. **Sign-off is recorded with a git commit** on a branch created for the study; the sign-off commit precedes all run commits.
3. **Post-signoff scope changes** (substituting a case, swapping a concept, adjusting the rubric) require a new sign-off entry and invalidate any runs affected by the change.
4. **The sign-off file is the methodological audit trail**. A reviewer should be able to read `SIGN-OFF.md` and identify exactly what was approved, by whom, and when.

This is not bureaucratic — it is the mechanism by which the study can withstand post-hoc challenge on case selection, rubric design, or methodology.
