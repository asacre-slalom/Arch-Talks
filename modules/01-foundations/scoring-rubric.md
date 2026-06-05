# Scoring Rubric — Module 01: Architect's Mindset

**Minimum score to advance**: 60 / 100  
**Critical threshold**: no dimension can be rated CRITICAL

> This is the entry module. The goal is activation, not filtering. The bar is set at 60 to give space for participants who are early in the mindset shift — not to lower standards, but to reward genuine engagement over polished performance.

---

## Evaluation Dimensions

| # | Dimension | Weight | What it evaluates |
|---|---|---|---|
| 1 | Architectural Framing | 30% | Does the participant describe the system at the right level of abstraction, focusing on components, flows, and boundaries — not code, tables, or tool configs? |
| 2 | Trade-off Identification | 30% | Can the participant name real, specific trade-offs embedded in the system, including what was gained and what was sacrificed? |
| 3 | Decision Classification | 25% | Can the participant correctly distinguish between architectural decisions and implementation details, and justify the difference? |
| 4 | Depth of Reflection | 15% | Does the participant demonstrate a genuine shift in perspective — not just a summary of what they did? |

**Total: 100%**

---

## Performance Levels by Dimension

### Dimension 1: Architectural Framing (30 pts)

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 30 pts | The map shows components, flows, and boundaries at a consistent level of abstraction. The participant explains the map without being prompted, including team ownership and handoff points. If asked "why is it shaped this way?", they answer immediately without going back to implementation details. |
| **ACHIEVED** | 22 pts | The map correctly shows the main components and flows. Some detail creeps in (e.g., a specific table or DAG name appears), but the participant recovers when prompted and returns to the architectural level. |
| **DEVELOPING** | 15 pts | The map mixes architectural and implementation views. The participant struggles to describe the system without referencing specific tools, queries, or configurations. Needs prompting to zoom out. |
| **CRITICAL** | 0 pts | The map is a list of tools or a pipeline diagram, not an architecture map. The participant cannot describe the system without referencing code or configuration. No evidence of architectural framing. |

---

### Dimension 2: Trade-off Identification (30 pts)

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 30 pts | Presents 3 specific trade-offs with all four elements present: what was decided, what it makes easy, what it makes hard, and who bears the cost today. At least one trade-off includes reflection on whether the original constraint still applies. No prompting needed. |
| **ACHIEVED** | 22 pts | Presents 3 trade-offs that are real and specific. Two elements are consistently present (benefit + cost). May need one prompt to articulate who bears the cost or whether the constraint is still valid. |
| **DEVELOPING** | 15 pts | Identifies 1–2 trade-offs, but they are generic ("it's slow", "it doesn't scale"). Or presents 3 trade-offs but they are implementation-level, not architectural. Needs significant prompting to reach specificity. |
| **CRITICAL** | 0 pts | Cannot identify any architectural trade-off. Describes limitations ("it has latency issues") without connecting them to a design decision. Or presents 3 items that are clearly implementation details reframed as trade-offs. |

---

### Dimension 3: Decision Classification (25 pts)

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 25 pts | When asked "is that an architectural or implementation decision?", answers correctly and justifies the answer using the impact/reversibility frame without being coached. Spontaneously uses the distinction when presenting decisions. |
| **ACHIEVED** | 19 pts | Correctly classifies decisions when prompted. May not spontaneously use the distinction, but understands it when it's raised. Gets at least 2 of 3 decisions correctly classified under pressure. |
| **DEVELOPING** | 12 pts | Conflates architecture and implementation in at least one of the three decisions. May understand the distinction conceptually but cannot apply it consistently to their own work. |
| **CRITICAL** | 0 pts | Cannot distinguish between architectural decisions and implementation details. All three "decisions" are implementation choices. Shows no understanding of the concept even after prompting. |

---

### Dimension 4: Depth of Reflection (15 pts)

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 15 pts | The reflection reveals a specific, named change in perspective. The participant can say "I used to see this as [X], now I see it as [Y]" with concrete examples. The shift is about how they think, not what they now know. |
| **ACHIEVED** | 11 pts | The reflection shows a genuine shift but stays somewhat abstract ("I now think more about the big picture"). The change is real but not yet fully articulated. |
| **DEVELOPING** | 7 pts | The reflection is a summary of the assignment rather than a perspective shift ("I found three trade-offs and mapped the system"). No evidence of changed thinking. |
| **CRITICAL** | 0 pts | No reflection is presented, or the reflection is entirely generic and could have been written without doing the assignment. |

---

## Scoring Sheet (for facilitator use during ceremony)

| Dimension | Weight | Level | Score |
|---|---|---|---|
| 1. Architectural Framing | 30% | ________ | ___ / 30 |
| 2. Trade-off Identification | 30% | ________ | ___ / 30 |
| 3. Decision Classification | 25% | ________ | ___ / 25 |
| 4. Depth of Reflection | 15% | ________ | ___ / 15 |
| **TOTAL** | **100%** | — | **___ / 100** |

---

## Final Decision

| Condition | Decision |
|---|---|
| Score ≥ 60 AND no dimension is CRITICAL | ✅ **ADVANCES** to Module 02 |
| Score < 60 OR any dimension is CRITICAL | 🔁 **REINFORCES** — retry at next available ceremony |

---

## If REINFORCES: Next Steps

The facilitator must communicate the following in writing within 24 hours:

**Step 1 — Name the specific dimension(s) that need work**

Do not say "overall you need to improve." Say "Dimension 2 (Trade-off Identification) scored DEVELOPING because the trade-offs you named were generic. Here is what a specific trade-off looks like: [example]."

**Step 2 — Point to the material**

| If the weak dimension is... | Direct them to... |
|---|---|
| Architectural Framing | `material.md` Section 2 (Systems Thinking) and the diagram example |
| Trade-off Identification | `material.md` Section 4 (Reading Implicit Trade-offs) — re-read both examples |
| Decision Classification | `material.md` Section 3 — re-read the table and litmus test |
| Depth of Reflection | No specific section — this is about thinking time, not content |

**Step 3 — Define the delta for the retry**

Be specific about what the retry needs to show that the first attempt didn't.

Examples:
- "Redo Deliverable 2 with trade-offs that name a specific cost and a specific beneficiary. Generic trade-offs will not pass."
- "Re-draw your architecture map removing all implementation details. If a tool version or a table name appears, the map needs another pass."
- "Your reflection needs to answer: what did you believe about this system before that you no longer believe? Be specific."

**Step 4 — Set the timeline**

Retry window: next available ceremony, maximum 1 week out. The participant does not restart the module — they revise the specific deliverable(s) that scored below ACHIEVED.
