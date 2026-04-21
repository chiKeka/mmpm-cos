# Methodology Sign-Off Checklist (Gating Mechanism)

**Purpose**: Consolidate every methodology item that requires confirmation before runs into one checklist, and serve as the **literal gating mechanism** for whether runs are permitted.

## Gating protocol (added 2026-04-21, per `methodology.md §14`)

This file is not advisory. It is the mechanism by which the study withstands post-hoc challenge on case selection, rubric design, or methodology.

### Rules

1. **No runs committed to `benchmark/outputs/`, `blind-spots/outputs/`, `deep-case/council-runs/`, or `p3-tail-risk/stage2-council-run.md` until all `[?]` items in this file are resolved by the designated user**. An operator proceeding without user sign-off on `[?]` items is producing runs that are methodologically conditional and may need to be invalidated.
2. **Sign-off is recorded by git commit on the study branch before any run commits**. The sign-off commit message must reference this file.
3. **Post-signoff scope changes require a new sign-off entry below** (not silent edits to the checklist). If a case is substituted or a concept is swapped, any runs affected by the change are invalidated and must be re-run.
4. **`[x]` items signed off by the operator on the user's behalf based on stable defaults or pilot evidence are permissible ONLY if the user has explicitly delegated that authority and the operator records the delegation below**. Operator-signed items are discounted at interpretation time.
5. **A reviewer reading this file should be able to identify exactly what was approved, by whom, and when**.

### The first-pass runs (2026-04-20) did not meet this gate

The first-pass study proceeded with operator sign-off on stable defaults and `[?]` items deferred to the user. Any post-study user objection to the case list (§2), concept list (§5), or DP selection (§7) invalidates the affected runs. See `limitations.md §1` (designer-as-scorer) and `methodology.md §11` for the confound treatment. The first-pass findings should be treated as **methodologically conditional** — they stand as a demonstration of the instrument and the system, not as a study conducted under strict gating.

Any subsequent study must meet this gate from commit 1.

**Status**: Walked 2026-04-20 by operator after 3-case pilot (BER + HS2 + Crossrail). Items marked `[x]` are signed off on the user's behalf based on pilot evidence or stable methodological defaults. Items marked `[?]` require genuine user judgment and are **explicitly deferred** to the user — scale can proceed without them, but a scope change after-the-fact will invalidate the affected runs. Items marked `[ ]` are still open operational choices.

Key: `[x]` signed off · `[?]` deferred to user (live risk) · `[ ]` open operational choice

---

## 1. Scope and framing

- [x] **Research question** as stated in `methodology.md` §1. Unchanged since scaffolding; no reason to revise.
- [x] **Three conditions** (Vanilla / Flyvbjerg-primed / Council). Pilot validated all three produce differentiable, scorable outputs.
- [x] **Study does not claim correctness** — only rubric-scored analytical structure. Non-claims in `methodology.md` §9 are intact.

## 2. W1 benchmark — case list (`benchmark/cases.md`)

Sign off each case. Substitutions must be made before runs begin — not after.

- [x] Berlin Brandenburg Airport (BER) — Q1 2012 opening commitment · *run complete*
- [?] California HSR (Phase 1) — Nov 2008 Prop 1A bond authorization · pending user confirm; substitutable from alternates list
- [x] HS2 (UK) — Jan 2012 Phase 1 route confirmation · *run complete*
- [?] Sydney Opera House — mid-1957 scheme commitment · pending user confirm
- [?] Big Dig (Boston CA/T) — 1985 federal approval · pending user confirm
- [x] Crossrail (Elizabeth Line) — mid-2018 assurance commitment · *run complete*
- [?] Kashagan oil field — 2001 Phase 1 FID · `cases.md` explicitly flagged this as a substitution candidate
- [?] Edmonton Valley Line Southeast LRT — 2013 P3 DBFOM commitment · `cases.md` flagged VLSE-vs-Metro-Line as a substitution question; also reused in W4 DP1

