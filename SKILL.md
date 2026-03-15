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

## Resolution Order

Follow this sequence for every routing decision. Stop at the first sufficient resolution.

### Step 1 — Identify the dominant capability

Determine the single most important capability the task requires. Reference `references/capability-taxonomy.md` if the capability is ambiguous.

Do not decompose the task into a long list of sub-capabilities. Find the dominant one.

### Step 2 — Inspect installed skills

Read the user's installed skill environment (the `available_skills` list or equivalent). Build a mental map of what is already present.

### Step 3 — Find the strongest installed match

Match the dominant capability against installed skills. Prefer:

1. **Direct match** — an installed skill whose primary purpose is this capability
2. **Strong secondary match** — an installed skill that handles this capability well, even if it is not the skill's primary purpose
3. **Small combination** — two installed skills used together, but only if the combination materially changes the outcome vs. using one alone

Do not combine more than two skills unless the user explicitly asks for a complex pipeline.

### Step 4 — Apply the enough-is-enough rule

If the best installed match is good enough to complete the task to a reasonable standard, **route there and stop**. Do not search for something better.

"Good enough" means: the user would not be materially harmed or meaningfully slowed by using this skill instead of a hypothetical perfect one.

### Step 5 — Discovery (only if Steps 3–4 fail)

If no installed skill can reasonably handle the dominant capability:

1. State clearly what capability is missing
2. Search for candidate skills (via skill registries, MCP search, or web search as appropriate)
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

## Five Routing Behaviors

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

---

## Guidance on Edge Cases

### Multiple equally strong matches

If two or more installed skills match equally well, prefer:
1. The one the user has used more recently (if you can tell)
2. The one with narrower scope (specialists over generalists)
3. Either one — just pick and move on. Do not present a comparison unless the user asks.

### The user asks for a specific skill by name

If the user names a specific installed skill, use it. Do not second-guess. Skill Router respects explicit intent.

### The user wants to explore / browse skills

This is a legitimate use case. Help them explore, but do not treat browsing as an installation mandate. Showing options ≠ recommending installation.

### A task is too simple for any skill

Some tasks do not need a skill at all. If the task can be done directly (a quick answer, a one-liner, a small edit), just do it. Do not route to a skill for the sake of routing.

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
