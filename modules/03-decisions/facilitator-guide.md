# Facilitator Guide — Module 03: Architecture Decision Records

## Purpose of This Module (Facilitator Perspective)

Module 03 tests a specific and difficult skill: **intellectual honesty under the social pressure of having already made a decision.**

Writing an ADR after a decision is made — which is most of the time — requires the author to honestly document the alternatives they rejected, including the ones that had real merit, and to name the costs of their own choice, including the ones they'd prefer not to advertise.

Most people, in most professional contexts, have learned to write documentation that makes them look good. An ADR that does this is worse than no ADR — it creates false confidence in future readers and conceals the real trade-offs from the people who will maintain the system.

Your job as facilitator is to distinguish **honest documentation** from **advocacy dressed as documentation**.

The signal you are watching for: **does the participant know what their decision cost, and are they willing to say it out loud?**

---

## Before the Ceremony

**48 hours before:**
- [ ] Read both ADRs per participant (20–25 min each) with two questions in mind:
  1. Could I understand this decision completely from the ADR alone, without talking to the author?
  2. Does the Consequences → Negative section contain real costs, or is it empty / trivial?
- [ ] Read the weak ADR review for each participant — note whether they identified the most critical problem (empty negative consequences)
- [ ] For each participant, identify 1 ADR section you want to probe in Q&A — where does the ADR feel like advocacy?
- [ ] Have the scoring sheet ready; Dimension 4 (Consequence Honesty) is your primary watchpoint

**Day of:**
- [ ] Remind participants at the start: "The purpose of an ADR is to be useful to someone with no context. Present the *reasoning* — not just what was decided."

---

## What to Observe During the Presentation

### Dimension 1 — ADR Structure Completeness

Read the submitted ADRs before the ceremony so you already know the structure. During the presentation, watch for:
- Does the participant refer to the ADR or present it? (referring = reading sections aloud; presenting = explaining the reasoning behind each section — the latter is better)
- If you ask "what follow-on decisions does this ADR trigger?" — can they answer without looking at the document?

**Red flag**: participant says "I put N/A for that section" for anything other than trivial fields.

### Dimension 2 — Context Clarity

During the presentation, listen to the first 90 seconds of how they frame the context. Does it feel like a neutral description or like someone who has already decided?

**Tell**: compare these two framings of the same situation:
- Neutral: "The team was choosing between three storage formats for the Gold layer. We had an existing Databricks contract and three engineers with Delta Lake experience."
- Advocacy: "We needed a robust, production-ready storage format for the Gold layer. We evaluated our options and found that Delta Lake was the clear choice given our Databricks environment."

The second version pre-argues for the conclusion. It would not be useful to a future engineer evaluating whether to change the decision.

**Red flag**: the Context section ends with a sentence that sounds like a recommendation.

### Dimension 3 — Options Coverage

Watch for the straw man. It usually appears as an option that:
- Is described in 2 sentences while the chosen option gets 8
- Has only cons listed (no pros at all)
- Is described with language that makes it sound obviously wrong ("while Option B is theoretically possible, it would be impractical for a team of our size")

If you suspect a straw man, use Q3 in the Q&A.

**Also watch for**: the missing option. In the Airflow weak ADR review, the correct answer includes recognizing that the ADR didn't consider managed orchestration services (MWAA, Cloud Composer, Astro) — a common gap when engineers evaluate only open-source vs. open-source.

### Dimension 4 — Consequence Honesty

This is your most important observation. Before the ceremony, scan the Consequences sections of both submitted ADRs. Note:

- Does the Negative section exist?
- If it exists: are the items real costs or trivial overhead?
- Are the negatives proportional to the significance of the decision?

Some reference points for what "real" negative consequences look like:

| Decision | Real negative consequence (example) |
|---|---|
| Adopt Delta Lake for Gold layer | All Gold tables require conversion if the team moves to a non-Databricks compute engine — this is a significant, potentially multi-month migration |
| Use Airflow for orchestration | DAG authoring in Python means the orchestration layer requires engineering expertise; data analysts cannot debug or modify pipelines without engineering support |
| Single-tenant Snowflake model | RBAC misconfiguration can expose sensitive data across teams; there is no physical isolation barrier |
| Batch over streaming ingestion | Data freshness is bounded by the batch interval for all downstream use cases — not just current ones |

**Red flag**: Consequences → Negative is empty, says "none identified," or lists only "requires monitoring."

### Dimension 5 — Review Quality

When the participant presents their weak ADR feedback, listen for specificity.

- Generic feedback: "The options section should include more alternatives" — this could be said by anyone who skimmed the document
- Specific feedback: "The Prefect option lists only cons. Prefect's orchestration model is actually more suited to dynamic, event-driven pipelines than Airflow's static DAG model — that's a meaningful pro that was omitted, and its absence makes the comparison look like a straw man"

The test: would a developer receiving this feedback know exactly what to change?

---

## Q&A Questions Bank

Use 2–3 per presenter. Questions Q1–Q3 are diagnostic; Q4–Q6 are adversarial.

### Diagnostic questions