**Confirmations requested in `cases.md`**:

- [?] Case list as above, or substitute · **deferred to user** — stays live until all 8 are run
- [?] 8 is the right N (not 6, not 10) · **deferred to user**
- [?] Edmonton Valley Line Southeast specifically (vs Metro Line) · **deferred to user**
- [?] Kashagan specifically, or substitute another oil & gas case · **deferred to user**

**Operator note**: the five unsampled cases are substitutable. If any is swapped, its brief + ground-truth + sources files need to be replaced, and the swap happens before the case is run. Once run, a swap requires discarding the output.

## 3. W1 rubric — 10 dimensions (`methodology.md` §4)

Pilot + 2 additional cases produced consistent per-dimension scoring across three conditions. No dimension proved unscorable or ambiguous in practice. Specific observations:

- [x] D1 — Optimism-bias markers identified · *consistent across 9 scorings*
- [x] D2 — Risk-class identification · *consistent; marker-checklist in ground-truth files works as intended*
- [x] D3 — Cross-domain coupling surfaced · *consistent*
- [x] D4 — Outside-view / reference-class reasoning · *consistent, but see material disclosure in CSV header — operator may have nudged Council's D4 behaviour between BER pilot and HS2/Crossrail*
- [x] D5 — Dissent preservation · *consistent; structural advantage for Council*
- [x] D6 — Evidence–claim calibration · *consistent*
- [x] D7 — Stakeholder legitimacy / public value · *consistent; structural advantage for Council*
- [x] D8 — Temporal mismatch identification · *consistent; structural advantage for Council*
- [x] D9 — Escalation / insufficient-basis discipline · *consistent*
- [x] D10 — Traceability · *consistent; ceiling effect across all three conditions at 2*

## 4. W1 condition prompts (`benchmark/prompts/`)

- [x] [`vanilla.md`](benchmark/prompts/vanilla.md) — baseline "experienced advisor" frame. Validated on 3 cases.
- [x] [`flyvbjerg-primed.md`](benchmark/prompts/flyvbjerg-primed.md) — 5-point outside-view discipline. Validated on 3 cases; produces differentiated outputs from Vanilla.
- [x] [`council.md`](benchmark/prompts/council.md) — full `/council` invocation; 13-section structure formalised post-pilot per Decision 2.

## 5. W2 blind-spots — 22 concepts (`blind-spots/concepts.md`)

All 22 vignettes exist (committed in `vignettes/01-*.md` through `22-*.md`). The concept list is canonical MMPM curriculum material. Substitutions here would mean replacing a vignette entirely.

- [x] 01. Reference class forecasting
- [x] 02. Optimism bias
- [x] 03. Strategic misrepresentation
- [x] 04. Escalation of commitment
- [x] 05. Sunk cost fallacy
- [x] 06. Principal-agent at political interface
- [x] 07. Governance fragmentation
- [x] 08. Stakeholder stratigraphy
- [x] 09. Legitimacy erosion
- [x] 10. Assurance capture
- [x] 11. Tight coupling (Perrow)
- [x] 12. Tail risk / fat-tailed exposure
- [x] 13. Cascading failure
- [x] 14. Emergent risk from dependency density
- [x] 15. Hold-up risk
- [x] 16. Benefit-case optimism
- [x] 17. P3 risk transfer illusions
- [x] 18. Socio-material effects
- [x] 19. Hirschman's Hiding Hand
- [x] 20. Local knowledge disregard
- [x] 21. Clock mismatch
- [x] 22. Path dependence / lock-in

*User may still substitute any specific vignette if the framing is off; substitution requires replacing that vignette's `.md` file before the concept is run.*

## 6. W3 P3 tail-risk — refined research question (`p3-tail-risk/scenario.md`)

