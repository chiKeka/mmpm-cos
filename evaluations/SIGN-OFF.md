# Methodology Sign-Off Checklist

**Purpose**: Consolidate every "DRAFT v0 — awaiting verification" item scattered across the evaluation tree into one checklist. Sign-off gates the start of runs. Once signed, DRAFT v0 status strings are bumped to `v1 — signed off YYYY-MM-DD`.

**Status**: pending

---

## 1. Scope and framing

- [ ] **Research question** as stated in `methodology.md` §1:
  > "Does a constitutional multi-agent architecture grounded in Oxford MMPM doctrine (MMPM-COS) produce measurably better programme-decision judgment than (a) unprimed Claude Opus and (b) Claude Opus primed with a short outside-view / reference-class-forecasting preamble?"
- [ ] **Three conditions** (Vanilla / Flyvbjerg-primed / Council) as the comparative frame.
- [ ] **Study does not claim correctness** — only rubric-scored analytical structure. Explicit non-claims are listed in `methodology.md` §9.

## 2. W1 benchmark — case list (`benchmark/cases.md`)

Sign off each case. Substitutions must be made before runs begin — not after.

- [ ] Berlin Brandenburg Airport (BER) — Q1 2012 opening commitment
- [ ] California HSR (Phase 1) — Nov 2008 Prop 1A bond authorization
- [ ] HS2 (UK) — Jan 2012 Phase 1 route confirmation
- [ ] Sydney Opera House — mid-1957 scheme commitment
- [ ] Big Dig (Boston CA/T) — 1985 federal approval
- [ ] Crossrail (Elizabeth Line) — mid-2018 assurance commitment
- [ ] Kashagan oil field — 2001 Phase 1 FID
- [ ] Edmonton Valley Line Southeast LRT — 2013 P3 DBFOM commitment

**Confirmations requested in `cases.md`**:

- [ ] Case list as above, or substitute
- [ ] 8 is the right N (not 6, not 10)
- [ ] Edmonton Valley Line Southeast specifically (vs Metro Line)
- [ ] Kashagan specifically, or substitute another oil & gas case

## 3. W1 rubric — 10 dimensions (`methodology.md` §4)

Each scored 0 / 1 / 2. Sign off each dimension or request revision.

- [ ] D1 — Optimism-bias markers identified
- [ ] D2 — Risk-class identification (scored against contemporaneous markers, not outcomes)
- [ ] D3 — Cross-domain coupling surfaced
- [ ] D4 — Outside-view / reference-class reasoning
- [ ] D5 — Dissent preservation
- [ ] D6 — Evidence–claim calibration
- [ ] D7 — Stakeholder legitimacy / public value
- [ ] D8 — Temporal mismatch identification
- [ ] D9 — Escalation / insufficient-basis discipline
- [ ] D10 — Traceability

## 4. W1 condition prompts (`benchmark/prompts/`)

- [ ] [`vanilla.md`](benchmark/prompts/vanilla.md) — baseline "experienced advisor" frame, no doctrine
- [ ] [`flyvbjerg-primed.md`](benchmark/prompts/flyvbjerg-primed.md) — 5-point outside-view discipline (reference class, optimism audit, strategic misrep, escalation, uncertainty preservation)
- [ ] [`council.md`](benchmark/prompts/council.md) — full `/council` invocation with Chair-proposed parameters accepted as-is

## 5. W2 blind-spots — 22 concepts (`blind-spots/concepts.md`)

Sign off the concept list. Substitutions must be made before vignette construction — already done, so substitutions here mean replacing a vignette.

**Strategy & decision-making**
- [ ] 01. Reference class forecasting
- [ ] 02. Optimism bias
- [ ] 03. Strategic misrepresentation
- [ ] 04. Escalation of commitment
- [ ] 05. Sunk cost fallacy

**Governance & institutional**
- [ ] 06. Principal-agent at political interface
- [ ] 07. Governance fragmentation
- [ ] 08. Stakeholder stratigraphy
- [ ] 09. Legitimacy erosion
- [ ] 10. Assurance capture

**Risk & uncertainty**
- [ ] 11. Tight coupling (Perrow)
- [ ] 12. Tail risk / fat-tailed exposure
- [ ] 13. Cascading failure
- [ ] 14. Emergent risk from dependency density

**Commercial & contracting**
- [ ] 15. Hold-up risk
- [ ] 16. Benefit-case optimism
- [ ] 17. P3 risk transfer illusions

**Socio-technical / impact**
- [ ] 18. Socio-material effects
- [ ] 19. Hirschman's Hiding Hand
- [ ] 20. Local knowledge disregard

**Temporal**
- [ ] 21. Clock mismatch
- [ ] 22. Path dependence / lock-in

## 6. W3 P3 tail-risk — refined research question (`p3-tail-risk/scenario.md`)

- [ ] The four structural blind spots to be tested:
  - (a) PERT-mean fat-tail collapse
  - (b) Independent-risk assumption across cost / operating / demand / force majeure
  - (c) Binary risk allocation with no return-of-risk under distress
  - (d) Absent legitimacy / community / public-value pricing
- [ ] Baseline: [`stage1-vfm-writeup.md`](p3-tail-risk/stage1-vfm-writeup.md) as the "competent practitioner VfM" comparator
- [ ] Single-condition comparison (Council only; no Flyvbjerg-primed for this workstream) — research question is structural-critique coverage, not comparative judgment

## 7. W4 Edmonton Valley Line SE — 4 decision points (`deep-case/decision-points.md`)

- [ ] DP1 — 2013 P3 DBFOM delivery-model commitment *(reuses W1 Edmonton brief — no separate Council run)*
- [ ] DP2 — 2014–2015 alignment, low-floor technology, grade-separation, RFP scope
- [ ] DP3 — Late-2019 signalling integration under concession performance regime
- [ ] DP4 — Late-2021 acceptance of TransEd's mid-2022 opening proposal after Bombardier → Alstom counterparty change

## 8. Named limitations (`limitations.md`)

These are acknowledged confounds, not sign-off items per se. Confirm the list is complete:

- [ ] §1 Designer is scorer
- [ ] §2 No co-rater
- [ ] §3 Single-model, single-prompt-per-condition
- [ ] §4 Small N
- [ ] §5 Case-selection bias
- [ ] §6 Brief construction leaks hindsight
- [ ] §7 Rubric is the system's own rubric
- [ ] §8 Council verbosity
- [ ] §9 Scorer fatigue
- [ ] §10 MMPM-COS is a specification, not a trained model
- [ ] §11 P3 is a single-scenario case study *(revised from earlier "external artifact" framing)*
- [ ] §12 Timeboxing
- [ ] §13 Sources are canonically named, not URL-verified *(added in cleanup pass)*
- [ ] §14 Condition A/B execution environment *(added in cleanup pass)*

## 9. Operational decisions before runs

- [ ] **Conditions A/B execution environment**: run in a clean Claude.ai session (no MMPM-COS context), OR run here with isolated sub-agents and residual-contamination note in output headers, OR run here accepting contamination as documented per §14. Pick one.
- [ ] **Scale**: pilot-first (BER across 3 conditions, validate, then scale) vs batch-all.
- [ ] **Session scope**: single session or multi-session execution (73 runs plus scoring is multi-session work).

---

## Sign-off

When all boxes above are checked:

- All `DRAFT v0 — awaiting verification` statuses bump to `v1 — signed off YYYY-MM-DD`.
- This file is retained as a record of what was signed off and when.
- Any post-signoff changes to scope require a new SIGN-OFF entry, not silent edits.

Signed off by: ________________
Date: ________________
