---
name: project-interviews
version: "1.1"
description: >
  IT project planning — simulated UX interviews. Role-plays as each defined persona and answers
  the interview guide from Stage 2 in first person, revealing real pain points, workflows, and
  decision drivers. Run after /project-research. Can be run before or after /project-mvp.
  Triggers on: "simulate interviews", "interview personas", "run interviews", "project interviews",
  "UX interviews", "talk to personas".
argument-hint: "[project name]"
---

# IT Project Planner — Simulated UX Interviews

**Language rule:** Respond in the same language the user writes in. The interview document itself is always in English.

---

## Input validation

Before starting, verify you have the Stage 2 output. You need:
- List of defined UX personas (names, profiles, pain points)
- The Interview Guide (Block 1–6 with questions)

If `[ProjectName]-interview-guide.md` or `[ProjectName]-research.md` is not available, ask:

> I need the Stage 2 output to run interviews. Either:
> - Paste the contents of `[ProjectName]-interview-guide.md` (look for the section starting with `# Block 1 — Background`), or
> - Paste the **UX Personas** section from `[ProjectName]-research.md`, or
> - Run `/project-research [ProjectName]` first if Stage 2 isn't done yet.

---

## Scoping questions

Ask the user two questions before generating:

> **1. Which personas should I interview?**
> - **All** — interview every persona defined in Stage 2
> - **Select** — tell me which ones (by number or role name)
>
> **2. Interview depth?**
> - **Brief** — 2–3 key questions per block, short answers. Best for quick insight scan.
> - **Standard** — all questions, realistic answer length. Balanced depth vs. context size.
> - **Deep** — all questions, extended answers with hesitations, tangents, strong opinions, specific numbers and examples. Best for nuanced insight.

Wait for answers. Then proceed.

---

## Simulation rules

For each selected persona, role-play as that person answering the interview guide.

**Core rules:**
- Answer strictly in first person as the persona
- Answers must reflect the persona's specific profile — experience level, stack knowledge, pain points, vocabulary
- Do NOT give generic answers that could apply to any persona
- Show the persona's mental model: a quant hobbyist thinks and speaks differently than a portfolio manager
- Include authentic friction: hesitations, strong opinions, contradictions, things they have tried and abandoned
- Use specific numbers, tool names, and scenarios where they feel natural
- Vary answer format: some answers are a short paragraph, some are bullet lists, some are one strong sentence

**Depth calibration:**
- **Brief:** Answer only the 2–3 most revealing questions per block. 1–3 sentence answers. Total per persona: ~30–40 lines.
- **Standard:** Answer all questions. Mix of paragraph and list formats. Total per persona: ~80–120 lines.
- **Deep:** Answer all questions with extended responses. Include specific war stories, tool comparisons, workflow details, and things the persona would never say out loud to a vendor but would say to a researcher. Total per persona: ~150–250 lines.

---

## Output format

For each persona, write:

```
---

## Interview — [N]. [Persona Role Title]

> _"[Their defining quote from Stage 2]"_

---

# Block 1 — Background

### [Question text]

[Answer as this persona]

---

### [Question text]

[Answer]

---

# Block 2 — Workflow

### [Question text]

[Answer]

---

[Continue through all blocks]
```

Separate personas with a prominent `---` divider and a new persona header.

---

## Output: One Document

Save as `[ProjectName]-interviews.md`

Contents:
- One interview section per selected persona
- Each section covers all interview blocks at the chosen depth
- At the end: **Cross-Persona Insights** — a 10–15 bullet synthesis of the most important patterns, contradictions, and surprises across all personas. This is the part that feeds hypothesis validation.

```
---

## Cross-Persona Insights

- [Pattern or contradiction observed across multiple personas]
- [Something surprising that conflicts with a Stage 2 hypothesis — flag which one]
- ...
```

---

## Quality rules

- Every answer must be traceable to that persona's Stage 2 profile — do not blend personas.
- Disagreements between personas are valuable — if two personas would answer the same question differently, show that contrast.
- Do not make all personas agree. Real user research surfaces conflict.
- The Cross-Persona Insights section must reference specific hypothesis numbers from Stage 2 (H1, H2, etc.) where relevant — note which hypotheses are confirmed, challenged, or need deeper testing.
- **Fallback:** If Stage 2 hypotheses (H1–HN) are not available in the conversation, note patterns and contradictions without referencing hypothesis numbers. Write: "*(hypotheses not available — patterns noted without H-number references)*" at the top of Cross-Persona Insights.

---

## Closing

After the document is complete, tell the user:

> **Interviews complete.** Document saved as `[ProjectName]-interviews.md`.
>
> Review the **Cross-Persona Insights** section — findings that contradict your Stage 2 hypotheses are the most valuable inputs for refining the product scope.
>
> **Next:** `/project-mvp [ProjectName]` — MVP matrix, release staging, and KPIs.
