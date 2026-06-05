# Scoring Rubric — Module 04: Architect's Voice

**Minimum score to advance**: 70 / 100
**Critical threshold**: no dimension can be rated CRITICAL

> Module 04 introduces a new type of difficulty: communication under observation and pressure. The bar stays at 70 but the skills being measured are fundamentally different from M01–M03. Technical precision is still required — but so is clarity, adaptability, and composure.

---

## Evaluation Dimensions

| # | Dimension | Weight | What it evaluates |
|---|---|---|---|
| 1 | Audience Calibration | 25% | Do the two presentations feel genuinely different — vocabulary, frame, diagram, and ask — or is one just a shorter version of the other? |
| 2 | Abstraction Control | 20% | Can the participant move up and down the abstraction ladder fluidly during presentation and Q&A? |
| 3 | Trade-off Communication | 20% | Are trade-offs communicated accurately in both versions? Is the non-technical version honest — or were the costs sanitized out? |
| 4 | Composure Under Pressure | 20% | How does the participant handle the hot seat? Do they hold their position under challenge — without defensiveness or capitulation? |
| 5 | Diagram Effectiveness | 15% | Are the diagrams designed for their audience? Does each diagram answer one question clearly? |

**Total: 100%**

---

## Performance Levels by Dimension

### Dimension 1: Audience Calibration (25 pts)

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 25 pts | The two presentations use clearly different vocabulary, different diagrams, and different frames. The non-technical version opens with a business problem or outcome — not with the system. The technical version goes directly into constraints and decisions. The "ask" at the end of each version is appropriate to that audience (budget decision vs. design review). Switching between the two feels natural, not mechanical. |
| **ACHIEVED** | 19 pts | The two presentations are meaningfully different. The non-technical version may use one or two technical terms but recovers quickly or explains them in context. The frame is mostly right for each audience. The ask is present in at least one version. |
| **DEVELOPING** | 12 pts | The non-technical version is recognizably the technical version with some terms swapped or removed. The frame is still technical — it opens with the system, not the business outcome. Or both versions use the same diagram with a different title. |
| **CRITICAL** | 0 pts | Only one version was delivered, or the two versions are indistinguishable in vocabulary, frame, and diagram choice. No evidence of audience mapping. |

---

### Dimension 2: Abstraction Control (20 pts)

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 20 pts | The participant moves up and down the abstraction ladder deliberately and visibly. When a technical detail appears in the non-technical presentation, the participant connects it immediately to a business implication. When a business statement appears in the technical presentation, the participant backs it with a mechanism. During Q&A, the participant adjusts depth based on the question without losing the thread. |
| **ACHIEVED** | 15 pts | The participant operates at the right altitude for most of each presentation. May get pulled into implementation detail during the technical presentation without recovering, or may stay too high during a technical Q&A. Corrects when prompted. |
| **DEVELOPING** | 10 pts | The participant stays at one altitude for most of the presentation regardless of audience. Either explains everything at the technical level (including to non-technical stakeholders) or stays permanently at the business level (including to engineers who want depth). |
| **CRITICAL** | 0 pts | The participant cannot adjust abstraction level even when directly prompted by the facilitator. The two presentations are at the same altitude despite having different audiences. |

---

### Dimension 3: Trade-off Communication (20 pts)

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 20 pts | In both versions, at least one trade-off is communicated using the 4-sentence structure (gained / accepted / why / trigger). The non-technical version names the cost of the key decision in business terms — it is honest, not sanitized. The accepted risk from M02 appears in the non-technical version in language a VP would understand. |
| **ACHIEVED** | 15 pts | Trade-offs are present in both versions. At least one uses the 4-sentence structure. The non-technical version may soften the framing of a cost slightly ("this limits some future options" rather than "this locks us into Databricks for all Gold layer tables") but does not hide it entirely. |
| **DEVELOPING** | 10 pts | Trade-offs are present in the technical version but absent or hidden in the non-technical version. The non-technical version presents the design as the obviously correct answer with no costs. Or trade-offs are stated but not explained — the audience is told "there's a trade-off" without being told what it is. |
| **CRITICAL** | 0 pts | No trade-offs communicated in the non-technical version. The non-technical presentation is pure advocacy — only benefits, no costs. This is a different failure from M03's consequence honesty: here the cost was known but intentionally omitted for the audience. |

---

### Dimension 4: Composure Under Pressure (20 pts)

> **This dimension is evaluated on the hot seat segment only.** It cannot be assessed from submitted documents. The facilitator scores this live.

