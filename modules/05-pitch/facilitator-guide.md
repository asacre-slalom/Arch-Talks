# Facilitator Guide — Module 05: Full Architecture Pitch

## Purpose of This Module (Facilitator Perspective)

Module 05 is the integration test. You are not evaluating any single skill — you are evaluating whether the participant can operate as a data architect under professional conditions: producing complete work, presenting it coherently, and defending it under pressure.

Your role in this ceremony is different from all prior modules. You are not a neutral evaluator facilitating a discussion. For 5 minutes, you are a skeptical VP of Engineering who has organizational history with failed data projects, a budget constraint, and genuine technical objections. That role must be played convincingly — a facilitator who pulls punches in the adversarial Q&A deprives the participant of the validation the module is designed to provide.

The question you are answering throughout: **does this person perform like a data architect, or like a data engineer presenting a very detailed design?**

The difference is visible in how they handle pressure, how they talk about risk, how they respond to the first challenge that doesn't have a clean technical answer, and whether the proposal exists to get a decision or to show how much they know.

---

## Before the Ceremony

**72 hours before (more than prior modules — this ceremony requires more prep):**
- [ ] Read the full submitted proposal (30–40 min) — this is a real proposal, not a short assignment
- [ ] Read both ADRs in full
- [ ] Read the executive summary and note: are there technical terms? Is the ask explicit?
- [ ] Identify the 2–3 weakest points in the proposal — these become your adversarial targets
- [ ] Select your 5 adversarial challenges from the list below (or adapt them to the specific proposal)
- [ ] Prepare the sequence: the adversarial Q&A should escalate — start with a technical challenge, move to a political one, end with the hardest
- [ ] Have the scoring sheet ready with Dimension 3 as a separate notepad for real-time notes

**Day of:**
- [ ] Brief the audience (other participants): "Today's ceremony includes a 5-minute adversarial Q&A. I'll be playing the role of a skeptical VP. The rest of you should watch and learn — you'll be in this position next."
- [ ] Set a visible timer for each segment: 12 / 5 / 3

---

## How to Prepare and Run the Adversarial Q&A

### The setup

Immediately after the 12-minute presentation ends, without a pause, say:

> "Thank you. I have some questions as the VP of Engineering — and I want to be direct with you. I've seen three data platform initiatives in the last five years. None of them delivered what they promised. I'm going to ask you to help me understand why this one is different."

Then go directly into your first challenge. The transition without a pause is intentional — you want the participant to go from presentation mode to defense mode without a reset.

### How hard to push

There is a calibration question here that matters. The adversarial Q&A should feel like a real executive conversation — real pressure, real stakes, real challenges. It should not feel like a gotcha exercise or an attempt to make the participant fail.

The right calibration: **push until they push back.** A participant who has internalized the skills will push back — will defend their position, acknowledge the concern, and return to the recommendation. A participant who hasn't will either collapse (capitulate without a reason) or harden defensively. Your pressure reveals which.

Specific calibration notes:
- **First challenge**: medium pressure. A challenge that has a clear constraint-based answer.
- **Second challenge**: higher pressure. A political objection that requires acknowledging organizational history.
- **Third challenge (if time)**: the hardest. A challenge that either reveals a genuine gap in the proposal or requires the participant to hold a position against sustained skepticism.

If a participant gives a genuinely strong answer to the first two challenges, acknowledge it briefly and escalate. If a participant collapses on the first challenge, you have the information you need — don't pile on. Shift to a softer challenge and close the segment.

### When to stop

Stop at 5 minutes. Even if the session is going well. Even if you have more challenges ready. The time limit is part of the test.

If a participant is struggling significantly, you may pause at 3 minutes and say: "Let me try one more. This is your most important decision in the proposal — walk me through it one more time as if you're talking to someone who is skeptical." This gives them a chance to reset, which reveals whether the skill is there and needs to be unlocked, or whether it isn't there yet.

---

## Six Adversarial Challenges

These are designed for the UrbanBasket scenario. Each targets a different dimension or constraint. Choose based on the specific weaknesses you identified in the submitted proposal.

---

**Challenge 1 — The CTO's history** *(targets: Adversarial Resilience + Proposal Completeness)*
> "You mentioned this is a 12-week Phase 1. I approved a data lake initiative in 2020 that was supposed to take 6 months and ran for 14 months before we pulled the plug. You're asking me to trust a data platform timeline again. What specifically makes this proposal different from that one?"

**What you're testing**: can they distinguish this proposal from the past failure using structural evidence from the proposal itself — phased delivery, specific definition of done, bounded scope? Or do they just say "this time we'll do it right"?

