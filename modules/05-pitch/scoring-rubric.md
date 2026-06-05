# Scoring Rubric — Module 05: Full Architecture Pitch

**Minimum score to advance**: 75 / 100
**Critical threshold**: no dimension can be rated CRITICAL

> Module 05 is the program's capstone. The threshold rises to 75 because the skills being measured are integrative — a participant who passes needs to demonstrate M01 through M04 competencies simultaneously, plus the new adversarial resilience skill. Reaching 75 means all five dimensions are performing at or above ACHIEVED level.

---

## Evaluation Dimensions

| # | Dimension | Weight | What it evaluates |
|---|---|---|---|
| 1 | Proposal Completeness | 20% | Are all six required sections present, substantive, and honest? Is the proposal self-contained — usable without oral explanation? |
| 2 | Design Coherence | 25% | Do the current state assessment, proposed architecture, ADRs, and roadmap tell a consistent story? Do the ADRs explain the design, or are they disconnected appendices? |
| 3 | Adversarial Resilience | 25% | Does the participant defend decisions with constraint-grounded logic under 5 minutes of sustained pressure? Does the core recommendation survive intact unless a legitimate technical gap is revealed? |
| 4 | Roadmap Realism | 15% | Is Phase 1 actually deliverable by the team described in the scenario? Are the trigger conditions for Phase 2 specific and testable? |
| 5 | Integration of Prior Modules | 15% | Are M01–M04 skills explicitly visible in the proposal? Is the current state framed architecturally (M01)? Is the design constraint-driven (M02)? Do the ADRs have honest consequences (M03)? Is the executive summary audience-calibrated (M04)? |

**Total: 100%**

---

## Performance Levels by Dimension

### Dimension 1: Proposal Completeness (20 pts)

| Level | Score | Observable behavior |
|---|---|---|
| **EXEMPLARY** | 20 pts | All six sections are present and substantive. The risk register includes the GDPR compliance risk and the ThreadCo IT dependency as distinct entries with specific responses. Both ADRs follow the complete M03 structure with non-trivial negative consequences. The executive summary is one page, uses no technical terms, and ends with a specific ask. The proposal could be handed to a new engineer to begin Phase 1 without a briefing meeting. |
| **ACHIEVED** | 15 pts | All six sections are present. One or two are thinner than ideal (e.g., the risk register has 3 of the required 4 risk types, or Phase 2 trigger conditions are present but slightly vague). Both ADRs exist with the required structure, though one negative consequence section may be understated. Executive summary is present and mostly non-technical. |
| **DEVELOPING** | 10 pts | One or more sections are missing or present as placeholder text. Common gaps: risk register exists but contains only generic risks ("project may be delayed"), or Phase 2 is described with a date rather than a trigger condition, or one ADR is missing the negative consequences section. |
| **CRITICAL** | 0 pts | More than two sections are missing. Or the proposal is a design document rather than a pitch — it describes the architecture without making a business case, documenting decisions, or specifying a roadmap. Or the GDPR requirement is entirely absent from the proposal. |

---

### Dimension 2: Design Coherence (25 pts)

| Level | Score | Observable behavior |
|---|---|---|
| **EXEMPLARY** | 25 pts | The current state assessment identifies the specific problems the proposed design solves — a reader can trace each proposed component back to a diagnosed problem. The ADRs explain decisions that are visible in the architecture diagram. The roadmap's Phase 1 scope matches the team's capacity and the budget. The design explicitly routes around the ThreadCo IT 4–6 week lead time — it does not assume on-demand access to Oracle. The timezone issue (UTC vs. US/Eastern) is addressed explicitly in the design or an ADR. |
| **ACHIEVED** | 19 pts | The proposal tells a mostly consistent story. The current state connects to the proposed design. ADRs cover the most significant decisions. The roadmap is plausible. One coherence gap is present but not critical (e.g., a component in the architecture diagram is not referenced in the ADRs, or the Phase 1 timeline is slightly optimistic for the team size). |
| **DEVELOPING** | 12 pts | The proposal has significant internal inconsistencies. Common examples: the architecture diagram includes a streaming component but the VP of Data's explicit constraint rules it out; Phase 1 deliverables exceed what 3 data engineers could build in the stated timeline; ADRs cover decisions that aren't in the architecture, or the most consequential decisions (GDPR handling, multi-cloud topology) have no ADR. |
| **CRITICAL** | 0 pts | The proposal is internally incoherent — the sections contradict each other. Or the design ignores the most significant constraint in the scenario (GDPR, the multi-cloud reality, the ThreadCo IT dependency). |

