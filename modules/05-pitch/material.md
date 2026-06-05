# Material — Module 05: Full Architecture Pitch

---

## Section 1: Structure of a Complete Architecture Proposal

A complete data architecture proposal is not a design document and it is not a presentation deck. It is a structured argument that moves from problem to solution to consequences to plan. Every section exists to serve the audience's ability to make a decision — or to execute on one.

### The six required sections

```
┌─────────────────────────────────────────────────────────────────┐
│  SECTION 1: Business Context & Problem Statement                │
│  Answers: Why are we here? What breaks without this?            │
├─────────────────────────────────────────────────────────────────┤
│  SECTION 2: Current State Assessment                            │
│  Answers: What exists today? What does it cost us?              │
├─────────────────────────────────────────────────────────────────┤
│  SECTION 3: Proposed Architecture                               │
│  Answers: What will be built? How does it work?                 │
├─────────────────────────────────────────────────────────────────┤
│  SECTION 4: Key Decisions (ADRs)                                │
│  Answers: Why this design and not another? What did we reject?  │
├─────────────────────────────────────────────────────────────────┤
│  SECTION 5: Phased Roadmap                                      │
│  Answers: When will value be delivered? What comes in phases?   │
├─────────────────────────────────────────────────────────────────┤
│  SECTION 6: Risk Register                                       │
│  Answers: What could go wrong? What are we accepting?           │
└─────────────────────────────────────────────────────────────────┘
```

**Every section is mandatory.** A proposal missing any section is incomplete. A proposal with a weak Section 6 (risks) is not honest. A proposal with a vague Section 5 (roadmap) is not actionable.

---

### Section 1: Business Context & Problem Statement

This section does two things: it establishes shared understanding of the problem, and it creates the criterion by which the proposal will be judged successful.

**What to include:**
- The business problem in language the stakeholders use, not language engineers use
- The specific costs of the current state: manual effort, data quality failures, missed decisions, compliance exposure
- The outcome the proposal will deliver: not "a better data platform" but "Finance eliminates 2 days/week of manual consolidation and gets auditable margin reports in real time"
- The decision being requested: what approval, funding, or commitment is needed

**The test**: could a new VP read this section and understand why the project exists, without reading anything else?

---

### Section 2: Current State Assessment

This is your M01 skill in action. Before proposing anything, you must honestly characterize what exists — including its trade-offs, its costs, and its hidden dependencies.

**What to include:**
- Architecture map of the current state (Level 2 diagram)
- The key implicit trade-offs that the current state encodes (from M01 — name the decisions that shaped the current system)
- What the current state makes hard (these become the requirements for the new design)
- What must be preserved (not everything in the current state is broken; some of it is intentional and correct)

**The test**: does the current state map reveal the *specific* problems your design solves? If you could read the current state section without knowing the proposal, could you predict what the main architectural challenges will be?

---

### Section 3: Proposed Architecture

This is your M02 and M04 skills combined. The proposed architecture must be designed under the real constraints of the scenario — not the ideal architecture for an unlimited team with unlimited budget.

**What to include:**
- Architecture diagram at the appropriate level (Level 2 for a design review, Level 1 for an executive summary)
- The constraint canvas that shaped the design (or a summary of it)
- What Phase 1 delivers vs. what is deferred to Phase 2
- A brief narrative for each major component: its role, its relationships, and why it belongs in the design

**The test**: if you handed this section to a senior engineer, could they begin implementation work on Phase 1 without asking you a question? If not, you have left something out.

---

### Section 4: Key Decisions (ADRs)

This is your M03 skill. Every significant architectural decision deserves an ADR — or at minimum, a decision record that captures the context, the options, and the consequences.

**What to include:**
- Minimum 2 full ADRs for the most consequential decisions in your proposal
- Each ADR must follow the full structure from M03: context, decision drivers, options considered, decision, consequences (positive AND negative)
- At least one ADR should document a decision where the alternative had real merit — otherwise you are not documenting a decision, you are documenting an obvious choice

