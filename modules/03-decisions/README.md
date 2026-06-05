# Module 03 — Architecture Decision Records

> _Systems don't decay because the code rots. They decay because the reasoning behind the decisions is lost._

---

## Why This Module Exists

Imagine inheriting a data platform with no documentation. You find a Gold layer built entirely on a star schema. You find three separate ingestion pipelines doing nearly the same thing. You find PII stored in the Bronze layer, masked only in Gold. You find a CDC connector running alongside a scheduled batch job pulling from the same source.

Are these mistakes? Deliberate choices? Compromises someone made under pressure three years ago? Features that a team built and then abandoned? Nobody knows. The engineers who made those calls have moved on. The Slack threads are buried. The Confluence pages were deleted in a migration.

So your team does what every team does in this situation: **they guess.** They refactor what looks wrong. They add what looks missing. They delete what looks unused. Some guesses are right. Others — the ones that touch something that was deliberately designed — break things in ways that take weeks to diagnose.

**The Architecture Decision Record (ADR) exists to prevent this.** It is not a documentation artifact. It is institutional memory written into the codebase, committed alongside the code it explains, readable by the engineer who joins three years from now and asks "why is it like this?"

In Module 02 you designed under constraints and made real decisions. Now you learn to make those decisions durable.

---

## The Lifecycle of a Decision

```
WITHOUT AN ADR
──────────────────────────────────────────────────────────────
  "We chose Delta Lake      →  System built.   →  6 months later:
   for the Gold layer."        ADR not written.    engineer leaves.
                                                        │
                                              18 months later:
                                              new engineer arrives.
                                                        │
                                              "Why Delta Lake?"
                                                        │
                                         ┌──────────────┘
                                         ▼
                                   Nobody knows.
                                         │
                               ┌─────────┴──────────┐
                               ▼                    ▼
                        "It's clearly wrong.   "Let's add Iceberg
                         Let's rewrite it."     on top — it's
                                                 obviously missing."
                               │
                               ▼
                        Expensive mistake.
                        Root cause: lost context.

WITH AN ADR
──────────────────────────────────────────────────────────────
  "We chose Delta Lake      →  ADR-001 committed  →  18 months later:
   for the Gold layer."        to /decisions/         new engineer
                               alongside the code.    arrives.
                                                           │
                                                  "Why Delta Lake?"
                                                           │
                                             git log → ADR-001 →
                                             Context: Databricks
                                             contract. Options
                                             considered: Iceberg,
                                             Parquet. Consequences:
                                             vendor lock-in accepted.
                                                           │
                                                           ▼
                                                  Informed decision.
                                                  No guessing.
                                                  No expensive mistake.
```

---

## Learning Objectives

By the end of this module, you will be able to:

- **Write** a complete ADR that includes context, decision drivers, options considered, the decision, and both positive and negative consequences
- **Distinguish** between a decision that warrants an ADR and one that is an implementation detail
- **Reverse-engineer** the reasoning behind an existing architectural decision, even when no documentation exists
- **Review** another person's ADR and give structured technical feedback that identifies specific gaps
- **Recognize** the difference between an ADR written to record honest reasoning and one written as post-hoc justification

---

## Prerequisites

- Completed Module 02 (Design Under Constraints) with result ADVANCES
- You will write ADRs for decisions from your M02 NovaMart assignment — have that work accessible

---

## Estimated Time

| Activity | Estimated Time |
|---|---|
| Read `material.md` | 2–3 hours |
| Complete `assignment.md` | 4–6 hours |
| Ceremony presentation | ≤ 12 minutes |
| **Total** | **6–9 hours** |

---

## How to Use This Module

1. **Read `material.md` fully** before writing any ADR — especially Section 3 (the decision threshold) and the two complete examples in Section 4
2. **Start with the retroactive ADR** — reverse-engineering existing reasoning is harder than it sounds and will reveal gaps in your constraint thinking from M02
3. **Write both ADRs before doing the weak ADR review** — reviewing someone else's ADR after you've written your own is more instructive
4. **Submit all three deliverables** before your ceremony
5. **Present in the ceremony** (≤ 12 minutes) — walk through one ADR in detail and summarize the other; save 2 minutes for your review findings
6. **Receive your result** within 24 hours with written feedback

---

## How Do I Know I'm Ready?

Before submitting, check these:

- Can someone who has never seen NovaMart read my ADR and understand what was decided, why, and what the cost was — in under 3 minutes?
- Does my ADR list negative consequences? If not, it is not an ADR — it is advocacy.
- For the options I didn't choose: did I explain *why* they were rejected using evidence, not just preference?
- In my weak ADR review, did I name specific missing elements with specific evidence — or did I just say "it needs more detail"?

If your consequence section reads like a product pitch, you have a post-hoc justification, not an ADR. Go back to Section 5 of `material.md`.

---

> _Read the material:_ [`material.md`](material.md)
> _See what to deliver:_ [`assignment.md`](assignment.md)
> _See how you'll be evaluated:_ [`scoring-rubric.md`](scoring-rubric.md)
