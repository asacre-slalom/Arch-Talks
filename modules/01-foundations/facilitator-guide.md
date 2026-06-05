# Facilitator Guide — Module 01: Architect's Mindset

## Purpose of This Module (Facilitator Perspective)

Module 01 is not a test of technical knowledge — it's a test of perspective. Your job as facilitator is not to assess whether the participant chose the "right" system or found the "right" trade-offs. It's to assess whether they are *seeing the system differently* than they would have before.

The most important thing you are watching for: **does this person describe what a system does, or does this person describe why a system is shaped the way it is?**

That distinction will tell you everything about whether the mindset shift has happened.

---

## Before the Ceremony

**48 hours before:**
- [ ] Confirm all presenters have submitted their deliverables to the repository
- [ ] Read each submission (15–20 min per person) — not to grade it, but to understand what system they chose and what decisions they identified
- [ ] Prepare 1–2 specific questions per presenter based on their actual submission (see templates below)
- [ ] Have the scoring sheet from `scoring-rubric.md` printed or open in a tab

**Day of:**
- [ ] Set a visible timer for each presentation (use a phone, laptop, projector) — the 12-minute limit is part of the exercise
- [ ] Have a notepad for real-time scoring annotations

---

## What to Observe During the Presentation

Use these signals while the participant is presenting to inform your scoring in real time.

**Watch for in Dimension 1 (Architectural Framing):**
- Does the map have components and flows, or does it look like a pipeline diagram with task boxes?
- Does the participant describe roles (ingestion layer, serving layer) or tools (Airflow, Snowflake, dbt)?
- Can you understand the structure of the system from the map alone, or do you need the presenter to explain every element?
- Red flag: the participant says "here we have the DAG that runs at 9am and loads data into this table" — that's implementation, not architecture

**Watch for in Dimension 2 (Trade-off Identification):**
- Are the trade-offs specific or generic? ("it's harder to scale" vs. "streaming freshness below 5 minutes is not achievable without a full replatform")
- Does the participant name who pays the cost? Teams? Stakeholders? Use cases?
- Does at least one trade-off include a reflection on the original constraint?
- Red flag: the participant describes technical limitations without tracing them back to a decision ("it has high latency" without explaining that it was a deliberate choice to use batch)

**Watch for in Dimension 3 (Decision Classification):**
- Does the participant spontaneously use the architecture/implementation distinction?
- When they say "we decided X", is X actually an architectural decision or an implementation detail?
- Red flag: all three "decisions" are things like "we chose to partition by date" or "we use dbt macros for naming conventions"

**Watch for in Dimension 4 (Depth of Reflection):**
- Is the reflection a summary ("I found three trade-offs") or a genuine perspective shift ("I used to assume the 5-minute batch was a technical limitation — now I realize it was a deliberate choice to not hire a streaming engineer")?
- Does the participant sound surprised by something they discovered?
- Red flag: the reflection is generic and could have been written by anyone

---

## Q&A Questions Bank

Use these questions to probe depth during the 3-minute Q&A. Pick 2–3 max — you don't have time for all of them. Prioritize questions that target the participant's weakest dimension.

### Questions that reveal mindset (not memorization)

**Q1 — The "why" question** *(targets Dimension 1 and 3)*
> "You showed me that the system uses [X]. But why is it designed that way? Not how it works — why was that the design choice?"

Use this when the map looks more like a flow diagram than an architecture diagram, or when the participant seems more comfortable describing what the system does than why it's shaped that way.

---

**Q2 — The cost question** *(targets Dimension 2)*
> "You said [trade-off X] makes [Y] easy. Who is paying the cost right now — today — for that decision? Can you name a specific team or a specific use case?"

Use this when trade-offs were identified but feel abstract or unconnected to real impact.

---

**Q3 — The reversal question** *(targets Dimension 2 and 3)*
> "If you could redesign this from scratch with no legacy constraints, what would you change first — and what would you keep exactly as is? Why?"

Use this to test whether the participant can separate the "decisions that made sense then" from the "decisions that still make sense now." A strong answer requires distinguishing architectural from implementation choices.

---

**Q4 — The classification challenge** *(targets Dimension 3)*
> "You called [specific decision from their submission] an architectural decision. Could someone reverse that without redesigning the system? How?"

Use this when you're unsure whether the participant genuinely understands the distinction or is pattern-matching on what sounds architectural.

---

**Q5 — The consequence question** *(targets Dimension 2)*
> "You identified [decision X] as a trade-off. What would have to be true for this system to outgrow that decision? What's the trigger?"

Use this to test whether the participant can think forward in time — a core architectural skill.

---

**Q6 — The adversarial question** *(targets Dimension 1 and 4)*
> "Your map shows [component X] connecting to [component Y]. I'd argue that's actually an implementation detail, not an architectural choice. Why is it on your map?"

Use this near the end if the participant seems confident and ready for a challenge. This is not a "gotcha" — it's a probe. A participant with the right mindset will either defend the choice with an argument or immediately agree and reconsider. A participant who hasn't shifted yet will get flustered.

---

## Handling the Most Common Error: Describing Implementation Instead of Architecture

This will happen in roughly 60–70% of first-time presentations. The participant presents a list of tools, a detailed pipeline flow, or a set of configuration choices — and calls it an architecture map.

**Do not correct them during the presentation.** Let them finish.

**During Q&A, use Q1 ("why") to redirect:**
> "I see the components. Help me understand — why is it *shaped* this way? Not how it runs, but why these components and not others? Why this boundary and not a different one?"

If they still respond with implementation details, follow up with:
> "Let me try a different angle: imagine someone joins your team next week with no context. What would they need to understand about *why* this system is designed this way before they can make any decision about changing it?"

This usually unlocks the architectural level — they know it, they just haven't been asked to articulate it before.

**In the scoring**, a participant who did this but showed genuine recovery during Q&A can still reach ACHIEVED on Dimension 1 if they demonstrated understanding under prompting. The rubric gives you room for that.

---

## Signals: Ready to Advance vs. Needs Reinforcement

### Ready to advance (ADVANCES)
- Can explain the system's shape without being prompted
- Uses trade-off language naturally ("we sacrificed X for Y")
- Correctly identifies at least 2 of 3 decisions as architectural under pressure
- Reflection reveals a genuine insight, not a summary

### Needs more time (REINFORCES)
- Defaults to "what the system does" instead of "why it's designed this way"
- Trade-offs are real but generic ("it doesn't scale well" without specifying the design decision behind it)
- All three "decisions" are implementation details
- Reflection is a task summary

### A note on edge cases

Sometimes a participant has the mindset but delivered it poorly in the presentation (nerves, time pressure, unclear map). Before scoring REINFORCES, consider:
- Did the Q&A reveal understanding that wasn't clear in the presentation?
- Is the deficit in framing (how they communicated it) or in thinking (whether the mindset shift happened)?

Framing can improve with practice. A mindset that hasn't shifted yet needs more time in Module 01. Your call — use the rubric as your anchor.

---

## Closing the Ceremony

After all presentations:

1. Give 2–3 minutes of consolidated feedback to the group (patterns you saw across all presentations — not individual scores)
2. Remind them: results and individual written feedback will arrive within 24 hours
3. For participants advancing to Module 02: let them know the next module builds directly on this one — their architecture map will likely be useful again
