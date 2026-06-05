# DataArch-Speak

### From data engineer to data architect — not by learning more tools, but by learning to think, decide, and defend differently.

---

## What This Program Is

DataArch-Speak is a five-module program that develops the capabilities data engineers need to operate as data architects. It does not teach Spark, dbt, Snowflake, or any other platform. It teaches something harder to acquire and harder to measure: how to see a system and understand why it's shaped the way it is, how to design under real constraints and be honest about what that costs, how to document decisions in a way that serves the people who inherit your work, and how to stand in front of a skeptical room and defend a recommendation without flinching.

Most training programs ask you to watch, read, and answer questions. This one asks you to produce real work, present it to your peers, and be evaluated on whether it holds up. That is harder, takes longer, and is worth considerably more.

---

## What You Will Be Able to Do When You Finish

- Look at a system you didn't build, map the architectural decisions embedded in it — including the ones nobody documented — and explain why it's shaped the way it is and what it costs.
- Design two genuinely viable architectural options for the same problem, compare them against the same criteria, and make a recommendation that references constraints rather than preferences.
- Write an Architecture Decision Record that a new engineer, joining three years from now, can read in five minutes and understand what was decided, what was rejected, and what the decision cost.
- Present the same architectural proposal to a VP and to a senior engineer — with different vocabulary, different diagrams, and different asks — and be accurate in both versions.
- Walk into a room with a skeptical decision-maker, a 12-minute window, and a proposal you built from scratch, and leave with a decision.

---

## The Journey

```
  Data Engineer
  ─────────────────────────────────────────────────────────────
  You know how to build. You're good at it.
  What you can't do yet: see why systems are shaped the way they are.
        │
        ▼
  ┌─────────────────────────────┐
  │  M01 — Architect's Mindset  │
  └─────────────────────────────┘
  You stop describing what pipelines do
  and start explaining why they were designed that way.
        │
        ▼
  ┌──────────────────────────────────┐
  │  M02 — Design Under Constraints  │
  └──────────────────────────────────┘
  You stop designing for an ideal world
  and start designing for the world you actually have.
        │
        ▼
  ┌────────────────────────────────────────┐
  │  M03 — Architecture Decision Records   │
  └────────────────────────────────────────┘
  You stop making decisions that evaporate
  and start making ones that last.
        │
        ▼
  ┌──────────────────────────┐
  │  M04 — Architect's Voice  │
  └──────────────────────────┘
  You stop explaining your work
  and start getting people to act on it.
        │
        ▼
  ┌──────────────────────────────┐
  │  M05 — Full Architecture     │
  │        Pitch                 │
  └──────────────────────────────┘
  You stop hoping your proposals survive scrutiny
  and start knowing they will.
        │
        ▼
  Data Architect
  ─────────────────────────────────────────────────────────────
```

---

## The Five Modules

| # | Module | Skill developed | What changes after you complete it |
|---|---|---|---|
| 01 | **Architect's Mindset** | Reading systems architecturally | You can look at a system you didn't build and explain not just what it does, but why it's shaped that way and what decisions are embedded in it. |
| 02 | **Design Under Constraints** | Designing under real conditions | You no longer propose the best possible architecture — you propose the best architecture given a specific team, budget, timeline, and debt. And you can explain the difference. |
| 03 | **Architecture Decision Records** | Documenting decisions with rigor | You understand that an ADR without negative consequences isn't a record — it's advocacy. You write the kind of documentation that actually helps the person who comes after you. |
| 04 | **Architect's Voice** | Communicating to mixed audiences | You can take the same architectural argument and make it land for a VP in 60 seconds and for a senior engineer in 3 minutes — without losing accuracy in either version. |
| 05 | **Full Architecture Pitch** | Producing and defending complete proposals | You can build a full architecture proposal from a blank page, present it in 12 minutes, and defend every decision under adversarial questioning without capitulating or going quiet. |

---

## How the Program Works

Each module follows a two-week cycle:

1. **Self-study** — Read the module material on your own (2–4 hours). It is designed to be complete without an instructor. There are no videos, no quizzes, no passive content — just material dense enough to work with.

