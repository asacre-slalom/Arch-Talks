# Material — Module 01: Architect's Mindset

---

## Section 1: What Does It Mean to Think Like an Architect?

Most engineers think in terms of tasks: ingest this data, transform it, load it, test it, deploy it. That thinking is correct and necessary — pipelines don't build themselves.

An architect thinks in terms of **systems**: how do the parts relate? What does the system optimize for? What does it make easy, and what does it make hard? What would break if the business grew 10x?

The shift is not about seniority. It's not about knowing more tools. It's about changing the question you ask first.

| Engineer's first question | Architect's first question |
|---|---|
| "How do I build this?" | "Why should this exist in the first place?" |
| "Which tool fits here?" | "What constraints shape the design space?" |
| "What does this pipeline do?" | "What problem does this system solve, and for whom?" |
| "How do I make this faster?" | "Is speed the right thing to optimize for here?" |

This doesn't mean architects never write code or never think tactically. It means they hold a wider frame before zooming in.

---

## Section 2: Systems Thinking Applied to Data

A data system is not a collection of pipelines. It is a set of **components with relationships**, organized to move, transform, and serve data for a purpose.

When you look at a system with an architect's lens, you see:

### Components
The building blocks: ingestion layer, transformation layer, storage layer, serving layer, orchestration, catalog, monitoring. Not specific tools — roles.

### Flows
How data moves between components. Direction matters. Volume matters. Frequency matters. Failures matter.

### Boundaries
Where one team's responsibility ends and another's begins. Where one system hands off to another. Boundaries are where most problems live.

### Dependencies
What breaks if this component goes down? What does this component need to function? Hidden dependencies are technical debt waiting to be discovered.

### Example: A Reporting Data Platform

Instead of describing it as "we have Airflow, dbt, Snowflake, and Tableau", an architect describes it as:

```
[Source Systems]
  ERP (Oracle)         ─────┐
  CRM (Salesforce)     ─────┤──► [Ingestion Layer]  ──► [Raw Zone]
  Events (Kafka)       ─────┘         (Fivetran)        (S3 / GCS)
                                                              │
                                                              ▼
                                                    [Transformation]
                                                        (dbt Cloud)
                                                              │
                                                    ┌─────────┴──────────┐
                                                    ▼                    ▼
                                              [Serving Layer]    [ML Feature Store]
                                               (Snowflake)         (Feast / Redis)
                                                    │
                                                    ▼
                                            [BI / Analytics]
                                              (Tableau / Looker)
```

This map makes visible what a list of tools doesn't: the ERP feeds the ingestion layer, but the Events stream bypasses it — why? That's a design decision worth asking about.

---

## Section 3: The Difference Between Architecture and Implementation

This distinction is the most important concept in this module. Confusing the two is the most common reason data engineers struggle to grow into architects.

**An architectural decision** is a choice that:
- Defines the structure, shape, or behavior of the system at a high level
- Has lasting consequences that are expensive to reverse
- Affects more than one component or team
- Reflects a trade-off between competing values (cost vs. freshness, flexibility vs. simplicity, etc.)

**An implementation decision** is a choice that:
- Specifies how a component is built or configured
- Can be changed without restructuring the surrounding system
- Affects primarily the people building that component
- Optimizes within a given design, not across designs

### Examples

| Decision | Type | Why |
|---|---|---|
| "We will use a medallion architecture (Bronze/Silver/Gold)" | Architectural | Defines how all data flows are structured across the platform |
| "We will use Delta Lake as the file format for our lakehouse" | Architectural | Affects storage, compute, tooling, and team skills for years |
| "The Bronze layer will partition data by ingestion date" | Implementation | Affects one layer's performance; reversible without redesigning the system |
| "We will use dbt macros to standardize column naming" | Implementation | A convention within the transformation layer |
| "All PII data will be stored only in the Gold layer, masked in earlier layers" | Architectural | Defines a constraint that shapes how every downstream pipeline is built |
| "We use `created_at` as the partition key for the customers table" | Implementation | A performance choice within one table |

### The litmus test

Ask: *if this decision changed, how many teams would be affected and how much would need to be rebuilt?*

- Many teams, major rebuild → architectural
- One team, localized change → implementation

---

## Section 4: Reading Implicit Trade-offs in Existing Systems

Every system you've ever worked on was built by someone making real decisions under real constraints. Budget was limited. The team was small. There was a deadline. A vendor was already purchased. A previous system couldn't be replaced.

Those constraints are usually invisible by the time you arrive. What you see is the shape of their decisions — but not the reasoning.

An architect learns to read the shape and infer the reasoning.

### How to identify implicit trade-offs

For each design choice you observe, ask:

1. **What does this make easy?** (the benefit someone chose)
2. **What does this make hard?** (the cost someone accepted)
3. **Who bears that cost today?**
4. **What constraint would have to change for this to be designed differently?**

### Real example: A streaming pipeline built as micro-batch

You find a "streaming" pipeline that actually runs every 5 minutes via Airflow, instead of using Kafka or a real streaming framework.

| Question | Inference |
|---|---|
| What does this make easy? | Simpler to build, debug, and operate. The team didn't need streaming expertise. |
| What does this make hard? | Freshness is bounded to 5 minutes. Scaling to seconds is a full redesign. |
| Who bears the cost? | Downstream dashboards that show "near real-time" but are actually 5–10 minutes stale. |
| What would have to change? | The team would need streaming expertise, or the business case for <1 min freshness would need to be made. |

**The implicit trade-off**: simplicity of operations vs. data freshness. Neither choice is wrong — but the cost was never explicitly accepted by the stakeholders who now complain about stale dashboards.

### Real example: A single monolithic warehouse with no separation of concerns

All data — raw, intermediate, and final — lives in one Snowflake database with no access control between layers.

| Question | Inference |
|---|---|
| What does this make easy? | Fast to start. No permissions to manage. Analysts can query anything. |
| What does this make hard? | Governance, compliance, data contracts, and onboarding new teams safely. |
| Who bears the cost? | The data platform team, which now fields dozens of "why did this column change?" questions because raw tables are queried directly. |
| What would have to change? | Either a governance-first culture change, or a platform migration to enforce layer separation. |

**The implicit trade-off**: agility to start vs. governance at scale. Valid in year 1. Painful in year 3.

---

## Section 5: How Architecture Decisions Compound Over Time

Single decisions don't break systems. Accumulation does.

Each architectural decision constrains the space of future decisions. A system built for batch processing at 10 customers/day will resist becoming a real-time system for 10M users — not because it's impossible, but because every subsequent decision was made within the original frame.

This is why reading history matters. The systems you inherit are layers of decisions made at different moments in time, each one narrowing what's possible.

As an architect, you need to understand not just what the system is, but **what it was optimized for** — and whether that's still true.

---

## Key Concepts Summary

| Concept | One-line definition |
|---|---|
| Systems thinking | Seeing components, flows, and boundaries — not tasks |
| Architectural decision | A choice that shapes the system and is expensive to reverse |
| Implementation decision | A choice within a component, reversible without systemic impact |
| Implicit trade-off | A cost/benefit decision that was made but never documented |
| Decision compounding | How early architectural choices constrain all future ones |

---

## Recommended Reading (Optional)

- *Fundamentals of Software Architecture* — Mark Richards & Neal Ford (Chapters 1–3)
- *Designing Data-Intensive Applications* — Martin Kleppmann (Chapter 1: Reliable, Scalable, and Maintainable Applications)
- *Architecture Decision Records* — Michael Nygard (original ADR proposal, freely available online)
