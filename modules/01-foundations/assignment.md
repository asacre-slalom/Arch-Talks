# Assignment — Module 01: Architect's Mindset

## The Challenge

You've worked inside data systems. Now step outside one and describe it as an architect would.

Pick a **real data system** you have worked with in the past year — a pipeline, a data platform, a warehouse, a data product. It doesn't have to be complex. It has to be something you know well enough to explain honestly.

Your job is not to describe what the system does. Your job is to explain **why it is shaped the way it is**.

---

## What You'll Deliver

### Deliverable 1 — Architecture Map

A visual map of the system at the architectural level.

**Requirements:**
- Show the main components (not specific table names or DAG IDs — the roles: ingestion, transformation, storage, serving, orchestration, etc.)
- Show data flows between components (direction, frequency if relevant)
- Mark the boundaries (what team owns what? where does one system hand off to another?)
- You can draw it as a diagram (Mermaid, draw.io, Excalidraw, whiteboard photo) or as a structured ASCII diagram

**What not to include:**
- Code snippets
- Table schemas
- Pipeline configurations
- Tool versions

This is a map, not documentation. It should be readable in 30 seconds by someone who doesn't know the system.

---

### Deliverable 2 — Three Implicit Decisions

Identify exactly 3 architectural decisions that are embedded in this system but were never formally documented.

For each decision, write a short analysis using this structure:

**Decision [#]: [Give it a name, e.g., "Micro-batch over streaming"]**

| Field | Your answer |
|---|---|
| What was decided | [Describe the design choice in one sentence] |
| What it makes easy | [What benefit did this choice create?] |
| What it makes hard | [What cost did this choice introduce?] |
| Who bears the cost today | [Which team, user, or use case pays the price?] |
| What would need to change for this to be different | [What constraint made this choice — and is that constraint still real?] |

**Requirements:**
- All 3 decisions must be architectural (not implementation) — refer to Section 3 of `material.md` if unsure
- The trade-offs must be real and specific, not generic ("it's slow" is not a trade-off; "it sacrifices freshness below 5 minutes in exchange for operational simplicity" is)
- At least 1 decision should involve a constraint that no longer applies today

---

### Deliverable 3 — One Thing You Now See Differently

In 3–5 sentences: what did you understand differently about this system after doing this exercise that you didn't see before?

This is not a summary of the assignment. It is a genuine reflection on your shift in perspective. There is no wrong answer — but a vague answer will score low.

---

## Format and Submission

**File structure in your submission folder:**

```
modules/01-foundations/submissions/[your-name]/
├── architecture-map.[png|pdf|md]     ← Deliverable 1
├── implicit-decisions.md             ← Deliverable 2 (all 3 decisions in one file)
└── reflection.md                     ← Deliverable 3
```

**Deadline**: Submit before your ceremony date (recommended: no later than Day 12 of the 2-week cycle, to leave time to review before presenting)

---

## Presentation Guide (for the ceremony)

You have **≤ 12 minutes**. Structure it like this:

| Time | What to cover |
|---|---|
| 0:00 – 1:00 | One sentence: what system, what it does, why you chose it |
| 1:00 – 4:00 | Walk through your architecture map — components, flows, boundaries |
| 4:00 – 10:00 | Present your 3 implicit decisions — use the trade-off framing |
| 10:00 – 12:00 | Your reflection: what you now see differently |

Do not spend time on implementation details. If you catch yourself explaining how a DAG works or what a specific table contains, zoom out.

---

## High-Level Success Criteria

Your submission is strong when:

- The architecture map shows the system's structure, not its contents
- A person who doesn't know the system can read your map and understand its shape in under 30 seconds
- Your trade-offs are specific — a stranger could verify them by looking at the system
- Your reflection reveals a genuine change in perspective, not a summary
- You used the words "trade-off", "constraint", "consequence", and "boundary" — and they were earned, not decorative