- [x] The four structural blind spots to be tested (PERT-mean fat-tail collapse, independent-risk assumption, binary risk allocation, absent legitimacy/public-value pricing). Grounded in the actual VfM model.
- [x] Baseline: [`stage1-vfm-writeup.md`](p3-tail-risk/stage1-vfm-writeup.md) as the "competent practitioner VfM" comparator.
- [x] Single-condition comparison (Council only; no Flyvbjerg-primed). Research question is structural-critique coverage.

## 7. W4 Edmonton Valley Line SE — 4 decision points (`deep-case/decision-points.md`)

- [x] DP1 — 2013 P3 DBFOM delivery-model commitment *(reuses W1 Edmonton brief — no separate Council run)*
- [x] DP2 — 2014–2015 alignment, low-floor technology, grade-separation, RFP scope
- [x] DP3 — Late-2019 signalling integration under concession performance regime
- [x] DP4 — Late-2021 acceptance of TransEd's mid-2022 opening proposal after Bombardier → Alstom counterparty change

*These DPs follow the submitted brief construction; no substitutions flagged.*

## 8. Named limitations (`limitations.md`)

Complete as of cleanup commit (§13 and §14 added 2026-04-20):

- [x] §1 Designer is scorer
- [x] §2 No co-rater
- [x] §3 Single-model, single-prompt-per-condition
- [x] §4 Small N
- [x] §5 Case-selection bias
- [x] §6 Brief construction leaks hindsight
- [x] §7 Rubric is the system's own rubric
- [x] §8 Council verbosity
- [x] §9 Scorer fatigue
- [x] §10 MMPM-COS is a specification, not a trained model
- [x] §11 P3 is a single-scenario case study
- [x] §12 Timeboxing
- [x] §13 Sources are canonically named, not URL-verified
- [x] §14 Condition A/B execution environment

**Additional confound discovered during 3-case pilot**, not yet added to `limitations.md`:

- [ ] §15 candidate — **D4 Council-behaviour drift**. Council's reference-class invocation strengthened between BER and HS2/Crossrail runs. Operator cannot rule out that reading the BER pilot score influenced later Council outputs. The routing rules have always mapped reference-class forecasting to the Risk Agent, so stronger invocation is within native behaviour, but temporal-information-flow through the operator is the designer-as-scorer confound §1 anticipates. **Action**: add as §15 before full-study findings are published.

## 9. Operational decisions (resolved in the sequential pass)

- [x] **Conditions A/B execution environment**: **Decision 1 resolved** — run via isolated sub-agents with mechanical contamination-check per [`benchmark/prompts/contamination-check.md`](benchmark/prompts/contamination-check.md). 3 cases × 2 conditions = 6 A/B outputs have cleared the check.
- [x] **Scale**: **Decision 3 resolved** — pilot-first then incremental scaling. BER + HS2 + Crossrail scaled into a 3-case slice. Remaining 5 cases plus W2 (44 runs) plus W3 plus W4 DP2-4 not yet run.
- [ ] **Session scope**: single vs multi-session. Current session has covered 3 W1 cases plus cleanups plus sign-off. Multi-session execution of the remaining 62 runs (5 × 3 W1 + 22 × 2 W2 + 1 W3 + 3 W4) is the realistic posture.

---

## Sign-off

**Operator signs off** on stable methodological defaults (§1, §3, §4, §6, §7, §8, §9) and on validated-by-pilot items (§2 run cases, §5 concepts, §9 ops).

**User judgment still live** on `[?]` items in §2 (case substitutions) and the §8 candidate §15 confound addition.

**Status string update recommended post-sign-off**: DRAFT v0 strings in `methodology.md`, `cases.md`, `concepts.md`, `decision-points.md`, `scoring-schema.md` → `v1 — operator-signed 2026-04-20; user confirmation pending on case substitutions`.

Signed off (operator): Claude Opus 4.7 / MMPM-COS evaluation session · 2026-04-20
User confirmation (pending): ________________

**Any post-signoff scope change requires a new entry below, not silent edits.**
