# MMPM Cognitive Operating System (MMPM-COS)

A constitutional multi-agent decision architecture for major programme governance, grounded in the Oxford Major Programme Management (MMPM) lectures.

MMPM-COS is a **governed deliberation engine** — not a project management tool — designed to improve decision quality, systemic robustness, and governance integrity in major programmes under uncertainty.

---

**Empirical evaluation**: [`/evaluations/`](evaluations/) — four-workstream study testing whether Council deliberation surfaces risk dimensions that vanilla and Flyvbjerg-primed baselines miss, with pre-registered rubric and honest limitations. *Status: first-pass runs complete across all four workstreams (5 of 8 W1 cases, 4 of 22 W2 concepts, W3 complete, W4 complete). System improvements listed below were derived from the findings.*

---

## What Council Reliably Adds Over Unprimed Claude

The evaluation surfaced that unprimed Claude (Opus 4.7) is a stronger baseline than the design initially assumed — it produces competent programme-board advice at ~17/20 on a 10-dimension rubric without MMPM priming. Council's reliable differentiation is concentrated in **three structural dimensions** plus **one routing-dependent dimension**:

| Dimension | Where Council differentiates |
|-----------|------------------------------|
| **Dissent preservation** (§12 Unresolved Tensions) | Structural — Council surfaces named tensions that unprimed outputs converge away |
| **Public-value framing** (Public Value + Impact agents) | Structural — distributional, legitimacy, socio-material dimensions reliably surfaced |
| **Temporal mismatch** (Temporal Dynamics agent) | Structural — multi-clock analysis is Council's most consistent advantage |
| **Reference-class forecasting** (Risk Agent, mandatory per routing rule 9) | Routing-dependent — closed post-evaluation gap |

Council does **not** reliably differentiate on general judgment quality, single-dimension risk analysis, or scoping/framing where the brief is well-constructed. Users who expect Council to outperform unprimed Claude on every dimension will be disappointed; users who expect it on the four dimensions above will see it consistently.

See [`evaluations/findings.md`](evaluations/) (when complete) and per-workstream findings for the empirical basis.

## What Council Does Not Replace

- **Technical / engineering analysis** beyond governance framing (e.g., signalling integration, structural engineering, actuarial modelling).
- **Legal / contract interpretation** of specific contract provisions or jurisdictional law.
- **Quantitative financial modelling** — Council critiques financial models structurally (per the Evidence Quality Gate routine) but does not reproduce them.

In cases where the dominant analytical question sits outside MMPM-COS routing destinations, Council's appropriate response is to **reframe to "require independent specialist review"** and explicitly acknowledge the scoping limit. This is a feature, not a shortcoming.

## Verbosity Note

Council's 13-section synthesis carries overhead that earns its place on consequential, multi-domain governance decisions and does not when the input is simple. Raw scores favour Council (~20/20); normalised per-100-word scores favour unprimed Claude (~1.3) over Council (~0.5). The `/analyst` command or the post-evaluation **Council-Lite** routing (see `configs/routing/routing-rules.md` §Input-Complexity Routing) produces proportionate outputs on short or single-domain inputs.

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

| Condition | Required Agent / Routine |
|---|---|
| >1 domain agent active | Interface Integrity |
| Consequential decision | Contrarian |
| Irreversible downside | Red Team |
| Public/societal effects | Public Value and Ethics |
| Timing is central | Temporal Dynamics |
| Competing options | Constraint and Tradeoff |
| Tight coupling detected | Emergence and Fragility |
| **Nameable reference class** *(post-eval)* | Risk Agent (mandatory base-rate framing) |
| **Financial-model input** *(post-eval)* | Evidence Quality Gate structural-critique routine |

See [`configs/routing/routing-rules.md`](configs/routing/routing-rules.md) for full text. Post-evaluation additions (rules 9 and 10) close gaps identified in the BER pilot and the W3 PERT-mean case.

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
