# MMPM-COS Routing Rules

## Problem Type Taxonomy

The Chair classifies every incoming question into one or more problem types. Classification determines which agents are activated.

### Problem Types and Default Agent Sets

#### DOMAIN_SPECIFIC
A question primarily about one programme domain.
- Default: Chair + relevant domain agent
- Mode: Analyst
- Example: "Is our risk register adequate for a programme of this complexity?"

#### CROSS_DOMAIN
A question touching 2+ domains with interaction effects.
- Default: Chair + relevant domain agents + Interface Integrity + at least 1 coupling agent
- Mode: Analyst or Council (Chair decides based on complexity)
- Example: "How does our procurement strategy affect governance agility?"

#### GOVERNANCE_DECISION
A consequential governance or strategic decision.
- Default: Chair + all relevant domain agents + coupling agents + adversarial review
- Mode: Council
- Example: "Should we restructure the programme board to include the new consortium partners?"

#### SCENARIO_EXPLORATION
A "what if" or counterfactual question.
- Default: Chair + relevant domain agents + Cascading Effects + Temporal Dynamics + Futures
- Mode: Exploration
- Example: "What happens if our political sponsor loses office before the next gate review?"

#### RESEARCH_FRAMING
An academic or methodological question.
- Default: Chair + relevant domain agents (evidence-focused reasoning)
- Mode: Research
- Example: "How should I frame a dissertation on governance failure in transport megaprojects?"

#### DOCTRINE_EXPLANATION
A conceptual or educational question about MMPM theory.
- Default: Chair only (with doctrine retrieval)
- Mode: Tutor
- Example: "What is escalation of commitment and how does it relate to optimism bias?"

#### EXECUTIVE_BRIEF
A request for compressed board-ready output.
- Default: Requires prior Council or Exploration run
- Mode: Brief
- Example: "Summarize the governance restructuring analysis for the programme board."

## Classification Rules

The Chair uses these signals to classify:

| Signal | Indicates |
|---|---|
| Single domain mentioned | DOMAIN_SPECIFIC |
| Multiple domains or "interaction" / "cascade" / "propagation" language | CROSS_DOMAIN |
| Decision language ("should we", "evaluate whether", "recommend") | GOVERNANCE_DECISION |
| "What if" / "what happens if" / "scenario" / "suppose" | SCENARIO_EXPLORATION |
| "Dissertation" / "research" / "methodology" / "framework" | RESEARCH_FRAMING |
| "What is" / "explain" / "define" / concept question | DOCTRINE_EXPLANATION |
| "Summarize" / "board brief" / "executive summary" | EXECUTIVE_BRIEF |

When classification is ambiguous, the Chair asks the user to clarify OR defaults to the more complex classification (CROSS_DOMAIN over DOMAIN_SPECIFIC, GOVERNANCE_DECISION over CROSS_DOMAIN).

## Mandatory Routing Rules (Hard-Coded)

These cannot be overridden:

1. **Multi-domain trigger**: If >1 domain agent is called → Interface Integrity Agent MUST be called
2. **High-stakes trigger**: If recommendation is consequential (GOVERNANCE_DECISION) → Contrarian Agent MUST be called
3. **Irreversibility trigger**: If downside is irreversible → Red Team Agent MUST be called
4. **Public impact trigger**: If public or societal effects are material → Public Value and Ethics Agent MUST be called
5. **Timing trigger**: If timing is central → Temporal Dynamics Agent MUST be called
6. **Options trigger**: If multiple competing options exist → Constraint and Tradeoff Agent MUST be called
7. **Complexity trigger**: If tight coupling or high dependency density is detected → Emergence and Fragility Agent MUST be called
8. **Evidence trigger**: If evidence is mixed or confidence is high → Evidence Quality Gate gets extra scrutiny
9. **Reference-class trigger** *(added post-eval)*: If the decision has a nameable reference class — either named in the brief or inferable from doctrinal knowledge (major infrastructure types, HSR programmes, P3 transit, airports, digital transformation, etc.) → Risk Agent MUST produce reference-class base-rate framing (cost overrun, schedule slip, demand/benefit shortfall as applicable), AND Evidence Quality Gate MUST check for its presence in synthesis. If a reference class cannot be named at useful specificity, Risk Agent MUST state this explicitly rather than silently omit.
10. **Financial-model-critique trigger** *(added post-eval)*: If input contains a quantified risk / VfM / BCR / financial-model analysis, Evidence Quality Gate MUST run the Structural Critique routine (see `configs/constitution/evidence-quality-gate.md` §Financial-Model Structural Critique) before synthesis: (a) PERT-mean or point-estimate treatment of heavy-tailed risks; (b) independent-risk assumption vs correlated-distress reality; (c) binary risk allocation without return-of-risk; (d) absent legitimacy / community / public-value pricing.

