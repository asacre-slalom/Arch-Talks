# Facilitator Guide — Module 04: Architect's Voice

## Purpose of This Module (Facilitator Perspective)

Module 04 is the first module where the primary observable behavior happens live — in the ceremony — rather than in submitted documents. The hot seat segment is the heart of the evaluation and cannot be replicated in writing.

Your job as facilitator is twofold:

1. **During the prepared presentations**: evaluate whether the two versions are genuinely different, or whether the participant performed audience adaptation without achieving it
2. **During the hot seat**: be a credible, challenging VP — pressure the participant enough to reveal whether the skill is internalized, without going so hard that the exercise becomes adversarial

The signal you are watching for throughout: **does this person communicate the architecture, or do they perform communication while presenting the architecture?**

The difference is visible. Communication means the audience is served — the technical audience understands the design well enough to act on it, and the non-technical audience understands the decision well enough to support it. Performance means the presentation looks like communication but doesn't actually serve either audience.

---

## Before the Ceremony

**48 hours before:**
- [ ] Review both submitted presentations per participant (15–20 min each)
- [ ] For each participant, identify:
  - One technical term in the non-technical presentation that shouldn't be there (use it in Q&A)
  - One trade-off that's present in the technical version but absent from the non-technical version (probe it)
  - One place where the diagram choice doesn't match the audience level
- [ ] Prepare your hot seat challenge for each participant (see below)
- [ ] Have the scoring sheet ready; Dimension 4 has a dedicated section for hot seat notes

**Day of:**
- [ ] Remind participants at the start: "The hot seat happens after the non-technical presentation. You'll have 90 seconds to respond to a VP challenge I'll give you. No prep, no notes."
- [ ] Set a visible timer — 10 min / 5 min / 90 sec respectively

---

## How to Run the Hot Seat

### Timing and transition

The hot seat starts immediately after the non-technical presentation ends — no pause, no recap. This is intentional: you want the participant still in non-technical mode when the challenge lands.

Say: "Okay. You've just presented this to the VP of Data. She has one concern before she'll approve the budget. Here it is: [challenge]."

Then wait. Do not prompt, clarify, or help. The 90 seconds starts when you finish speaking.

### Preparing your hot seat challenge

Pick one challenge from this list, or adapt to the specific design. Choose one that targets the most significant constraint or trade-off in their NovaMart recommendation — the one where capitulating would matter most.

**Challenge 1 — The cost challenge**
> "The $22K incremental spend is fine. But your team will spend the next 10 weeks building this instead of the Customer 360 project Marketing has been waiting for. Why is this the right priority?"

