# Facilitator Guide — Module 02: Design Under Constraints

## Purpose of This Module (Facilitator Perspective)

Module 02 is where participants face the core challenge of real architecture work: designing under pressure, with imperfect information, in a space they didn't define.

Your primary task as facilitator is not to evaluate the technical merit of the proposed architecture. A Snowflake-based design and a Databricks-based design are both potentially correct for NovaMart — what you are evaluating is **whether the design is shaped by the constraints or despite them**.

The question you are answering throughout the presentation:
> "Did this person design *for* NovaMart, or did they design *a data platform* and then retrofit NovaMart's context onto it?"

These are fundamentally different cognitive processes, and the difference will be visible in how they present.

---

## Before the Ceremony

**48 hours before:**
- [ ] Confirm all presenters have submitted their deliverables
- [ ] Read each submission (20–25 min per person) with these two questions in mind:
  1. Does the Constraint Canvas contain anything that isn't in the assignment text? (inferred constraints = good sign)
  2. Is Option B a genuine alternative or a straw man?
- [ ] Note 1–2 specific challenges per presenter for the Q&A
- [ ] Have the scoring sheet open during the presentation

**Day of:**
- [ ] Set a visible 12-minute timer — M02 presentations tend to run long because participants want to explain both options in detail. The time constraint itself is a test.

---

## What to Observe During the Presentation

### Dimension 1 — Constraint Identification

The first signal comes before the architecture diagrams appear. Does the participant open by framing the constraint space, or do they jump straight to the design?

- **Strong signal**: "The key tension in this design is the 10-week deadline for the executive dashboards versus the 3–4 week IT approval cycle for ERP access. That constraint shaped almost every decision." → They started from constraints.
- **Weak signal**: "I decided to use a medallion architecture with three layers..." → They started from a pattern.

