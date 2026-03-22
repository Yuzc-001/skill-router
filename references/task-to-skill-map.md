# Task-to-Skill Map

A lightweight local-default record for recurring routing decisions.

This file is no longer the center of the system.
It exists only to prevent repeated comparison in places where the environment has already taught us a stable default.

---

## What this file is for

Use this file to record:
- recurring overlap clusters that already have a stable default
- installed defaults that repeatedly save comparison cost
- local overrides that the user clearly prefers

Do **not** use this file to:
- build a giant universal routing taxonomy
- force every task into a mapping table
- record distinctions that do not change the next action
- replace judgment with a lookup ritual

If a mapping does not reduce repeated routing waste, it does not belong here.

---

## How to use it

1. Ask whether the task even needs routing
2. If routing is needed, check whether this file already contains a stable local default
3. If yes, use it and stop
4. If no, resolve the task through the main path in `SKILL.md`
5. Only record the result here if it is likely to reduce recurring comparison later

---

## What belongs here

Good entries usually look like one of these:
- a recurring browser-skill overlap with a stable default
- a recurring search overlap with a stable default
- a platform-specific preference that repeatedly beats the generic option
- a strong local preference the user wants preserved

Bad entries usually look like one of these:
- one-off tasks
- mappings that are obvious without recording
- distinctions that never change the next action
- speculative defaults for tools not actually installed

---

## Entry format

Use a compact format:

```text
Task / overlap cluster → default skill | Confidence: high|medium
Notes: only if they materially change routing
```

Keep notes short.
If the note is longer than the routing decision, the entry is probably not worth keeping.

---

## Local Defaults

```text
# Record only stable defaults that reduce recurring routing waste.
# Example format:
# Browser control / interactive web tasks → pinchtab-browser | Confidence: high
# Notes: prefer agent-browser only when headless fallback is specifically needed
```

---

## Local Overrides

```text
# Record only explicit user or environment overrides.
# Example format:
# Web search → tavily-search | Confidence: medium
# Notes: user prefers Tavily summaries over broader search results in this environment
```

---

## Maintenance rule

This file should stay small.

If it keeps growing without clearly reducing repeated comparison, it is being misused.

The purpose of this map is not coverage.
The purpose is convergence.

---

## Bottom line

A good task-to-skill map is not comprehensive.
A good task-to-skill map quietly removes a few recurring sources of decision waste.
