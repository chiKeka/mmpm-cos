<!--
Run metadata
============
case_id: ber
condition: vanilla
model: claude-opus-4-7 (role-played via general-purpose sub-agent)
temperature: 0 (nominal — sub-agent temperature not directly controllable)
run_date: 2026-04-20
prompt_source: evaluations/benchmark/prompts/vanilla.md
word_count: 1150 (approximate; recount during scoring)
execution_environment: Claude Code session with MMPM-COS CLAUDE.md loaded in parent context; executed via general-purpose sub-agent with explicit role-isolation instructions. Residual-contamination risk per `limitations.md §14`. Reviewed for telltale MMPM-COS signatures (Chair, Public Value Agent, Evidence Quality Gate, Contrarian, Red Team, multi-agent structure) — none detected. Output cleared for use.
pilot: true — first BER run, used to validate pipeline before scale
-->

# Analysis and Recommendation: BER Opening Commitment Decision

## My view in one sentence

The board should **defer the 3 June 2012 opening date now, on the board's own initiative, and re-plan from the fire protection critical path outward** — not reaffirm, and not "defer the decision." I hold this view with **high confidence**, and I want to explain why the third option (defer the decision itself) is the most tempting and the most dangerous.

---

## How I read the situation

Strip away the scheduling language and what you have is this: an independent technical certifier has raised preliminary concerns about a life-safety system in a large public terminal, that system has not passed commissioning, the contractor interface is fragmented across multiple subcontractors, and your internal engineering view and the certifier's view do not align in emphasis. You are roughly ten to twelve weeks from a hard public opening date that already represents a slip from the previous commitment.

Every other item on the brief — airline readiness, tenant activation, regulatory sign-off sequencing, Tegel's licence wind-down, passenger communications — is **downstream of one gate you do not control**: TÜV certification of the Brandschutzanlage. No airport in Germany opens to passengers without that sign-off. It is not a schedule item you can negotiate, compress, or share risk on. It is binary.

So the real question in front of the board is not "should we open on 3 June?" The real question is: **do we have credible, independently validated evidence that the fire protection system will be certified in time, with margin, and with the building management system interface resolved?**

On the evidence in the brief, the answer is no. You have contractor representations (which are contested), preliminary TÜV concerns (which are unresolved), a complex multi-subcontractor interface (which is a known pattern for late-emerging integration failure), and a commissioning regime whose adequacy for a terminal of this scale is itself being questioned. That is not a package that supports a reaffirmation.

---

## Why each option looks the way it does

**Reaffirm 3 June 2012.** This is the option that carries the highest expected cost and the worst failure mode. If you reaffirm and then fail to certify in May, you are not making a controlled deferral — you are making an emergency, publicly visible, last-minute cancellation with aircraft inbound, passengers ticketed, tenants stocked, and staff rostered. The reputational, contractual, and political damage from a late forced cancellation is materially larger than the damage from an orderly deferral announced in Q1. You also lose the option value of re-planning: every week you spend pretending the date is real is a week your commissioning team is not re-sequencing against a realistic finish. I would need to see a specific, TÜV-countersigned pathway with float before I could support reaffirmation, and the brief contains no such evidence.

**Defer the decision pending further technical review.** This is the option boards reach for when the evidence is uncomfortable, and it is the one I want to push back on hardest. "Defer the decision" sounds prudent but in practice it is a reaffirmation with extra steps, because every day the 3 June date remains the public working assumption, airlines, tenants, regulators and your own staff continue to commit irreversibly against it. Deferring the decision does not buy you optionality — it burns it, because the commitments downstream of the date keep hardening while you deliberate. You also lose the single most valuable asset the board has right now, which is the ability to announce a deferral **before** the situation forces one.

**Defer the opening, now, on the board's initiative.** This is the option that preserves the most future capability. It converts a looming forced disclosure into a controlled disclosure. It lets you re-baseline the commissioning plan against the real critical path. It lets you re-negotiate airline and tenant commitments from a position where you are not yet in breach. It lets you commission a proper independent technical review of the fire protection system and its BMS interface without the pressure of a countdown. And critically, it lets you confront the governance question — three public shareholders, a tripartite board, turnover in technical leadership — which is almost certainly contributing to why a problem of this type has persisted this long.

---

## What I would specifically recommend the board do

1. **Do not set a new opening date in the same meeting.** The single most common and most damaging pattern in programmes of this type is replacing one unsupported date with another unsupported date. Announce a deferral without a replacement date, commit to a timeline for setting one (e.g. within 90 days), and hold to that.

2. **Commission an independent technical review of the fire protection system, the smoke extraction / BMS interface, and the commissioning test regime itself.** The brief indicates the adequacy of the current test regime is contested. That is a signal the problem may be larger than the item in front of you. Scope the review to include the interface architecture, not just the Brandschutzanlage in isolation.

3. **Map the subcontractor interface and assign single-point integration accountability.** Multi-subcontractor life-safety systems with diffuse interface responsibility are a well-known failure pattern. Someone needs to own the integrated system, not just their scope slice.

4. **Re-examine the technical leadership capacity on the FBB side.** Turnover in technical leadership during a programme of this scale and complexity is a material governance signal. The board should satisfy itself that the current technical leadership has the authority, the engineering depth, and the mandate to own the commissioning critical path.

5. **Pre-align the three shareholders before any public announcement.** A tripartite public-shareholder structure announcing a major deferral inconsistently across Berlin, Brandenburg, and the federal level will do more reputational damage than the deferral itself. Get to one position first.

6. **Engage airlines and major tenants privately before the public announcement** so their operational plans and public messaging can move with you rather than against you. This also materially reduces your contractual exposure.

7. **Address the Tegel licence interaction deliberately.** If Tegel's operating licence is structured against BER's opening date, a deferral has second-order regulatory consequences that need to be handled in parallel, not discovered afterwards.

---

## Confidence and what would change my view

**Confidence: high** that reaffirmation is the wrong call on the evidence presented. **Confidence: high** that "defer the decision" is a worse option than "defer the opening." **Confidence: moderate** on the specific re-planning steps, because the right sequence depends on facts not in the brief.

I would change my view toward reaffirmation only if the board could put in front of me: (a) a written TÜV position that certification within the required window is achievable with identified residual items, (b) an independent engineering view that the BMS interface issue is resolvable without substantive rework, (c) a credible integrated commissioning schedule with float, and (d) evidence that subcontractor reporting has been independently validated against on-site condition. The brief suggests none of these are currently in hand.

---

## One closing observation for the board

The pattern in the brief — repeated opening-date commitments that have been made and then revised, scope expansion absorbed during construction, technical leadership turnover, contested subcontractor reporting, a late-surfacing life-safety certification risk — is not a scheduling pattern. It is a governance and assurance pattern. The 3 June date is the symptom the board has been asked to rule on. The underlying condition is that the programme's assurance system has not been giving the board reliable forward visibility. Whatever the board decides about the date, I would urge it to treat the assurance question as a separate, equally urgent item on its agenda. Getting the date right once is valuable. Getting the assurance system right is what prevents the board from being in this position again in six months.