**A strong answer includes**: reference to the Phase 1 definition of done (Finance closes books from dashboard), the explicit scope exclusions (no real-time, no Customer 360 in Phase 1), and at least one mechanism that bounds the timeline (e.g., the 4-week IT approval window forces a specific integration sequencing).

---

**Challenge 2 — The cost challenge** *(targets: Adversarial Resilience + Design Coherence)*
> "Your Phase 1 costs $75K in new cloud infrastructure, plus 3 data engineers for 12 weeks. That's approximately $200K in fully loaded team cost. For $275K, I need to understand exactly what UrbanBasket gets that it doesn't have today."

**What you're testing**: can they translate the architecture into specific business outcomes — not "a unified data platform" but "Finance eliminates 2 days/week of manual reconciliation and the Q4 revenue discrepancy between UrbanBasket and ThreadCo is resolved"?

**A strong answer includes**: specific current-state costs that the proposal eliminates (the $280K inventory discrepancy required 6 weeks to trace; the $275K investment pays for itself if it prevents one such incident), and specific deliverables that each business team gets.

---

**Challenge 3 — The GDPR gap** *(targets: Design Coherence + Proposal Completeness)*
> "You say GDPR is handled in the Bronze layer. Legal told me last week that we need to be able to delete a customer's data within 72 hours across every system — not just the warehouse. How does your architecture guarantee that?"

**What you're testing**: did they actually think through the GDPR constraint at the system level, or did they add "GDPR compliant" to the design without architectural specificity?

**A strong answer includes**: a description of the deletion workflow (deletion request triggers a process that propagates to Bronze, Silver, and Gold — probably via a deletion log or soft-delete pattern), acknowledgment that the operational systems (Shopify, Klaviyo) have their own GDPR mechanisms outside the data platform, and honest acknowledgment if this was not fully worked out ("this is a design decision that deserves its own ADR — I have the high-level approach but the implementation detail is a Phase 1 spike").

---

**Challenge 4 — The ThreadCo IT relationship** *(targets: Roadmap Realism + Adversarial Resilience)*
> "The ThreadCo IT team has told me they're not comfortable with the data team accessing the Oracle system directly. They're worried about performance impact. You've scoped ThreadCo integration into Phase 1. How does that work if they say no?"

**What you're testing**: did the participant account for the 4–6 week IT lead time and the territorial IT team in the roadmap? Or did they assume smooth access?

**A strong answer includes**: acknowledgment that the ThreadCo IT dependency is in the risk register, description of the integration approach that doesn't require direct Oracle access (read-only replica or scheduled export to SFTP), and a contingency: "If ThreadCo IT says no to the replica, Phase 1 excludes ThreadCo order data from the unified view, and we document this as a known gap. The Finance reconciliation problem still gets 80% solved with UrbanBasket data alone."

---

**Challenge 5 — The Marketing team** *(targets: Adversarial Resilience + Proposal Completeness)*
> "Marketing has been waiting for Customer 360 for two years. Your proposal puts it in Phase 2 again. They're going to see this and feel like they've been lied to again. How do you talk to them about this?"

**What you're testing**: can they handle a political objection with empathy and honesty — acknowledging the team's frustration without making a promise the architecture can't keep?

**A strong answer includes**: acknowledgment of the history ("Marketing has been told Phase 2 before — I understand the skepticism"), an explanation of why Phase 2 isn't Phase 1 that references a specific constraint (the ThreadCo data quality error rate makes a reliable Customer 360 impossible until it's resolved), and a specific trigger that Marketing can hold the data team accountable to: "Phase 2 starts when the ThreadCo error rate drops below 2%. Here's how Marketing can track that."

---

**Challenge 6 — The "over-engineered" challenge** *(targets: Adversarial Resilience — hardest)*
> "I've been looking at this proposal and I think it's over-engineered. You have Bronze, Silver, Gold layers, two ADRs, a risk register, a phased roadmap. What if I told you we just need Fivetran into Snowflake and Tableau on top? Done in 4 weeks, costs $20K. What's wrong with that?"

**What you're testing**: this is the most direct challenge to the proposal's existence. Can the participant hold their recommendation against a simpler-sounding alternative without being dismissive or defensive?

**A strong answer includes**: acknowledgment that a Fivetran → Snowflake → Tableau stack would solve the immediate BI problem, then a specific explanation of what it doesn't solve (GDPR deletion workflow requires layer separation; the ThreadCo timestamp issue requires transformation logic; the $280K inventory discrepancy requires reconciliation logic that Tableau can't do), and a fair concession: "If the only requirement was Finance dashboards for UrbanBasket data only, the simpler approach would work. The full set of requirements — multi-brand reconciliation, GDPR compliance, ThreadCo integration — is what drives the layers."

