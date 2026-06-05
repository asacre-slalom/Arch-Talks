# Material — Module 02: Design Under Constraints

---

## Section 1: Constraints First — Always

The most dangerous moment in an architecture process is when someone says "let me show you what I've been thinking" before the constraints are on the table.

It's not dangerous because the idea is bad. It's dangerous because once a proposal is in the room, the conversation shifts from "what is the right design for this problem?" to "should we accept or reject this specific design?" That's a worse conversation. It anchors the group, it creates defensiveness, and it often leads to a design that was optimized for being accepted rather than for being right.

The discipline of an architect is to **document constraints before proposing anything**. This is not bureaucracy — it's how you protect the quality of the design.

### The six constraint categories

| Category | What to capture | Why it matters |
|---|---|---|
| **Capacity** | Number of engineers available, skill set, current bandwidth | Determines what can be built and maintained |
| **Economic** | Cloud budget (annual/monthly), migration budget, licensing costs | Eliminates options that look good on paper but can't be funded |
| **Time** | Hard deadlines, dependencies on product launches, contract expirations | Determines whether you can phase delivery or must deliver whole |
| **Technical debt** | What systems are broken, fragile, or unsupported today | Constrains what you can touch and what you must route around |
| **Compliance and governance** | Data residency requirements, PII rules, audit obligations, security policies | Non-negotiable constraints — violating them is not a trade-off, it's a failure |
| **Organizational** | Existing vendor contracts, team ownership boundaries, political dependencies | Often the most invisible and most impactful constraints |

### The discipline: separate gathering from designing

When you start a constraint conversation, follow this rule strictly:

> **First hour**: ask questions, listen, write down constraints. Do not propose anything.  
> **Second hour**: design against what you learned.

If you catch yourself saying "but we could just..." during the constraint gathering phase, stop. Write the idea down, finish gathering constraints, and come back to it. The idea will be better for having waited.

---

## Section 2: The Constraint Canvas

The Constraint Canvas is a lightweight one-page framework to make all constraints visible before any design work begins. It is not a document for stakeholders — it is a thinking tool for the architect.

### Structure

```
┌─────────────────────────────────────────────────────────────────────┐
│                        CONSTRAINT CANVAS                            │
│                  [Problem / System being designed]                  │
├──────────────────────┬──────────────────────────────────────────────┤
│  CAPACITY            │  ECONOMIC                                    │
│                      │                                              │
│  Team: ___           │  Cloud budget: ___/year                      │
│  Skills available:   │  Migration budget: ___                       │
│  ___                 │  Licensing locked: ___                       │
│  Bandwidth: ___      │                                              │
├──────────────────────┼──────────────────────────────────────────────┤
│  TIME                │  TECHNICAL DEBT                              │
│                      │                                              │
│  Hard deadline: ___  │  Fragile systems: ___                        │
│  Phases allowed?     │  Cannot-touch zones: ___                     │
│  Dependencies: ___   │  Integration limits: ___                     │
├──────────────────────┼──────────────────────────────────────────────┤
│  COMPLIANCE          │  ORGANIZATIONAL                              │
│                      │                                              │
│  Data residency: ___ │  Vendor contracts: ___                       │
│  PII rules: ___      │  Team ownership lines: ___                   │
│  Audit needs: ___    │  Political blockers: ___                     │
└──────────────────────┴──────────────────────────────────────────────┘

  KEY TENSION:  [The single most constraining trade-off for this problem]
  MUST-HAVES:   [Constraints that are non-negotiable — violating = failure]
  NICE-TO-HAVES: [Constraints that are real but could be relaxed with justification]
```

### How to use it

Fill the canvas before designing. Then answer two questions:

1. **What does the canvas make impossible?** (Options you can rule out immediately)
2. **What does the canvas make necessary?** (Design choices that are forced, not chosen)

What's left after answering those two questions is your actual design space.

---

## Section 3: Comparing Architectural Options with Explicit Criteria

Once you have your constraints documented and your design space understood, you will typically have 2–4 viable options. The architect's job is to compare them honestly — not to advocate for the one they prefer.

### The comparison anti-pattern

Most engineers, when asked to compare options, build a straw man: Option A is their preferred design, fully thought through. Option B is a weak alternative included to make A look better. This is not comparison — it's advocacy with extra steps.

**A real comparison requires that all options be genuinely viable given the constraints.** If Option B wouldn't work at all, it shouldn't be in the comparison — it wastes everyone's time. If it would work, it deserves honest analysis.

### A structured comparison table

For each option, evaluate across the same dimensions:

| Dimension | Option A | Option B |
|---|---|---|
| **Fits within budget** | Yes / No / Partial | Yes / No / Partial |
| **Deliverable by deadline** | Yes / No / Phased | Yes / No / Phased |
| **Requires skills we have** | Yes / No / Gap: __ | Yes / No / Gap: __ |
| **Handles compliance requirements** | Yes / No | Yes / No |
| **Operational complexity** | Low / Medium / High | Low / Medium / High |
| **Reversibility** | Easy / Hard / Irreversible | Easy / Hard / Irreversible |
| **Scales to 3x current volume** | Yes / No / With changes | Yes / No / With changes |
| **Technical debt created** | Low / Medium / High | Low / Medium / High |

Use the same dimensions for every option. Do not add dimensions that only favor one option.

### What "recommendation quality" looks like

A weak recommendation sounds like:
> "I recommend Option A because it uses a modern lakehouse pattern and is more scalable."

A strong recommendation sounds like:
> "I recommend Option A because given the 3-engineer team and the 8-week deadline, the simpler ingestion layer requires no new tooling expertise and can be delivered in two phases. Option B's streaming component would require 2+ months of ramp-up time we don't have. The cost of Option A's lower freshness ceiling (15 minutes) is acceptable given that the current SLA is daily batch — we are already improving by 96x."

