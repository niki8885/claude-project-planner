---
name: project-research
version: "1.1"
description: >
  IT project planning Stage 2 — competitor research, UX personas, user hypotheses, requirements,
  value proposition, strategic positioning, and user stories.
  Use after the user has confirmed a project variant from /project-init.
  Triggers on: "stage 2", "research phase", "find competitors", "user personas", "user stories",
  "I've chosen my project", "let's do research", "next stage".
argument-hint: "[project name]"
allowed-tools: WebSearch
---

# IT Project Planner — Stage 2: Research & Requirements

**Language rule:** Respond in the same language the user writes in. All generated documents are always in English.

---

## Input validation

Before starting, verify you have the Stage 1 handoff. Look for:
- Project name and one-line description
- Confirmed variant
- Team composition (solo/team, roles)
- Known stack and learning stack (if educational)
- Scope decisions (backend, frontend, mobile, deployment)

If the `[ProjectName]-requirements.md` file or Stage 1 Handoff Summary is not present in the conversation, ask:

> I need the Stage 1 output to proceed. Either:
> - Paste the **Stage 1 Handoff Summary** from `[ProjectName]-requirements.md`, or
> - Run `/project-init [topic]` first if you haven't completed Stage 1 yet.

Do not proceed without this data. Do not invent project parameters.

---

## Execution sequence

Work through steps in order. Show a progress header before each step so the user sees progress. Do not ask for input between steps — gather everything yourself.

---

## Step 1 — Competitor Research

Search the internet for **3 to 5 real competitors or closely related products**.

Use domain-based queries, not the project name. Always include the current year for fresh results:
- `"[domain] software platform 2025"`
- `"best tools for [use case] 2025"`
- `"[domain] app alternatives 2025"`
- `"[domain] SaaS comparison 2025"`

**Fallback rule:** If fewer than 3 real direct competitors are found, include analogous tools from adjacent domains and mark each with **[adjacent]** in the product name. Do not invent tools — adjacent real products are always available.

For **each competitor**, write:

```
### N. [Product Name] ([Parent Company]) [adjacent — if applicable]

**Website:** [URL]

**Product:**
[2–3 sentences: what this product is and what it actually does.]

**Market Position:**
[Who uses it, what segment, how it is perceived.]

**Capabilities:**
- [Key capability 1]
- [Key capability 2]
- [Key capability 3]
- [Key capability 4]

**Limitations:**
- [Limitation 1]
- [Limitation 2]
- [Limitation 3]
```

Only use real, verifiable products. Do not fabricate capabilities or limitations.

---

## Step 2 — UX Personas

Based on the project domain, competitor research, and typical users of such tools, define **3 to 5 personas**.

Number of personas:
- Solo project, simple scope → 3 personas
- Team project or broad user base → 4–5 personas

Each persona:

```
### N. [Role Title]

_"[One-sentence quote capturing their core frustration or goal.]"_

**Profile:** [2–3 sentences: experience level, what they do, tools they use, how they think.]

**Context:** [When and how they use tools like this. Frequency, environment, workflow.]

**Pain Points:**
- [Specific pain point 1]
- [Specific pain point 2]
- [Specific pain point 3]
- [Specific pain point 4]

**Goals:** [What they're ultimately trying to achieve — outcomes, not features.]

**Key Need:** [The single most critical capability this persona needs.]
```

Personas must be distinct from each other and grounded in the competitor research.

---

## Step 3 — User Hypotheses

Write **8 to 12 hypotheses** about what users value and what will drive or block adoption.

```
**H1** [Concrete, testable hypothesis. 2–3 sentences. Non-obvious — not "users want it to work."]

**H2** ...
```

Focus on: interpretation vs. raw data preferences, adoption drivers, insights from the market gap between competitors.

---

## Step 4 — User Requirements

Group into **4 to 6 thematic sections** based on the product's feature areas.

```
### [Section Name]

- **[Requirement Name]:** [One sentence: what the user needs and why it matters.]
```

