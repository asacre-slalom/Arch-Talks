# Assignment — Module 02: Design Under Constraints

## The Scenario: NovaMart Analytics Expansion

NovaMart is a mid-size retail chain with 140 physical stores and an e-commerce site that generates 35% of total revenue. The company has been growing steadily for 3 years and recently promoted its first Head of Data, who has a mandate to "build a real analytics capability" before the holiday season.

Read the following briefing carefully. Some constraints are stated explicitly. Others are embedded in the text and must be inferred.

---

### Business Context

The Head of Data has outlined three priorities:

1. **Inventory analytics**: store managers need daily visibility into stock levels, reorder alerts, and supplier performance. Currently this information lives in the ERP and requires IT to run manual reports on request.

2. **Customer 360**: the marketing team wants a unified view of customer behavior across in-store (point-of-sale) and online (website + app) to personalize campaigns. They currently have no cross-channel view.

3. **Executive dashboards**: the CFO has requested weekly margin analysis by product category and region. Finance currently exports Excel files from 4 different systems and consolidates manually — a process that takes 2 days each week.

The Head of Data has been told: "If you can get the executive dashboards working by the end of Q3, the rest of the budget is yours."

---

### The Current State

NovaMart's data landscape today:

- **ERP** (SAP, on-premise): source of truth for inventory, orders, suppliers, and financials. Has a read-only reporting database that can be queried via JDBC. IT must approve and schedule any new query workloads.
- **POS System** (NCR, on-premise): transaction data from physical stores. Nightly flat-file exports to an SFTP server. No API. File format is fixed-width text with a schema that "changes sometimes."
- **E-commerce Platform** (Shopify, cloud): order, customer, and behavior data available via Shopify's REST API. Webhook support available for real-time events.
- **CRM** (Salesforce, cloud): customer profiles and marketing interaction history. Fivetran connector available. Data includes PII (email, phone, address).
- **Current "data warehouse"**: a shared SQL Server instance used by the BI team, containing 4 years of ERP exports loaded manually. No documentation, no ownership, used by ~20 analysts directly. Schema changes happen without notice.

---

### The Team and Resources

- **Data team**: 2 data engineers (both mid-level), 1 analytics engineer (dbt-skilled), 1 BI analyst
- **Cloud contract**: AWS, signed 2 years ago. $65,000/year committed spend, currently using $28,000. Moving to Azure or GCP is not possible under the current contract.
- **Timeline**: The CFO's executive dashboard deadline is **10 weeks from today**. The full platform roadmap has no hard deadline beyond that.
- **IT relationship**: IT controls the ERP and POS environments. They are cooperative but slow — any new integration request takes 3–4 weeks to approve and schedule.
- **Compliance**: NovaMart is not subject to GDPR (US-only operations), but the legal team has flagged that customer PII (from CRM and e-commerce) must not be stored in any system accessible to contractors or third-party vendors.
- **Existing tooling**: The team uses dbt Cloud (already licensed), GitHub, and has experimented with Airflow but it is not in production.

---

## What You Must Deliver

### Deliverable 1 — Constraint Canvas

Complete the Constraint Canvas from `material.md` Section 2 for the NovaMart scenario.

**Requirements:**
- Every cell must be filled based on the scenario — no blanks
- The "KEY TENSION" must name a single, specific trade-off that shapes the entire design
- The "MUST-HAVES" list must include at least one constraint that is not explicitly stated in the briefing (you must infer it)
- The "NICE-TO-HAVES" list must include at least one constraint that could be relaxed with justification

---

### Deliverable 2 — Two Architectural Options

Design two genuinely viable architectural options for NovaMart's data platform. Both must satisfy the MUST-HAVE constraints. They should differ in at least two meaningful dimensions.

For each option, provide:

**a) Architecture diagram** — component-level (not tool-level — show roles, not just names). Can be ASCII, Mermaid, or an image.

**b) Constraint fit table** — using the dimensions from `material.md` Section 3:

| Dimension | Option A | Option B |
|---|---|---|
| Fits within budget | | |
| Deliverable by 10-week deadline | | |
| Requires skills the team has | | |
| Handles compliance (PII) | | |
| Operational complexity | | |
| Reversibility | | |
| Scales to 3x current volume | | |
| Technical debt created | | |

**c) One paragraph** describing what each option optimizes for and what it accepts as a cost.

---

### Deliverable 3 — Recommendation with Justification

State your recommendation clearly (Option A or Option B) and justify it in 3–5 paragraphs.

**Your justification must:**
- Reference at least 3 specific constraints from your Constraint Canvas
- Name the constraint or limitation that ruled out the alternative option
- Name at least one thing your recommended design intentionally defers, with a documented trigger for revisiting

**Your justification must not:**
- Recommend a design because it's "more modern" or "industry best practice" without connecting to a constraint
- Dismiss the alternative option without explaining why it fails given a specific constraint

---

### Deliverable 4 — One Risk You Are Accepting

In 2–3 sentences: what is the single biggest risk in your recommended design? Not a risk you're mitigating — a risk you're consciously accepting because the alternative is worse given the constraints. Name it honestly.

---

## File Structure for Submission

```
modules/02-design/submissions/[your-name]/
├── constraint-canvas.md         ← Deliverable 1
├── option-a/
│   ├── diagram.[md|png|pdf]     ← Deliverable 2a for Option A
│   └── analysis.md              ← Deliverable 2b + 2c for Option A
├── option-b/
│   ├── diagram.[md|png|pdf]     ← Deliverable 2a for Option B
│   └── analysis.md              ← Deliverable 2b + 2c for Option B
├── recommendation.md            ← Deliverable 3
└── accepted-risk.md             ← Deliverable 4
```

**Deadline**: Submit before your ceremony (recommended: by Day 12 of the 2-week cycle)

---

## Presentation Guide (for the ceremony)

You have **≤ 12 minutes**:

| Time | What to cover |
|---|---|
| 0:00 – 1:30 | State the key tension from your Constraint Canvas — one sentence that frames the entire design challenge |
| 1:30 – 4:00 | Walk through Option A: architecture + constraint fit |
| 4:00 – 6:30 | Walk through Option B: architecture + constraint fit |
| 6:30 – 9:30 | Your recommendation — name the constraints, name what was ruled out, name what was deferred |
| 9:30 – 12:00 | The risk you are accepting — and why you accepted it |

Do not spend time on implementation details (how the pipelines will be coded, what the dbt models will look like). Focus on why the design is shaped as it is, given the constraints.

---

## High-Level Success Criteria

Your submission is strong when:

- The constraint canvas contains at least one constraint you inferred, not just copied from the briefing
- Both options are genuinely viable — Option B is not a straw man
- The recommendation names constraints, not preferences
- The deferred component has a specific trigger, not "we'll do it later"
- The accepted risk is honest — it's not a risk you secretly mitigated
