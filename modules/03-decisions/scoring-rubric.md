# Scoring Rubric — Module 03: Architecture Decision Records

**Minimum score to advance**: 70 / 100
**Critical threshold**: no dimension can be rated CRITICAL

> Module 03 raises the bar from M02. The participant is no longer proposing — they are documenting reasoning with enough precision that a future stranger can make informed decisions from it. The threshold increases because rigor is now the central skill, not just awareness.

---

## Evaluation Dimensions

| # | Dimension | Weight | What it evaluates |
|---|---|---|---|
| 1 | ADR Structure Completeness | 20% | Are all required sections present and substantively filled? Is the ADR usable as written, without oral explanation? |
| 2 | Context Clarity | 20% | Does the Context section give a complete, neutral picture of the situation? Could a reader with no prior knowledge understand the problem? |
| 3 | Options Coverage | 25% | Are the options considered genuinely viable alternatives, each treated with equal rigor? Is at least one non-obvious option included? |
| 4 | Consequence Honesty | 25% | Does the Consequences section include real, specific negative outcomes? Does the participant acknowledge what the decision costs, not just what it gains? |
| 5 | Review Quality | 10% | Does the weak ADR feedback identify specific, evidence-backed gaps — not vague suggestions? |

**Total: 100%**

---

## Performance Levels by Dimension

### Dimension 1: ADR Structure Completeness (20 pts)

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 20 pts | Both ADRs have all required sections filled with substantive content. Status, Date, and Deciders are present. The follow-on decisions section names at least one downstream decision triggered by each ADR. The participant can explain any section without referring back to notes. |
| **ACHIEVED** | 15 pts | All required sections are present. One or two sections are thinner than ideal (e.g., Decision Drivers lists broad categories rather than specific factors) but the ADR is functional as a standalone record. The retroactive ADR is correctly labeled as reconstructed. |
| **DEVELOPING** | 10 pts | One or more required sections are missing or present only as placeholder text ("TBD", "N/A", "none identified"). The ADR requires the author's oral explanation to be useful — it cannot stand alone. |
| **CRITICAL** | 0 pts | The submitted documents are not ADRs — they are design documents, meeting notes, or technical write-ups that don't follow the ADR structure. Or only one ADR was submitted. |

---