The difference: the strong recommendation names the constraints, names the option it rules out, and names the accepted cost.

---

## Section 4: Designing for Evolution, Not Perfection

There is a version of "good architecture" that is a trap: the design that tries to solve every foreseeable future problem today. It's typically over-engineered, over-budget, and over-schedule — and it arrives too late to matter.

The alternative is not underengineering. It is **intentional deferral**.

### The three-question rule for every component

For every component in your proposed design, ask:

1. **Does it need to exist now?** Is there a real, current requirement that justifies building this today?
2. **If deferred, what breaks?** What is the actual cost of not building this yet?
3. **What would need to change for us to build it?** What trigger — business, technical, or organizational — should prompt revisiting this decision?

If a component can't answer question 1 with "yes, here's the current requirement," defer it and document why.

### A deferral is not a failure — it's a decision

When you defer something, record it explicitly:

> "We are not building a real-time streaming layer in Phase 1. The current SLA is daily reporting. This decision should be revisited when: (a) business requires sub-hourly data freshness, or (b) event-driven use cases emerge (e.g., fraud detection, personalization). At that point, the ingestion layer is the primary component to replace."

This makes your Phase 2 predictable rather than reactive. The system evolves with intention instead of accumulating surprises.

---

## Section 5: Real Examples — Same Problem, Different Constraints, Different Valid Designs

### The problem: Build a unified analytics data platform

A company has data scattered across 3 operational systems (ERP, CRM, custom app), no central warehouse, and analysts running queries directly against production databases. They want a unified analytics platform.

---

### Case A: Early-stage startup

**Constraints:**
- 1 data engineer (full-stack, generalist)
- $18K/year total cloud budget
- 12-week timeline to first dashboard
- No compliance requirements yet
- No legacy infrastructure to integrate with
- 3 data sources, all accessible via API

**Design chosen:**
```
[Source APIs]
  ERP API ──────┐
  CRM API ───────►  [ELT Tool]  ──►  [Cloud DWH]  ──►  [BI Tool]
  Custom App ───┘  (Fivetran/      (BigQuery/         (Looker/
                    Airbyte)        Snowflake)          Metabase)

No transformation layer in Phase 1 — analysts query the raw tables
directly and iterate. dbt is introduced in Month 4 once query patterns
are understood.
```

**Why this design:** One engineer cannot build and maintain a multi-layer pipeline. The simpler ELT-direct approach gets value to analysts in 6 weeks and can be refactored once patterns are known. The cost of raw-table querying (no data contracts, potential schema breaks) is acceptable because there are only 5 analysts who can coordinate informally.

**What was deferred:** transformation layer, data contracts, catalog, monitoring. Trigger for revisiting: team grows past 3 data engineers or analyst count exceeds 15.

---

### Case B: Mid-size enterprise

**Constraints:**
- 6 data engineers (3 senior, 3 mid)
- $180K/year cloud budget
- 18-month timeline for full platform
- SOC 2 compliance required (PII masking, audit logs)
- 2 legacy on-prem systems that can't be migrated yet
- 12 data sources, 4 of which require custom connectors
- 3 existing teams consuming data (BI, DS, Product Analytics)

**Design chosen:**
```
[Source Systems]
  Legacy On-prem ──► [CDC / SFTP]  ──► [Bronze Zone]
  Cloud SaaS ────► [Managed ELT]  ──►  (raw, masked PII)
  Custom APIs ────► [Custom ingest] ──►        │
                                               ▼
                                        [Silver Zone]
                                         (dbt, validated,
                                          deduplicated)
                                               │
                                    ┌──────────┴──────────┐
                                    ▼                     ▼
                              [Gold Zone]          [ML Features]
                          (domain models,           (Feast,
                           serving layer)            Redis)
                                    │
                           ┌────────┴────────┐
                           ▼                 ▼
                       [BI / Reporting]   [Self-serve]
                        (Tableau)         (Databricks
                                           SQL)
```

**Why this design:** The compliance requirement forces explicit PII masking at ingestion (Bronze zone). The three consumer teams with different needs require a clean serving layer (Gold) rather than shared intermediate tables. The team is large enough to maintain a three-layer architecture.

**What was deferred:** real-time streaming (current SLA is hourly), data catalog (Phase 2, 6 months out), data contracts (Phase 2, after patterns stabilize). Trigger for revisiting: streaming when product team needs event-driven data, catalog when external teams begin consuming.

---

### The key insight from both cases

Neither design is "better." Both are correct given the constraints of their context. A startup that tried to implement Case B would fail — the complexity would outlast the team. An enterprise that tried to implement Case A would fail — compliance alone rules it out.

**The constraint canvas is what separates them.** Same problem. Different space. Different valid solution.

---

## Key Concepts Summary

| Concept | One-line definition |
|---|---|
| Constraint Canvas | A one-page framework to surface all constraints before designing |
| Option comparison | Evaluating multiple viable alternatives against the same criteria |
| Intentional deferral | Explicitly deciding not to build something now, with a documented trigger for when to revisit |
| Design space | The set of solutions that are still possible after constraints are applied |
| Recommendation quality | A recommendation that names constraints, eliminates options, and accepts a cost explicitly |

---

## Recommended Reading (Optional)

- *Designing Data-Intensive Applications* — Martin Kleppmann, Chapter 1 (trade-offs under real constraints)
- *Team Topologies* — Manuel Pais & Matthew Skelton (organizational constraints on architecture)
- *The Art of Doing Twice the Work in Half the Time* — Jeff Sutherland (phased delivery and deferral thinking)
