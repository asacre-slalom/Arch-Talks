# Assignment — Module 04: Architect's Voice

## Overview

You have already done the hard architectural work. In Module 02 you designed NovaMart's data platform. In Module 03 you documented the decisions behind it.

Now the work is communication: taking what you built and making it land for two fundamentally different audiences.

This assignment has three components:

1. **Technical presentation** — 10 minutes for engineers and architects
2. **Non-technical presentation** — 5 minutes for VP-level and business stakeholders
3. **Hot seat** — live, unscripted, in the ceremony (not submitted in advance)

---

## Source Material

Use your work from Module 02 and Module 03:

- The NovaMart constraint canvas and architecture recommendation (M02)
- At least one of your ADRs (M03) — preferably ADR-002 (the NovaMart forward-looking one)

You are not designing anything new. You are communicating what you already built, to two audiences who need different things from it.

---

## Deliverable 1 — Technical Presentation (10 minutes)

**Audience**: Senior data engineers and architects who need to understand your architectural reasoning well enough to implement, extend, or challenge it.

**What they need to leave with**:
- The key design decisions and why you made them
- The constraints that shaped the design
- What was deferred and under what conditions it changes
- Confidence that the design is technically sound

**Requirements**:
- Uses a Level 2 (Container) diagram — component roles, flows, boundaries
- Presents at least 2 architectural decisions with constraint-backed reasoning
- References at least one ADR by name and explains what it protects against
- Covers what Phase 1 does NOT include, and why
- Uses technical vocabulary accurately — this audience will notice imprecision

**Format**: slides, structured markdown document, or a combination. No prose-only format — at minimum, one diagram must be present.

**Length check**: time yourself. If you can't cover the required content in 10 minutes, you have too much content — not too little time.

---

## Deliverable 2 — Non-Technical Presentation (5 minutes)

**Audience**: VP of Data, Head of Analytics, or similar — a business decision-maker who controls budget or organizational priorities and needs to understand the design's business impact and risks.

**What they need to leave with**:
- What will change for them and their teams
- What it costs (time, money, people)
- What risks exist and how they're managed
- What isn't in scope for Phase 1 and when it comes

**Requirements**:
- Uses a Level 1 (Context) diagram — system and its relationships to people and systems, no internal components
- Explains at least one trade-off using the 4-sentence structure from `material.md` Section 3
- Contains no unexplained technical terms (Airflow, dbt, schema, medallion, DAG, CDC, etc.)
- Has an explicit ask: what does this audience need to approve, provide, or decide?
- Is accurate — the architecture's trade-offs and accepted risks must be present, not hidden

**The hardest part**: the 5-minute version must convey the same architectural honesty as the 10-minute version. You cannot hide the trade-offs to make it sound better. If something is a limitation, name it in business terms.

**Format**: slides or structured document with the Context diagram. Maximum 7 slides / sections.

---

## Deliverable 3 — Hot Seat (Live in Ceremony)

This is not submitted in advance. It happens at the ceremony, after your non-technical presentation.

The facilitator will ask you to explain one specific decision from your NovaMart design, as if you are talking to a skeptical VP who has just raised a concern. You will not know which decision or which concern until the moment it's asked.

You have 90 seconds to respond.

### What you are being tested on

- Can you access the architectural reasoning from M02 and M03 spontaneously — not from a slide?
- Can you adapt your vocabulary and frame to the VP context in real time?
- Can you hold your position when challenged, without becoming defensive or caving?

### How to prepare

You cannot prepare a script — the question is unknown. What you can do:

1. **Know your decisions cold.** For every major decision in your NovaMart design, be able to state in one sentence: what was gained, what was accepted, and what the trigger is for revisiting it.
2. **Practice the 4-sentence trade-off structure** (Section 3 of `material.md`) until it feels natural, not mechanical.
3. **Anticipate the three most likely VP challenges** for your design:
   - "This sounds expensive/complex — why can't we do something simpler?"
   - "How long until [use case not in Phase 1] is ready?"
   - "What happens if this doesn't work — how do we recover?"
   Being ready for these three covers most of what can be asked.

---

## File Structure for Submission

```
modules/04-voice/submissions/[your-name]/
├── technical-presentation.[md|pdf|pptx]     ← Deliverable 1
└── nontechnical-presentation.[md|pdf|pptx]  ← Deliverable 2
```

The hot seat (Deliverable 3) has no submission file.

**Deadline**: Submit both presentations before your ceremony (recommended: by Day 12 of the 2-week cycle)

---

## Ceremony Format

| Time | Activity |
|---|---|
| 0:00 – 10:00 | Technical presentation (Deliverable 1) |
| 10:00 – 15:00 | Non-technical presentation (Deliverable 2) |
| 15:00 – 16:30 | Hot seat: facilitator poses a VP challenge, participant responds (90 sec) |
| 16:30 – 20:00 | Q&A from peers and facilitator |

> Total per participant: ~20 minutes. Plan accordingly when scheduling 2–3 participants per ceremony.

---

## High-Level Success Criteria

Your submission is strong when:

- The two presentations use different vocabulary, different diagrams, and different frames — not the same content with some terms removed
- The non-technical version still accurately represents the trade-offs — it's elevated, not sanitized
- Your Level 1 diagram contains no internal components, no tool names, no layer labels
- Your Level 2 diagram shows components and flows at the right altitude — not a pipeline diagram, not an ERD
- In the hot seat, you hold the core recommendation intact under pressure and change it only if the challenge reveals a genuine technical gap
