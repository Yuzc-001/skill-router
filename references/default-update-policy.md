# Default Update Policy

Use this file when the question is not just “what is the current default?” but:

# should the current default stay, update, or be ignored?

This file exists to keep Skill Router from becoming either rigid or noisy.

---

## Core rule

A default exists to reduce repeated routing waste.

If it is no longer reducing waste, no longer fits the real overlap, or is clearly weaker than a new stable option, it should be re-evaluated.

---

## When to keep the current default

Keep the current default when:
- it still matches the recurring task shape
- it still produces sufficient quality for the user’s actual bar
- no newly installed skill materially improves the decision
- the current default is still the shortest stable path

In these cases, avoid re-opening comparison.

---

## When to update the default

Update the default when a new option materially improves one or more of these:
- **match precision** — it is more clearly dedicated to the recurring task
- **platform precision** — it is more directly aligned with the named platform or destination
- **quality threshold** — it better satisfies the user’s stated bar
- **repeatability** — it gives a more stable and reusable default for the same recurring overlap

A new skill should not replace an old default just because it is newer.
It should replace it only when it materially improves the recurring decision.

---

## Override vs default

A local override is not the same thing as a default.

### Default
- emerges because it repeatedly reduces routing waste for a recurring overlap

### Override
- exists because the user or environment explicitly prefers a path

Do not silently convert one into the other.

---

## When to ignore an override

Ignore or narrow an override when:
- the current task is outside the override’s original scope
- the user explicitly changes their mind for this task
- the override no longer reduces waste in the current environment

Do not let a narrow override leak into unrelated task types.

---

## One-off instruction rule

A one-off instruction should guide the current task.
It should **not** automatically become a durable default or override.

Durability requires recurrence or explicit user intent.

---

## Map update rule

Record or update the map only when all are true:
1. the overlap is likely to recur
2. the chosen default clearly reduced comparison cost
3. the scope of the default is narrow enough to stay reliable

Do not update the map for:
- one-off tasks
- noisy experiments
- vague preferences
- unstable situations where the best default is still unclear

---

## Output guidance

When the old default still holds:
- `Use X.`

When the default should update:
- `Use Y.`
- if needed, one short note: `Y is now the stronger recurring default for this task.`

When an override does not apply:
- `Use X.`
- if needed, one short note: `The stored override does not apply to this task type.`

---

## Bottom line

Defaults should converge.
Overrides should stay narrow.
One-off choices should not harden into policy.