---

## Most Common M05 Error: Architecturally Timid Proposals

The most common failure mode in Module 05 is not technical weakness — it is **architectural timidity**.

The participant designs what they think will be approved, not what the problem requires. They scope Phase 1 conservatively to avoid pushback. They leave GDPR vague because they're not sure they know the answer. They write ADRs for easy decisions and avoid writing ADRs for the hard ones. They phrase trade-offs softly to avoid conflict.

The result is a proposal that is technically sound but architecturally insufficient — it doesn't actually solve the business problem in the scenario, it solves the part of the problem that felt safe.

### How to detect it

- Phase 1 scope is smaller than what the business context requires (the Finance reconciliation problem is partially but not fully solved)
- GDPR is mentioned but not architected — it appears as a note ("we will comply with GDPR") rather than as a design decision ("PII data is masked at ingestion in the Bronze layer; EU-origin records are flagged for residency routing; deletion requests trigger a propagation job to all three layers with a 72-hour SLA — documented in ADR-002")
- ADRs are written for decisions that don't require ADRs (partition key choice, naming conventions) and not written for decisions that do (multi-cloud data routing, GDPR deletion architecture)
- The risk register contains only mitigated risks — accepted risks are absent

### How to address it in ceremony

Use Challenge 6 (the "over-engineered" challenge) in reverse: instead of challenging the complexity, challenge the simplicity. If the proposal seems timid, ask:

> "Your Phase 1 scope solves the Finance reconciliation problem. But the Marketing campaign overlap issue — the 34% duplicate customer list — isn't addressed. Why not? Is that a Phase 2 problem or a Phase 1 problem?"

A timid proposal will either have no answer or will defer everything to Phase 2. A strong proposal will have a clear argument for why deduplication is Phase 2 (the ThreadCo data quality isn't reliable enough yet), not just silence.

**In feedback**: "Your proposal is technically careful. The gap is scope: the business context describes four specific problems, and Phase 1 addresses two of them. An architect doesn't scope Phase 1 to what's comfortable — they scope it to what the business needs by the funding round, then show how the constraints make that achievable. Your Phase 1 looks safe because it defers too much. For your retry, start from the business outcomes required by the funding round and work backward to what Phase 1 must deliver."

---

## How to Celebrate Program Completion

Module 05 is the end of the program. When a participant completes it — and only then — take a moment to mark what happened.

This is not bureaucratic. The program asked participants to do something genuinely hard over several months: to see differently, to design under pressure, to document honestly, to communicate with clarity, and to hold their ground when challenged. Most professional development programs don't ask for any of that. This one asks for all of it.

### In ceremony (in front of their peers)

After announcing the result (COMPLETES), say something specific — not generic praise. Reference something you saw across their modules:

> "When [name] started Module 01, they presented a pipeline diagram and called it an architecture map. Today they presented a complete proposal — six sections, two ADRs, a risk register, and a defense that held up to 5 minutes of pressure. The gap between those two moments is the program working. That's worth acknowledging."

Then open the floor briefly: 2–3 minutes for other participants to share one observation from the ceremony. This is not critique — it is witnessing.

### In writing (within 24 hours)

The written feedback for a COMPLETES result should do two things:

1. **Acknowledge what they built across the program** — not just Module 05. If you've facilitated their journey, you've seen the growth. Name it specifically.

2. **Name the one skill they'll use first** — the most immediately applicable capability they demonstrated. This gives the completion a forward orientation rather than a backward one.

> "Your strongest skill across the program is design under constraints. You're at your best when you have a problem, a constraint canvas, and a whiteboard. What you'll want to practice next is the adversarial defense — today was the first time you did it at full pressure, and you held. Do it more, in lower-stakes settings, until it stops taking energy."

### Across the cohort

If multiple participants complete in the same cohort, consider a brief group celebration at the end of the final ceremony — not a long event, just a moment where the whole cohort can acknowledge the work they did together. The ceremonial format of the program was designed precisely to create these moments.

---

## A Note to the Facilitator on This Program

Running DataArch-Speak well requires you to hold two things simultaneously: the rigor of a consistent rubric and the judgment of someone who has done this work and knows when the standard is being met in spirit even when it's not being met in form.

The rubric is a tool. Use it. But the program's purpose is not to produce rubric-compliant engineers — it is to produce data architects. Those are not always the same thing.

When a participant shows genuine architect-level thinking in a way the rubric didn't anticipate, note it. When a participant scores above the threshold but showed concerning patterns the rubric didn't penalize, note that too. The rubric is the floor; your judgment is the ceiling.

The participants who go through this program are building something real. Honor the work they did.