**The test**: could someone who disagrees with your recommendation read the ADRs and understand exactly where to find the disagreement? If the ADRs are so airtight that there is no point of entry for challenge, they are probably post-hoc advocacy.

---

### Section 5: Phased Roadmap

A roadmap is not a project plan. It is a statement of what value will be delivered when, at what level of detail.

**Phase 1 must be fully specified:**
- Scope: exactly what is included and excluded
- Team and effort: who builds this and how long it takes, given the constraints
- Milestones: 2–3 intermediate checkpoints, not just start and end
- Definition of done: what must be true for Phase 1 to be considered complete

**Phase 2 must be stated as intent:**
- What capability Phase 2 adds
- The trigger condition for starting Phase 2 (not a date — a condition: when X happens, Phase 2 begins)
- What in Phase 1 was designed to enable Phase 2 (the architectural hook)

**The test**: if the business triggers change in month 3, does Phase 2 still make sense? If not, Phase 2 is a date-driven afterthought, not an evolution plan.

---

### Section 6: Risk Register

A risk register is not a list of things that could go wrong. It is a structured acknowledgment of the risks you are accepting, the ones you are mitigating, and the ones you cannot control.

**For each risk, capture:**

| Field | Content |
|---|---|
| Risk | What could go wrong |
| Likelihood | High / Medium / Low, with brief justification |
| Impact | What happens to the project or business if it materializes |
| Owner | Who is responsible for monitoring and responding |
| Response | Mitigate / Accept / Transfer — with the specific action |

**Include at least:**
- One technical risk (a component that could fail or not deliver as expected)
- One organizational risk (a dependency on a team, vendor, or person who is outside your control)
- One compliance risk (if the scenario includes regulatory requirements)
- One "accepted risk" — something you know could go wrong and are consciously not mitigating, because the cost of mitigation exceeds the risk

**The test**: if someone read only the risk register, would they understand the biggest threats to this project's success? If the risks feel generic ("project may take longer than expected"), they are not specific enough.

---

## Section 2: The Difference Between a Design Review and a Pitch

These two formats serve different purposes and require different preparation.

| Design Review | Architecture Pitch |
|---|---|
| Audience: engineers and architects | Audience: decision-makers with mixed backgrounds |
| Goal: validate technical soundness | Goal: secure approval, funding, or commitment |
| Tone: collaborative, exploratory | Tone: confident, decisive |
| What you bring: diagrams, ADRs, implementation details | What you bring: full proposal, business case, risk register |
| What you're asking: "does this design work?" | What you're asking: "will you let us build this?" |
| Success: the team understands the design | Success: a decision is made |

**The most common pitch failure**: architects treat an executive pitch like an engineering design review. They walk the audience through every component, every trade-off, every implementation detail — and by the time they reach the ask, the audience has lost the thread.

In a pitch, the structure is argument-first:

```
DESIGN REVIEW order:          PITCH order:
1. Current state               1. The problem (and its cost)
2. Requirements                2. The proposed solution (high altitude)
3. Design options              3. Why this solution (key decisions)
4. Recommended design          4. What it costs and when it delivers
5. Trade-offs                  5. What could go wrong
6. Questions                   6. The ask
```

The pitch opens with the audience's problem, not with the architect's design. It closes with a specific ask, not with "questions?"

---

## Section 3: Handling Adversarial Questions

In a high-stakes architecture pitch, not all questions are equal. Some are genuine technical challenges. Some are political. Some come from confusion. Each requires a different response.

### Type 1: Genuine Technical Challenge

**Signature**: specific, technical, points to a real limitation or gap in the design.

> "Your proposal uses a single Snowflake account for all three business units. What happens when Business Unit B's reporting workload spikes and takes down the BI queries for Business Unit A?"

This is a good challenge. The questioner has identified a real risk. Do not be defensive.

