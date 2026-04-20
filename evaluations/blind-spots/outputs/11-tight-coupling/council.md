<!--
concept_id: 11
concept_name: Tight coupling (Perrow)
condition: council
model: claude-opus-4-7
run_date: 2026-04-20
followup_used: no
parameters: auto-inferred per /council protocol
-->

# PROGRAMME GOVERNANCE COUNCIL BRIEF

## 1. PROBLEM FRAMING

A nuclear refurbishment outage with four workstreams, a 180-day window, a hard logical dependency between WS3 (digital I&C upgrade) and WS4 (auxiliary recommissioning), with WS2 already 14 days late and WS3 forecasting a further 21–60 day software-integration extension. The Chair classifies as CROSS_DOMAIN with consequential decision pending (mid-outage management). The dominant analytical question is the system-architecture: this is a **tightly coupled** programme in the Perrow sense — interactive complexity plus tight coupling — and the board's framing as four parallel workstreams is missing the system-level dynamic.

## 2. PROGRAMME CONTEXT AND PARAMETERS

Inferred: strategic_criticality high (nuclear, regulated, hard external constraints); risk_tolerance very low (safety case); tail_risk_sensitivity high (digital integration tail); schedule_rigidity high (outage window externally constrained); time_horizon short. Mandatory triggers: Risk; Interface Integrity; Cascading Effects; Temporal Dynamics; Emergence & Fragility; Constraint & Tradeoff; Red Team (irreversible safety downside); Public Value (regulator and grid).

## 3. AGENTS CONSULTED

Chair plus: Risk; Commercial; Strategic Leadership; Interface Integrity; Cascading Effects; Temporal Dynamics; Emergence & Fragility; Constraint & Tradeoff; Contrarian; Red Team; Public Value & Ethics. Eleven agents engaged.

## 4. KEY FINDINGS BY DOMAIN

### 4.1 Risk Agent

The WS3 digital integration tail (21–60 days) is the dominant programme risk and is qualitatively different from the mechanical workstreams. Reference class for digital control-system commissioning shows that "last 10% of integration" routinely consumes 40% of allocated time, and software-defect tail distributions are right-skewed with heavy tails. The 60-day upper bound is almost certainly optimistic; a stretched scenario of 90+ days should be in the planning case. Reference class on outages with similar structure (TVA Sequoyah, AREVA / EDF outage extensions) shows that extension by 30-100% of original window is not unusual when digital integration is on the critical path.

### 4.2 Strategic Leadership

The decision-quality question: workstream-level reporting frames each WS as independent. The Council finding is that the system-level view is the relevant one. Re-framing required at board level.

### 4.3 Commercial

Four contractors with separate quality-acceptance gates produces accountability diffusion at the integration boundary. No single contractor owns the integrated outcome. Commercial structure is a contributor to the coupling problem.

## 5. CROSS-DOMAIN INTERACTIONS — primary findings

### 5.1 Interface Integrity

**The WS3 → WS4 handover is a hard logical dependency, not a schedule convenience**. Auxiliary systems cannot be safely recommissioned against unverified interlocks. The interface is not negotiable. Any attempt to parallelise WS3/WS4 to recover schedule introduces safety-significant risk and should be ruled out at board level. Interface finding: the board needs a single integration authority with decision rights across the WS3/WS4 boundary; contractor-led coordination will not hold under pressure.

### 5.2 Cascading Effects

WS2 (14 days late) and WS3 (21–60 days late) appear independent in the workstream view. They are not. They share float, management attention, and shared resources (commissioning engineers, regulator-interface staff, integration testing infrastructure). Concurrent pressure across workstreams degrades decision quality at exactly the moment decisions matter most. Cascade also extends to: regulator submission timeline, grid commitments, fuel cycle, public communication.

### 5.3 Temporal Dynamics

Three clocks. (a) Software-debug clock (slow, distribution-driven, cannot be compressed). (b) Outage-window clock (180 days, externally fixed by grid + regulator). (c) Workstream-handover clock (logical dependency, bounded by clock (a)). The fastest clock (b) is anchored to a hard external date; the slowest clock (a) sets the realistic envelope. The current management plan does not visibly anchor (b) on (a).

### 5.4 Emergence & Fragility — primary finding

