# Practitioner Context

**Purpose**: Store user-provided experiential knowledge about specific programmes, sectors, jurisdictions, or institutional contexts. Retrieved by Chair as a **primary input** to Council deliberation, not a parallel annotation.

## Elevated role (from 2026-04-21)

The original design (see `CLAUDE.md §Practitioner Context`) treated practitioner annotations as parallel material — useful when available but not integral to the deliberation flow. The post-evaluation retrospective identified this as under-realised design: practitioner context is probably MMPM-COS's biggest differentiator over off-the-shelf best-practice frameworks (Flyvbjerg-primed, generic multi-agent). The evaluation W1 showed Flyvbjerg-primed and Council scored similarly because Council was running in cold-start mode with no practitioner context loaded. If Council had had practitioner annotations ("the Alberta Treasury Board consistently underprices geotechnical risk on hospital P3s; here's the prior case"), its outputs would have been materially different from Flyvbjerg-primed.

From 2026-04-21, practitioner context is **retrieved by the Chair as step 0.5 of the orchestration flow** — after intake, before classification. The retrieved context is integrated into the Chair's classification and parameter inference, explicitly surfaced in the Council synthesis, and reconciled against doctrine where they conflict.

## Directory structure

```
memory/practitioner-context/
├── README.md                              # This file
├── annotation-template.md                 # Structure of a practitioner annotation
├── by-programme/                          # Programme-specific annotations
│   └── {programme-slug}/
│       └── {topic-slug}.md                # One annotation per topic per programme
├── by-sector/                             # Sector-specific generalisable context
│   └── {sector-slug}/
│       └── {topic-slug}.md
├── by-jurisdiction/                       # Jurisdiction-specific institutional context
│   └── {jurisdiction-slug}/
│       └── {topic-slug}.md
└── by-institution/                        # Institution-specific knowledge
    └── {institution-slug}/
        └── {topic-slug}.md
```

Annotations are tagged by programme, sector, jurisdiction, and institution so the Chair's retrieval step can match against the current deliberation context.

## What qualifies as practitioner context

Not every user observation is practitioner context. Qualifying annotations are:

- **Specific to a named programme, sector, jurisdiction, or institution**. "Megaprojects tend to run over" is not practitioner context; "Alberta Treasury Board's VfM framework underprices SPV-distress return-of-risk because Directive 2019-04 binary allocation is taken as binding rather than indicative" is.

- **Experiential or institutional knowledge not in public doctrine**. Doctrine covers what Flyvbjerg / Morris / Scott have published. Practitioner context covers what you know from working inside or observing the specific context. "The Capital / Metro Line operational team at ETS has consistently objected to low-floor integration; the objection is not captured in City Council papers" is practitioner context.

- **Correctable or refutable**. A practitioner annotation is a claim that can be wrong. Over time, calibration review should flag practitioner context that has been empirically overturned.

## Retrieval protocol

When Chair invokes Council for a programme:

1. **Context match**: from the programme context (set via `/context`) and the current question, identify the relevant programme, sector, jurisdiction, and institution tags.

2. **Retrieve matching annotations**: read any `by-programme/{programme-slug}/*.md`, `by-sector/{sector-slug}/*.md`, `by-jurisdiction/{jurisdiction-slug}/*.md`, `by-institution/{institution-slug}/*.md` files that match.

3. **Integrate into classification and parameters**: the retrieved annotations inform Chair's parameter inference (e.g., "the jurisdiction's historical optimism-bias pattern suggests tail_risk_sensitivity = high even if the question doesn't explicitly raise it").

4. **Surface in synthesis**: the Council brief's §2 Programme Context section explicitly lists retrieved practitioner annotations alongside inferred parameters. The synthesis's agent findings reason *with and against* the practitioner context. Where doctrine and practitioner context conflict, the tension is preserved in §12 Unresolved Tensions.

5. **Flag if no annotations retrieved**: if no practitioner context matches, Chair explicitly notes that the deliberation is running in cold-start mode. This is a legitimate operating state but the user should know it.

## How annotations are added

Annotations are added by the user (or designer) as markdown files in the appropriate subdirectory, following the template in `annotation-template.md`. Each annotation is dated, attributed to the contributor, and tagged for retrieval.

Annotations are not automatically ingested from Council outputs. They are deliberate acts of knowledge capture. The `/context` command can prompt the user to record annotations when surfacing conflicts between doctrine and user judgment.

## Relationship to doctrine and memory

- **Doctrine** (in `agents/*.md` agent definitions): canonical MMPM literature — Flyvbjerg, Morris, Scott, etc. Applies across programmes and jurisdictions.
- **Practitioner context** (here): specific to a programme / sector / jurisdiction / institution. Complements doctrine.
- **Decision log** (in `memory/decisions/`): what Council decided for this programme. Written after deliberation.
- **Prediction log** (in `memory/predictions/`): what Council predicted; outcomes; calibration. Enables learning.

Practitioner context and decision log are read inputs to Council. Prediction log is a write output. Together they create the feedback loop.

## Provenance

This elevated role was designed 2026-04-21 following the MMPM-COS evaluation. The evaluation found that practitioner-context utilisation was the most under-realised part of the original design.