**Q1 — The cold reader test** *(Dimension 1 and 2)*
> "Imagine I'm a new engineer who just joined the team. I found your ADR in the `/decisions` folder. After reading it, I have one question: [pick a specific gap from their submitted document]. What would I find in your ADR to answer it?"

Use when: the ADR has structural gaps or thin sections. This question asks the participant to evaluate their own ADR from the perspective of its intended user.

---

**Q2 — The negative consequence probe** *(Dimension 4)*
> "You listed [negative consequence X] in your Consequences section. What does that cost look like in practice — how would an engineer discover that cost the first time? What would go wrong?"

Use when: the negative consequences exist but feel abstract or underweighted. This question forces the participant to make the cost concrete. If they can't answer, the consequence wasn't real — it was written to fill the section.

---

**Q3 — The straw man challenge** *(Dimension 3)*
> "You described [Option B] as having [specific weakness]. Is there a team or context where Option B would actually be the right choice? Walk me through that scenario."

Use when: Option B feels like a straw man. A participant who genuinely evaluated Option B can describe a context where it wins. A participant who built a straw man will struggle to answer this without making Option B sound like their actual recommendation.

---

### Adversarial questions

**Q4 — The future engineer test** *(Dimension 2 and 4)*
> "Three years from now, a new architect reads your ADR and decides the decision should be revisited. What in your ADR would give them the evidence they need to make that call? Is anything missing?"

Use when: you want to test whether the participant understands the ADR as a time-travel artifact — written for the future, not for today. A strong participant will point to the context section (conditions that would have to change) and the negative consequences (the costs that become unbearable at scale). A weak participant will say "they can just read it and decide."

---

**Q5 — The honest cost challenge** *(Dimension 4)*
> "You chose [decision]. What is the worst-case scenario if that decision turns out to have been wrong? Not a risk you mitigated — the actual worst case."

Use when: the Consequences → Negative section feels like it's minimizing the real costs. This question forces the participant out of documentation mode and into honest reflection. The answer reveals whether they've genuinely accepted the trade-off or just rationalized it.

---

**Q6 — The post-hoc test** *(Dimension 3 and 4)*
> "When did you write this ADR — before or after the decision was made? And if it was after: how do you know you haven't just written a justification for what was already decided?"

Use when: the ADR feels like post-hoc advocacy — the options section is thin, the chosen option has no downsides, and the decision section sounds like a press release. This is a direct question about the honesty of the record. A strong participant will say: "I wrote it after, and here's how I checked for bias: I specifically went looking for cons I wouldn't want to include." A weak participant will be defensive.

---

## Handling the Most Common M03 Error: Post-Hoc Justification

This is the defining failure mode of Module 03, and it's the most common one. It occurs because:

1. ADRs are almost always written after the decision
2. The author knows what was decided and has organizational ownership of that decision
3. The social cost of documenting downsides feels higher than the benefit of future honesty

The result is an ADR where:
- The options section lists weak alternatives with only cons
- The chosen option has 4–5 pros and 0–1 weak cons
- The decision section reads like a product announcement
- The consequences section is either empty or has only positive items

**How to detect it during the presentation:**
- Ask Q6 (the post-hoc test) directly
- Ask Q2 (the negative consequence probe) on the weakest negative consequence — if the author can't explain the cost concretely, it wasn't real

**How to handle it in feedback:**

Be direct. Do not soften this feedback because it's uncomfortable — the purpose of Module 03 is precisely to develop the intellectual honesty skill, and vague feedback doesn't develop it.

Say: "Your ADR-001 reads like advocacy. The Consequences → Negative section has [item X], which is a trivial operational overhead, not a meaningful cost of this decision. The real cost — [specific cost you identified from reading the ADR] — is not documented. Before your retry, ask yourself: 'what does this decision make harder forever, not just temporarily?' That's what belongs in the negative consequences section."

---

## A Note on Retroactive ADRs

The retroactive ADR (Part 1 of the assignment) is the harder and more revealing exercise. Participants who do it well demonstrate:
- The ability to reason backward from a system's design to its original decision context
- Comfort with uncertainty (they must say "this was likely the reasoning" rather than pretending to have certainty)
- Honesty about consequences they can observe but may not like

Participants who struggle with the retroactive ADR often produce one that looks like the post-hoc justification pattern — because they default to writing what sounds professionally correct rather than what they genuinely believe the reasoning was.

When you see a retroactive ADR that feels too clean, use Q4 (the future engineer test) and Q5 (the honest cost challenge) to probe whether the reconstruction is honest or polished.

---

## Closing the Ceremony

After all M03 presentations:

1. Note the most common pattern you saw: ADRs without real negative consequences, or ADRs with straw man options — give the group the name for what you saw without attributing it
2. Remind participants: in Module 04 they will be presenting their architectural work to non-technical audiences. The ADRs they wrote here will be the content they're communicating. The discipline of honest documentation makes the communication work harder — if you can't name what your decision costs, you can't explain it to a VP either.
3. For participants advancing to M04: encourage them to review their ADR-002 (NovaMart) before starting M04 — it will be one of the artifacts they adapt for different audiences.
