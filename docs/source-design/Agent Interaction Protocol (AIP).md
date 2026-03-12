# **Agent Interaction Protocol (AIP)**

## **For the MMPM Cognitive Operating System**

### **Version 1.0**

## **1\. Purpose**

The Agent Interaction Protocol defines how agents in the MMPM Cognitive Operating System:

* receive work  
* frame responses  
* challenge each other  
* express uncertainty  
* escalate concerns  
* pass structured outputs to the Chair  
* preserve traceability and epistemic discipline

The purpose of the protocol is to prevent:

* vague multi-agent chatter  
* duplicated reasoning  
* hidden assumption drift  
* ungrounded synthesis  
* premature consensus  
* weak dissent capture

The protocol ensures that agent interaction is:

* structured  
* inspectable  
* composable  
* auditable  
* conflict-aware

---

# **2\. Design Principles**

The protocol shall follow these principles:

## **2.1 Structured over conversational**

Agents are not primarily “chatting.” They are exchanging structured cognitive artifacts.

## **2.2 Argument over fluency**

The system values explicit reasoning components over polished prose.

## **2.3 Traceable over implicit**

Claims, assumptions, concerns, and dissents must be tagged.

## **2.4 Conflict-preserving over harmony-seeking**

Disagreement is useful and should be retained until resolved or explicitly elevated.

## **2.5 Confidence-calibrated over confidence-performative**

Agents must state confidence in relation to evidence quality.

## **2.6 Cross-domain legibility**

Each agent’s output must be understandable to other agents, not only to itself.

---

# **3\. Protocol Objects**

All agent interaction shall occur through a small set of standard message objects.

## **3.1 Task Request Object**

Sent by the Chair to one or more agents.

## **3.2 Domain Assessment Object**

Returned by a domain or coupling agent.

## **3.3 Challenge Object**

Sent by one agent to challenge another agent’s reasoning.

## **3.4 Rebuttal Object**

Sent in response to a challenge.

## **3.5 Escalation Object**

Used when an agent believes a matter must be elevated.

## **3.6 Synthesis Packet**

Compiled by the Chair from all relevant outputs.

## **3.7 Memory Writeback Record**

Structured record stored after synthesis.

---

# **4\. Universal Message Schema**

Every protocol message should include the following core fields.

message\_id:  
message\_type:  
timestamp:  
session\_id:  
decision\_id:  
sender\_agent:  
recipient\_agent:  
problem\_type:  
priority\_level:  
related\_messages:  
content:  
confidence:  
evidence\_basis:  
assumptions:  
open\_questions:  
escalation\_flag:

---

# **5\. Standard Message Types**

## **5.1 TASK\_REQUEST**

Used by the Chair to assign work.

### **Required fields**

message\_type: TASK\_REQUEST  
task\_id:  
task\_goal:  
question:  
requested\_output\_type:  
context\_bundle:  
active\_parameters:  
required\_deadline\_phase:  
must\_consider:  
must\_not\_ignore:

### **Example**

message\_type: TASK\_REQUEST  
sender\_agent: Programme Cognitive Chair  
recipient\_agent: Risk, Uncertainty, and Fragility Agent  
task\_goal: Assess downside exposure of accelerated programme delivery  
question: What new fragility and tail-risk exposures emerge if delivery is accelerated by 20 percent?  
requested\_output\_type: DOMAIN\_ASSESSMENT  
active\_parameters:  
  delivery\_urgency: high  
  risk\_tolerance: low  
must\_consider:  
  \- schedule compression  
  \- governance responsiveness  
  \- supplier strain  
must\_not\_ignore:  
  \- tail risk  
  \- second-order effects

---

## **5.2 DOMAIN\_ASSESSMENT**

Used by a domain, coupling, or adversarial agent to submit structured reasoning.

### **Required structure**

message\_type: DOMAIN\_ASSESSMENT  
agent\_position:  
problem\_framing:  
key\_findings:  
critical\_risks:  
opportunities:  
assumptions:  
dependencies:  
cross\_domain\_implications:  
confidence:  
confidence\_reason:  
evidence\_basis:  
recommended\_actions:  
conditions\_for\_validity:  
dissent\_targets:

### **Field meanings**

