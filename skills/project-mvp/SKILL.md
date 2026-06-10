---
name: project-mvp
version: "1.1"
description: >
  IT project planning Stage 3 — MVP matrix with Impact/Complexity/Stack Risk evaluation,
  release staging from Prototype to final version, primary KPI with formula, advanced economic model,
  and system positioning. Run after /project-research.
  Triggers on: "stage 3", "MVP", "prioritize stories", "KPI", "release plan", "roadmap",
  "what goes in the MVP", "plan the MVP", "which stories first".
argument-hint: "[project name]"
allowed-tools: WebSearch
---

# IT Project Planner — Stage 3: MVP Matrix, Release Staging & KPIs

**Language rule:** Respond in the same language the user writes in. The generated document is always in English.

---

## Input validation

Before starting, verify you have Stage 2 output. You need:
- Project name, description, confirmed variant
- Team composition, stack, complexity level (from Stage 1)
- Full list of User Stories US1–USN with cluster groupings (from Stage 2)

If `[ProjectName]-research.md` or the user stories are not available, ask:

> I need the Stage 2 output to build the MVP plan. Either:
> - Paste the **User Stories** section from `[ProjectName]-research.md` and the **Stage 1 Handoff Summary** from `[ProjectName]-requirements.md`, or
> - Run `/project-research [ProjectName]` first if Stage 2 isn't done yet.

Do not proceed without the user stories. Do not invent priorities or stories.

---

## Scoping question

Ask:

> **What do you want me to produce?**
>
> **A)** MVP Matrix only — evaluate all user stories, mark which go to Prototype and which to later releases. Faster, one document.
>
> **B)** Full release breakdown — distribute every story across all stages: Prototype → MVP → Post-MVP → Final version. More detailed.

Wait for the answer. Then proceed.

---

## Step 1 — Evaluation Dimensions

Open the document with this section, adapted to the actual project:

```
## Evaluation Dimensions

- **User Impact**
    - High — Critical for core value delivery; removing it breaks the product promise
    - Medium — Useful, expected, but the product functions without it at first
    - Low — Enhancement, edge case, or niche need

- **Implementation Complexity**
    - High — Requires ML / external APIs / hardware / advanced math / unfamiliar technology
    - Medium — Standard backend/frontend logic, API integration, data processing
    - Low — Basic UI, simple logic, CRUD, configuration

- **Stack Risk**
    - Elevated — Story requires technology the team does not yet know
    - Normal — Story uses technology the team is comfortable with
```

Calibrate "High complexity" to the actual stack. If the team is learning Haskell, any Haskell story is High. Solo developer + external API = Elevated risk.

---

## Step 2 — Full Matrix

Every story from Stage 2 must appear. No story may be silently dropped.

```
| US ID | User Story (short name) | Impact | Complexity | Stack Risk | Priority | Rationale |
|-------|------------------------|--------|------------|------------|----------|-----------|
```

**Priority values — Option A:**
`Prototype` / `MVP` / `Post-MVP` / `Backlog`

**Priority values — Option B:**
`Prototype` / `MVP` / `v1.1` / `v1.5` / `v2.0` / `Backlog`

