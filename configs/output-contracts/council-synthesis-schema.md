# Council Synthesis — Structured Output Schema

Added 2026-04-21 as part of the feedback-loop infrastructure. Every Council synthesis (full 14-section format per `agents/programme-cognitive-chair.md`) is accompanied by a machine-extractable metadata block. The metadata block enables the prediction-log extraction, calibration review, and cross-case pattern detection that make MMPM-COS a learning system rather than a static doctrine layer.

## Metadata block location

At the top of every Council output, after the HTML comment metadata header (run environment) and before `# PROGRAMME GOVERNANCE COUNCIL BRIEF`:

```markdown
<!-- Run metadata (existing) -->
<!-- ... -->

<!-- COUNCIL SYNTHESIS METADATA (structured, machine-extractable) -->
```yaml
schema_version: 1.0
output_mode: council | council_lite
programme:
  slug: {programme-slug}
  canonical_name: {full name}
  sector: {sector-slug}
  jurisdiction: {jurisdiction-slug}
  institution: {institution-slug or null}
decision:
  slug: {decision-slug}
  one_line: {the decision in a sentence}
  moment: {ISO-8601 date or date-range}
  classification: DOMAIN_SPECIFIC | CROSS_DOMAIN | GOVERNANCE_DECISION | SCENARIO_EXPLORATION
practitioner_context:
  retrieved_annotations: [list of annotation_id]
  cold_start: boolean
  annotations_acted_on: [list of annotation_id — subset of retrieved]
parameters:
  strategic_criticality: low | moderate | high | critical
  public_visibility: low | moderate | high
  stakeholder_fragmentation: low | moderate | high
  risk_tolerance: low | moderate | high
  tail_risk_sensitivity: low | moderate | high
  schedule_rigidity: flexible | moderate | rigid
  equity_weighting: low | moderate | high
  cultural_sensitivity: low | moderate | high
  environmental_sensitivity: low | moderate | high
  time_horizon: short | medium | long
  disruption_sensitivity: low | moderate | high
  # Add additional inferred parameters as relevant
mandatory_routing_triggers:
  fired: [list of rule numbers from routing-rules.md §Mandatory Routing Rules]
  not_fired_but_flagged: [list]
agents_consulted:
  - name: {agent name}
    confidence: very_low | low | moderate | moderate-to-high | high | very_high
    primary_findings_count: {N}
recommendation:
  direction: proceed | proceed_with_conditions | defer | reject | reframe
  confidence: very_low | low | moderate | moderate-to-high | high | very_high
  conditionality: unconditional | time-bounded | evidence-bounded | subject_to_escalation
  one_line: {primary recommendation in a sentence}
alternative_options_count: {N}
key_risks:
  - name: {risk name}
    severity: LOW | MODERATE | MODERATE-HIGH | HIGH | CRITICAL
    source_agents: [list]
    mitigation_in_rec: boolean
red_team_scenarios:
  - name: {scenario name}
    likelihood: low | moderate | high
    severity: LOW | MODERATE | HIGH | CRITICAL
unresolved_tensions_count: {N}
unresolved_tensions:
  - name: {tension name}
    agents_dissenting: [list]
    chair_preference: {stated | not stated}
escalation_status: none | recommended | required
escalation_items: [list of specific escalation questions]
chair_self_audit:
  coverage: complete | partial | incomplete_with_reason
  agent_refusals_or_hedges: boolean
  contrarian_integration: substantive | procedural | absent
  synthesis_honesty: integrated | papered_over | flagged_as_papered_over
  scoping_limits_flagged: [list]
  chair_confidence_in_orchestration: high | moderate | low
evidence_quality_gate:
  reference_class_check_passed: boolean | not_applicable
  financial_model_critique_ran: boolean | not_applicable
  fluency_trap_detected: boolean
  confidence_downgrades_applied: [list of reasons]
auditable_predictions:
  # One entry per P# in the prediction record
  - id: P1
    claim: {specific, outcome-auditable prediction}
    horizon: {short | medium | long — when this prediction can be checked}
  - id: P2
    claim: ...
    horizon: ...
word_count: {integer}
```
<!-- END COUNCIL SYNTHESIS METADATA -->
```

## Why this exists

Three purposes:

1. **Prediction-log extraction**: the prediction-log write step in `memory/predictions/` extracts `auditable_predictions` directly from this block, plus `recommendation`, `key_risks`, `red_team_scenarios`, and `unresolved_tensions` for the prediction record's prose sections.

2. **Cross-case pattern detection**: a calibration review (or any analytical pass over the Council output corpus) can operate over the structured metadata without needing to parse free-text prose. Queries like "across all Council outputs with `tail_risk_sensitivity: high`, how often did Red Team flag HIGH-severity scenarios?" become trivially computable.

3. **Chair Self-Audit auditability**: `chair_self_audit` block makes the Self-Audit structurally extractable and comparable across cases. A calibrator can detect patterns like "chair_confidence_in_orchestration: high on every case" (which would indicate the Self-Audit is not working honestly).

## Discipline

- **No hiding in prose**. A recommendation in the prose that is not reflected in `recommendation.direction` is a schema violation. The Chair MUST reconcile them.
- **No fake structure**. Empty lists are legitimate (e.g., `agent_refusals_or_hedges: false`). Fabricated entries are not.
- **Version the schema**. `schema_version: 1.0` is bumped when the schema structure changes. Calibration tools must handle version drift.
- **Optional fields clearly marked**. Fields that don't apply (e.g., `evidence_quality_gate.financial_model_critique_ran: not_applicable` on a non-financial decision) use explicit `not_applicable` rather than omission.

## Coexistence with existing `benchmark/outputs/*` format

The evaluation W1 / W4 Council outputs committed earlier on this branch predate this schema and use only the HTML-comment run-metadata header. They do not need retrofitting. Subsequent Council outputs include both headers: the HTML comment for run environment and the YAML block for synthesis metadata.

## Provenance

Drafted 2026-04-21 as part of the architectural evolution from the post-evaluation retrospective. This schema is the bridge between Council's prose output and the feedback-loop infrastructure.
