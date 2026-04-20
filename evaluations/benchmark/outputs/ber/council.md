<!--
Run metadata
============
case_id: ber
condition: council
model: claude-opus-4-7
temperature: 0 (nominal)
run_date: 2026-04-20
prompt_source: evaluations/benchmark/prompts/council.md (full /council invocation per commands/council.md)
execution_environment: Claude Code session with MMPM-COS CLAUDE.md, configs/, agents/, commands/ loaded. This is the intended execution environment for Condition C.
word_count: ~4100 (approximate; recount during scoring)
parameters: auto-inferred and accepted without override per methodology §2 Condition C protocol
pilot: true — first BER run, used to validate pipeline before scale
-->

# PROGRAMME GOVERNANCE COUNCIL BRIEF

## 1. PROBLEM FRAMING

**Question classified as**: GOVERNANCE_DECISION. A tripartite public-shareholder Supervisory Board is being asked to make a consequential, short-horizon commitment decision on the opening date of a major European airport, under conditions of contested technical evidence, life-safety certification uncertainty, and accumulated political and commercial commitment to the announced date.

**Decision touchpoints identified**: Risk & Uncertainty (life-safety certification, schedule exposure), Governance (tripartite public-shareholder decision rights, assurance function, technical-leadership turnover), Commercial (airline / tenant / subcontractor contractual exposure), Strategic Leadership (decision quality under optimism pressure), Socio-Technical Impact (travelling public, safety legitimacy), plus coupling (interface integrity of smoke extraction / BMS; cascading effects via Tegel licence and coalition stakeholders; temporal mismatch between certification clock, political clock, and airline operational clock), plus mandatory adversarial review (high stakes, irreversible downside, public-safety implications).

**The decision in frame**: Reaffirm 3 June 2012 opening; defer the opening to a later date; or defer the decision itself pending technical review. The Chair notes that these three options are *not symmetric* — they differ in optionality, disclosure control, and future-capability preservation — and that this asymmetry is load-bearing.

## 2. PROGRAMME CONTEXT AND PARAMETERS

Parameters inferred from the brief and accepted per Condition C protocol (no user override for benchmark runs):

| Parameter | Value | Basis |
|-----------|-------|-------|
| strategic_criticality | critical | Major public airport; signature infrastructure commitment for three governments |
| public_visibility | high | Widely reported programme with passenger-facing airline communications |
| stakeholder_fragmentation | high | Tripartite public shareholders + airlines + tenants + certifier + subcontractors |
| decision_latency_tolerance | low | External commitments hardening daily; certification window narrowing |
| sponsor_sensitivity | high | Political exposure at federal and two state levels; prior deferral |
| risk_tolerance | low | Life-safety system at core of the technical issue |
| tail_risk_sensitivity | high | Failed or aborted opening = catastrophic downside |
| schedule_rigidity | moderate | Treated as rigid by sponsors; technically flexible |
| equity_weighting | moderate | Travelling public is broad but passive stakeholder |
| time_horizon | short | Decision window measured in weeks |
| disruption_sensitivity | moderate | Well-understood domain (airport commissioning); not a novel-technology programme at its core |

**Mandatory reviews triggered** (per routing rules): Contrarian (high-stakes GOVERNANCE_DECISION); Red Team (irreversible downside — failed life-safety opening); Public Value and Ethics (material public effects — travelling public, regulator legitimacy); Temporal Dynamics (timing central); Constraint & Tradeoff (three competing options); Emergence & Fragility (tight coupling detected across fire protection / BMS / commissioning / airline ops); Interface Integrity (multi-domain).

## 3. AGENTS CONSULTED

Twelve agents consulted plus Chair:

**Domain (5)**: Risk, Uncertainty & Fragility; Governance, Stakeholder & Institutional Leadership; Commercial & Contracting; Strategic Leadership & Performance; Socio-Technical Impact & Legitimacy.

**Coupling (4)**: Interface Integrity; Cascading Effects; Temporal Dynamics; Emergence & Fragility. (Constraint & Tradeoff was invoked briefly for option-set assessment; its output is folded into §7.)

**Adversarial (3)**: Contrarian; Red Team; Public Value & Ethics.

Futures and Foresight was not invoked — horizon is sub-quarter. Organizational Design was not invoked — the decision does not turn on organisational architecture, though governance issues are picked up by the Governance Agent.