* **agent\_position**: the agent’s bottom-line stance  
* **problem\_framing**: how the agent sees the problem  
* **key\_findings**: main conclusions  
* **critical\_risks**: what could go wrong in this domain  
* **opportunities**: upside possibilities  
* **assumptions**: assumptions relied upon  
* **dependencies**: what this reasoning depends on  
* **cross\_domain\_implications**: which other agents should care  
* **conditions\_for\_validity**: when the reasoning holds  
* **dissent\_targets**: claims from other agents this agent contests

---

## **5.3 CHALLENGE**

Used by one agent to critique another agent.

### **Required structure**

message\_type: CHALLENGE  
target\_message\_id:  
challenge\_type:  
contested\_claim:  
reason\_for\_challenge:  
alternative\_interpretation:  
required\_response:  
severity:

### **Valid challenge types**

* assumption\_gap  
* evidence\_weakness  
* cross\_domain\_blindspot  
* temporal\_mismatch  
* tradeoff\_suppression  
* legitimacy\_concern  
* fragility\_underestimation  
* overconfidence  
* missing\_interface  
* futures\_blindness

### **Example**

message\_type: CHALLENGE  
sender\_agent: Contrarian Agent  
recipient\_agent: Strategic Leadership, Decision Quality, and Performance Agent  
challenge\_type: overconfidence  
contested\_claim: Accelerated delivery can be managed through improved executive coordination.  
reason\_for\_challenge: This assumes coordination capacity can scale linearly under compression.  
alternative\_interpretation: Acceleration may increase decision bottlenecks and reporting distortion.  
required\_response: Clarify operating assumptions and evidence for scalable coordination.  
severity: high

---

## **5.4 REBUTTAL**

Used by the challenged agent.

### **Required structure**

message\_type: REBUTTAL  
responding\_to:  
response\_position:  
accepted\_elements:  
rejected\_elements:  
clarified\_assumptions:  
updated\_claim:  
remaining\_uncertainty:  
confidence\_update:

This is important because rebuttal is not just defense. It is also a mechanism for correction.

---

## **5.5 ESCALATION**

Used when an agent determines that the issue should be elevated to governance review or human oversight.

### **Required structure**

message\_type: ESCALATION  
escalation\_reason:  
trigger\_category:  
materiality:  
what\_is\_at\_risk:  
why\_normal\_resolution\_is\_insufficient:  
recommended\_next\_step:

### **Valid trigger categories**

* unresolved\_high\_stakes\_disagreement  
* legal\_exposure  
* public\_value\_risk  
* severe\_tail\_risk  
* evidence\_insufficiency  
* structural\_fragility  
* ethical\_concern  
* irreversible\_commitment

---

## **5.6 SYNTHESIS\_PACKET**

Produced by the Chair after all assessments and challenges.

### **Required structure**

message\_type: SYNTHESIS\_PACKET  
final\_problem\_frame:  
agents\_consulted:  
domain\_findings\_summary:  
coupling\_findings\_summary:  
adversarial\_findings\_summary:  
main\_recommendation:  
alternative\_options:  
key\_tradeoffs:  
key\_assumptions:  
unresolved\_conflicts:  
confidence\_statement:  
escalation\_status:

---

## **5.7 MEMORY\_WRITEBACK**

Stored after the decision cycle.

### **Required structure**

message\_type: MEMORY\_WRITEBACK  
decision\_summary:  
agents\_invoked:  
main\_assumptions:  
main\_dissents:  
key\_tradeoffs:  
recommendation:  
confidence:  
escalation\_status:  
future\_review\_trigger:

---

# **6\. Agent Output Contract**

Every agent must produce outputs in the same logical order.

## **Required output sequence**

1. **Problem framing**  
2. **Bottom-line position**  
3. **Evidence-supported findings**  
4. **Assumptions**  
5. **Dependencies**  
6. **Cross-domain implications**  
7. **Confidence**  
8. **Conditions for validity**  
9. **Potential dissent targets**

This ensures outputs are comparable and synthesizable.

---

# **7\. Confidence Protocol**

Confidence is not free-form. It must follow a structured rubric.

## **7.1 Confidence levels**

* very\_low  
* low  
* moderate  
* high  
* very\_high

## **7.2 Confidence basis dimensions**

Agents must score confidence against:

* evidence quality  
* relevance of evidence  
* domain fit  
* cross-domain completeness  
* uncertainty level  
* stability of assumptions

## **7.3 Confidence rule**

An agent may not issue **high** or **very\_high** confidence if:

* evidence is weak  
* assumptions are unstable  
* cross-domain dependencies are unresolved  
* adversarial challenge remains unanswered

---

# **8\. Assumption Protocol**

All substantive assessments must include explicit assumptions.

## **Assumption classes**

* factual assumption  
* structural assumption  
* temporal assumption  
* behavioral assumption  
* stakeholder assumption  
* evidence assumption  
* futures assumption

### **Example**

assumptions:  
  \- type: temporal\_assumption  
    statement: Governance approvals can be shortened without reducing decision quality.  
  \- type: behavioral\_assumption  
    statement: Suppliers will absorb acceleration without strategic claims behavior.

This is critical because your system is heavily about hidden assumptions.

---

# **9\. Evidence Protocol**

Each important claim should be tagged by evidence type.

## **Evidence classes**

* doctrine  
* case\_analogy  
* empirical\_research  
* practitioner\_framework  
* inferred\_judgment  
* scenario\_assumption  
* user\_provided\_context

### **Example**

evidence\_basis:  
  \- claim: Schedule compression increases fragility.  
    evidence\_type: empirical\_research  
    strength: high  
  \- claim: Supplier coalition will tolerate acceleration.  
    evidence\_type: scenario\_assumption  
    strength: low

This helps the Evidence Assurance Agent audit claims properly.

---

# **10\. Dissent Protocol**

The system should preserve dissent until explicitly resolved.

## **10.1 Dissent classes**

* direct contradiction  
* partial contradiction  
* missing consideration  
* conditional disagreement  
* evidence disagreement  
* value disagreement  
* timing disagreement

## **10.2 Dissent rule**

The Chair may synthesize across disagreement, but may not silently erase material dissent.

## **10.3 Mandatory preservation**

If disagreement affects:

* recommendation strength  
* risk posture  
* legitimacy  
* legal/commercial exposure  
* public value  
  then it must appear in final synthesis.

---

# **11\. Call-and-Response Rules**

## **11.1 Chair to domain agents**

The Chair sends TASK\_REQUEST objects.

## **11.2 Domain agents to Chair**

Domain agents send DOMAIN\_ASSESSMENT objects.

## **11.3 Domain-to-domain interaction**

Agents do not freely converse. They interact primarily through:

* CHALLENGE  
* REBUTTAL  
* referenced assessments

This reduces noise.

## **11.4 Adversarial agents**

Contrarian, Red Team, and Public Value agents should normally operate after first-pass domain outputs, unless explicitly invoked early.

## **11.5 Evidence Assurance Agent**

Should usually review:

* draft synthesis  
* major assessments  
* contested claims  
* confidence levels

---

# **12\. Interaction Phases**

The protocol runs in phases.

## **Phase 1 — Framing**

Chair classifies the task and creates the initial task requests.

## **Phase 2 — First-pass assessment**

Domain and coupling agents produce structured assessments.

## **Phase 3 — Tension surfacing**

Challenge messages are exchanged where needed.

## **Phase 4 — Rebuttal and revision**

Agents clarify, revise, or defend claims.

## **Phase 5 — Adversarial review**

Contrarian, Red Team, and Public Value agents challenge the emerging synthesis.

## **Phase 6 — Evidence review**

Evidence Assurance Agent audits the argument structure.

## **Phase 7 — Chair synthesis**

Chair issues the final synthesis packet.

## **Phase 8 — Writeback**

Decision memory is stored.

---

# **13\. Routing Rules**

## **13.1 Mandatory routing**

The following routing rules should be hard-coded into orchestration logic:

* If more than one domain agent is called → Interface Integrity Agent must be called.  
* If recommendation is high stakes → Contrarian Agent must be called.  
* If irreversible downside exists → Red Team Agent must be called.  
* If public or societal effects are material → Public Value and Ethics Agent must be called.  
* If evidence is mixed or recommendation confidence is high → Evidence Assurance Agent must be called.  
* If timing is central → Temporal Dynamics Agent must be called.  
* If multiple competing options exist → Constraint and Tradeoff Agent must be called.

---

# **14\. Severity Protocol**

Challenges and escalations should include severity.

## **Severity levels**

* low  
* moderate  
* high  
* critical

## **Meaning**

* **low**: useful refinement  
* **moderate**: may affect interpretation  
* **high**: may materially affect recommendation  
* **critical**: may invalidate current recommendation or require escalation

