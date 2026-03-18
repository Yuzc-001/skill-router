---
name: skill-router
description: >
  A low-presence routing layer for skill-heavy agent environments. Use this skill whenever the user
  asks "which skill should I use?", "do we already have a skill for this?", or when multiple installed
  skills could fit a task and selection matters. Also triggers when the user wants to find, compare,
  or vet new skills before installing them, or when a task clearly exceeds all installed capabilities
  and discovery is needed. Do NOT trigger for simple tasks where the right skill is already obvious
  or active — Skill Router stays quiet when routing adds no value. Think of it as the decision layer
  that activates only when skill *choice* itself becomes part of the problem.
---

# Skill Router

A low-presence routing layer for skill-heavy agent environments.

> Choose the best installed skill first. Discover only when existing skills are clearly insufficient.

---

## Core Principle

**Installed reality beats local preference.**

Do not assume what the user should have. Route based on what they actually have installed.

**Operational rule:**

**Discovery is for insufficiency, not novelty.**

Search for new skills only when the installed set genuinely cannot handle the task — not because a newer or shinier option might exist somewhere.

---

## When This Skill Activates

Skill Router activates when skill *selection* is part of the task:

- The user asks "which skill should I use?" or "do we have a skill for X?"
- Multiple installed skills could plausibly handle the task
- An installed skill exists but is easy to forget (buried in a large collection)
- No installed skill fits and discovery needs to happen
- The user wants to install an unfamiliar third-party skill and vetting is appropriate

Skill Router does **not** activate when:

- The task is simple and should just be done directly
- The right skill is already clearly active and working
- Adding routing commentary would make the task heavier than the work itself
- Only one installed skill is an obvious match — just use it

---

## Bootstrap Protocol

When Skill Router is first used in a new environment — or when the Local Map in `references/task-to-skill-map.md` is empty — run a one-time Bootstrap Scan before the first routing decision:

1. Read the full list of installed skills with their names and descriptions
2. For each skill, identify the capability category it primarily serves (reference `references/capability-taxonomy.md`)
3. Add the mapping to the Local Map section of `references/task-to-skill-map.md`
4. If two skills map to the same capability, note both and apply the tiebreaking rules under Step 3 to establish a default

The bootstrap scan transforms an empty routing table into a working one without manual configuration. After bootstrap, normal routing uses the map as a fast path.

**Trigger conditions:**
- First invocation in a new environment where the Local Map is empty — runs automatically, once
- User says "rescan my skills" or "rebuild the routing map"
- A new skill has been installed and the user wants it mapped

After the initial bootstrap, do not re-scan automatically — only when explicitly triggered.

---

## Resolution Order

Follow this sequence for every routing decision. Stop at the first sufficient resolution.

### Step 0 — Fast path: check the Local Map

Before running the full resolution sequence, check whether Bootstrap has run. If the Local Map is empty, **stop here and run the Bootstrap Protocol first** (see Bootstrap Protocol above), then return to this step.

Once the Local Map is populated, check `references/task-to-skill-map.md` for a fast-path match:

1. Check the **Local Map** for an entry matching this task type.
   - If an entry exists **and** the skill is still installed → invoke that skill. Skip Steps 1–4.
2. If no Local Map entry matches, check the **Portable Defaults** section of the same file.
   - If a Portable Default matches, scan the installed skill list to find the skill whose description matches (Portable Defaults use capability descriptions, not skill names). Once the skill name is identified and confirmed installed → invoke it. Skip Steps 1–4.
3. If neither layer matches → proceed to Step 1.

The Local Map is a cache of previous routing decisions. The Portable Defaults are environment-agnostic baseline mappings that apply in virtually any skill environment. A hit on either means the routing problem is already solved.

### Step 1 — Identify the dominant capability

Determine the single most important capability the task requires. Reference `references/capability-taxonomy.md` if the capability is ambiguous.