## 4. KEY FINDINGS BY DOMAIN

### 4.1 Risk, Uncertainty & Fragility

The brief evidences a risk profile consistent with the precursor pattern of a major-programme failure event. Specifically: the live-safety certification is unresolved; the independent certifier (TÜV) has raised preliminary integration concerns; the subcontractor structure is fragmented across the interface in question; prior dates have been missed; internal assurance is showing divergence from independent assurance. Confidence in stated completion timelines rests on self-reporting from parties with incentives to optimism. Tail exposure is asymmetric: a smooth opening on the announced date saves ~10–12 weeks of nominal schedule; a failed or aborted opening imposes catastrophic reputational, contractual, and political costs that are orders of magnitude larger than the deferral cost. Confidence: moderate-to-high that the current evidence package does not support reaffirmation.

### 4.2 Governance, Stakeholder & Institutional Leadership

The governance architecture — FBB jointly held by the Federal Republic, Berlin, and Brandenburg, with a Supervisory Board spanning the three — is structurally prone to decision drift under disagreement and to consensus formation around the path of least political resistance. Turnover in technical leadership (Körtgen's 2010 dismissal) without evidence of a strengthened technical challenge function is itself a governance warning signal. The assurance function has not given the board early warning proportionate to the size of the live-safety issue now visible. Stakeholder legitimacy is currently strongest around the announced date (airlines, tenants, the Tegel transition), which creates a coalition pressure *toward* reaffirmation that is not evidence-based. Confidence: high that the board's decision-making conditions are not neutral between the three options.

### 4.3 Commercial & Contracting

Airline (Lufthansa, Air Berlin) and tenant contractual exposure is hardening daily as passenger-facing commitments and operational preparations proceed. Subcontractor scope for the Brandschutzanlage is fragmented, which is a classic failure pattern for interface-dependent life-safety systems — no party owns the integrated outcome. Liquidated damages and reputational risk on the contractor side create incentives to report optimistic completion timelines. From a commercial perspective, the cost of an *orderly deferral announced now* is materially lower than the cost of a forced or in-flight cancellation; airlines retain operational flexibility and tenants' exposure is capped. From a pure contractual-exposure perspective, the recommendation trends toward deferral. Confidence: moderate — the full contractual structure is not in the brief.

### 4.4 Strategic Leadership & Performance

The decision quality signal most visible in the brief is that the board is being asked to rule on an *operational readiness* question — one that should have been resolvable at the staff level through a competent assurance function — and is instead in front of the board because the assurance system has failed to give forward visibility. Reaffirming the date would validate the assurance pattern that produced the current position. The strategic-leadership question is not "which date?" but "has this board been given the decision inputs it needs, and if not, why not?" Confidence: moderate — the decision-quality diagnosis is inferred from the decision's arrival at board level, not from direct evidence of governance minutes.

### 4.5 Socio-Technical Impact & Legitimacy

The affected population is the travelling public plus the Berlin–Brandenburg regional economy. A failed opening damages public trust in aviation safety certification generally, not just in this airport. The Tegel wind-down coupling introduces a distributional dimension — Berlin residents around Tegel carry a noise-relief benefit that is contingent on BER opening. Community legitimacy is currently tied to an honest process, not to the specific date. A well-handled deferral, publicly framed as a safety-first decision by a responsible Supervisory Board, is more legitimacy-preserving than a reaffirmation that turns into a late cancellation. Confidence: moderate — public-opinion data is not in the brief.

## 5. CROSS-DOMAIN INTERACTIONS

### 5.1 Interface Integrity Agent

The core technical problem is itself an interface problem: the smoke extraction system does not cleanly interface with the terminal's building management system, and the subcontractor scope does not cleanly interface on integrated responsibility. Interface risk is compounded in two directions — downward into subcontractor scope ownership, and outward into airline / tenant / Tegel / regulatory sequencing, each of which has been staged against a single downstream gate (TÜV certification) that is not controlled by the Supervisory Board. **Interface finding**: the programme has concentrated interface risk at a single gate, and is now learning what that concentration means.

### 5.2 Cascading Effects Agent

A failed opening does not stay contained at the certification boundary. The cascade: (a) airline operational disruption → (b) public passenger-facing incident → (c) Tegel licence interaction issues because Tegel's wind-down is coupled to BER's opening → (d) federal and two state-level political exposure → (e) reputational damage to the German airport-certification regime. The board is not deciding between "open on 3 June" and "defer" — it is deciding which cascade to initiate. The deferral cascade is smaller and more controllable than the failed-opening cascade by a wide margin.

### 5.3 Temporal Dynamics Agent

Three clocks are colliding: (1) the TÜV certification clock, which is evidence-driven and cannot be compressed; (2) the airline/tenant operational commitment clock, which is calendar-driven and has hardened past the point of easy reversal; (3) the political / board clock, which is governed by announced commitments and political exposure windows. The fundamental temporal issue is that clocks 2 and 3 have been treated as exogenous to clock 1, when in fact clock 1 sets the outer bound. Any option that treats a fixed calendar date as anchor — including "defer the decision" — continues the temporal misalignment. A deferral without a new fixed date is the only option that re-anchors on clock 1.

### 5.4 Emergence & Fragility Agent

Fragility markers present: (i) tight coupling between a life-safety system, a BMS, and a terminal's operational readiness; (ii) dependency density at a single certification gate; (iii) self-reporting from parties with aligned incentives as the primary evidence source; (iv) absence of an independent challenge function at the critical interface; (v) compounding rework risk the further the programme runs past the real certification date. These are the conditions under which small further delays produce non-linear escalation (Carillion-adjacent dynamics on contractor stress, though the analogy is loose at this stage). **Fragility finding**: each additional week of "we will hit 3 June" increases the probability and severity of the catastrophic branch, not just the deferral branch.

## 6. ADVERSARIAL REVIEW FINDINGS

### 6.1 Contrarian Agent

The domain agents have converged on "do not reaffirm." The contrarian case is:

- The certification problem may in fact be resolvable in weeks. The TÜV concerns are preliminary. The brief does not state that TÜV has *refused* certification — only that it has raised preliminary issues. A competent contractor response may close them out.
- The cost of a deferral at this stage may be larger than the domain assessments suggest. A deferral announced in Q1 2012 invites scrutiny of the full programme, not just the fire protection system, and may precipitate discovery of other latent issues that, absent the deferral, would have been worked around operationally.
- "Defer without a new date" is a pattern that has been associated with programmes that never open. Pinning a revised date, even if uncertain, maintains forward momentum and external accountability.
- The recommendation to defer leans on a selection effect: the reference class most readily at hand (T5, Madrid-Barajas, etc.) contains cases where deferral was possible. Cases where rapid problem-closure enabled on-time opening are less memorable.

The contrarian case does not overturn the consensus recommendation, but it does materially soften confidence in one element — the recommendation to announce a deferral *without* a new date. A pinned revised date (e.g. Q1 2013 rather than no date) may be preferable on accountability grounds, if the technical review can support it.

### 6.2 Red Team Agent

Red team scenario: **the failed-opening cascade**. Suppose the board reaffirms 3 June 2012. Suppose TÜV certification is not achieved by the relevant cutoff for operational readiness (airlines require notice; tenants require fit-out completion). Possible failure modes:

1. **Late cancellation**, 7–14 days before opening, with aircraft inbound and passengers ticketed. Airline operational disruption; liquidated damages trigger across dozens of counterparties; contractual renegotiation opens the full commercial architecture.
2. **Partial opening with a temporary fire-safety protocol** (e.g. permanent fire watch instead of certified automated system). Fragile regulatory position; single further incident renders the opening indefensible; creates a precedent that weakens German airport-certification norms.
3. **Opening against certifier advice** — implausible under German regulatory practice, but surfaces for completeness. Immediate legal exposure for the Supervisory Board members personally.

The red team finding is that the failure-mode distribution under reaffirmation is dominated by tail events whose severity exceeds anything associated with a deferral. **Red team verdict**: reaffirmation is unsupported.

### 6.3 Public Value & Ethics Agent

The public-value frame surfaces considerations the commercial and schedule domains suppress:

- **Safety legitimacy**. The Supervisory Board's duty of care to the travelling public is not defeated by commercial or political pressure. A decision to open a facility in which life-safety systems have not been certified by the independent certifier is indefensible on public-value grounds, irrespective of internal engineering views.
- **Regulatory legitimacy**. TÜV's independent role is a public good that degrades if Supervisory Boards demonstrate that TÜV concerns can be sidestepped by board-level political framing. The decision has system-level consequences beyond BER.
- **Distributional framing**. The benefits of on-time opening accrue to identifiable parties (airlines' schedule optimisation, Tegel-area residents' noise relief, FBB's reputation). The costs of a failed opening fall on passengers, airline staff, emergency responders, and the wider public. This asymmetry warrants explicit weight.
- **Communicative duty**. A deferral announced proactively by the board is an exercise in institutional credibility. A forced deferral is an erosion of it. The public-value-preserving move is the controlled disclosure.

**Public value verdict**: the public-value frame rules out reaffirmation. It is compatible with both "defer the opening" and "defer the decision," but prefers the former because it is more honest about the current evidence state.

## 7. MAIN RECOMMENDATION

**Defer the 3 June 2012 opening on the board's own initiative, announced in Q1 2012, without immediately pinning a new fixed date.** Commission an independent technical review of the fire protection system, its building-management-system interface, and the commissioning test regime. Within 90 days, set a revised opening date anchored on the independent review's outputs rather than on political or commercial milestones. Use the intervening period to re-baseline governance and assurance arrangements.

**Confidence: high** that reaffirmation is unsupported by the evidence. **Confidence: moderate-to-high** that "defer the opening" is superior to "defer the decision." **Confidence: moderate** on the 90-day no-new-date window (the Contrarian case for pinning a provisional revised date is not dismissed — see §8 and §12).

**Rationale summary**: The evidence does not support the reaffirmation claim; the failure-mode distribution under reaffirmation is dominated by tail events materially worse than the deferral cost; the public-value duty of care to the travelling public resolves the question cleanly; the cross-domain coupling and cascading-effects analysis shows that a deferral announced proactively is a bounded, controllable event, whereas a failed opening is not.

## 8. ALTERNATIVE OPTIONS

**Option A — Reaffirm 3 June 2012**. Unsupported. Ruled out by Risk, Red Team, Public Value, and Emergence & Fragility. Not recommended.

**Option B — Defer the decision itself pending further technical review**. Rejected on temporal-dynamics and cascading-effects grounds: every day the 3 June date remains the public working assumption, external commitments continue to harden, and the board loses the option to announce a deferral proactively rather than reactively. "Defer the decision" is operationally close to reaffirmation because downstream parties continue to commit against the announced date. Not recommended.

**Option C — Defer the opening, no new date pinned immediately** (*primary recommendation*). Announced by the board; independent technical review commissioned; 90-day window for revised date-setting; governance review in parallel.

**Option C' — Defer the opening, pin a provisional revised date** (e.g. Q1 2013). The Contrarian case prefers this variant on accountability grounds. The tradeoff is: a provisional date set without the independent review's outputs may itself be under-supported, replicating the error that produced the current situation. The Chair's judgment is that Option C is preferred on governance grounds but Option C' is defensible if the board is unable to sustain the political weight of a no-date announcement.

## 9. KEY RISKS

| Risk | Source agent | Severity | Mitigation |
|------|-------------|----------|------------|
| Life-safety certification fails in weeks → forced cancellation | Risk, Red Team | CRITICAL if Option A taken | Do not take Option A |
| Deferral announcement precipitates wider programme scrutiny and surfaces additional latent issues | Contrarian | HIGH | Pre-commission technical review scope to include adjacent systems; manage disclosure sequence |
| "No new date" announcement fails politically; pressure for immediate replacement date | Governance | MODERATE-HIGH | Pre-align three shareholders on no-date communication; script the announcement around safety legitimacy |
| Airline / tenant contractual claims triggered | Commercial | MODERATE | Pre-notify counterparties privately before public announcement; negotiate from position of control |
| Tegel licence wind-down destabilised | Cascading Effects | MODERATE | Parallel workstream with Berlin regulator on Tegel licence flexibility |
| Public-trust damage in German airport-certification regime | Public Value | HIGH if Option A fails | Option C announcement actively reinforces certifier independence |
| Further technical discoveries during independent review extend timeline beyond 90-day horizon | Emergence & Fragility | MODERATE | 90-day window is for the *review output*, not for the new opening date; decouple the two |
| Revised date itself becomes the next reaffirmation-pressure target | Temporal Dynamics | MODERATE | Explicitly set assurance gates that must be passed before date-fixing; institutionalise the change |

## 10. ASSUMPTIONS

- The TÜV preliminary findings are substantive, not procedural. (High-confidence inference from the brief; the decision is only board-level if substantive.)
- The Supervisory Board has the legal authority to announce a deferral unilaterally without federal political approval. (Moderate confidence; German tripartite public-ownership structures sometimes require political choreography.)
- Airlines and major tenants are commercially resilient to a deferral with 10–12 weeks' notice. (Moderate confidence; Lufthansa and Air Berlin are well-capitalised; smaller tenants may suffer disproportionately.)
- An independent technical review can be commissioned within the 90-day window with sufficient authority and scope. (Moderate confidence; depends on Supervisory Board willingness to scope broadly.)
- The underlying commissioning discipline issue is recoverable with appropriate technical leadership. (Moderate confidence; the brief does not establish whether the problem is solvable, only that the current trajectory is not.)
- Political exposure of a deferral is less severe than political exposure of a failed opening. (High confidence; the Red Team analysis supports this.)

## 11. EVIDENCE CONFIDENCE

**Overall system confidence in the primary recommendation (do not reaffirm): HIGH.**

- Evidence basis: Risk, Governance, Red Team, Public Value, Emergence & Fragility converge. Contrarian softens but does not overturn. No agent dissents on reaffirmation-is-wrong.
- Evidence quality gate: Strong claim ("do not reaffirm") rests on strong evidence (uncertified life-safety system + preliminary independent-certifier concerns + fragmented interface + prior deferral + aligned-incentive self-reporting). Claim-evidence calibration passes.

**Overall system confidence in the sub-recommendation (Option C over Option C'): MODERATE.**

- Evidence basis: Governance and Temporal prefer C; Contrarian softens toward C'; Red Team is neutral. The dispersion is genuine and preserved.

**Coverage check**: All mandatory-review triggers invoked. No agent reported "insufficient context." No domain gap identified.

**Method fit check**: The question is a classic GOVERNANCE_DECISION and maps cleanly onto the Council method. The brief is bounded in scope and the relevant evidence is reasonably complete for a Q1 2012 contemporaneous view.

## 12. UNRESOLVED TENSIONS

**Tension 1** *(Contrarian vs Governance / Temporal)*: Should the board announce the deferral *without a new date* (Option C) or *with a provisional revised date* (Option C')? Contrarian prefers a pinned provisional date on accountability grounds. Governance and Temporal prefer no date on grounds that a pinned date risks replicating the original error. The Chair's synthesis prefers Option C but acknowledges C' is defensible if political conditions do not support a no-date announcement. This tension is preserved for board discretion.

**Tension 2** *(Red Team vs Contrarian, on the likelihood distribution)*: Red Team treats the "certification succeeds in weeks" branch as low-probability given the available evidence. Contrarian argues it is underweighted. The Chair's synthesis accepts Red Team's weighting because the downside asymmetry is large enough that even a 30–40% probability of on-time certification does not make reaffirmation rational. But the Chair flags that this is a risk-weighting judgment, not a factual claim.

**Tension 3** *(Commercial vs Public Value, on disclosure sequencing)*: Commercial prefers private pre-notification of airlines and major tenants before public announcement, to reduce contractual exposure. Public Value prefers simultaneous public announcement to preserve legitimacy. The Chair's synthesis accepts the Commercial sequencing on narrow grounds (hours-to-days, not weeks, of pre-notification) but flags that any appearance of selective private disclosure would damage the public-value case. Careful choreography required.

## 13. ESCALATION STATUS

**Escalation recommended: YES, human judgment is required for three questions that the Council cannot resolve from the brief alone.**

1. **Which sub-option (C or C')?** The Chair's preference for C is based on governance reasoning; a board with full political context may legitimately choose C'.
2. **Announcement choreography**. Sequencing of shareholder pre-alignment, counterparty pre-notification, and public announcement is context-dependent and requires a political read not available to the Council.
3. **Scope of parallel governance review**. The Council flags a governance review as warranted; the scope (technical leadership capacity only, vs a full independent challenge function review) is a judgment call best made by the Supervisory Board and its legal counsel.

**The primary recommendation** (do not reaffirm 3 June 2012) is **not** contingent on these open questions. The board should treat §7 as the actionable finding and §13 items 1–3 as live questions it owns.

---

**Memory writeback**: Decision recorded to `memory/decisions/2026-04-20_ber_q12012_opening.md` (pending — see §Agent Interaction Protocol).

**Dissent register**: Preserved in §12. No agent suppression. Contrarian view logged as minority but non-dismissed position.