| Level | Score | Observable behavior during the hot seat |
|---|---|---|
| **EXEMPLARY** | 20 pts | The participant responds in under 90 seconds with a clear position. Acknowledges the VP's concern without dismissing it. Uses the 4-sentence structure or equivalent naturally. Holds the core recommendation intact. If the challenge reveals a genuine gap in the design, says "that's a valid concern — let me think about that and come back to you" rather than improvising an incorrect answer. Tone is confident without being arrogant. |
| **ACHIEVED** | 15 pts | The participant holds their position under the first challenge. May hedge slightly or use some technical vocabulary before catching themselves. The core recommendation remains intact. Response is within 90 seconds but may feel slightly mechanical (visibly using the 4-sentence structure rather than speaking naturally from it). |
| **DEVELOPING** | 10 pts | The participant either capitulates partially ("you're right, maybe we should reconsider...") without a new technical reason, or becomes defensive in a way that closes the conversation. The recommendation survives but the communication is notably worse under pressure than during the prepared presentation. |
| **CRITICAL** | 0 pts | The participant either abandons their recommendation entirely under social pressure (without a valid technical reason), or shuts down — says nothing meaningful, defers to "I'd need to check" on something they should know, or becomes openly defensive. A participant who significantly misrepresents the architecture under pressure to make it sound better also qualifies as CRITICAL. |

---

### Dimension 5: Diagram Effectiveness (15 pts)

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 15 pts | Two clearly different diagrams: a Level 1 (context) for the non-technical version showing the system and its relationships to people and systems only; a Level 2 (container) for the technical version showing components, flows, and boundaries. Each diagram answers exactly one question. The participant can explain any element when asked. No element is on either diagram that doesn't serve its communication purpose. |
| **ACHIEVED** | 11 pts | Two diagrams that are meaningfully different. The non-technical diagram may have one internal component visible but otherwise is at the right level. The technical diagram is a legitimate container diagram but may have one or two implementation-level details present (a specific tool version, a table name). Participant can explain diagram choices when asked. |
| **DEVELOPING** | 7 pts | The same diagram (or minor variations of it) used for both audiences. Or one of the diagrams is a pipeline diagram (boxes representing tasks, not components) rather than an architecture diagram. Or the diagram contains so much information that it cannot be read without the presenter's narration. |
| **CRITICAL** | 0 pts | No diagram submitted for one or both presentations. Or the diagram is an architecture map from M01/M02 copied without modification — showing no understanding that communication diagrams serve a different purpose than documentation diagrams. |

---

## Scoring Sheet (for facilitator use during ceremony)

| Dimension | Weight | Level | Score |
|---|---|---|---|
| 1. Audience Calibration | 25% | ________ | ___ / 25 |
| 2. Abstraction Control | 20% | ________ | ___ / 20 |
| 3. Trade-off Communication | 20% | ________ | ___ / 20 |
| 4. Composure Under Pressure | 20% | ________ | ___ / 20 |
| 5. Diagram Effectiveness | 15% | ________ | ___ / 15 |
| **TOTAL** | **100%** | — | **___ / 100** |

> Score Dimension 4 only after the hot seat is complete. Do not score it during the prepared presentations.

---

## Final Decision

| Condition | Decision |
|---|---|
| Score ≥ 70 AND no dimension is CRITICAL | ✅ **ADVANCES** to Module 05 |
| Score < 70 OR any dimension is CRITICAL | 🔁 **REINFORCES** — retry at next available ceremony |

> Note: a CRITICAL on Dimension 4 (Composure Under Pressure) is a hard block regardless of total score. Module 05 involves a full adversarial Q&A under higher stakes — a participant who shuts down or capitulates in the M04 hot seat is not ready for that environment.

---

## If REINFORCES: Next Steps

The facilitator must communicate the following in writing within 24 hours:

**Step 1 — Name the specific dimension(s) that need work**

| If the weak dimension is... | Direct them to... | What the retry must show |
|---|---|---|
| Audience Calibration | `material.md` Section 2 (audience mapping) | Two presentations with different vocabulary, frame, diagrams, and asks — not one shortened |
| Abstraction Control | `material.md` Section 1 (the abstraction ladder) | Evidence of deliberate altitude changes: at least one up-move and one down-move during the presentation |
| Trade-off Communication | `material.md` Section 3 (4-sentence trade-off) | At least one trade-off in the non-technical version using the full 4-sentence structure, including the cost |
| Composure Under Pressure | `material.md` Section 5 (defending under pressure) | A re-run of the hot seat with a different challenge — facilitator scores this at the retry ceremony |
| Diagram Effectiveness | `material.md` Section 4 (C4 levels) | Two diagrams at the right C4 level for each audience — Level 1 for non-technical, Level 2 for technical |

**Step 2 — For CRITICAL on Composure Under Pressure specifically**

The retry for this dimension requires a new hot seat, not new documents. The retry can happen at the next ceremony — the participant presents their existing presentations again and the hot seat is re-run with a different challenge.

Before the retry: recommend the participant practice the 4-sentence trade-off structure aloud, for every major decision in their NovaMart design, until it stops feeling like a structure and starts feeling like how they naturally talk about the work. The hot seat reveals whether the skill is internalized or performed — the only way to internalize it is to say it aloud many times before the pressure situation.