---

### Dimension 3: Adversarial Resilience (25 pts)

> **This is the most important dimension in Module 05** and the hardest to score from submitted documents alone. Dimension 3 is scored primarily from the 5-minute adversarial Q&A — the facilitator must take notes in real time.

| Level | Score | Observable behavior during adversarial Q&A |
|---|---|---|
| **EXEMPLARY** | 25 pts | The participant correctly identifies the type of challenge (technical / political / confusion) and responds differently to each. Core recommendation survives all 5 minutes intact. When a challenge reveals a genuine gap, the participant names the gap, states what would change, and asks a clarifying question to determine if it's a hard requirement — rather than either dismissing or over-capitulating. Tone stays confident without becoming combative. Uses the anchor technique: returns to the core recommendation after each challenge. |
| **ACHIEVED** | 19 pts | The participant holds their position under most challenges. May capitulate slightly on one point under pressure (softens the language of a cost rather than defending it). Core recommendation survives. Distinguishes genuine technical concerns from political objections at least 2 of 3 times when asked. Tone may become slightly defensive under the hardest challenge but recovers. |
| **DEVELOPING** | 12 pts | The participant begins to hedge under sustained pressure — "it might depend," "we could reconsider," "you raise a fair point, maybe we should..." without a technical reason for the change. The core recommendation is weakened or blurred by the end of the 5 minutes. Or the participant becomes noticeably defensive rather than engaging with the substance of challenges. |
| **CRITICAL** | 0 pts | The participant abandons the core recommendation under social pressure without a legitimate technical reason. Or becomes openly defensive and stops engaging with challenges substantively. Or significantly misrepresents the design to make it sound better under pressure. This is the capstone module — a participant who cannot defend their own proposal under 5 minutes of pressure is not ready for architect-level work. |

---

### Dimension 4: Roadmap Realism (15 pts)

| Level | Score | Observable behavior |
|---|---|---|
| **EXEMPLARY** | 15 pts | Phase 1 scope is deliverable by 3 data engineers + 1 analytics engineer in the stated timeline, accounting for the ThreadCo IT 4–6 week lead time (meaning ThreadCo integration is either excluded from Phase 1 or explicitly scoped after the approval window). Phase 1 has 2–3 intermediate milestones. Definition of done is specific (e.g., "Finance closes Q3 books from the dashboard"). Phase 2 trigger conditions are testable (a condition, not a date). The Phase 1 design includes the architectural hook that enables Phase 2. |
| **ACHIEVED** | 11 pts | Phase 1 is plausible for the team size. Timeline may be slightly optimistic but defensible. ThreadCo integration is present in Phase 1 but scoped conservatively (e.g., read-only from the Azure SQL warehouse rather than direct Oracle access). Phase 2 trigger is present but may be somewhat vague. Definition of done is present. |
| **DEVELOPING** | 7 pts | Phase 1 includes scope that is not achievable by the given team in the given time. Common examples: Phase 1 includes a real-time streaming component (explicitly ruled out by the VP), or ThreadCo Oracle direct integration in week 2 (ignoring the 4–6 week IT lead time), or 6 major components for a 3-engineer team in 10 weeks. Phase 2 trigger is a date ("Q2 next year") rather than a condition. |
| **CRITICAL** | 0 pts | No roadmap, or the roadmap is a single-phase "big bang" delivery with no phasing. Or Phase 1 requires resources, team skills, or timeline that are explicitly not available in the scenario. |

---

### Dimension 5: Integration of Prior Modules (15 pts)

