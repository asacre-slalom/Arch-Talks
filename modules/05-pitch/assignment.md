# Assignment — Module 05: Full Architecture Pitch

## The Scenario: UrbanBasket

UrbanBasket is a direct-to-consumer apparel brand founded 6 years ago. It started as a Shopify store, grew to $85M in annual revenue, and 18 months ago acquired a regional competitor ("ThreadCo") for $22M to expand its geographic footprint.

The acquisition was a commercial success. Operationally, it has been a slow-motion disaster for the data team.

Read the following briefing carefully. As in Module 02, some constraints are stated explicitly and others are embedded in the narrative. This scenario has a higher density of hidden constraints than NovaMart. Read it twice.

---

### Business Context

The new VP of Data joined 3 months ago. Her first week on the job included:

- A Finance team that couldn't reconcile Q4 revenue because UrbanBasket and ThreadCo count "a sale" differently (UrbanBasket counts at checkout; ThreadCo counts at shipment)
- A Marketing team running a Black Friday campaign against a customer list that had 34% overlap between the two brands with no deduplication
- A Data Science team that abandoned a Customer Lifetime Value model because the training data was inconsistent across pre- and post-acquisition records
- An Operations team that discovered a $280K inventory discrepancy between the two warehousing systems — traced 6 weeks later to a timezone handling difference in how orders are timestamped

The VP of Data's mandate from the CEO: "Fix the data. I don't care how. I need one version of the truth before the next funding round."

The next funding round is in **9 months**.

---

### The Current State

**UrbanBasket's data landscape:**
- **Shopify** (cloud): orders, customers, inventory. Primary source of truth for the UrbanBasket brand. Reliable, well-documented API.
- **Klaviyo** (cloud): email marketing data, customer segments. Connected to Shopify natively. No dedicated BI connector.
- **Google Analytics 4** (cloud): web behavior data. Available via BigQuery Data Transfer (already configured).
- **Current "warehouse"**: a PostgreSQL instance on a single EC2 node, set up by a contractor 3 years ago. 4TB of data. No documentation. 2 data pipelines load into it: one from Shopify (dbt-based, reasonably maintained), one from a now-defunct third-party tool (nobody knows who maintains it). Analysts connect Metabase directly to production PostgreSQL.

**ThreadCo's data landscape (acquired):**
- **Custom order management system** (on-premise, Oracle 19c): ThreadCo's source of truth for orders, inventory, and customers. Managed by a 2-person IT team in the acquired company that reports to Operations, not Data.
- **Microsoft Dynamics** (cloud CRM): customer records, interaction history. The ThreadCo sales team uses it daily. PII-heavy.
- **Legacy data warehouse** (Azure SQL): 7 years of ThreadCo sales history. Maintained by the same IT team. No active pipelines — reports are run as stored procedures by the Operations team.
- **Known issues**: the Oracle OMS uses local timezone (US/Eastern) for order timestamps. All UrbanBasket data uses UTC. This is the root cause of the $280K inventory discrepancy and has not been fixed.

---

### The Team and Resources

- **Data team**: 3 data engineers (2 mid-level, 1 senior), 1 analytics engineer (dbt-skilled), 1 data scientist (on the CLV model, currently blocked)
- **Cloud environment**: AWS is the primary cloud. The Google Analytics BigQuery integration is already in GCP and the VP of Data does not want to move it. ThreadCo runs on Azure.
- **Budget**: $75,000/year for new cloud infrastructure. The existing PostgreSQL EC2 instance costs $1,200/month and is included in this budget.
- **Compliance**: UrbanBasket has customers in the EU (18% of revenue). GDPR applies. Legal has confirmed that customer PII from EU orders must be: (a) stored in EU-region infrastructure, (b) deletable within 72 hours of a verified deletion request, (c) not processed by any AI/ML system without explicit consent flags.
- **Constraints in the ThreadCo IT relationship**: the ThreadCo IT team will cooperate but has a 4–6 week lead time for any changes to the Oracle OMS. They will not give the data team direct database access — all integration must go through approved exports or a read-only replica.
- **The VP of Data's one explicit constraint**: "I do not want to build something that requires us to hire a streaming engineer. We don't have the operational maturity for it."