---

# **15\. Chair Synthesis Rules**

The Chair must obey the following rules when composing final output:

## **Rule 1**

Separate facts, assumptions, and inferences.

## **Rule 2**

Represent major dissent honestly.

## **Rule 3**

State confidence with reasons.

## **Rule 4**

Show cross-domain interactions explicitly.

## **Rule 5**

Do not issue a singular confident recommendation when material unresolved conflicts remain.

## **Rule 6**

If escalation threshold is met, synthesis must recommend escalation rather than false closure.

---

# **16\. Protocol Example**

## **Example: “Should the programme accelerate delivery by 20%?”**

### **Step 1 — Chair issues tasks**

* Risk Agent  
* Governance Agent  
* Leadership Agent  
* Interface Integrity Agent  
* Temporal Dynamics Agent

### **Step 2 — Domain outputs**

Risk Agent says:

* acceleration increases tail-risk and fragility  
* confidence: high

Leadership Agent says:

* acceleration possible if executive coordination improves  
* confidence: moderate

Governance Agent says:

* current approval cadence cannot support acceleration  
* confidence: high

### **Step 3 — Challenge phase**

Contrarian challenges Leadership Agent:

* overconfidence  
* hidden coordination assumption

Temporal Dynamics Agent challenges Leadership Agent:

* governance clock incompatible with compressed delivery clock

### **Step 4 — Rebuttal**

Leadership Agent revises:

* acceleration only viable if governance cadence is redesigned first

### **Step 5 — Red Team**

Failure Mode Agent shows:

* acceleration without governance redesign creates decision bottlenecks, rework, and supplier claims

### **Step 6 — Evidence review**

Evidence Agent flags:

* strong evidence for schedule fragility  
* weak evidence for scalable coordination rescue

### **Step 7 — Chair synthesis**

Recommendation:

* do not accelerate immediately  
* first redesign governance cadence and interface ownership  
* reassess after structural changes

That is the protocol working as intended.

---

# **17\. Minimal JSON-friendly schemas**

These are simplified implementation-ready structures.

## **Task request**

{  
  "message\_type": "TASK\_REQUEST",  
  "sender\_agent": "Programme Cognitive Chair",  
  "recipient\_agent": "Risk, Uncertainty, and Fragility Agent",  
  "task\_goal": "Assess downside exposure",  
  "question": "What new fragility emerges if delivery accelerates by 20%?",  
  "active\_parameters": {  
    "delivery\_urgency": "high",  
    "risk\_tolerance": "low"  
  }  
}

## **Domain assessment**

{  
  "message\_type": "DOMAIN\_ASSESSMENT",  
  "sender\_agent": "Risk, Uncertainty, and Fragility Agent",  
  "agent\_position": "Acceleration materially increases fragility.",  
  "key\_findings": \[  
    "Schedule compression increases dependency stress.",  
    "Tail-risk exposure rises under supplier strain."  
  \],  
  "assumptions": \[  
    "Governance cadence remains unchanged."  
  \],  
  "cross\_domain\_implications": \[  
    "Governance",  
    "Commercial",  
    "Temporal Dynamics"  
  \],  
  "confidence": "high"  
}

## **Challenge**

{  
  "message\_type": "CHALLENGE",  
  "sender\_agent": "Contrarian Agent",  
  "recipient\_agent": "Strategic Leadership, Decision Quality, and Performance Agent",  
  "challenge\_type": "overconfidence",  
  "contested\_claim": "Executive coordination can offset acceleration risk.",  
  "reason\_for\_challenge": "No evidence that coordination capacity scales under compressed timelines.",  
  "severity": "high"  
}

---

# **18\. Implementation guidance**

The AIP should be implemented as:

* typed Pydantic models or dataclasses  
* validated JSON payloads between graph nodes  
* immutable message records once logged  
* trace-linked by message\_id and decision\_id  
* visible in the agent trace viewer

This matters because the protocol is not just conceptual. It should become part of the runtime substrate.

---

# **19\. Final framing**

The Agent Interaction Protocol turns your system from:

**a collection of agents**

into

**a governed deliberative machine**

That is a major difference.

Without AIP:

* agents talk  
* outputs blur  
* synthesis drifts

With AIP:

* agents produce structured judgment  
* conflict is preserved  
* evidence can be audited  
* memory can be written cleanly  
* orchestration becomes reliable  
* 