| Level | Score | Observable behavior |
|---|---|---|
| **EXEMPLARY** | 15 pts | M01 is visible: current state is framed as a set of implicit decisions and their trade-offs — not just a list of tools. M02 is visible: the proposed design is explicitly shaped by the constraint canvas — specific constraints are named when justifying design choices. M03 is visible: both ADRs have honest negative consequences and the decision threshold was applied (only architectural decisions have ADRs). M04 is visible: the executive summary is demonstrably different from the technical sections — different vocabulary, different frame, specific ask. |
| **ACHIEVED** | 11 pts | Three of four prior modules are clearly visible. One is present but weaker: e.g., the executive summary exists but still contains technical terms, or the current state is described factually rather than architecturally, or one ADR has thin negative consequences. |
| **DEVELOPING** | 7 pts | One or two modules are visible; the others are absent or surface-level. A common pattern: technically strong proposal with good ADRs (M03) and good design (M02) but no architectural framing of the current state (M01) and an executive summary that is just the introduction section copied with some terms removed (M04). |
| **CRITICAL** | 0 pts | The proposal shows no evidence of M01–M04 skills. It is a stand-alone technical design document with no constraint framing, no ADRs, no architectural current state, and no audience calibration. |

---

## Scoring Sheet (for facilitator use during ceremony)

| Dimension | Weight | Level | Score |
|---|---|---|---|
| 1. Proposal Completeness | 20% | ________ | ___ / 20 |
| 2. Design Coherence | 25% | ________ | ___ / 25 |
| 3. Adversarial Resilience | 25% | ________ | ___ / 25 |
| 4. Roadmap Realism | 15% | ________ | ___ / 15 |
| 5. Integration of Prior Modules | 15% | ________ | ___ / 15 |
| **TOTAL** | **100%** | — | **___ / 100** |

> Score Dimension 3 during and immediately after the adversarial Q&A. Do not reconstruct it from memory later.

---

## Final Decision

| Condition | Decision |
|---|---|
| Score ≥ 75 AND no dimension is CRITICAL | ✅ **COMPLETES** the DataArch-Speak program |
| Score < 75 OR any dimension is CRITICAL | 🔁 **REINFORCES** — retry at next available ceremony |

> A participant who COMPLETES Module 05 has demonstrated all five capabilities of the DataArch-Speak program under integration and pressure. This is a significant achievement — treat it as one.

---

## If REINFORCES: Next Steps

Module 05 retry guidance must be honest about what the retry requires — this is the hardest module and a retry is substantial work.

**Step 1 — Triage the gap**

| If the weak dimension is... | What the retry requires |
|---|---|
| Proposal Completeness | Rebuild the missing or thin sections — the retry is a revised full proposal |
| Design Coherence | The architecture, ADRs, and roadmap need to be reconciled — this is usually a significant revision, not a patch |
| Adversarial Resilience | A new ceremony with a new set of adversarial challenges; the proposal may not need revision if the gap was purely in live performance |
| Roadmap Realism | Phase 1 scope must be renegotiated against the actual team capacity — the retry proposal will have a different scope |
| Integration of Prior Modules | The weakest module skill needs to be made visible in the proposal — usually this means rewriting the current state (M01) or the executive summary (M04) |

**Step 2 — Set expectations honestly**

A Module 05 retry is typically 4–8 hours of revision work, not 1–2 hours of polishing. Be direct about this. If a participant scored DEVELOPING or CRITICAL in multiple dimensions, discuss with them whether a partial retry (one ceremony) is realistic or whether they would benefit from revisiting a prior module first.

**Step 3 — CRITICAL on Adversarial Resilience specifically**

This is the hardest feedback to give and the most important. Say directly:

"The core skill of Module 05 is defending your proposal under pressure. In the adversarial Q&A, you [describe what happened: capitulated / became defensive / abandoned the recommendation]. This is the behavior the program has been building toward the ability to change. Before your retry, I'd recommend two things: (1) re-read Section 3 of `material.md` on adversarial question types, and (2) practice the anchor technique — write your core recommendation in one sentence, and practice returning to it after every challenge, in front of a peer who agrees to push back hard."