Tests: can they frame the opportunity cost argument (what they're getting is worth the delay), without dismissing Marketing's concern.

**Challenge 2 — The simplicity challenge**
> "I've seen these data platform projects before. They start simple and turn into 3-year migrations. Why won't this one?"

Tests: can they explain what makes this design bounded (phasing, deferred components, documented triggers), without over-promising.

**Challenge 3 — The risk challenge**
> "If this doesn't work — if in week 8 the dashboards are wrong or Finance can't use them — what happens? How do we recover?"

Tests: can they explain the rollback / recovery story (Bronze layer as safety net, existing SQL Server still running in parallel) without either minimizing the risk or catastrophizing it.

**Challenge 4 — The vendor challenge**
> "You're recommending we go deeper with Snowflake and Airflow. We're already talking to Databricks about a new contract. Should we wait?"

Tests: can they hold the recommendation (the platform is designed to be portable at the ingestion layer, ADR-002 documents this) without dismissing the procurement concern.

**Challenge 5 — The team challenge**
> "Your team has 2 data engineers. You're describing a platform that needs ongoing operations, data quality monitoring, and governance. Are 2 engineers enough to run this after it's built?"

Tests: can they address the operational sustainability concern honestly — naming what's been scoped out for Phase 1 and what the trigger for adding capacity is — without either falsely reassuring the VP or undermining the proposal.

### What you're evaluating during the 90 seconds

| Signal | What it means |
|---|---|
| Starts with a direct acknowledgment of the concern | Good — they're not dismissing the challenge |
| Uses business vocabulary, not technical terms | Good — they stayed in the right register under pressure |
| Holds the core recommendation | Good — they're not capitulating |
| Cites a specific constraint or decision | Good — the skill is internalized, not performed |
| Becomes visibly flustered or defensive | Concerning — pressure is revealing a gap |
| Changes the recommendation | Requires evaluation: was it for a good technical reason, or social pressure? |
| Says "I'd need to check on that" | Acceptable if genuinely uncertain; not acceptable for something they should know |
| Goes silent for more than 5 seconds | Score Dimension 4 as DEVELOPING or CRITICAL |

### After the 90 seconds

Acknowledge what worked, then ask one follow-up: "If I pushed back further and said the timeline still feels aggressive — what's the one thing that would make me more confident?" This gives you a second data point on composure and tests whether they have a reserve argument.

---

## What to Observe During the Prepared Presentations

### Dimension 1 — Audience Calibration

The clearest signal is the opening line of each presentation.

- **Non-technical version opening (strong)**: "Today Finance spends two days per week consolidating data manually. That ends in 10 weeks." → Opens with the audience's problem.
- **Non-technical version opening (weak)**: "I'm going to walk you through the proposed three-layer analytics architecture for NovaMart." → Opens with the system, not the audience.

Also watch: does the non-technical version end with a clear ask? A presentation without an ask is a briefing, not communication.

### Dimension 2 — Abstraction Control

Watch for the altitude drift during Q&A. The most common pattern: a technical question during the non-technical presentation pulls the participant down into implementation detail, and they don't come back up.

Listen for the recovery: after answering a technical detail, does the participant bridge back to business terms? "...and what that means for the Finance team is that restatements happen overnight without disrupting dashboard access."

### Dimension 3 — Trade-off Communication

Scan the submitted non-technical presentation for the word "trade-off" or equivalent framing. If it's absent, that's a signal — the trade-offs were likely sanitized.

During the ceremony, ask directly: "What's the main limitation of Phase 1 that a VP should know going in?" A participant who sanitized the trade-offs will have to answer this honestly in real time and the gap will become visible.

### Dimension 4 — Composure Under Pressure (hot seat)

Score this after the hot seat. Keep notes in real time — composure details are hard to reconstruct afterward.

Note specifically:
- How long before they gave a direct answer (< 5s = good, 5–10s = developing, > 10s = critical)
- Whether they acknowledged the concern before responding
- Whether the core recommendation survived intact
- Whether technical vocabulary crept back in under pressure

### Dimension 5 — Diagram Effectiveness

Check both diagrams before the ceremony. During the presentation, ask: "Tell me why you chose to show [specific element] in the non-technical diagram." If they can't answer — if the element is there because it was on the technical diagram and they forgot to remove it — it's a diagram carried over, not designed.

---

## Q&A Questions Bank

Use 2–3 per participant after the hot seat. These probe the prepared presentations, not the live segment.

**Q1 — The diagram challenge** *(Dimension 5)*
> "In your non-technical diagram you have [Snowflake / Airflow / dbt / specific component]. Why is that element there for a VP audience? What decision does knowing that help them make?"

Use when: a technical component appears in the Level 1 diagram. The right answer is either "you're right, it shouldn't be there" or a specific explanation of why that element is relevant to the business audience's decision. Either is acceptable — the important thing is that the participant has a reason.

---

**Q2 — The translation test** *(Dimension 1 and 2)*
> "In your technical presentation you said [specific technical phrase]. How would you say that same thing in your non-technical version?"

Use when: you want to test whether the audience calibration is internalized or performed. A participant who genuinely adapted will answer immediately and naturally. A participant who performed adaptation will struggle or produce a version that's still technical.

---

**Q3 — The missing trade-off** *(Dimension 3)*
> "In your non-technical version, I noticed you didn't mention [specific cost or limitation from the technical version]. Was that intentional?"

Use when: a real trade-off from the technical version is absent from the non-technical version. This question asks them to own the omission. Acceptable answer: "Yes — I judged that detail was below the VP's level of concern, and here's the version I would give if she asked." Unacceptable answer: "I didn't think it was important."

---

**Q4 — The audience flip** *(Dimension 2)*
> "A senior engineer on your team just walked in. They've been in a meeting and missed the technical presentation. Can you give them a one-minute version of the key architectural decision in your proposal?"

Use this as a live Dimension 2 test: can the participant shift altitude from non-technical mode (where they just were) back to technical mode, on demand?

---

**Q5 — The received feedback probe** *(Dimension 4)*
> "In the hot seat, I challenged you with [the challenge you gave them]. After thinking about it — was your 90-second response the best response you could have given? What would you change?"

Use after the hot seat to test self-awareness. A participant with genuine composure can reflect on their performance without either dismissing the challenge ("I think I handled it fine") or catastrophizing ("I completely failed"). This also shows the facilitator whether the participant learned from the pressure moment.

---

**Q6 — The diagram-free test** *(All dimensions)*
> "If I took all your slides away right now — no diagrams, no documents — can you explain your NovaMart recommendation in 2 minutes to me, as a VP?"

Use at the end, for any participant. This is the ultimate test: does the communication live in the material, or in the architect? A participant who has genuinely internalized the work will answer this fluently. One who relied on the slides to carry the message will struggle.

---

## Handling the Most Common M04 Error: Simplification vs. Elevation

Roughly 50–60% of first-time non-technical presentations are not elevated — they are simplified. The participant removes technical content until what remains is too vague to be useful, and calls that "making it accessible."

The result typically sounds like: "We're building a data platform that will give the business better access to their data in a more reliable and scalable way."

This communicates nothing. It could describe any data project. It tells the VP nothing about the decision that was made, the constraints that shaped it, or the trade-offs that were accepted.

**How to identify it during the ceremony:**
- The non-technical presentation has fewer than 3 factual claims
- No specific numbers appear (cost, timeline, freshness SLA, team size)
- No trade-off is named
- The ask at the end is missing or vague ("your support is appreciated")

**How to address it in Q&A:**
Ask Q3 (the missing trade-off): "What's the main limitation of Phase 1 that a VP should know?" If they answer with something specific, they had the knowledge but omitted it — that's a calibration error. If they can't answer specifically, they may not have understood the architecture well enough to elevate it — that's a deeper gap.

**In feedback**: "Your non-technical presentation removed the architectural reasoning along with the jargon. The goal is to raise the altitude, not to reduce the content. A VP needs to understand what the decision costs and why it was worth it — in business terms. That understanding is missing from your non-technical version. For your retry, use the 4-sentence trade-off structure for the two most important decisions in your design, and include specific numbers (timeline, cost, what changes for each team)."

---

## A Note on Ceremony Pacing With Multiple Participants

M04 is the most time-intensive ceremony in the program. Each participant uses ~20 minutes (10 + 5 + hot seat + Q&A). Limit to 2 participants per ceremony — 3 is possible with strict time management but creates pressure that affects the hot seat quality.

Suggested ceremony format with 2 participants:
- 0:00 – 20:00 — Participant 1 full session
- 20:00 – 40:00 — Participant 2 full session
- 40:00 – 50:00 — Group feedback and patterns from both sessions
- 50:00 – 60:00 — Buffer / overflow / Q&A

The 10-minute buffer is not optional. Hot seat discussions often generate follow-on conversation that is valuable to the whole group.

---

## Closing the Ceremony

After all M04 sessions:

1. Name the single most effective thing you saw across the group — a specific moment where communication worked, without attributing it unless the group is small and comfortable
2. Name the most common gap — typically the simplification vs. elevation problem or the trade-offs disappearing in the non-technical version
3. Transition to M05: "In the next module, everything you practiced here is the baseline — you'll be building and defending a complete proposal from scratch, with adversarial Q&A from a panel. Your architecture maps from M01, your constraint canvases from M02, your ADRs from M03, and the communication skills from this module all come together there."
