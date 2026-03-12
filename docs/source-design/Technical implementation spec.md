---

## **2\. Technical implementation spec**

Now the implementation layer.

---

# **A. Technical design principles**

The system should be built as a **stateful, graph-orchestrated, tool-augmented, memory-aware agent platform**.

Core design choices:

* **Graph-based orchestration**, not loose agent chat  
* **Typed state**, not unstructured conversational drift  
* **Hybrid retrieval**, not vector-only search  
* **Explicit memory writes**, not passive context accumulation  
* **Evaluation-first development**, not prompt-first improvisation  
* **Human-review gates**, not blind autonomy

---

# **B. Recommended stack**

## **Orchestration engine**

**LangGraph** as the primary orchestration runtime.

Why:

* explicit node/edge control  
* stateful multi-step execution  
* durable execution  
* branching and conditional routing  
* good fit for Chair → agents → review → synthesis flow

## **Model layer**

Use a strong reasoning model for:

* Chair  
* Risk Agent  
* Evidence Agent  
* Contrarian Agent  
* Synthesis

Use lighter, cheaper models for:

* classification  
* simple retrieval summarization  
* metadata extraction  
* batch chunk tagging

## **Retrieval layer**

Hybrid retrieval stack:

* vector search for semantic similarity  
* BM25 / keyword search for exact doctrinal and citation recall  
* metadata filtering for module, concept, method, case type  
* optional reranker for precision

## **Storage**

* **Postgres** for structured state, decisions, agent outputs, metadata  
* **Vector DB** such as Qdrant, Weaviate, or pgvector for semantic retrieval  
* **Graph DB** such as Neo4j for concept graph and relationship reasoning  
* object storage for PDFs, notes, and source artifacts

## **API layer**

FastAPI or similar for:

* session management  
* orchestration invocation  
* user interface integration  
* admin and evaluation endpoints

## **Front end**

Two surfaces initially:

* **analyst chat / scenario workspace**  
* **board brief dashboard**

Later add:

* doctrine explorer  
* agent trace viewer  
* evaluation console

---

# **C. Core data model**

## **1\. Agent registry table**

Fields:

* agent\_id  
* name  
* version  
* domain\_type  
* identity\_kernel  
* principles  
* call\_rules  
* output\_schema  
* escalation\_rules  
* status

## **2\. Source document table**

Fields:

* source\_id  
* title  
* module  
* author  
* year  
* source\_type  
* method\_type  
* evidence\_strength\_hint  
* tags  
* file\_location

## **3\. Chunk table**

Fields:

* chunk\_id  
* source\_id  
* chunk\_text  
* concept\_tags  
* argument\_type  
* domain\_relevance  
* cross\_domain\_relevance  
* embedding  
* citation\_locator

## **4\. Concept graph tables**

Nodes:

* concept\_id  
* concept\_name  
* concept\_type

Edges:

* source\_concept  
* target\_concept  
* relation\_type  
* confidence  
* originating\_source

## **5\. Session table**

Fields:

* session\_id  
* user\_id  
* mode  
* active\_parameters  
* start\_time  
* end\_time

## **6\. Decision record table**

Fields:

* decision\_id  
* session\_id  
* problem\_type  
* question\_text  
* agents\_invoked  
* main\_recommendation  
* alternatives  
* assumptions  
* confidence  
* escalation\_status  
* final\_output  
* timestamp

## **7\. Agent output table**

Fields:

* output\_id  
* decision\_id  
* agent\_id  
* prompt\_context\_hash  
* retrieved\_sources  
* output\_json  
* confidence  
* dissent\_flag  
* timestamp

## **8\. Memory tables**

Separate memory by type:

* constitutional\_memory  
* semantic\_memory  
* episodic\_memory  
* reflective\_memory

---

# **D. State model for orchestration**

The LangGraph state object should be typed roughly like this:

class ProgrammeState(TypedDict):  
    session\_id: str  
    user\_query: str  
    mode: str  
    problem\_type: str  
    active\_parameters: dict  
    retrieved\_context: list  
    selected\_agents: list  
    agent\_outputs: dict  
    coupling\_outputs: dict  
    adversarial\_outputs: dict  
    evidence\_review: dict  
    synthesis: dict  
    escalation\_status: str  
    memory\_writeback: dict  
    trace: list

This is important because your system is not just passing messages. It is building a **decision object**.

---

# **E. Workflow graph**

## **Primary graph**

\[Input\]  
   ↓  
\[Task Classifier\]  
   ↓  
\[Context Builder\]  
   ↓  
\[Chair Routing Node\]  
   ↓  
\[Domain Agent Fan-Out\]  
   ↓  
\[Coupling Review Nodes\]  
   ↓  
\[Adversarial Review Nodes\]  
   ↓  
\[Evidence Assurance Node\]  
   ↓  
\[Chair Synthesis Node\]  
   ↓  
\[Escalation / Governance Gate\]  
   ↓  
\[Memory Writeback\]  
   ↓  
\[Output Renderer\]

## **Conditional logic**

* if simple doctrinal question → Tutor flow  
* if dissertation or research question → Evidence Agent early, then Research mode  
* if high stakes → Contrarian \+ Red Team mandatory  
* if more than one domain invoked → Interface Integrity mandatory  
* if time-based conflict detected → Temporal Dynamics invoked  
* if option comparison requested → Constraint and Tradeoff invoked

---

# **F. Retrieval and indexing design**

## **Ingestion pipeline**

1. ingest PDFs / notes / cases  
2. parse and clean text  
3. chunk by idea and argument  
4. generate metadata  
5. embed chunks  
6. store vector, keyword, and graph representations  
7. attach doctrine tags

