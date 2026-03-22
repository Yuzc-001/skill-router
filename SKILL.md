---
name: skill-router
description: >
  Use when the user asks which skill to use, whether an installed skill already exists,
  whether the current skill environment is sufficient, or whether an unfamiliar skill should be
  vetted before installation. Also use when multiple installed skills overlap enough that the
  default choice is genuinely unclear. Do NOT use for simple execution, obvious single-skill
  matches, or cases where routing would not change the next action.
---

# Skill Router

Use this skill only when **skill choice itself** is blocking progress.

Its job is to reduce:
- repeated discovery of already-installed skills
- repeated comparison between overlapping skills
- unnecessary installation when the current environment is already enough
- routing commentary that costs more than the decision itself

If routing will not change the next real action, do not use this skill further.

## Trigger boundary

### Activate when
- the user asks which skill to use
- the user asks whether a skill already exists for the task
- multiple installed skills plausibly fit and the default is genuinely unclear
- the current installed environment may be insufficient
- the user wants to evaluate an unfamiliar skill before installation

### Do not activate when
- the task should just be executed directly
- one installed skill is the obvious match
- the correct skill is already active
- the user explicitly named the skill to use
- more routing detail would not change the next action

If unsure, prefer silence.

## Main path

Follow this path and stop as soon as a sufficient answer appears.

### Step 0 — Decide whether routing is needed
Ask:

**Will a routing decision materially change the next action?**

If no, stop. This task does not need skill-router.

### Step 1 — Prefer installed reality
Check the installed environment first.

If there is already:
- a clearly sufficient installed skill, or
- a stable local default for this overlap,

use it and stop.

### Step 2 — Test genuine insufficiency
Only escalate if the installed set is actually not enough.

Use the minimum test:
1. Can an installed skill accept the task input?
2. Can an installed skill produce the needed output?
3. Is the quality sufficient for the user’s real purpose?

If all three are yes, stay with the installed path.
If any answer is no, continue.

### Step 3 — Discover only for a real gap
If the installed environment is genuinely insufficient:
- state what capability is missing
- keep the candidate set small
- prefer concrete candidates over broad browsing
- if `find-skills` is installed, prefer delegating discovery to it

### Step 4 — Vet unfamiliar candidates before recommendation
If a candidate is unfamiliar, third-party, or broad in permissions:
- vet it before recommending installation
- compare scope to stated purpose
- check source accountability
- prefer caution over enthusiasm

## Output style

Default outputs should be short and executable.

Preferred shapes:
- `Use X.`
- `The installed set is sufficient; use X.`
- `The installed set is not enough; discover candidates.`
- `Candidate is unfamiliar; vet before recommendation.`
- `This task does not need skill-router.`

Do not output long routing analysis unless the user explicitly asks for reasoning.

## Default rules

Use these only when they change the decision:
- installed beats imagined
- sufficient beats newer
- dedicated beats general
- platform-specific beats generic
- recurring overlap should converge to a stable default

## Reference files

Read only when needed.

| File | Read when |
|---|---|
| `references/task-to-skill-map.md` | checking or recording a stable local default |
| `references/micro-routing-examples.md` | you need short examples for overlap / insufficiency / vetting |
| `references/local-overrides-example.md` | the user has an explicit local routing preference |
| `references/publish-safe-runtime-contract.md` | vetting an unfamiliar candidate |
| `references/resolution-order.md` | you need the expanded version of the main path |
| `references/sufficiency-policy.md` | the real question is whether the installed path is actually strong enough for the user’s bar |
| `references/default-update-policy.md` | the question is whether a stored default/override should stay, update, narrow, or be ignored |
| `references/crowded-environment-policy.md` | environment size is creating fake routing complexity or irrelevant-skill noise |
| `references/ambiguity-fallback-policy.md` | routing is needed but the task is still under-specified or unusually ambiguous |
| `references/distrust-and-clarification-policy.md` | the user expresses distrust, uncertainty, or the real issue may be missing task information |
| `references/capability-taxonomy.md` | the task is unusually ambiguous and installed reality still does not reveal the dominant path |
| `docs/public-surface.md` | checking what this skill publicly promises |

## Keep in mind

This skill is successful only if it reduces decision waste.
If it is adding commentary without changing the decision, it is failing.
n mind

This skill is successful only if it reduces decision waste.
If it is adding commentary without changing the decision, it is failing.
sion, it is failing.
