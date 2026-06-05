# Module 02 — Design Under Constraints

> _Anyone can design a great architecture with unlimited time, budget, and talent. The job is to design a great architecture with what you actually have._

---

## Why This Module Exists

In Module 01 you learned to read systems — to see the shape of decisions made by others, the trade-offs they accepted, the constraints that drove their choices.

Now you're on the other side of the table. You're the one making the decisions.

And here's what nobody tells you in a whiteboard session: **the design space is never open**. By the time you're asked to propose an architecture, someone has already set constraints you didn't choose:

- The team has 3 data engineers, not 10
- The cloud budget is $40K/year, not unlimited
- There are 6 months of technical debt in the ingestion layer that can't be touched
- The deadline is 8 weeks, not 6 months
- Compliance requires data to stay in a specific region
- A vendor contract that expires in 14 months locks you into a tool you'd never pick today

The gap between "architect who designs beautiful systems on paper" and "architect who solves real problems" is exactly this: the ability to produce strong, defensible designs within constraints you didn't set — and to be honest about what those constraints cost.

This module develops that ability.

---

## The Constraint Space

Every architectural decision lives inside a space defined by forces pulling in different directions. The job is not to escape the space — it's to understand it clearly and design the best solution within it.

```
                         IDEAL DESIGN
                              ★
                             /|\
                            / | \
                           /  |  \
                          /   |   \
          ───────────────────────────────────────
         |                                       |
  BUDGET ◄──────────── DESIGN SPACE ────────────► TEAM SKILLS
         |                                       |
          ───────────────────────────────────────
                          \   |   /
                           \  |  /
                            \ | /
                             \|/
                         TIME / DEBT

  ┌──────────────────────────────────────────────────────────┐
  │  Constraints don't ruin the design.                      │
  │  They ARE the design context.                            │
  │  An architect who ignores them isn't being bold —        │
  │  they're being irresponsible.                            │
  └──────────────────────────────────────────────────────────┘
```

The forces vary by situation:

| Constraint type | Examples |
|---|---|
| **Capacity** | Team size, skills available, bandwidth for migration |
| **Economic** | Cloud budget, licensing costs, migration cost |
| **Time** | Delivery deadlines, product launches, contract expirations |
| **Technical** | Existing debt, legacy systems, integration limits |
| **Compliance** | Data residency, PII handling, audit requirements |
| **Organizational** | Vendor contracts, political dependencies, team ownership |

A design that ignores any of these will fail — not because the architecture was wrong, but because it was designed for a world that doesn't exist.

---

## Learning Objectives

By the end of this module, you will be able to:

- **Identify and document** all relevant constraints for a given architectural problem before proposing any solution
- **Apply** the Constraint Canvas to surface hidden constraints that aren't stated explicitly
- **Design** two or more architectural options for the same problem with explicit, comparable criteria
- **Recommend** a specific option with a justification that references constraints — not just technical preference
- **Articulate** what the recommended design defers, and under what conditions those deferrals should be revisited

---

## Prerequisites

- Completed Module 01 (Architect's Mindset) with result ADVANCES
- Familiarity with at least one cloud data platform (AWS, Azure, or GCP) at a working level

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

1. **Read `material.md` fully** — pay special attention to the Constraint Canvas (Section 2) before touching the assignment
2. **Do not start designing** until you've completed your constraint documentation — this is the discipline the module is training
3. **Work through both options** honestly — the option you don't recommend must be genuinely viable, not a straw man
4. **Submit your deliverables** to the repository before your ceremony
5. **Present in the ceremony** (≤ 12 minutes) — your constraint canvas and option comparison are the primary artifacts
6. **Receive your result** within 24 hours with written feedback

---

## How Do I Know I'm Ready?

Before submitting, answer these honestly:

- If someone asked me "why didn't you go with Option B?" — can I answer in one sentence that references a constraint, not a preference?
- Did I discover any constraint that was hidden in the problem description that I almost missed? (If no — re-read the scenario more carefully)
- Does my recommended design have anything intentionally left out? Can I name exactly what was deferred and why?
- Would a different team with different constraints solve this same problem with a different architecture — and would that also be correct?

If you can't answer the last question with a confident "yes," your constraint thinking isn't there yet. Go back to Section 5 of `material.md`.

---

> _Read the material:_ [`material.md`](material.md)
> _See what to deliver:_ [`assignment.md`](assignment.md)
> _See how you'll be evaluated:_ [`scoring-rubric.md`](scoring-rubric.md)