## **Metadata schema**

Each chunk should include:

* module  
* session/day  
* concept family  
* theory vs case vs method  
* evidence type  
* sector relevance  
* cross-domain relevance  
* quote eligibility  
* confidence hint

## **Retrieval strategy**

The system should retrieve in layers:

1. doctrinal core  
2. relevant case analogues  
3. methodological checks where needed  
4. personal synthesis notes if enabled

This stops the system from over-relying on semantically similar but epistemically weak passages.

---

# **G. Tool stack by agent type**

## **Chair tools**

* task classifier  
* routing rules engine  
* parameter interpreter  
* synthesis formatter

## **Design agent tools**

* interface mapper  
* org-structure analyzer

## **Governance agent tools**

* stakeholder salience mapper  
* coalition analyzer  
* governance checklist engine

## **Commercial agent tools**

* contract pattern analyzer  
* incentive-alignment checker

## **Risk agent tools**

* scenario stress tester  
* tail-risk framing tool  
* dependency-risk mapper

## **Leadership agent tools**

* decision-quality checklist  
* influence map analyzer  
* performance distortion checker

## **Impact agent tools**

* legitimacy scan  
* metric politics review  
* stakeholder distribution lens

## **Futures agent tools**

* scenario builder  
* weak-signal tracker  
* horizon map tool

## **Evidence agent tools**

* evidence grader  
* method-fit checker  
* citation and claim classifier

## **Coupling agents**

* propagation mapper  
* temporal conflict detector  
* tradeoff matrix builder  
* fragility scanner

## **Adversarial agents**

* assumption challenger  
* pre-mortem generator  
* public value test

---

# **H. Memory model**

## **Constitutional memory**

Static and versioned.  
Stores:

* constitution  
* system purpose  
* agent principles

## **Semantic memory**

Slow-changing.  
Stores:

* doctrine summaries  
* concept relationships  
* canonical interpretations

## **Episodic memory**

Per session and per decision.  
Stores:

* what was asked  
* which agents were called  
* what was concluded

## **Reflective memory**

Updated when outcomes become available.  
Stores:

* which assumptions failed  
* which patterns recurred  
* which agents were most accurate

## **Write policy**

Not every interaction writes equally.  
Write:

* major decisions  
* strong disagreements  
* novel cases  
* later outcome reviews

Do not write:

* trivial doctrinal clarifications  
* low-stakes exploratory chatter

---

# **I. Evaluation framework**

## **1\. Benchmark library**

Create a test suite of:

* canonical megaproject cases  
* governance failures  
* risk tail events  
* stakeholder legitimacy conflicts  
* impact mismeasurement cases  
* futures-blind decisions

## **2\. Evaluation metrics**

Track:

* doctrine accuracy  
* retrieval relevance  
* agent routing correctness  
* coupling detection rate  
* dissent usefulness  
* evidence calibration  
* output usefulness  
* escalation appropriateness

## **3\. Human review**

Use expert scoring for:

* strategic usefulness  
* governance quality  
* legitimacy sensitivity  
* epistemic discipline

## **4\. Replay harness**

Re-run past cases under different parameter settings and compare:

* invoked agents  
* recommendations  
* sensitivity to toggles  
* stability of conclusions

---

# **J. Governance and safety controls**

## **Decision class gating**

Outputs labeled as:

* exploratory  
* analytical  
* advisory  
* board brief  
* escalation required

## **Human-in-the-loop rules**

Human review required for:

* irreversible commitments  
* high public-value exposure  
* weak evidence but strong recommendation  
* legal/commercial exposure  
* material ethical tradeoffs

## **Traceability**

Every final output should preserve:

* agents invoked  
* sources used  
* assumptions made  
* confidence level  
* dissent captured

---

# **K. MVP build order**

## **Phase 1**

Build:

* Chair  
* Design Agent  
* Governance Agent  
* Risk Agent  
* Leadership Agent  
* Impact Agent  
* Futures Agent  
* Evidence Agent  
* Interface Agent  
* Contrarian Agent

## **Phase 2**

Add:

* Commercial Agent  
* Cascading Effects Agent  
* Temporal Dynamics Agent  
* Constraint and Tradeoff Agent  
* Fragility Agent  
* Red Team Agent  
* Public Value and Ethics Agent

## **Phase 3**

Add:

* board-brief UI  
* trace viewer  
* reflective memory  
* evaluation dashboard  
* scenario sandbox  
* project-specific corpus ingestion

---

# **L. Recommended repository structure**

mmpm-cognitive-os/  
│  
├── app/  
│   ├── api/  
│   ├── orchestration/  
│   ├── agents/  
│   ├── tools/  
│   ├── retrieval/  
│   ├── memory/  
│   ├── evaluation/  
│   └── rendering/  
│  
├── configs/  
│   ├── constitution/  
│   ├── agent\_cards/  
│   ├── routing\_rules/  
│   └── output\_schemas/  
│  
├── data/  
│   ├── doctrine/  
│   ├── cases/  
│   ├── embeddings/  
│   └── graph/  
│  
├── tests/  
│   ├── unit/  
│   ├── integration/  
│   ├── replay/  
│   └── benchmark/  
│  
└── docs/  
    ├── architecture/  
    ├── agent\_registry/  
    ├── evaluation/  
    └── operations/

---

# **M. Final implementation framing**

The implementation should not be treated as “multi-agent chat.”

It should be treated as a **decision operating system** with:

* explicit state  
* controlled invocation  
* typed outputs  
* doctrine-grounded retrieval  
* adversarial review  
* memory  
* evaluation  
* traceability

That is what preserves the seriousness of the architecture.