This is a **tightly coupled system in the Perrow sense**: interactive complexity (digital I&C interfacing with mechanical, control, and safety systems) plus tight coupling (no buffering between workstreams; hard logical dependencies; shared resources; safety-significant interlocks). Perrow's "normal accidents" framework predicts that programmes of this configuration produce non-linear failure under stress: small issues propagate because there is no slack to absorb them, and recovery actions in one workstream introduce cascading effects in others. The board must recognise that the standard "manage each workstream" framing is structurally inadequate for a system of this type. Confidence: high.

### 5.5 Constraint & Tradeoff

Three options: (i) extend outage; (ii) staged return-to-service (some systems back online before others); (iii) descope WS3/WS4 to fit window. Each carries different cost, regulatory, and safety profiles. The board must own the tradeoff, not have it forced by the calendar.

## 6. ADVERSARIAL REVIEW FINDINGS

### 6.1 Contrarian

The four-workstream, four-contractor structure has worked through WS1 successfully and most of WS2. It is not inherently dysfunctional. The Council's "tight coupling" framing may over-dramatise what is in fact a manageable late-stage integration challenge. Counter-recommendation: trust the WS3 contractor's range, manage the WS4 handover carefully, and reserve drastic re-architecting for evidence of further slip. The Contrarian softens the framing but does not overturn the recommendation for proactive reframing — only the urgency.

### 6.2 Red Team

Failure scenario: WS3 software issues extend to 90 days; WS4 cannot start; outage window blown; safety case for staged return-to-service requires regulator review under time pressure; pressure to compress WS4 acceptance testing; decision-quality degrades; safety-significant defect enters service. This is the cascade the board must prevent. Red Team verdict: act on the system-level framing now.

### 6.3 Public Value & Ethics

Nuclear safety legitimacy requires that integration testing not be compressed under schedule pressure. Public value places safety above schedule by structural priority. Regulator interface and grid operator must be pre-briefed on the realistic distribution.

## 7. MAIN RECOMMENDATION

Reframe at the board level: this is not four parallel workstreams; it is a tightly coupled integration programme. Specific actions: (i) commission independent technical review of WS3 software-issue distribution before accepting the contractor's 21–60 day range; (ii) establish single integration authority with decision rights across WS3/WS4 handover; (iii) set a formal decision point at outage day 90 with pre-agreed criteria for outage extension vs staged return-to-service; (iv) brief regulator and grid operator on the realistic distribution now, not later; (v) protect the WS3/WS4 acceptance-testing integrity from schedule pressure. **Confidence: high**.

## 8. ALTERNATIVE OPTIONS

Wait for WS3 contractor to confirm upper bound (rejected — temporal-dynamics analysis). Parallelise WS3/WS4 to recover time (rejected — Interface Integrity safety finding). Reframe and act now (primary).

## 9. KEY RISKS

| Risk | Source | Severity |
|------|--------|----------|
| WS3 software tail beyond 60 days | Risk, Emergence | HIGH |
| Safety-significant defect from WS4 acceptance compression | Red Team, Public Value | CRITICAL |
| Outage window blown | Risk, Temporal | HIGH |
| Concurrent workstream pressure degrading decision quality | Cascading | MODERATE-HIGH |
| Regulator/grid relations damaged by late disclosure | Public Value | MODERATE-HIGH |

## 10. ASSUMPTIONS

- WS3 contractor's 21-60 day range is optimistic at the upper bound (high confidence per reference class).
- Safety case requires verified interlocks before WS4 acceptance (high confidence — nuclear regulatory framework).
- Regulator can be engaged on contingency (high confidence).

## 11. EVIDENCE CONFIDENCE

Primary recommendation: HIGH. Reference-class evidence for digital-integration tails is robust; safety-case framework is well-established. Coverage check: all relevant agents consulted.

## 12. UNRESOLVED TENSIONS

Contrarian on urgency. Chair's synthesis preserves urgency on grounds that delaying the reframe consumes the option of an orderly contingency, but acknowledges Contrarian view is defensible if the board has private information about WS3 progress.

## 13. ESCALATION STATUS

Escalation: YES on regulator engagement — the timing and content of regulator pre-briefing is outside Council inputs and requires nuclear-regulatory expertise. Primary recommendation otherwise actionable.

---

**Concept-surfacing note**: "Tight coupling" named explicitly in §5.4 with Perrow citation; "interactive complexity" framing applied; "normal accidents" referenced; small-issues-propagate-because-no-slack causal mechanism stated.
