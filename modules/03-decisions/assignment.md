# Assignment — Module 03: Architecture Decision Records

## Overview

In Module 02 you designed a data architecture for NovaMart under real constraints. You made real decisions — which ingestion pattern, which storage model, which components to defer. You justified those decisions with a constraint canvas and a recommendation document.

Now those decisions need to be made durable.

This assignment has three parts:

1. **Two ADRs you write** — documenting architectural decisions from your own domain
2. **One ADR review** — structured feedback on a weak ADR provided below

---

## Part 1 — ADR for an Existing Decision (Retroactive)

Write a complete ADR for an architectural decision that has already been made in a system you have worked on.

This is harder than it sounds. The decision was made without a written record. You must reconstruct the context, the options that were likely considered, the drivers that shaped the choice, and the consequences that materialized — including the negative ones.

**Choose a decision that:**
- Is architectural (meets the threshold from `material.md` Section 3)
- You know well enough to reconstruct honestly
- Has visible consequences — positive and negative — that you can observe today
- Was NOT your own decision (if possible) — reverse-engineering someone else's reasoning is the real test

**Requirements:**
- Follow the full ADR structure from `material.md` Section 2
- The Context section must be written neutrally — not pre-arguing for the decision
- Options Considered must include at least 2 alternatives with pros and cons
- Consequences must include at least 2 negative items — things the decision made harder, not impossible
- Add a line at the top: `> *Note: This is a retroactive ADR. Context and options were reconstructed from available evidence.*`

**Suggested title format**: `ADR-001: [Short imperative phrase — what was decided]`

---

## Part 2 — ADR for a Forward-Looking Decision (NovaMart)

Write a complete ADR for one of the architectural decisions from your Module 02 NovaMart recommendation.

Pick the single most important decision in your recommended design — the one that a new engineer would most need to understand before making any change to the system.

Good candidates from the NovaMart scenario:
- The choice of ingestion pattern for the POS SFTP flat-file source
- The decision on how to handle PII data across layers (given the compliance constraint)
- The storage and warehouse model chosen (given the AWS contract and budget)
- Whether to use managed ELT (e.g., Fivetran) vs. custom ingestion for the CRM/Shopify sources

**Requirements:**
- Follow the full ADR structure from `material.md` Section 2
- Decision Drivers must reference specific NovaMart constraints from your M02 constraint canvas
- Options Considered must match the options from your M02 comparison — but written in ADR form, not table form
- Consequences must include the accepted risk you named in your M02 submission (Deliverable 4)
- The decision must be forward-looking: written as if the decision is being made now, not already in production

**Suggested title format**: `ADR-002: [Short imperative phrase]`

---

## Part 3 — Weak ADR Review

Read the following ADR carefully. Then write structured feedback identifying its specific gaps.

---

### The Weak ADR (to review)

```markdown
# ADR-003: Use Apache Airflow for Pipeline Orchestration

**Status**: Accepted
**Date**: 2024-03-10
**Deciders**: Data Engineering Team

## Context

We need an orchestration tool to schedule and monitor our data pipelines.
After evaluating the options, we decided to use Apache Airflow.

## Decision Drivers

- It's open source
- The team has some experience with it
- It's widely used in the industry

## Options Considered

### Apache Airflow
A popular open-source workflow orchestration platform.
- **Pro**: Open source, widely adopted, large community
- **Pro**: Python-based DAGs are flexible
- **Pro**: Supports complex dependency graphs

### Prefect
A newer orchestration tool with a modern UI.
- **Con**: Less mature than Airflow
- **Con**: Smaller community
- **Con**: Team has no experience with it

## Decision

We decided to use Apache Airflow because it is the industry standard and
the team already knows it. It will allow us to build our pipelines quickly
and reliably.

## Consequences

### Positive
- Fast onboarding since the team knows Airflow
- Large community means good documentation and support
- Flexible DAG structure supports all our pipeline patterns

### Negative
(none identified at this time)
```

---

### Your Review Task

Write structured feedback on this ADR. Your feedback document must:

1. **Identify every structural gap** — sections that are missing, empty, or inadequately filled
2. **Identify at least 2 factual or logical problems** — claims that are incorrect, unsupported, or that would mislead a future reader
3. **Identify at least 1 missing option** that should have been considered and wasn't
4. **Write the Consequences → Negative section** as it should appear, based on the publicly known trade-offs of Airflow

Your feedback must be specific. Avoid generic comments like "needs more detail." Reference specific lines, claims, or sections.

---

## File Structure for Submission

```
modules/03-decisions/submissions/[your-name]/
├── ADR-001-retroactive.md       ← Part 1: retroactive ADR
├── ADR-002-novamart.md          ← Part 2: forward-looking NovaMart ADR
└── adr-review.md                ← Part 3: feedback on the weak ADR
```

**Deadline**: Submit before your ceremony (recommended: by Day 12 of the 2-week cycle)

---

## Presentation Guide (for the ceremony)

You have **≤ 12 minutes**:

| Time | What to cover |
|---|---|
| 0:00 – 1:00 | Frame the two ADRs: what decision type each one represents (retroactive vs. forward-looking) and why you chose those decisions |
| 1:00 – 5:00 | Walk through ADR-001 (retroactive) — focus on Context and Consequences. What did you have to reconstruct? What negative consequences did you find? |
| 5:00 – 9:00 | Walk through ADR-002 (NovaMart) — focus on Decision Drivers and Options. How do your M02 constraints map to ADR form? |
| 9:00 – 12:00 | Key findings from the weak ADR review — name the 2 most critical gaps and explain why they matter to a future reader |

Do not read the ADR text aloud. Present the *reasoning* — what made this decision hard, what was genuinely rejected and why, and what the design cost.

---

## High-Level Success Criteria

Your submission is strong when:

- A stranger can read your ADR-001 and understand what was decided, why, and what it cost — without asking you any questions
- Both ADRs have non-trivial negative consequences (not "none identified" and not "minor operational overhead")
- Your options were genuinely evaluated — not advocacy with a straw man
- Your ADR review names specific problems with specific evidence — not vague suggestions
- The NovaMart ADR connects explicitly to constraints from your M02 work
