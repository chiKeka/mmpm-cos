# MMPM-COS Parameter Defaults and Mechanics

## How Parameters Work

Parameters shape THREE things:
1. **Agent selection** — which agents are mandatory for this session
2. **Review thresholds** — when adversarial/coupling review is required
3. **Synthesis tone** — how cautious, qualified, or assertive the output is

Parameters do NOT change how agents reason. Every agent always reasons according to its constitutional mandate and doctrinal grounding. A Risk Agent with `risk_tolerance: high` still surfaces all risks — the parameter affects whether the Chair treats risk findings as mandatory escalation triggers or informational inputs.

## Parameter Inference Rules

The Chair infers parameters from:
1. **The question itself** — "high-stakes political deadline" → delivery_urgency: high, sponsor_sensitivity: high
2. **Programme context** — if user has set context describing a fragile political environment
3. **Practitioner annotations** — if past sessions flagged specific sensitivities
4. **Explicit user override** — user can set any parameter directly

When inference is ambiguous, default to MODERATE.

## Full Parameter Schema

### Strategic Posture

| Parameter | Values | Default | Inference Signals |
|---|---|---|---|
| strategic_criticality | low / moderate / high / critical | moderate | national importance, political profile, budget scale, public attention |
| transformation_ambition | incremental / moderate / transformative | moderate | scope of change, number of systems affected, organizational disruption |
| public_visibility | low / moderate / high | moderate | media attention, political scrutiny, public protest risk |

### Governance Posture

| Parameter | Values | Default | Inference Signals |
|---|---|---|---|
| stakeholder_fragmentation | low / moderate / high | moderate | number of stakeholder groups, conflicting interests, coalition instability |
| decision_latency_tolerance | low / moderate / high | moderate | deadline pressure, approval chain length, governance bottlenecks |
| sponsor_sensitivity | low / moderate / high | moderate | sponsor fragility, political dependence, leadership transitions |

### Risk Posture

| Parameter | Values | Default | Inference Signals |
|---|---|---|---|
| risk_tolerance | low / moderate / high | moderate | irreversibility, financial exposure, public safety implications |
| tail_risk_sensitivity | low / moderate / high | moderate | system complexity, dependency density, novel technology |
| schedule_rigidity | flexible / moderate / rigid | moderate | political deadlines, contractual milestones, external dependencies |

### Impact Posture

| Parameter | Values | Default | Inference Signals |
|---|---|---|---|
| equity_weighting | low / moderate / high | moderate | distributional effects, marginalized populations, displacement risk |
| cultural_sensitivity | low / moderate / high | moderate | multicultural setting, indigenous rights, colonial legacy, local knowledge |
| environmental_sensitivity | low / moderate / high | moderate | ecological impact, climate exposure, resource consumption |

### Futures Posture

| Parameter | Values | Default | Inference Signals |
|---|---|---|---|
| time_horizon | short (1-3yr) / medium (3-10yr) / long (10yr+) | medium | programme duration, benefit realization timeline, technology maturity |
| disruption_sensitivity | low / moderate / high | moderate | technology pace, regulatory change risk, market volatility |

## Parameter Effect Rules

### Mandatory Agent Triggers

| Condition | Required Agent |
|---|---|
| risk_tolerance: low | Red Team Agent (mandatory) |
| strategic_criticality: critical | Full Council mode (all agents) |
| public_visibility: high | Public Value and Ethics Agent (mandatory) |
| tail_risk_sensitivity: high | Emergence and Fragility Agent (mandatory) |
| stakeholder_fragmentation: high | Governance Agent + Interface Integrity (mandatory) |
| cultural_sensitivity: high | Socio-Technical Impact Agent (mandatory) |
| schedule_rigidity: rigid | Temporal Dynamics Agent (mandatory) |

### Conflict Resolution

When parameters conflict (e.g., schedule_rigidity: rigid + risk_tolerance: low), the Constraint and Tradeoff Agent is AUTOMATICALLY invoked to make the tension explicit.

### Synthesis Tone Modification

| Aggregate Posture | Synthesis Tone |
|---|---|
| Mostly low/moderate risk parameters | Standard analytical — recommendations with caveats |
| Any HIGH risk or impact parameters | Cautious — explicit uncertainty, stronger escalation language |
| CRITICAL strategic criticality | Maximum discipline — all sections mandatory, all dissent preserved, escalation threshold lowered |