### Dimension 2: Context Clarity (20 pts)

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 20 pts | The Context section reads neutrally — it describes the situation without pre-arguing for the eventual decision. A reader with no prior knowledge of the system or organization would understand the problem completely. The retroactive ADR shows evidence of research or reasoning to reconstruct context that wasn't documented at the time. |
| **ACHIEVED** | 15 pts | Context is mostly clear and mostly neutral. May have one sentence that hints at the conclusion ("we needed a more robust solution" pre-argues for replacing the current system). Sufficient for a knowledgeable reader; may leave gaps for a complete newcomer. |
| **DEVELOPING** | 10 pts | Context is either too brief (one or two sentences that don't explain the situation), or it pre-argues for the decision throughout ("since the current system was clearly inadequate..."). The problem cannot be understood without asking the author. |
| **CRITICAL** | 0 pts | The Context section is missing, is a copy-paste of the problem statement with no synthesis, or is entirely advocacy rather than description. |

---

### Dimension 3: Options Coverage (25 pts)

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 25 pts | Both ADRs include at least 2 options with balanced pros and cons. At least one option in each ADR is non-obvious (not just "use Tool A vs. Tool B" — includes an option like "don't build this / solve with a different approach"). Options that were rejected have specific, evidence-backed reasons, not vague dismissals. No straw men. |
| **ACHIEVED** | 19 pts | Options are present and mostly balanced. The non-chosen option(s) are genuine alternatives. Rejection reasons are present but may be thin ("Option B has less community support" without citing what that means in practice). One option per ADR may feel slightly weaker than the others but is not a straw man. |
| **DEVELOPING** | 12 pts | One or more options is a straw man — described so briefly or negatively that it could not plausibly have been chosen. Or all options have the same cons, making comparison meaningless. Or the participant lists only one option (the chosen one) with no alternatives. |
| **CRITICAL** | 0 pts | No options considered section, or all options listed are variants of the same approach. The ADR records a decision without showing it was a decision — it appears as the only path considered. |

---

### Dimension 4: Consequence Honesty (25 pts)

> **This is the most important dimension in Module 03.** An ADR that lists only positive consequences is not an ADR — it is advocacy written after the fact. The CRITICAL level for this dimension reflects that a fundamentally dishonest ADR fails the purpose of the exercise regardless of other quality.

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 25 pts | Both ADRs list at least 2 specific negative consequences — real costs, not trivial inconveniences. The negative consequences are proportional to the significance of the decision (a decision affecting 5 years of data architecture has more than "minor operational overhead" as its downside). Risks are named specifically, not generically. Follow-on decisions show the participant has thought about what this decision opens or closes. |
| **ACHIEVED** | 19 pts | Both ADRs include negative consequences. At least one is specific and honest. The second may be softer or more generic ("increases operational complexity" without explaining what that means in practice). Follow-on decisions may be thin or absent in one ADR. |
| **DEVELOPING** | 12 pts | One ADR has real negative consequences; the other has vague or trivial ones ("requires monitoring" as the only negative for a major architectural choice). Or negatives are present but framed as temporary or easily mitigated, understating the real cost. |
| **CRITICAL** | 0 pts | Either ADR has no negative consequences, or the negative section contains only trivial items that do not reflect the real cost of the decision. "None identified at this time" when real, known consequences exist is a CRITICAL failure for this dimension. An ADR without honest negative consequences is advocacy — it is not fit for purpose. |

---

### Dimension 5: Review Quality (10 pts)

| Level | Score | Observable behavior during the presentation |
|---|---|---|
| **EXEMPLARY** | 10 pts | The review identifies all major structural gaps with specific references to sections and line content. Names at least 2 factual or logical problems with specific evidence (e.g., "The claim that Prefect has 'limited community support' is unsupported — Prefect has 9,000+ GitHub stars and active enterprise support"). Writes a substantive Consequences → Negative section that reflects real Airflow trade-offs. Feedback is written as if to a colleague — direct, specific, and actionable. |
| **ACHIEVED** | 7 pts | The review identifies the most critical gaps (missing negatives, straw man for Prefect, vague decision drivers). At least one factual problem is named. The written Consequences → Negative section is present and includes at least 2 real Airflow trade-offs. Feedback is specific but may miss some secondary gaps. |
| **DEVELOPING** | 4 pts | The review identifies problems generally ("the options section needs more detail") without citing specific evidence. The Consequences → Negative section is missing or too brief. The feedback could have been written by someone who skimmed the ADR rather than read it carefully. |
| **CRITICAL** | 0 pts | No review submitted, or the review is positive ("this is a good ADR") when the ADR has clear structural and honesty failures. |

---

## Scoring Sheet (for facilitator use during ceremony)

| Dimension | Weight | Level | Score |
|---|---|---|---|
| 1. ADR Structure Completeness | 20% | ________ | ___ / 20 |
| 2. Context Clarity | 20% | ________ | ___ / 20 |
| 3. Options Coverage | 25% | ________ | ___ / 25 |
| 4. Consequence Honesty | 25% | ________ | ___ / 25 |
| 5. Review Quality | 10% | ________ | ___ / 10 |
| **TOTAL** | **100%** | — | **___ / 100** |

---

## Final Decision

| Condition | Decision |
|---|---|
| Score ≥ 70 AND no dimension is CRITICAL | ✅ **ADVANCES** to Module 04 |
| Score < 70 OR any dimension is CRITICAL | 🔁 **REINFORCES** — retry at next available ceremony |

> Note: a CRITICAL on Dimension 4 (Consequence Honesty) is a hard block regardless of total score. An ADR that presents only positives cannot pass Module 03 — the skill being assessed is honest documentation, and an ADR without negative consequences fails that test unconditionally.

---

## If REINFORCES: Next Steps

The facilitator must communicate the following in writing within 24 hours:

**Step 1 — Name the specific dimension(s) that need work**

| If the weak dimension is... | Direct them to... | What the retry must show |
|---|---|---|
| ADR Structure Completeness | `material.md` Section 2 (structure template) | All sections present and substantively filled in both ADRs |
| Context Clarity | `material.md` Section 2 (Context guidance) | A context section written as neutral description, not pre-argument; a stranger can understand the situation |
| Options Coverage | `material.md` Section 4 (ADR examples) | At least 2 options per ADR with equal rigor; rejection reasons cite evidence |
| Consequence Honesty | `material.md` Section 4 (see negative consequences in both example ADRs) | At least 2 real, specific negative consequences per ADR that are proportional to the decision's significance |
| Review Quality | `material.md` Section 5 (how to write feedback) | Each feedback item cites a specific section or claim; at least one rewrites a section as it should appear |

**Step 2 — Define the retry scope**

Be explicit: the participant revises the specific ADR(s) or review document that scored below ACHIEVED. They do not rewrite everything.

**Step 3 — For CRITICAL on Consequence Honesty specifically**

Say directly: "Your [ADR-001 / ADR-002] has no real negative consequences documented. This is the core skill of Module 03. Before your retry, read Section 4 of `material.md` and find the negative consequence sections of both example ADRs. Then ask yourself: what did the decision I documented actually cost the team? What does it make harder today? Those are the negative consequences. They must appear in your ADR."
