# Scoring Rubric — Module 02: Design Under Constraints

**Minimum score to advance**: 65 / 100
**Critical threshold**: no dimension can be rated CRITICAL

> Module 02 raises the bar from M01. The participant is no longer reading a system — they are proposing one. The standard shifts accordingly: constraint awareness is now mandatory, not optional.

---

## Evaluation Dimensions

| # | Dimension | Weight | What it evaluates |
|---|---|---|---|
| 1 | Constraint Identification | 25% | Did the participant surface all relevant constraints, including hidden ones, before designing? |
| 2 | Option Comparison Rigor | 20% | Are both options genuinely viable? Are they compared against the same criteria without a straw man? |
| 3 | Recommendation Quality | 25% | Is the recommendation justified with constraints, not preferences? Does it name what was ruled out and why? |
| 4 | Trade-off Transparency | 20% | Does the participant honestly name the costs their recommended design accepts — including the accepted risk? |
| 5 | Design-for-Evolution Thinking | 10% | Does the recommended design explicitly defer things with documented triggers, not vague "Phase 2" promises? |

**Total: 100%**

---

## Performance Levels by Dimension

### Dimension 1: Constraint Identification (25 pts)

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 25 pts | The Constraint Canvas covers all six categories with specific, scenario-grounded content. At least one inferred constraint is present and named as inferred. The KEY TENSION names the single most important trade-off and is referenced throughout the design presentation. |
| **ACHIEVED** | 19 pts | The canvas is complete and mostly accurate. May miss one secondary constraint or conflate a nice-to-have with a must-have. The KEY TENSION is identified but may not be explicitly referenced when justifying design choices. |
| **DEVELOPING** | 12 pts | The canvas is partially filled. Focuses on obvious constraints (budget, timeline) while missing organizational or compliance constraints that are visible in the scenario. Does not distinguish must-haves from nice-to-haves. |
| **CRITICAL** | 0 pts | No constraint canvas, or a canvas so generic it could apply to any project. Design is proposed without prior constraint documentation. Participant cannot name the constraints that shaped their design when asked. |

---

### Dimension 2: Option Comparison Rigor (20 pts)

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 20 pts | Both options are genuinely viable designs, each with real strengths. The comparison table uses the same dimensions for both options. The participant proactively explains where Option B is actually stronger than Option A on specific dimensions — showing honest analysis. |
| **ACHIEVED** | 15 pts | Both options are viable. The comparison is structured and covers most relevant dimensions. May present Option B slightly less fully than Option A, but it's a real alternative, not a straw man. |
| **DEVELOPING** | 10 pts | Option B exists but is clearly a straw man (missing key components, obviously inferior on every dimension, or described vaguely). Or the comparison is unstructured — the participant argues for Option A without formally evaluating Option B. |
| **CRITICAL** | 0 pts | Only one option is presented, or Option B is so underdeveloped it cannot be evaluated. No comparative analysis. |

---

### Dimension 3: Recommendation Quality (25 pts)

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 25 pts | The recommendation opens by naming the constraint(s) that drove the decision. Names the specific constraint(s) that ruled out the alternative. Names at least one thing intentionally deferred with a concrete trigger. The participant can defend the recommendation without changing it under one round of Q&A pressure. |
| **ACHIEVED** | 19 pts | The recommendation is clear and references at least 2 constraints. May not explicitly name what ruled out the alternative — but can answer that question when asked. The deferral is present but the trigger is vague ("once we have more resources" is not a trigger — "once the team grows to 4 engineers" is). |
| **DEVELOPING** | 12 pts | The recommendation is made but justified with technical preference rather than constraints ("Option A is cleaner / more modern / better practice"). Or the recommendation is hedged ("either option could work") without a clear position. |
| **CRITICAL** | 0 pts | No recommendation is made, or the recommendation changes under the first Q&A question without a valid technical reason. |

---