Watch for:
- Does the KEY TENSION from their Constraint Canvas actually drive the narrative of the presentation?
- Do they name the IT approval timeline as a constraint? (It's the biggest hidden constraint in the scenario — participants who miss it are not reading carefully enough)
- Do they distinguish must-haves from nice-to-haves, or treat all constraints equally?

### Dimension 2 — Option Comparison Rigor

The straw man problem: Option B is described in one slide with half the detail of Option A, and all its trade-offs are described as dealbreakers.

Ask yourself while they present Option B: *could a different team, with different constraints, have legitimately chosen this option?*

- If yes → it's a real option
- If no → it's a straw man

Watch for:
- Does the participant proactively name any dimension where Option B is actually better than Option A?
- Does the comparison table use the same criteria for both options?
- Is the participant noticeably less confident when presenting Option B than Option A?

### Dimension 3 — Recommendation Quality

The recommendation should feel inevitable given the constraints — not like a preference the presenter held before they read the scenario.

- **Strong signal**: "Option A fits within the 10-week window because it doesn't require ERP integration in Phase 1 — we can deliver the executive dashboards from the Snowflake ERP export we already have. Option B requires the custom CDC connector which IT won't approve in time."
- **Weak signal**: "Option A is the better choice because it's more scalable and uses a modern architecture."

Watch for: does the recommendation explicitly eliminate the alternative by naming a constraint? Or does it just describe the preferred option's merits?

### Dimension 4 — Trade-off Transparency

The accepted risk section is where participants are most likely to be defensive. They often describe a risk they "have a plan to mitigate" rather than a risk they are genuinely accepting.

A genuine accepted risk sounds like: "We are accepting that the POS integration will be brittle until IT approves a proper JDBC connection. Until then, we depend on the SFTP flat-file export, which can fail silently. We are accepting this because the alternative — waiting for IT — would miss the 10-week deadline."

Watch for: does the accepted risk have a real cost? Would a reasonable person consider that risk meaningful?

### Dimension 5 — Design-for-Evolution Thinking

Does the participant present their design as complete, or as deliberately incomplete in specific ways?

Watch for: when they say "Phase 2" — do they name a trigger, or is it vague? A participant who says "we'll add real-time streaming when the business needs it" hasn't really thought about evolution. A participant who says "the Shopify webhook integration is ready to be enabled — we'll activate it when the product team requests sub-1-hour campaign data" has.

---

## Q&A Questions Bank

Use 2–3 of these per presenter. The first three are diagnostic (reveal gaps); the last three are adversarial (test whether they can hold their position).

### Diagnostic questions

**Q1 — The hidden constraint probe** *(Dimension 1)*
> "You listed [X] constraints in your canvas. The IT approval cycle for ERP and POS integrations takes 3–4 weeks. Is that in your canvas, and how did it affect your design?"

Use when: the participant didn't mention the IT timeline, or mentioned it but didn't factor it into Phase 1 delivery.

---

**Q2 — The straw man test** *(Dimension 2)*
> "Tell me the one scenario where Option B would actually be the right answer for NovaMart — not in general, but for NovaMart specifically, given what you know about them."

Use when: Option B feels like a straw man. A participant who genuinely evaluated Option B should be able to answer this. A participant who built a straw man will struggle.

---

**Q3 — The deferral probe** *(Dimension 5)*
> "You said [component X] is Phase 2. What specific event — technical, business, or organizational — should trigger that work? And what in your current design would you replace vs. extend when that happens?"

Use when: the presentation mentioned phasing but the triggers were vague. This question separates "I thought about evolution" from "I added Phase 2 to the slide."

---

### Adversarial questions

**Q4 — The constraint challenge** *(Dimension 3)*
> "You recommended Option A partly because of the 10-week deadline. But what if I told you the CFO is flexible and we have 20 weeks? Does your recommendation change?"

Use when: you want to test whether the recommendation is genuinely constraint-driven. A strong participant will say "yes, with 20 weeks I'd reconsider [specific component] — but the PII compliance requirement still rules out [specific aspect of Option B]." A weak participant will either say "yes, I'd go with Option B" (showing the recommendation was about time, not about the full constraint space) or "no, Option A is still better" without engaging the hypothetical.

---

**Q5 — The cost challenge** *(Dimension 4)*
> "You said the accepted risk is [X]. That sounds manageable. But what's the worst-case scenario if that risk materializes? How bad does it actually get?"

Use when: the accepted risk section felt defensive or understated. Push them to name the worst case. A participant who has genuinely accepted a risk can describe it clearly.

---

**Q6 — The preference challenge** *(Dimension 3)*
> "I looked at your design and I think you would have chosen this architecture even if NovaMart had different constraints. Is there anything in your design that you wouldn't have included if the constraints were different?"

Use when: the design feels like a favorite pattern with the constraints bolted on. This question asks directly whether the design is genuinely constraint-driven. A strong participant will point to 2–3 specific choices that were forced by constraints (e.g., "without the IT bottleneck, I would have used CDC from day 1 instead of the SFTP workaround"). A weak participant will defend the design as universally applicable.

---

## Handling the Most Common M02 Error: "The Perfect Solution"

About 40–50% of first-time M02 presentations look like this: a well-structured, technically sound architecture proposal where the constraints appear only in the opening slide and are never referenced again. The design is internally consistent and defensible — but it could have been built for any company.

**The tell**: when you ask "why didn't you include [streaming / real-time / a data catalog]?", the answer is "because we don't need it yet" — not "because given the 2-engineer team and $65K budget, the operational overhead would exceed the benefit."

**Do not penalize participants for having a good design.** Penalize them for not connecting the design to the constraints.

During Q&A, use Q6 (the preference challenge) to surface this. Then in the scoring:

- Dimension 1: if the canvas was complete but not referenced, DEVELOPING on Dimension 1
- Dimension 3: if the recommendation doesn't name constraints, DEVELOPING on Dimension 3

**In feedback**: be specific. "Your design is technically strong. The gap is that your recommendation reads as 'this is a good architecture' rather than 'this is the right architecture for NovaMart given these specific constraints.' For your retry, rewrite the recommendation section so that every sentence either names a constraint or names something it ruled out."

---

## Edge Case: The Participant Who Over-Constrains

Some participants, having understood the constraint message, apply it too aggressively. They end up with a design so stripped down that it can't actually meet the stated business requirements. For example: "Given the 2-person team, I recommend starting with CSV exports to a shared folder and Tableau connected directly."

This is not constraint-driven design — it's constraint surrender. The business requirement (executive dashboards in 10 weeks) still needs to be met.

If you see this, use Q4 (constraint challenge variant): "If I gave you one additional mid-level data engineer and $15K more in budget, would your design change significantly? Why or why not?"

A participant who over-constrained will say yes and describe a totally different design — showing the constraint was a blocker, not a design input. The feedback: "Constraints define the design space, but the solution must still solve the business problem. A constraint that makes the business requirement impossible is a constraint to escalate, not accept."

---

## Closing the Ceremony

After all M02 presentations:

1. **Highlight the best constraint framing you saw** — name it without naming the person (unless in a small group). This reinforces the behavior.
2. **Name the most common gap** across the group without calling anyone out.
3. Remind participants: the architecture maps they built in M01 and the constraint canvases from M02 will both be inputs to M03. Encourage them to keep these artifacts — they'll use them again.