**Response pattern:**
1. Acknowledge the validity: "That's a real concern — compute contention is a known risk in this model."
2. Explain what the design does about it: "We've addressed this with dedicated virtual warehouses per business unit, which isolate compute resources. A BU B spike won't affect BU A's virtual warehouse."
3. If the design doesn't address it: "You've identified a gap. I'd want to add a dedicated virtual warehouse per BU to the Phase 1 scope, and document that in the risk register. Can we note that and come back to it?"

The last option is the hardest and the most important. Admitting a gap in real time, committing to address it, and moving on is the mark of a mature architect. It is not a failure — it is the design improving.

### Type 2: Political Objection

**Signature**: not about the technical merit of the design, but about organizational dynamics, priorities, or history.

> "We tried a data platform project two years ago and it failed. The team spent 6 months building something nobody used. Why is this different?"

This is not a technical question. The questioner is expressing a fear rooted in organizational history.

**Response pattern:**
1. Name the fear directly: "That's a fair concern — platform projects have a history of overbuilding and under-delivering."
2. Name what's structurally different about this proposal: "This design has two specific differences: Phase 1 has a 10-week scope with a defined definition of done, not an open-ended platform vision. And the three deliverables in Phase 1 are owned by specific teams who are already asking for them."
3. Offer evidence: "If it would be useful, I can walk through the Phase 1 scope and the specific teams who will use it before we go further."

Do not argue against the past failure. Acknowledge it and explain the structural difference.

### Type 3: Confusion-Driven Question

**Signature**: the questioner is operating on a false premise or misunderstands a component.

> "So this Bronze layer — is that where we store all our sensitive customer data permanently? That sounds like a security risk."

The questioner has a real concern (security), but it's based on a misreading of the design.

**Response pattern:**
1. Correct the premise gently, before engaging the concern: "Not quite — the Bronze layer stores raw data temporarily, as a recovery mechanism. PII is masked before it reaches Bronze, and masked data is deleted after 30 days per the retention policy."
2. Then address the underlying concern: "Your security instinct is right — PII handling is one of the most sensitive parts of this design. ADR-002 documents exactly how we handle it, including the deletion workflow for GDPR compliance."

Do not dismiss the question because the premise is wrong. The concern behind it is often valid.

### Iterating in real time

Sometimes a question reveals a genuine gap that changes the design. This is not a failure. It is the pitch doing its job.

When a question exposes a real gap:
1. Acknowledge it directly: "That's a valid concern I didn't address in the proposal."
2. State what you'd change: "If we accepted that, Phase 1 scope would expand to include [X] — which adds approximately [cost/time estimate]."
3. Ask for clarity on the constraint: "Is that a hard requirement, or is it something we can address in Phase 2 with a documented trigger?"

The key discipline: you can modify the design in real time. You cannot abandon the core recommendation without a legitimate technical reason. If you change the recommendation because someone in the room is senior and seems unhappy, that is capitulation — not iteration.

---

## Section 4: Iterating Without Losing the Thread

The most common failure during adversarial Q&A is not capitulation — it is losing the thread. The participant accepts a point from the questioner, pivots to address it, and then cannot find their way back to the main recommendation.

### The anchor technique

Before the adversarial Q&A begins, write one sentence on a card or note: your core recommendation in plain language.

> "UrbanBasket needs a unified data platform built in two phases: Phase 1 delivers consolidated reporting for Finance and Operations in 12 weeks; Phase 2 delivers real-time customer behavior data for Marketing when the team reaches 5 engineers."

When a challenge pulls you into detail, answer the detail, then return to the anchor. Every time.

> "You're right that the GDPR deletion workflow adds complexity to the ingestion layer. We've scoped that into Phase 1 with a 3-day implementation estimate. [Return to anchor] That said, the core proposal remains: Phase 1 in 12 weeks, Phase 2 when the team is ready."

The anchor is not a rhetorical trick. It's how you maintain coherence when you're responding under pressure.

---

## Section 5: An Abbreviated Pitch — With Annotations