**Calibration rules:**
- Solo dev → elevate complexity by one level for any unfamiliar tech
- Team with role gaps → flag stories that require the missing role
- Educational project → learning technologies go to Prototype regardless of complexity (that's the point)
- High Impact + Low Complexity + Normal Stack Risk → never Backlog without an explicit written reason

---

## Step 3 — Core User Loop

The minimal sequence a user must complete for the product to be worth testing.

```
[Action 1] → [Action 2] → [Action 3] → [Outcome]
```

This loop must be fully covered by Prototype stories. If it isn't, move stories up.

---

## Step 4 — Prototype Scope

```
### Included in Prototype ([N] Stories)

| US | Feature | Role in Core Loop |
|----|---------|------------------|

### Excluded from Prototype

#### Technical Risk
- US#, US# → [reason]

#### External Dependencies
- US#, US# → [reason]

#### Non-Core Features
- US#–US# → enhancements that don't affect whether the core idea works
```

---

## Step 5 — Full Stage Breakdown (Option B only)

For each release stage:

```
## [Stage Name] — [Label, e.g. Prototype / MVP / v1.1]

### Goal
[One sentence: what must be true when this stage is complete?]

### Stories

| US | Feature | Rationale |
|----|---------|-----------|

### What this stage proves / delivers
[2–3 sentences on user value or learning unlocked]

### Team requirements
[Which roles needed, what skills exercised, any new tech introduced]
```

Stages must be realistic for team size — do not stack 20 stories into MVP for a solo developer.

---

## Step 6 — MVP Validation

```
| Criterion | Status | Explanation |
|-----------|--------|-------------|
| Complete  | Yes/No | Full user journey from input to outcome? |
| Minimal   | Yes/No | Can any included story be removed without breaking the core loop? |
| Realistic | Yes/No | Achievable given team size, stack, and timeline? |
| Testable  | Yes/No | Can real users validate the core hypothesis with what's included? |
```

Any "No" row must include a recommendation for how to fix it.

---

## Step 7 — Primary KPI

The single most important success metric. Must be:
- Tied directly to the core value proposition from Stage 2
- Measurable at Prototype or MVP stage
- Expressed as a formula where the project domain allows it

```
## Primary KPI — [Metric Name]

### Definition
[What this measures and why it is the best signal of product success.]

**Formula:**
[Plain text or LaTeX notation]

Variables:
- [var]: [definition]

**Measurement:**
- Unit: [%, seconds, dollars, events/day, etc.]
- Frequency: [daily / per session / per release]
- Source: [user logs / analytics / survey / etc.]

### Business Link

| Aspect | Explanation |
|--------|-------------|
| Value delivered | [What the user gains] |
| Willingness to pay | [Connection to monetization or retention] |
| Differentiation | [How this proves the product's unique claim] |

### KPI Targets

| Stage | Target | Stretch | Justification |
|-------|--------|---------|---------------|
| Prototype | ... | ... | ... |
| MVP | ... | ... | ... |
```

---

## Step 8 — Advanced KPI / Secondary KPIs

**Decision rule — which section to generate:**

Use **Advanced KPI** (mathematical model with formula) if the project measurably reduces or produces something with a countable unit:
- Time saved (hours/day, minutes/task)
- Money saved or earned (cost reduction, revenue increase)
- Error or risk reduced (error rate %, false negative rate)
- Resources optimized (hectares treated, API calls reduced, queries per second)

Use **Secondary KPIs** (table format) for everything else:
- Dev tools and internal tooling
- Dashboards and analytics viewers
- Educational and learning projects
- Platforms where value is engagement, not economic output

**If** the project fits the Advanced KPI trigger, add:

```
## Advanced KPI — Net [Impact] Value

### Definition
Integrates: [gain components] minus [cost/risk components]

### Mathematical Model
[Combined formula]

### Components
#### [Component name]: [Formula + variable definitions]
#### Risk Component: P(missed event) × damage value
#### System Cost: subscription + infra + optional hardware
```

**If** the project is a dev tool, educational, or has no clean economic model, replace with:

```
## Secondary KPIs

| Metric | Definition | Target at MVP | Why It Matters |
|--------|------------|---------------|----------------|
```

3–5 metrics covering: engagement, quality, performance, and — if educational — a **Learning KPI** tracking how deeply the target technology was exercised.

---

## Step 9 — System Positioning

```
## System Positioning

### What [Project Name] IS at Prototype:
- [Capability 1 — what users can actually do]
- [Capability 2]

### What [Project Name] IS NOT at Prototype:
- [Excluded capability — why intentionally excluded]

### What [Project Name] IS at MVP:
- [All prototype capabilities, plus:]
- [New capability]

### What [Project Name] IS NOT at MVP:
- [Still excluded — with rationale]
```

Be honest. Do not say the Prototype "is" something it only partially implements.

---

## Output: One Document

Save as `[ProjectName]-mvp.md`

Sections in order:
1. Evaluation Dimensions
2. Full Matrix
3. Core User Loop
4. Prototype Scope
5. Full Stage Breakdown (Option B only)
6. MVP Validation
7. Primary KPI
8. Advanced KPI / Secondary KPIs
9. System Positioning

---

## Closing

After the document is written, tell the user:

> **Stage 3 complete.** Saved as `[ProjectName]-mvp.md`.
>
> **Next:** `/project-sprints [ProjectName]` — Jira board setup, epics, sprint plan with typed tasks, full task cards with acceptance criteria, team assignment, and system architecture.
>
> **Note:** If you haven't run `/project-interviews` yet, you can still do it now. Interview findings can validate or challenge the priorities set in this MVP plan — useful before committing to the sprint breakdown.