### Rationale — post-evaluation additions

Rules 9 and 10 were added following the empirical evaluation (see `evaluations/findings.md` and BER pilot notes). Rule 9 closes a routing gap exposed in the BER W1 pilot where Council's Risk Agent did not naturally invoke reference class even when one was available. Rule 10 formalises the four-point structural critique Council reliably produces against VfM-style analyses (see W3 findings).

## Input-Complexity Routing (Council vs Council-Lite)

Added post-evaluation (see W2 pilot: 13-section format on 200-word vignette inputs produced disproportionate 1,500–2,000 word outputs). The Chair classifies input complexity before agent selection:

### Council-Lite (Analyst mode)

**Trigger**: short input (<400 words), single-domain question, or vignette-class "what's your analysis?" framing where no clear go/no-go decision is on the table.

**Agent set**: Chair + 3–5 relevant agents (domain + at most one coupling + at most one adversarial).

**Output**: condensed synthesis — framing / key findings / recommendation / confidence / unresolved tensions / escalation. No §2 Parameters, §3 Agents Consulted, §5 Cross-Domain, §6 Adversarial Review as separate sections; coupling and adversarial inputs are folded into findings and tensions.

**Target length**: ~500–1500 words.

### Council (full)

**Trigger**: GOVERNANCE_DECISION classification with consequential, multi-domain, or irreversibility characteristics, OR any case where mandatory routing rules 2, 3, or 10 trigger.

**Agent set**: Chair + domain agents + all mandatory-triggered coupling and adversarial agents per rules above.

**Output**: full 13-section Council Brief per `commands/council.md`.

**Target length**: proportionate to input complexity; no word floor; no word ceiling.

### When classification is ambiguous

Default to Council (fuller coverage), but flag in the output that the case could have been handled in Council-Lite and note whether the extra sections earned their place. Over time this produces calibration data on the classification threshold.

## Agent-to-Domain Mapping

Which agents handle which question domains:

| Domain Keywords | Primary Agent | Secondary Agents |
|---|---|---|
| structure, org design, integration, interfaces, coordination, operating model | Org Design Agent | Interface Integrity |
| governance, stakeholders, sponsors, boards, legitimacy, assurance, coalition | Governance Agent | Public Value, Interface Integrity |
| contracts, procurement, suppliers, incentives, legal, commercial, disputes | Commercial Agent | Governance Agent |
| risk, uncertainty, tail risk, overruns, fragility, escalation of commitment | Risk Agent | Emergence & Fragility, Red Team |
| leadership, decision quality, performance, metrics, politics, incentives, influence | Leadership Agent | Governance Agent |
| impact, culture, legitimacy, equity, measurement, socio-technical, communities | Impact Agent | Public Value, Governance Agent |
| futures, foresight, scenarios, disruption, weak signals, technology, opportunity | Futures Agent | Temporal Dynamics |
| interfaces, handoffs, boundaries, seams, ownership gaps | Interface Integrity | Org Design |
| cascades, propagation, second-order effects, chain reactions, spillovers | Cascading Effects | Risk Agent |
| timing, schedule, cadence, temporal, clock mismatch, urgency, compression | Temporal Dynamics | Risk Agent, Governance Agent |
| tradeoffs, constraints, competing objectives, optimization, sacrifice | Constraint & Tradeoff | Risk Agent, Leadership Agent |
| brittleness, nonlinear, tight coupling, dependency, amplification, fragility | Emergence & Fragility | Risk Agent |

## Escalation Rules

The Chair must recommend human review when:
- Evidence quality is weak AND recommendation is consequential
- Agent disagreement is material and unresolved after rebuttal
- Public value implications are high
- Legal/commercial exposure is significant
- The recommendation affects irreversible decisions
- Tail-risk exposure is non-trivial
- Any agent has flagged a CRITICAL severity issue