2. **Produce your deliverable** — Each module has a specific assignment (3–6 hours). Not a worksheet. A real artifact: an architecture map, a design proposal, two ADRs, a presentation, a full pitch. The kind of thing you would actually produce at work.

3. **Present at the ceremony** — Once a week, two or three participants present their module work in a shared one-hour session. You have 12 minutes. The room includes your peers and a facilitator who will ask hard questions. There is no option to hide behind a screen and submit something polished and safe.

4. **Receive your result** — Within 24 hours you receive a written result: **ADVANCES** or **REINFORCES**, with specific feedback tied to the module's scoring rubric. Not a grade. A decision with a reason.

### Why this format

You cannot develop these skills by watching a video or reading a framework. Architecture is a social practice — the design exists to be challenged, the communication exists to land with a real audience, the decision exists to be defended under pressure. The ceremony format creates that pressure deliberately, in a space where failure is safe and feedback is specific.

A self-paced online course lets you skip the parts that are hard for you. This program does not. If you REINFORCE a module, you have one week to revise and re-present. That's not punishment — that's the program working.

---

## What Is Expected of You

**Time**: between 6 and 10 hours per module, spread over two weeks. The on-demand format means you set your own schedule — but the ceremony deadline is fixed. There is no extension for "I got busy."

**Work quality**: each module's assignment asks for real thinking, not polished performance. The facilitator's rubric is designed to detect the difference between a participant who thought carefully and one who assembled something that looks right. You will get more from this program by submitting honest, imperfect work than by submitting a polished artifact that hides your gaps.

**Progression**: modules are sequential. You cannot start Module 02 before completing Module 01. This is not bureaucracy — each module builds on the previous one in ways that matter. The assignment in Module 03 asks you to write ADRs for decisions you made in Module 02. The presentation in Module 04 uses the architectural work from Modules 02 and 03 as its content. Skipping forward produces a gap that will surface.

**When you REINFORCE**: a REINFORCE result means one specific dimension of your work didn't meet the threshold. You will receive written feedback naming that dimension and describing exactly what the retry needs to show. Most retries pass. The ones that don't are ones where the participant submitted the same work without reading the feedback. Read the feedback.

**The one thing that determines whether you get value from this**: show up with real work. The participant who maps a system they actually maintain, designs a proposal for constraints they actually face, and writes ADRs for decisions their team actually made will learn more in five modules than someone who chooses toy examples to protect themselves from the feedback. The harder you make the work, the more the program gives back.

---

## Getting Started

```
modules/
├── 01-foundations/     ← Start here. Open README.md.
├── 02-design/
├── 03-decisions/
├── 04-voice/
└── 05-pitch/
```

Each module folder contains five files: `README.md` (start here), `material.md` (read before the assignment), `assignment.md` (what to produce), `scoring-rubric.md` (how you'll be evaluated), and `facilitator-guide.md` (for whoever runs your ceremony).

You don't need to read everything at once. Open [modules/01-foundations/README.md](modules/01-foundations/README.md) and start there.

---

## Repository Structure

```
.
├── README.md                        ← You are here
├── CLAUDE.md                        ← AI agent configuration for program development
│
├── context/                         ← Program context (for facilitators and program builders)
│   ├── program-vision.md
│   ├── target-audience.md
│   ├── ceremony-format.md
│   ├── module-design.md
│   └── loka-speak-reference.md
│
├── skills/                          ← AI agent skills for creating program content
├── templates/                       ← Reusable templates for modules and tracking
│
└── modules/
    ├── 01-foundations/              ← Architect's Mindset
    ├── 02-design/                   ← Design Under Constraints
    ├── 03-decisions/                ← Architecture Decision Records
    ├── 04-voice/                    ← Architect's Voice
    └── 05-pitch/                    ← Full Architecture Pitch
```

---

There is a gap between knowing what good architecture looks like and being someone who produces it under pressure, documents it honestly, and defends it in front of people who will push back. Most data engineers have crossed half that gap — they've developed strong technical instincts, real experience, and a genuine understanding of the systems they work with. What they haven't had is a structured environment to develop the other half: the judgment, the communication, and the resilience. That's what this program is for. It won't be the most comfortable training you've done. It will probably be the most useful.