### Dimension 4: Trade-off Transparency (20 pts)

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 20 pts | The participant names the single biggest risk in their recommended design and explains why they accepted it rather than mitigating it. They are direct about costs: "this design cannot support sub-hourly freshness without a replatform." No defensive framing of the downsides. |
| **ACHIEVED** | 15 pts | The accepted risk is named. The cost framing is mostly honest but may soften the language ("this might be a challenge for streaming use cases" vs. "this design cannot support streaming without replacing the ingestion layer"). |
| **DEVELOPING** | 10 pts | Trade-offs are acknowledged but minimized or buried. The accepted risk section describes something that was actually mitigated, not something genuinely accepted. Or the risks identified are trivial and don't reflect the real costs of the design. |
| **CRITICAL** | 0 pts | No trade-offs or risks acknowledged. The recommended design is presented as the best solution in all dimensions. "We can always add X later" without any documentation of what that means. |

---

### Dimension 5: Design-for-Evolution Thinking (10 pts)

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 10 pts | The presentation explicitly names 1–2 components that were deferred, with specific triggers (business condition, volume threshold, or team capacity change). The participant can explain what in the current design would be replaced vs. extended when the trigger is hit. |
| **ACHIEVED** | 7 pts | At least one deferral is documented with a trigger. The trigger is somewhat specific ("when we need real-time" is borderline — "when the product team requests sub-15-minute data freshness" is acceptable). |
| **DEVELOPING** | 4 pts | Deferrals are mentioned vaguely ("we'll add streaming in Phase 2") without triggers or without explaining how the current design accommodates the future addition. |
| **CRITICAL** | 0 pts | No phasing or deferral thinking. The design is presented as complete and final. Or the design attempts to solve every foreseeable future problem today without acknowledging the cost of that complexity. |

---

## Scoring Sheet (for facilitator use during ceremony)

| Dimension | Weight | Level | Score |
|---|---|---|---|
| 1. Constraint Identification | 25% | ________ | ___ / 25 |
| 2. Option Comparison Rigor | 20% | ________ | ___ / 20 |
| 3. Recommendation Quality | 25% | ________ | ___ / 25 |
| 4. Trade-off Transparency | 20% | ________ | ___ / 20 |
| 5. Design-for-Evolution Thinking | 10% | ________ | ___ / 10 |
| **TOTAL** | **100%** | — | **___ / 100** |

---

## Final Decision

| Condition | Decision |
|---|---|
| Score ≥ 65 AND no dimension is CRITICAL | ✅ **ADVANCES** to Module 03 |
| Score < 65 OR any dimension is CRITICAL | 🔁 **REINFORCES** — retry at next available ceremony |

---

## If REINFORCES: Next Steps

The facilitator must communicate the following in writing within 24 hours:

**Step 1 — Name the specific dimension(s) that need work**

| If the weak dimension is... | Direct them to... | What the retry must show |
|---|---|---|
| Constraint Identification | `material.md` Section 1 and 2 | A completed Constraint Canvas with at least one inferred constraint and a named KEY TENSION |
| Option Comparison Rigor | `material.md` Section 3 | A revised Option B that is a genuine alternative, evaluated on the same dimensions as Option A |
| Recommendation Quality | `material.md` Section 3 (Recommendation Quality block) | A recommendation that opens with a constraint, not a preference, and names what it rules out |
| Trade-off Transparency | `material.md` Section 4 | An accepted-risk statement that names a real cost, not a mitigated one |
| Design-for-Evolution | `material.md` Section 4 (three-question rule) | At least one deferred component with a specific trigger condition |

**Step 2 — Define the retry scope**

The participant does not redo the entire assignment. They revise the specific deliverable(s) that scored below ACHIEVED. Be explicit about which files to update.

**Step 3 — Set the timeline**

Retry window: next available ceremony, maximum 1 week. If the participant is struggling with the conceptual distinction between constraints and preferences, recommend a 30-minute 1:1 conversation before the retry — sometimes a single conversation unlocks what the material couldn't.
