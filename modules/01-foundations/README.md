# Module 01 — Architect's Mindset

> _Before you can design systems, you need to learn how to see them._

---

## Why This Module Exists

You've spent years getting really good at building things. You know how to write a pipeline that doesn't break, how to model a dataset cleanly, how to optimize a query that was killing production. That skillset is real and valuable.

But here's the uncomfortable truth: **the skills that made you a great data engineer are not the same skills that will make you a great data architect.**

An architect doesn't just build — they decide. They look at a system and ask *why is it shaped this way?* They see trade-offs where others see configuration. They understand that every design is a frozen set of decisions made by people under constraints, and that those decisions have consequences that ripple forward in time.

This module is about developing that lens. Not new tools. Not new frameworks. A new way of seeing systems.

---

## The Journey of This Module

```
You right now                       You after M01
─────────────────                   ──────────────────────────────
"This pipeline ingests               "This pipeline uses micro-batch
 data every 5 minutes"               instead of streaming because someone
                                     traded freshness for simplicity —
                                     and that decision now limits how
                                     fast the dashboards can react"

"We use a star schema                "We use a star schema, which optimizes
 in the warehouse"                   for read performance at the cost of
                                     write complexity — a valid trade-off
                                     when the team was smaller and analysts
                                     drove all the queries"

"Someone set up three                "Three separate ingestion pipelines
 ingestion pipelines"                exist because the systems were
                                     integrated at different points in time,
                                     each by a different team — the real
                                     cost is now deduplication logic spread
                                     across 4 places"
```

---

## Learning Objectives

By the end of this module, you will be able to:

- **Distinguish** between an architectural decision and an implementation detail in a real data system
- **Construct** an architecture map of a system you know, showing components, data flows, and boundaries — not code
- **Identify** at least 3 implicit trade-offs in an existing system that were never explicitly documented
- **Articulate** the "why" behind a design decision even when you were not the one who made it
- **Explain** the downstream consequences of a specific architectural choice to a peer in under 2 minutes

---

## Prerequisites

This is the first module in the DataArch-Speak program. There are no prior modules required.

You should have:
- 2+ years building or maintaining data pipelines, warehouses, or data platforms
- Hands-on experience with at least one data system in production (you own it, you know its pain)
- Comfort reading and discussing system design at a conceptual level

---

## Estimated Time

| Activity | Estimated Time |
|---|---|
| Read `material.md` | 2–3 hours |
| Complete `assignment.md` | 3–5 hours |
| Ceremony presentation | ≤ 12 minutes |
| **Total** | **5–8 hours** |

---

## How to Use This Module

1. **Read `material.md` fully** before touching the assignment — the concepts build on each other
2. **Pick a real system** you have worked with for the assignment (not a toy example)
3. **Work alone first**, then optionally discuss with a peer before the ceremony
4. **Submit your deliverables** to the repository before your scheduled ceremony
5. **Present in the ceremony** (≤ 12 minutes) — no slides required, your architecture map is the artifact
6. **Receive your result** (ADVANCES / REINFORCES) within 24 hours with written feedback

---

## How Do I Know I'm Ready?

Before submitting, ask yourself these questions. If you can answer them without looking at your notes, you are ready:

- Can I explain the system I mapped at three levels: to a junior engineer, to a product manager, and to a VP?
- For each trade-off I identified: what was gained? what was sacrificed? who paid the cost?
- Can I tell the difference between "we implemented it this way" and "we designed it this way"?
- If someone asked me "why doesn't this system do X?" — can I trace the answer back to a decision, not just a technical limitation?

If you're still conflating implementation with architecture, spend another session with Section 3 of `material.md` before submitting.

---

> _Read the material:_ [`material.md`](material.md)  
> _See what to deliver:_ [`assignment.md`](assignment.md)  
> _See how you'll be evaluated:_ [`scoring-rubric.md`](scoring-rubric.md)
