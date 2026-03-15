# Resolution Order

Detailed walkthrough of Skill Router's resolution sequence.

This expands on the resolution order in SKILL.md with worked examples and decision rationale.

---

## The Sequence

```
Task arrives
  → Step 1: Identify dominant capability
  → Step 2: Inspect installed skills
  → Step 3: Find strongest installed match
  → Step 4: Apply enough-is-enough rule
  → Step 5: Discovery (only if 3–4 fail)
  → Step 6: Vet before install (only if 5 finds unfamiliar candidates)
```

Each step is a **gate**. Stop at the first step that produces a sufficient resolution.

---

## Step 1 — Identify Dominant Capability

**Goal:** Reduce the task to a single capability category.

**Method:**
- Read the task as stated
- Ask: "What determines whether the user considers this successful?"
- Map that to a capability category (see `capability-taxonomy.md`)

**Common mistake:** Decomposing the task into 5+ sub-capabilities and trying to match each one. This leads to over-complex routing. Find the dominant one.

### Example

> "Research the top 5 CRM tools, compare their pricing, and create a slide deck for our team meeting."

Sub-capabilities: research, comparison, document creation.

**Dominant capability:** Document Creation. The deliverable is the slide deck. Research and comparison are inputs to that deliverable. Route to the best installed skill for creating presentations.

---

## Step 2 — Inspect Installed Skills

**Goal:** Build an accurate picture of what's already available.

**Method:**
- Read the full list of installed skills (names + descriptions)
- Note which ones are relevant to the dominant capability
- Note which ones are adjacent (might help as secondary support)

**Common mistake:** Skimming skill names without reading descriptions. A skill named `data-pipeline` might also handle CSV transformation. A skill named `report-builder` might also do presentations.

---

## Step 3 — Find Strongest Installed Match

**Goal:** Pick the best installed skill for the dominant capability.

**Priority order:**

### 3a. Direct Match

An installed skill whose **primary purpose** is the dominant capability.

> Task needs: Document Creation (presentations)
> Installed: `pptx` skill — primary purpose is creating PowerPoint files
> → Direct match. Route here.

### 3b. Strong Secondary Match

An installed skill that handles the dominant capability well, even though it's not the skill's main purpose.

> Task needs: Data Analysis (CSV insights)
> Installed: `xlsx` skill — primary purpose is spreadsheet creation, but it reads and analyzes CSVs well
> → Strong secondary match. Route here.

### 3c. Small Combination

Two installed skills used together, but **only** if the combination produces a materially better outcome than either alone.

> Task needs: "Analyze survey data and create a visual report"
> Installed: `xlsx` (data analysis) + `pdf` (report creation)
> → Combination adds value: xlsx for the analysis, pdf for the formatted output.

**Guard against over-combination.** If one skill can do the whole job at 80% quality, prefer it over a two-skill pipeline at 90% quality. The coordination cost matters.

---

## Step 4 — Enough-Is-Enough Rule

**Goal:** Decide if the installed match is sufficient. Stop searching if it is.

**The test:** Would the user be materially harmed or meaningfully slowed by using this skill instead of a hypothetical perfect one?

- If **no** → Route here. Done.
- If **yes** → Proceed to Step 5.

### Examples

**Enough:**
> Task: "Create a simple PDF summary of these meeting notes"
> Best installed match: `pdf` skill (handles PDF creation well)
> Is this enough? Yes. A basic PDF skill can produce a clean summary. The user is not harmed.

**Not enough:**
> Task: "Build a real-time collaborative dashboard with live data feeds"
> Best installed match: `frontend-design` skill (creates static web pages)
> Is this enough? No. The task requires real-time data and collaboration features that a static frontend skill cannot provide. Discovery is warranted.

**Borderline (still enough):**
> Task: "Create a professional-looking slide deck with custom animations"
> Best installed match: `pptx` skill (creates presentations, limited animation support)
> Is this enough? Yes. The skill can create a professional deck. Custom animations are a nice-to-have, not a requirement for the task to succeed.

---

## Step 5 — Discovery

**Goal:** Find candidate skills to fill a genuine capability gap.

**Triggers — proceed to discovery only when:**
- No installed skill can handle the dominant capability at all
- The best installed match would produce a result the user would clearly reject
- The task requires a specific integration or tool that no installed skill provides

**Do not discover when:**
- An installed skill is "okay but not great" — that's enough
- You think a better skill might exist somewhere — that's novelty, not insufficiency
- The user hasn't complained about the installed option — respect their setup

**Discovery method:**
1. State the missing capability clearly: "None of your installed skills handle [X]."
2. Search available registries or sources
3. Present 1–3 candidates with brief rationale
4. If candidates are from unfamiliar sources, proceed to Step 6

---

## Step 6 — Vet Before Install

**Goal:** Ensure unfamiliar third-party skills are safe and appropriate before installation.

**Applies to:**
- Skills from sources the user hasn't used before
- Skills with broad permission requests
- Skills from unknown authors or organizations

**Does not apply to:**
- Skills from the user's own collection
- Skills from trusted, known registries
- Skills the user has previously installed and used

See `publish-safe-runtime-contract.md` for the full vetting checklist.

---

## Quick Reference: Resolution Cheat Sheet

| Situation | Resolution |
|---|---|
| One obvious installed skill matches | Use it. Say nothing about routing. |
| Two installed skills match equally | Pick the more specific one. Move on. |
| Installed match is okay but not perfect | Use it. Enough is enough. |
| No installed skill matches at all | Discovery. State the gap clearly. |
| Discovery finds a familiar, trusted skill | Recommend installation. |
| Discovery finds an unfamiliar third-party skill | Vet first, then recommend if safe. |
| Task is too simple for any skill | Just do it directly. No routing needed. |
| User names a specific skill | Use that skill. Do not second-guess. |
