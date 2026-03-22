# Crowded Environment Policy

Use this file when the installed skill environment is large enough that noise itself becomes part of the problem.

This file exists to keep Skill Router focused on the few skills that materially matter.

---

## Core rule

A crowded environment should collapse to the same routing decision as a sparse environment when only a small number of skills are actually relevant.

Irrelevant installed skills should not create fake routing complexity.

---

## Relevance rule

Treat an installed skill as relevant only if it materially participates in the current decision.

A skill is relevant when at least one is true:
- it directly matches the task’s output or destination
- it belongs to the real overlap cluster for this task
- it materially changes the likely next action

If none of those are true, ignore it.

---

## Anti-noise rule

Do not expand routing because the environment is large.

The following are **not** reasons to add routing detail:
- many unrelated installed skills exist
- several skills have vaguely similar descriptions
- multiple meta/process skills are available but none clearly change the next action

Noise is not conflict.

---

## Overlap rule

Only real overlap clusters belong in the routing decision.

Examples of real overlap:
- two search skills for the same search task
- two browser-control skills for the same interaction task
- two publishing skills for the same destination platform

Examples of fake overlap:
- a document tool and a weather tool both being installed
- a broad process skill being present alongside a clearly dedicated tool
- many installed skills sharing abstract words like “automation” or “workflow”

---

## Crowded-environment output rule

Even in a 50-skill or 100-skill environment, the output should stay short.

Preferred shape:
- `Use X.`
- `The installed set is not enough; discover candidates.`

Do not let environment size turn routing into commentary.

---

## Bottom line

The larger the environment gets, the more important it is that Skill Router ignores what does not matter.
