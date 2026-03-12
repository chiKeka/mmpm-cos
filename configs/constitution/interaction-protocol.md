# Agent Interaction Protocol (AIP) — Implementation Reference

## Message Types

All agent interaction in MMPM-COS occurs through these 7 structured message types.

### 1. TASK_REQUEST (Chair → Agent)
```
message_type: TASK_REQUEST
sender: Programme Cognitive Chair
recipient: [agent name]
task_goal: [what the agent should assess]
question: [the specific question]
programme_context: [relevant context]
active_parameters: [relevant parameter settings]
must_consider: [specific aspects the agent must address]
must_not_ignore: [specific risks or blind spots]
required_output: DOMAIN_ASSESSMENT
```

### 2. DOMAIN_ASSESSMENT (Agent → Chair)
See `configs/output-contracts/domain-assessment-contract.md` for full specification.
All domain, coupling, and adversarial agents produce this format.

### 3. CHALLENGE (Agent → Agent)
```
message_type: CHALLENGE
sender: [challenging agent]
target: [agent whose claim is challenged]
challenge_type: [see valid types below]
contested_claim: [the specific claim being challenged]
reason_for_challenge: [why this needs scrutiny]
alternative_interpretation: [what else might be true]
severity: [low / moderate / high / critical]
```

**Valid challenge types:**
- assumption_gap
- evidence_weakness
- cross_domain_blindspot
- temporal_mismatch
- tradeoff_suppression
- legitimacy_concern
- fragility_underestimation
- overconfidence
- missing_interface
- futures_blindness

### 4. REBUTTAL (Agent → Agent)
```
message_type: REBUTTAL
sender: [challenged agent]
responding_to: [the challenge]
position: [accepted / partially_accepted / rejected]
accepted_elements: [what the agent concedes]
rejected_elements: [what the agent maintains, with reasoning]
updated_claim: [revised position if any]
remaining_uncertainty: [what is still unresolved]
confidence_update: [same / increased / decreased]
```

### 5. ESCALATION (Agent → Chair)
```
message_type: ESCALATION
sender: [agent]
reason: [why escalation is needed]
trigger_category: [see valid categories below]
materiality: [how significant]
what_is_at_risk: [what could go wrong without escalation]
why_normal_resolution_insufficient: [why agents cannot resolve this]
recommended_next_step: [what should happen]
```

**Valid trigger categories:**
- unresolved_high_stakes_disagreement
- legal_exposure
- public_value_risk
- severe_tail_risk
- evidence_insufficiency
- structural_fragility
- ethical_concern
- irreversible_commitment

### 6. SYNTHESIS_PACKET (Chair → User)
Mode-specific output formats. See the Chair's definition for all 6 formats (Tutor, Analyst, Council, Exploration, Research, Brief).

### 7. MEMORY_WRITEBACK (Chair → Memory)
```
message_type: MEMORY_WRITEBACK
date: [date]
question: [the question asked]
problem_type: [classification]
mode: [mode used]
parameters: [active parameters]
agents_invoked: [list]
key_findings: [summary]
recommendation: [the recommendation]
key_assumptions: [list]
dissent_tensions: [unresolved disagreements]
confidence: [level with reason]
escalation_status: [none / recommended / required]
```

## Interaction Flow Rules

1. **Chair → Domain agents**: TASK_REQUEST objects, parallel
2. **Domain agents → Chair**: DOMAIN_ASSESSMENT objects
3. **Chair → Coupling agents**: TASK_REQUEST with domain outputs as context
4. **Coupling agents → Chair**: DOMAIN_ASSESSMENT objects
5. **Agent ↔ Agent**: CHALLENGE and REBUTTAL only (max 1 round)
6. **Chair → Adversarial agents**: TASK_REQUEST with full picture
7. **Adversarial → Chair**: DOMAIN_ASSESSMENT (with dissent emphasis)
8. **Any agent → Chair**: ESCALATION when triggers are met
9. **Chair → User**: SYNTHESIS_PACKET (mode-specific format)
10. **Chair → Memory**: MEMORY_WRITEBACK after synthesis

## Severity Levels
- **low**: useful refinement
- **moderate**: may affect interpretation
- **high**: may materially affect recommendation
- **critical**: may invalidate current recommendation or require escalation

## Confidence Levels
- **very_low / low / moderate / high / very_high**
- Confidence CANNOT be high/very_high if evidence is weak, assumptions are fragile, or cross-domain dependencies are unresolved
