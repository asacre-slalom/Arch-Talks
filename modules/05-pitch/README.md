# Module 05 — Full Architecture Pitch

> _This is not a bigger assignment. It is a different kind of challenge. Everything you built in the previous four modules was preparation for one thing: standing in front of a skeptical audience with a complete proposal, defending every decision you made, and not flinching._

---

## Why This Module Exists

You've covered the full arc:

- In **Module 01** you learned to see systems — to read trade-offs where others see configuration
- In **Module 02** you learned to design under real constraints — to produce recommendations that are honest about what they cost
- In **Module 03** you learned to make decisions durable — to write ADRs that a stranger can read three years later and act on
- In **Module 04** you learned to communicate — to adapt the same architectural reasoning for a VP, an engineer, and a product manager, and to hold your position under pressure

Module 05 asks you to do all of that simultaneously, for a new problem you haven't seen before, and defend it under adversarial questioning from someone who is specifically trying to find the weaknesses.

That is what it means to be a data architect in practice.

---

## How Every Prior Module Feeds Into This One

```
┌─────────────────┐   ┌─────────────────┐   ┌─────────────────┐
│   MODULE 01     │   │   MODULE 02     │   │   MODULE 03     │
│ Architect's     │   │ Design Under    │   │ Architecture    │
│ Mindset         │   │ Constraints     │   │ Decision Records│
│                 │   │                 │   │                 │
│ ► Current state │   │ ► Constraint    │   │ ► ADRs for top  │
│   map of the    │   │   Canvas        │   │   decisions     │
│   legacy system │   │ ► Option        │   │ ► Honest        │
│ ► Trade-off     │   │   comparison    │   │   consequences  │
│   identification│   │ ► Phased design │   │ ► Decision      │
│                 │   │   with triggers │   │   threshold     │
└────────┬────────┘   └────────┬────────┘   └────────┬────────┘
         │                     │                     │
         └─────────────┬───────┘                     │
                       │                             │
          ┌────────────▼────────────┐                │
          │       MODULE 04        │                │
          │   Architect's Voice    │                │
          │                        │                │
          │ ► Executive summary    │                │
          │   calibrated for VP    │                │
          │ ► Technical sections   │                │
          │   for engineers        │                │
          │ ► Hot seat composure   │                │
          └────────────┬───────────┘                │
                       │                            │
                       └──────────────┬─────────────┘
                                      │
                                      ▼
                         ┌────────────────────────┐
                         │       MODULE 05        │
                         │  Full Architecture     │
                         │       Pitch            │
                         │                        │
                         │  New scenario.         │
                         │  Complete proposal.    │
                         │  All skills active.    │
                         │  Adversarial defense.  │
                         └────────────────────────┘
```

---

## What Makes This Different From Module 02?

Module 02 asked you to design for a scenario you were given, with constraints already identified.

Module 05 gives you a scenario and asks you to:

| M02 | M05 |
|---|---|
| Complete the constraint canvas | Surface constraints from a deliberately ambiguous brief |
| Design two options and compare | Produce one complete, defensible proposal |
| Write a recommendation | Write a full proposal: context + design + ADRs + roadmap + risks |
| Present with facilitator Q&A | Present with a 5-minute adversarial Q&A (facilitator as skeptical VP) |
| Threshold: 65/100 | Threshold: 75/100 |
| NovaMart scenario (structured) | UrbanBasket scenario (ambiguous, politically complex) |

The leap is real. Module 02 was about learning to design under constraints. Module 05 is about producing and defending complete architecture work under professional-grade pressure.

---

## Learning Objectives

By the end of this module, you will be able to:

- **Produce** a complete data architecture proposal from a blank page: business context, current state, proposed design, ADRs, phased roadmap, and risk register
- **Structure** a pitch that asks for a decision — not a briefing that informs one
- **Defend** every significant decision in your proposal under adversarial questioning, distinguishing genuine technical challenges from political objections from confusion-driven questions
- **Iterate** your proposal in real time based on feedback received during the presentation, without losing your core recommendation
- **Integrate** the skills from all prior modules into a single coherent deliverable

---

## Prerequisites

- Completed all of Modules 01–04 with result ADVANCES
- Familiarity with at least one modern cloud data platform (AWS, Azure, or GCP)
- Your M01–M04 deliverables are accessible — you may draw on any of your prior work

---

## Estimated Time

| Activity | Estimated Time |
|---|---|
| Read `material.md` | 2–3 hours |
| Complete `assignment.md` | 6–10 hours |
| Ceremony presentation + adversarial Q&A | ≤ 17 minutes |
| **Total** | **8–13 hours** |

> This is the most time-intensive module. Budget accordingly. The proposal is not complete until it can stand alone without oral explanation.

---

## How to Use This Module

1. **Read `material.md` fully** — especially the pitch structure (Section 1) and the adversarial Q&A handling (Section 3) before you start writing
2. **Read the UrbanBasket scenario in `assignment.md` twice** — the second time looking for constraints that are embedded in the narrative, not stated explicitly
3. **Start with the current state map** — you cannot propose a target design until you understand what you are replacing and why
4. **Write the ADRs before finalizing the design** — the discipline of writing a real ADR often reveals that the design needs adjustment
5. **Submit the full proposal** before your ceremony
6. **Present in the ceremony** — 12 minutes of presentation, then 5 minutes of adversarial Q&A you cannot predict
7. **Receive your result** within 24 hours

---

## How Do I Know I'm Ready?

Before submitting, answer these — honestly:

- Can I explain the core architectural recommendation in 60 seconds to a VP, without slides, and without technical jargon?
- For every major decision in my proposal: do I have an ADR, or at least a written justification that could become one?
- Is my Phase 1 roadmap actually deliverable by the team described in the scenario — or did I design for a team I wish they had?
- If someone asks "why not just use [an alternative I didn't choose]?" — can I give a constraint-grounded answer for every major decision?
- Am I ready to hear "this is over-engineered" and respond without flinching and without capitulating?

If you cannot answer the last question with confidence, spend another session with Section 3 of `material.md` before submitting.

---

> _Read the material:_ [`material.md`](material.md)
> _See what to deliver:_ [`assignment.md`](assignment.md)
> _See how you'll be evaluated:_ [`scoring-rubric.md`](scoring-rubric.md)