End with a **Technical & Performance Requirements** table (5–8 rows):

```
| User Need | Technical Requirement |
|-----------|----------------------|
| "[User quote]" | [What the system must do] |
```

---

## Step 5 — Value Proposition

### Core Value Proposition
1–2 sentences: what the product transforms, for whom, through what mechanism.

**Differentiator table** (3–5 rows, reference competitors by name):

```
| Component | Unique Edge vs. [Competitor] | Why Users Care |
|-----------|------------------------------|----------------|
```

### Problem Statement

Three paragraphs:
1. The broad industry problem (what exists but falls short)
2. Consequence for users (what they do instead and what it costs)
3. How this product solves it specifically

---

## Step 6 — Strategic Positioning

### Strategic Positioning
1–2 sentence statement: what kind of platform this is and what makes it distinct.

### Core Differentiators

4–6 subsections:
```
#### [Differentiator Name]
[2–3 sentences: the technical or UX mechanism and why competitors don't have it.]
```

### Market Gap
2–3 sentences: what enterprise tools get wrong, what lightweight tools lack, and the segment this fills. Close with 4–5 bullet list of what this product uniquely combines.

---

## Step 7 — Interview Guide

Generate a structured interview guide. This will be used by `/project-interviews` to simulate persona responses.

Organize into blocks matching the product domain:
- **Block 1 — Background** (experience, role, what they work on)
- **Block 2 — Workflow** (daily routine, tools, how they start their day)
- **Block 3 — [Core feature area 1]** (domain-specific questions)
- **Block 4 — [Core feature area 2]**
- **Block 5 — Risk & Decision-Making** (how they evaluate, what they fear)
- **Block 6 — Existing Tools** (what they use, hate, would replace)

5–8 open-ended, non-leading questions per block. Questions surface pain points, workarounds, and unmet needs.

```
# Block N — [Block Name]

## [Question text]

## [Question text]
```

---

## Step 8 — User Stories

Write **25 to 36 user stories** in **7 to 9 thematic clusters**.

```
## Cluster N: [Cluster Name]

**USN: [Story Title]** As a [persona role], I want [capability], so that [outcome] — without [current painful workaround].

- Acceptance Criteria:
    - [Testable criterion 1]
    - [Testable criterion 2]
    - [Testable criterion 3]
    - [Testable criterion 4]

---
```

Rules:
- "As a" references a defined persona role
- 4–5 acceptance criteria per story, specific and testable
- Most critical stories first within each cluster

---

## Output: Two Documents

### Document 1: `[ProjectName]-research.md`

Contents in this order:
1. Competitors
2. Strategic Positioning
3. User Hypotheses
4. User Requirements
5. UX Personas
6. Value Proposition + Problem Statement
7. User Stories

### Document 2: `[ProjectName]-interview-guide.md`

Contains only the Interview Guide (Step 7 output — Block 1 through Block 6 with all questions).
Saved separately so `/project-interviews` can load it without parsing the full research document.

---

## Quality rules

- All generated document content in **English** regardless of conversation language.
- All competitor data from real web search results — no invented capabilities.
- Hypotheses grounded in competitor research and personas — not generic platitudes.
- User stories traceable to at least one persona's pain point.
- Strategic positioning explicitly references 2–3 named competitors.
- Document must be self-contained — a reader who hasn't seen Stage 1 should understand the project from it.

---

## Closing

After both documents are written, tell the user:

> **Stage 2 complete.**
> - Research & requirements: `[ProjectName]-research.md`
> - Interview guide: `[ProjectName]-interview-guide.md`
>
> **Next steps:**
> - `/project-mvp [ProjectName]` — build the MVP matrix, release staging, and KPIs. *(required next step)*
> - `/project-interviews [ProjectName]` — simulate persona interviews. **Run this before `/project-mvp`** if you want interview findings to refine your hypotheses before building the MVP matrix. Skip if you want to move faster — interviews are optional.