Do not decompose the task into a long list of sub-capabilities. Find the dominant one.

### Step 2 — Inspect installed skills

Read the list of installed skills from the current context — in Claude Code this appears as the skill list in the system prompt or the `available-deferred-tools` section of the system reminder; in other environments use whatever skill enumeration mechanism the platform provides. Build a mental map of what is already present.

Note the following during inspection:

- **Skill families:** Skills with a shared prefix form coordinated sets. Routing to one may imply awareness of others in the same family. See the Skill Families section for family routing rules, and the Local Map for families discovered in your environment.
- **Example copies:** Skills prefixed with `example-skills:` are reference copies of their originals. If both `pdf` and `example-skills:pdf` are installed, always prefer the non-example version.
- **Pipeline skills:** Some families are designed for sequential use (plan → execute → review). When routing to a pipeline skill, determine whether the user's task calls for a single step or the full pipeline.

### Step 3 — Find the strongest installed match

Match the dominant capability against installed skills. Prefer:

1. **Direct match** — an installed skill whose primary purpose is this capability
2. **Strong secondary match** — an installed skill that handles this capability well, even if it is not the skill's primary purpose
3. **Small combination** — two installed skills used together, but only if the combination materially changes the outcome vs. using one alone

Do not combine more than two skills unless the user explicitly asks for a complex pipeline.

**Tiebreaking equal matches**

When two installed skills match equally well for the same capability, apply this priority order:

1. **Non-example over example** — `pdf` beats `example-skills:pdf`
2. **Dedicated over general** — a skill whose primary purpose is this capability beats one that handles it secondarily
3. **Platform-specific over generic** — if the task names a platform, the platform skill wins
4. **Most recently used** — if context suggests which one the user has used recently, prefer it

If none of these apply, pick either one and move on. Do not present a comparison.

### Step 4 — Apply the enough-is-enough rule

If the best installed match is good enough to complete the task to a reasonable standard, **invoke it and stop**. Do not search for something better.

Apply this three-question test:

1. Can this skill accept the task's input format?
2. Can this skill produce the output type the user needs?
3. Is the skill's output quality sufficient for the user's stated purpose?

If all three answers are yes — **invoke the selected skill by name** (using the Skill tool or equivalent invocation mechanism) and stop. Do not narrate the routing decision unless the user asks. If any answer is no — proceed to Step 5.

### Step 5 — Discovery (only if Steps 3–4 fail)

If no installed skill can reasonably handle the dominant capability:

1. State clearly what capability is missing
2. Search for candidate skills:
   - If `find-skills` is installed → delegate discovery to it
   - Otherwise → search via skill registries, MCP search, or web search
3. Present candidates with a brief rationale for each
4. Route unfamiliar third-party candidates through vetting (Step 6) before recommending installation

### Step 6 — Vet before install

For any candidate skill that is:

- from an unfamiliar or unvetted source
- third-party (not from the user's own collection or a trusted registry)
- requesting broad permissions or system access

Apply the vetting checklist from `references/publish-safe-runtime-contract.md` before recommending installation:

- What does it claim to do?
- What permissions does it request?
- Does the scope match the stated purpose, or is it suspiciously broad?
- Is the source identifiable and accountable?
- Would you be comfortable recommending this to a non-technical user?

If vetting raises concerns, say so plainly. Do not install first and vet later.

---

## Six Routing Behaviors

These are the behaviors Skill Router adds to the environment. They are not steps — they are principles that inform every routing decision.

### 1. Reuse-First

Always prefer an installed skill over discovering a new one. The cost of discovery (search time, evaluation, installation, learning curve) almost always exceeds the cost of using a slightly-less-perfect installed skill.

### 2. Installed-Reality-First

Route based on what the user actually has, not what you think they should have. Never say "you should install X" when an installed skill can do the job.

### 3. Discovery Only for Insufficiency

Search for new skills only when the installed set genuinely cannot handle the task. "There might be something better" is not a reason to search.

### 4. Vet Before Unfamiliar Install

Never recommend installing an unfamiliar third-party skill without reviewing it first. See Step 6 above.

### 5. Quiet by Default

If routing is obvious (one clear match, simple task, skill already active), say nothing about routing. Do not narrate your routing process. Do not add meta-commentary like "I chose this skill because..." unless the user explicitly asks why.

The goal is to be invisible when things are simple and helpful only when choice is genuinely hard.

### 6. Self-Updating Map

When a routing decision is made for a task type with no existing map entry, add it to `references/task-to-skill-map.md` after the task completes. The routing table should grow with use. Only add repeatable patterns, not one-off decisions.

---

## Guidance on Edge Cases

### Multiple equally strong matches

Apply the tiebreaking rules under Step 3 in order. If none of them break the tie, pick either one and move on. Do not present a comparison unless the user asks.

### The user asks for a specific skill by name

If the user names a specific installed skill, use it. Do not second-guess. Skill Router respects explicit intent.

### Two installed skills appear identical (e.g., `pdf` and `example-skills:pdf`)

Apply tiebreaking rule 1 from Step 3: always prefer the non-example version. The `example-skills:` prefix marks a reference copy. If the user explicitly asks to use the example version, respect that.

### The user wants to explore / browse skills

This is a legitimate use case. Help them explore, but do not treat browsing as an installation mandate. Showing options ≠ recommending installation.

### A task is too simple for any skill

Some tasks do not need a skill at all. If the task can be done directly (a quick answer, a one-liner, a small edit), just do it. Do not route to a skill for the sake of routing.

---

## Skill Families

Some installed skills belong to coordinated families — groups of skills that share a prefix and are designed to work together. Routing decisions should account for family-level behavior.

**Identifying families:** During Bootstrap Scan, Skill Router reads each installed skill's name and description, groups skills by shared prefix, and records discovered families in the Local Map. The specific families present depend entirely on what the user has installed — they are not known in advance.

**Routing rules that apply to all families:**

- **Prefix grouping:** Skills with a shared prefix (e.g. `foo-*` or `bar:*`) form a coordinated set. Routing to one skill in a family should account for what else in the family is available.
- **Pipeline families:** Some families are designed for sequential use (plan → execute → review). When routing to a pipeline family, determine whether the user needs a single step or the full pipeline before recommending one skill.
- **Process families:** Some families govern *how* work is approached rather than *what* is produced. These typically self-route based on the current phase of work. Skill Router does not need to actively route to them unless the user asks.
- **Example copies:** Skills prefixed with `example-skills:` are reference copies of their originals, included for learning purposes. Always lower priority than their non-example counterparts. If both `foo` and `example-skills:foo` are installed, route to `foo`.

---

## Reminder Policy

Skill Router follows the reminder policy in `references/reminder-policy.md`. The short version:

- Do not remind the user that Skill Router exists on every turn
- Do not add routing footers or headers to normal responses
- Surface routing information only when the user asks, or when a genuine routing decision was made that the user should know about
- If in doubt, say less

---

## Reference Files

Read these as needed — not on every invocation.

| File | When to read |
|---|---|
| `references/capability-taxonomy.md` | When the dominant capability is ambiguous or you need to classify a novel task |
| `references/resolution-order.md` | Detailed walkthrough of the resolution sequence with examples |
| `references/publish-safe-runtime-contract.md` | When vetting a third-party skill candidate |
| `references/reminder-policy.md` | When unsure how much to say about routing |
| `references/micro-routing-examples.md` | Quick reference for common routing patterns |
| `references/local-overrides-example.md` | When the user has local routing preferences or overrides |
| `references/task-to-skill-map.md` | When building or maintaining a local routing map |
| `docs/public-surface.md` | When checking what this skill publicly guarantees vs. what is local-only |