---

### The Political Dynamics

Read these carefully. They are constraints as real as any technical one.

- **The CTO** is skeptical of "enterprise data platform" projects. He approved a $400K data lake initiative 4 years ago that was abandoned after 14 months. He will ask hard questions about scope, timeline, and what specifically changes for the business.
- **The ThreadCo IT team** feels territorial about their Oracle system and does not want the data team treating it as "just another source." Their manager has raised concerns about performance impact on the OMS.
- **The Finance team** is the most motivated stakeholder — they are tired of manual reconciliation and will be the first to use the new platform. But they have been burned by data projects that delivered "a platform" instead of their specific reports.
- **The Marketing team** wants a Customer 360 view and real-time campaign data. They have been told "Phase 2" for 2 years and are skeptical that it will ever come.

---

## What You Must Deliver

### Deliverable 1 — Full Architecture Proposal

A complete, self-contained document with all six required sections from `material.md`:

1. **Business Context & Problem Statement** — What breaks without this project? What is the cost to the business today? What specific outcome does the proposal deliver? What decision are you requesting?

2. **Current State Assessment** — Architecture map of the current landscape (both UrbanBasket and ThreadCo stacks). The 3 most costly implicit trade-offs in the current state. What the current state makes impossible that the proposed design must fix.

3. **Proposed Architecture** — Architecture diagram (Level 2). Constraint canvas summary. What Phase 1 builds. What is deferred to Phase 2 and why. A brief narrative for each major component.

4. **Key Decisions** — Minimum 2 full ADRs for the most consequential decisions in your design (follow the complete structure from Module 03). Each must have real negative consequences documented.

5. **Phased Roadmap** — Phase 1 fully specified (scope, team allocation, milestones, definition of done). Phase 2 as triggered intent (capability, trigger condition, architectural hook in Phase 1).

6. **Risk Register** — Minimum 4 risks: 1 technical, 1 organizational (the ThreadCo IT dependency is an obvious candidate), 1 compliance (GDPR), 1 accepted risk with explicit justification.

---

### Deliverable 2 — Executive Summary (1 page)

A standalone one-page summary calibrated for the CTO and VP of Data. Must include:
- The problem in 2 sentences
- The proposed solution in 2 sentences (no technical terms)
- What it costs (budget + team time)
- What it delivers, by when
- The single biggest risk and how it's managed
- The decision needed

This is your M04 skill applied to M05 work.

---

## File Structure for Submission

```
modules/05-pitch/submissions/[your-name]/
├── architecture-proposal.md           ← Deliverable 1 (full proposal)
├── executive-summary.md               ← Deliverable 2 (1-page)
└── decisions/
    ├── ADR-001-[short-name].md        ← First ADR (from Section 4)
    └── ADR-002-[short-name].md        ← Second ADR (from Section 4)
```

**Deadline**: Submit before your ceremony (recommended: by Day 12 of the 2-week cycle — this proposal takes longer than prior modules)

---

## Ceremony Format

| Time | Activity |
|---|---|
| 0:00 – 12:00 | Architecture pitch presentation — all 6 sections |
| 12:00 – 17:00 | Adversarial Q&A — facilitator plays skeptical VP of Engineering |
| 17:00 – 20:00 | Open Q&A from peers |

The adversarial Q&A segment is different from all prior modules. The facilitator will challenge specific decisions with the intent of finding weaknesses. You will not know which decisions will be challenged. You have 5 minutes to defend your proposal under sustained pressure.

---

## High-Level Success Criteria

Your proposal is complete when:

- A person with no knowledge of UrbanBasket can read the proposal and understand the problem, the solution, the cost, and the risk — without asking you a question
- Both ADRs have real negative consequences documented — not softened, not "none identified"
- Phase 1 is deliverable by the team described: 3 data engineers, 1 analytics engineer, $75K/year, in the timeframe you proposed
- The GDPR constraint is addressed structurally in the architecture — not mentioned as a note and not deferred to Phase 2
- The ThreadCo IT dependency is in the risk register with a specific response
- The executive summary uses no technical terms and ends with a specific ask
- You can defend every decision in the adversarial Q&A with a constraint-grounded argument, not a preference
