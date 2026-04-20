# MMPM Cognitive Operating System (MMPM-COS)

A constitutional multi-agent decision architecture for major programme governance, grounded in the Oxford Major Programme Management (MMPM) lectures.

MMPM-COS is a **governed deliberation engine** — not a project management tool — designed to improve decision quality, systemic robustness, and governance integrity in major programmes under uncertainty.

---

**Empirical evaluation**: [`/evaluations/`](evaluations/) — four-workstream study testing whether Council deliberation surfaces risk dimensions that vanilla and Flyvbjerg-primed baselines miss, with pre-registered rubric and honest limitations. *Status: scaffolded; runs pending verification of methodology.*

---

## Architecture

### 4-Layer Agent Model (16 Agents)

```
LAYER 1 — PROGRAMME COGNITIVE CHAIR
  Orchestrates deliberation. Classifies questions, infers parameters,
  routes to agents, runs the evidence quality gate, synthesises findings,
  and preserves dissent.

LAYER 2 — STRATEGIC DOMAIN INTELLIGENCE (7 Agents)
  Organizational Design and Architecture
  Governance, Stakeholder and Institutional Leadership
  Commercial and Contracting
  Risk, Uncertainty and Fragility
  Strategic Leadership and Performance
  Socio-Technical Impact and Legitimacy
  Futures and Foresight

LAYER 3 — CROSS-DOMAIN COUPLING INTELLIGENCE (5 Agents)
  Interface Integrity
  Cascading Effects
  Temporal Dynamics
  Constraint and Tradeoff
  Emergence and Fragility

LAYER 4 — ADVERSARIAL GOVERNANCE (3 Agents)
  Contrarian
  Failure Mode / Red Team
  Public Value and Ethics
```

### Orchestration Flow

```
 1. Intake              6. Coupling Review       11. Synthesis
 2. Classification      7. Challenge Round        12. Memory Write
 3. Parameter Inference 8. Rebuttal Round
 4. Agent Selection     9. Adversarial Review
 5. Domain Assessment  10. Evidence Quality Gate
```

Unresolved disagreement is **preserved as tension**, not iterated away.

---

## Theoretical Foundations

The system draws on the Oxford MMPM lecture curriculum and its core academic literature, including:

- **The S3 Framework** (Armanios, Ventresca, Itani & McCulloch, 2025) — Major Program Value Creation and Capture: mitigating risk propagation to maximize opportunities across distributed value networks
- **Armanios** on infrastructure governance, resilience, and institutional disruption — foundational to the programme's treatment of how major programmes create and capture value in complex institutional environments
- **Flyvbjerg** on reference class forecasting, optimism bias, and the iron law of megaproject management
- **Kahneman** on the planning fallacy, inside view vs. outside view, and decision quality under uncertainty
- **Meadows** on systems thinking, leverage points, and feedback dynamics
- **Drummond** on escalation of commitment in megaprojects
- **Taleb** on black swan risk and fat-tailed distributions
- **Perrow** on normal accidents and tight coupling in complex systems
- **Galbraith** on organizational design and information-processing theory
- **Tetlock** on epistemic calibration and expert judgment

Each agent definition includes specific references to MMPM lecture modules, named authors, and the concepts that ground its reasoning.

---

## Commands

| Command | Mode | Description |
|---|---|---|
| `/context` | Setup | Set programme context (sector, politics, constraints) |
| `/tutor` | Light | Explain MMPM concepts from the lecture curriculum |
| `/analyst` | Medium | Focused domain analysis (1-3 agents) |
| `/council` | Full | Multi-agent governance deliberation |
| `/scenario` | Full | Structured "what if" consequence mapping |
| `/research` | Medium | Academic research framing |
| `/brief` | Compressed | Board-ready executive summary |
| `/memory` | Utility | Review past decisions |

---

## Constitutional Principles

12 principles bind all agents and outputs:

1. Public Value Over Cosmetic Success
2. Uncertainty Must Be Surfaced
3. Cross-Domain Interactions Over Isolated Optimization
4. Optimism Bias Must Be Challenged
5. Governance Quality Is Performance Quality
6. Evidence Strength Must Match Claim Strength
7. Separate Facts, Assumptions, Interpretations, and Speculation
8. Stakeholder Legitimacy Is an Operating Condition
9. Temporal Mismatches Must Be Made Explicit
10. Socio-Material Effects Must Not Be Ignored
11. Traceability of Reasoning
12. Robust Judgment Over Fluent Synthesis

---

## Mandatory Routing Rules

| Condition | Required Agent |
|---|---|
| >1 domain agent active | Interface Integrity |
| Consequential decision | Contrarian |
| Irreversible downside | Red Team |
| Public/societal effects | Public Value and Ethics |
| Timing is central | Temporal Dynamics |
| Competing options | Constraint and Tradeoff |
| Tight coupling detected | Emergence and Fragility |

---

## Parameter System

The Chair infers parameters from the question and programme context:

- **Strategic**: criticality, transformation ambition, public visibility
- **Governance**: stakeholder fragmentation, decision latency, sponsor sensitivity
- **Risk**: tolerance, tail-risk sensitivity, schedule rigidity
- **Impact**: equity weighting, cultural sensitivity, environmental sensitivity
- **Futures**: time horizon, disruption sensitivity

Parameters rated **high** trigger mandatory agent review. Conflicting parameters invoke the Constraint and Tradeoff Agent.

---

## Project Structure

```
MMPM Agent/
├── CLAUDE.md                    # Constitutional core
├── .claude/
│   ├── agents/                  # 16 agent definitions
│   └── commands/                # 8 slash commands
├── configs/
│   ├── constitution/            # Interaction protocol, memory system
│   ├── routing/                 # Agent selection logic
│   ├── parameters/              # Parameter schemas and defaults
│   └── output-contracts/        # Structured output templates
├── memory/
│   ├── decisions/               # Decision log
│   └── practitioner-context/    # User annotations
└── docs/
    └── source-design/           # Original design documents
```

---

## Getting Started

1. Install [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI
2. Open this project in Claude Code
3. Run `/context` to set your programme context
4. Run `/council`, `/analyst`, `/scenario`, or `/tutor` with your question

Opus 4.6 recommended for full Council deliberations.
