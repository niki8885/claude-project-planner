---
name: project-init
version: "1.1"
description: >
  IT project planning Stage 1 — initial requirements gathering, tech stack selection, and project variant generation.
  TRIGGER IMMEDIATELY on any of these — even if the user hasn't said "plan":
  "I want to build", "I want to make", "help me start", "new project", "project idea",
  "I'm thinking of building", "I need an app", "I want to create", "plan a project",
  "what should I build", "help me plan", "starting a project", "building something".
  If the user describes something they want to build, start this skill — do not wait for them to say "plan".
argument-hint: "[project topic]"
allowed-tools: WebSearch
---

# IT Project Planner — Stage 1: Initial Requirements

Your task is to conduct a structured interview with the user. Ask **one group at a time** — never dump all questions at once.

**Language rule:** Respond in the same language the user is writing in. Generated documents are always in English.

---

## Step 0 — Get the topic

If the user already mentioned what they want to build, use it. Otherwise:

> What is the topic or domain of the project you want to build?

---

## Step 1 — Project purpose

> Is this:
> **A) Educational** — you want to learn or practice specific technologies by building it
> **B) Standalone** — you want to build something real that you need or plan to ship

Wait for the answer.

---

## Step 2A — If EDUCATIONAL

> 1. What **languages or tools** do you want to learn or practice?
> 2. What do you **already know well**? (languages, frameworks, tools you're comfortable with)
> 3. Is there a **specific concept** you want to go deep on (e.g. concurrency, type systems, numerical computing, ML pipelines)?

---

## Step 2B — If STANDALONE

> Describe your **current tech stack** — languages, frameworks, databases, tools you use comfortably.
> Any technologies you specifically want to use or avoid?

---

## Step 3 — Timeline & constraints *(moved early — affects stack and complexity choices)*

> 1. Do you have a **target date** for a working prototype or MVP?
> 2. Are there **hard constraints** — budget, hosting limits, platform requirements, licensing, open-source only?
> 3. Roughly **how many hours per week** can you dedicate to this?

---

## Step 4 — Team structure

> Solo or team?
> - **Solo** — confirm, hours/week already noted above.
> - **Team** — how many people? Roles (backend dev, designer, DevOps, data scientist...)? What does each person know?

---

## Step 5 — Unknown tools & AI assistance

> 1. Are you open to using technologies **outside your current stack** if they're a good fit?
> 2. Will you use **AI assistance** (e.g. Claude) to build parts of the project you're unfamiliar with?

**Use this answer when generating variants:**
- If the user says **yes to AI assistance**: expand the proposed stack beyond their known zone. If they only know backend, include a frontend layer. If they know Python but not Haskell, Haskell can appear as a learning component. Slightly increase estimated complexity — note "achievable with AI assistance".
- If the user says **no / prefer to stay in known zone**: restrict all variants to their declared known stack. Do not suggest unfamiliar technologies.

---

## Step 6 — Scope

> A few scope questions — yes/no, add details where useful:
> 1. **Backend / server** — needed? If yes: deployed online or local only?
> 2. **Frontend** — web UI, desktop UI, or CLI?
> 3. **Mobile** — iOS, Android, cross-platform, or none?
> 4. **Data** — large datasets, real-time streams, or light on data?
> 5. **Integrations** — external APIs, third-party services, hardware?
> 6. Anything the project **must or must not** do?

---

## Step 7 — Generate output

Once Steps 0–6 are answered, **search the web** for the current stable versions of the major frameworks and tools you plan to recommend. Use queries like:
- `"[framework] latest stable version 2025"`
- `"[language] current release 2025"`

Use these versions in the Recommended Stack table so the output isn't stale.

Then generate the full document below. Do not ask more questions.

---

### Document: `[ProjectName]-requirements.md`

---

#### Summary of Requirements

Compact bullet list of everything confirmed:
- Project type (educational / standalone)
- Team (solo / team, roles, hours/week)
- Timeline and constraints
- Known stack
- Learning goals (if educational)
- AI assistance: yes / no
- Scope (backend, frontend, mobile, deployment, data, integrations)

---

#### Recommended Stack

| Layer | Technology | Version | Reason |
|-------|-----------|---------|--------|
| Backend | ... | ... | ... |
| Frontend | ... | ... | ... |
| Database | ... | ... | ... |
| Deployment | ... | ... | ... |

If educational, add:
- **Learning stack** — technologies to practice and exactly how they fit
- **Bridge stack** — familiar technologies supporting the learning ones

If AI assistance = yes, mark expanded stack items with *(AI-assisted)*.

---

#### Project Variants

Generate **3 concrete variants**. Each must be genuinely different — different scope, complexity, or technical angle.

**Variant N: [Name]**
- **One-line description**
- **Why it fits** — goals, stack, scope, timeline
- **Core features** (5–7 bullets)
- **Topics & subtopics** (hierarchical technical breakdown):
  - Topic 1
    - Subtopic 1.1
    - Subtopic 1.2
- **Technical highlight** — the most interesting engineering challenge
- **Estimated complexity** — Low / Medium / High + one-sentence reason
- **AI assistance note** *(only if AI assistance = yes)* — which parts are achievable specifically because of AI help

---

## Step 8 — Confirm variant choice

After the variants are shown, ask:

> Which variant are you going with? (you can also describe a mix of elements from multiple variants)

Wait for the answer. Then fill in the Handoff Summary and save the file.

---

#### Handoff to Stage 2

```
## Stage 1 Handoff Summary
- Project name: [confirmed name]
- Variant chosen: [filled after user confirms]
- Description: [one line]
- Type: Educational / Standalone
- Team: Solo ([N] hrs/week) / Team ([N] people — [roles])
- Known stack: [list]
- Learning stack: [list or N/A]
- AI assistance: yes / no
- Scope: backend=[yes/no/deployed], frontend=[type or no], mobile=[yes/no], deployment=[yes/no]
- Constraints: [list or none]
- Timeline: [date or none]
```

---

## Closing

> **Stage 1 complete.** Saved as `[ProjectName]-requirements.md`.
>
> **Next:** `/project-research [ProjectName]` — competitor research, UX personas, hypotheses, requirements, and user stories.

---

## Rules

- Do not generate variants until Steps 0–6 are answered. Missing info produces bad output.
- Do not save the file until the user confirms their variant choice in Step 8.
- Educational path: learning technologies must have a **non-trivial role** — not a hello-world wrapper.
- AI assistance = yes: expand stack, note which additions are AI-assisted, slightly raise complexity estimates.
- Variants must be **genuinely different** — not name variations of the same idea.
- Do not invent team members or skills the user didn't mention.
- Stack versions come from web search, not training data.