The following is a condensed architecture pitch for a fictional scenario, with annotations showing why each section is structured the way it is.

---

### Pitch: Unified Analytics Platform for UrbanBasket

---

**Opening — Business Context** *(annotation: starts with cost of the problem, not the solution)*

> "UrbanBasket's growth has outpaced its data infrastructure. The marketing team runs 14 separate campaign reports from 4 different tools, none of which agree on customer counts. The operations team discovered a $340K inventory discrepancy last quarter that took 3 weeks to trace — because the data lived in three places with no single source of truth. Finance closes the books manually, taking 2 days per quarter. These are not data team problems. They are business problems with a data root cause."

---

**Current State** *(annotation: names the implicit decisions in the current system using M01 framing)*

> "The current state has 3 implicit decisions baked in: (1) each team owns its own analytics tool, which traded cost for fragmentation; (2) Shopify is the de facto source of truth for revenue, which works until the acquisition's order management system disagrees; (3) there is no ingestion layer — analysts query operational databases directly, which creates load on production systems and makes auditability impossible."

---

**Proposed Design** *(annotation: constraint-led, names what's excluded and why)*

> "Given the team of 3 data engineers, a $60K/year cloud budget, and a hard requirement for EU data residency, Phase 1 is scoped to: a managed ingestion layer (Fivetran for SaaS sources, custom SFTP ingest for the legacy ERP), a three-layer warehouse on Snowflake (EU region), and a dbt transformation layer owned by the analytics engineer. Phase 1 does not include real-time streaming or Customer 360 — not because they're unimportant, but because the team cannot support streaming operations and the acquisition's data quality isn't clean enough yet for a reliable Customer 360."

---

**Key Decision** *(annotation: references ADR structure, names the rejected alternative explicitly)*

> "The single most contested decision is Snowflake over Redshift. ADR-001 covers this in detail, but the short version: the EU data residency requirement and the acquisition's Oracle environment both require cross-cloud compatibility. Redshift is AWS-native and would require all data to stay in AWS, creating a conflict with the Oracle source that runs on Azure. Snowflake's multi-cloud architecture resolves this. The cost premium is $8K/year — documented in ADR-001 as an accepted cost."

---

**Roadmap** *(annotation: Phase 1 fully specified, Phase 2 as triggered intent)*

> "Phase 1: 12 weeks. Weeks 1–4: ingestion layer and Bronze zone. Weeks 5–8: Silver layer with dbt, data quality checks active. Weeks 9–12: Gold layer and Finance dashboard validation. Definition of done: Finance closes the books from the dashboard, not Excel. Phase 2 begins when: the analytics engineer completes dbt certification AND the acquisition's data quality error rate drops below 2%. Until both conditions are true, Phase 2 is intentionally deferred."

---

**Risks** *(annotation: names the accepted risk explicitly, not just mitigated risks)*

> "The highest-impact risk is the acquisition's Oracle source. We have 14 known schema issues and an estimated 8% error rate in the order data. We are accepting this risk in Phase 1 by excluding the acquisition from the Gold layer — it feeds Bronze only, and analysts are warned explicitly. If the error rate doesn't improve before Phase 2, we may need to invest in a dedicated data quality sprint before proceeding."

---

**The Ask** *(annotation: specific, not vague — names what approval is needed and by when)*

> "We are asking for: $60K/year cloud budget approval, and 12 weeks of uninterrupted data team time — no context switching to ad-hoc projects during the Phase 1 window. With those two commitments, Finance gets clean books in Q3. Without the time commitment, the timeline doubles. The decision we need today is yes or no on those two conditions."

---

### What the annotations reveal

Every section serves the audience's ability to decide. The opening establishes cost. The current state establishes diagnosis. The design establishes the solution. The ADR establishes trust. The roadmap establishes accountability. The risk register establishes honesty. The ask establishes clarity.

An architecture pitch with any of these sections missing is asking for a decision without giving the audience what they need to make it.
