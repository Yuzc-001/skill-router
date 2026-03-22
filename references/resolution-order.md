# Resolution Order

Expanded reference for Skill Router v0.5.

Use this file only if the short main path in `SKILL.md` is not enough.
If the decision is already clear, do not read this file.

---

## The sequence

```text
Need routing?
→ If no: disappear
→ If yes: prefer installed default
→ If insufficient: discover a small candidate set
→ If unfamiliar: vet before recommendation
```

The goal is to stop as early as possible.

---

## Step 0 — Need routing?

Ask:

**Will routing materially change the next action?**

If no, stop.

Typical no-route cases:
- the task should just be executed directly
- one installed skill is obviously enough
- the correct skill is already active
- more routing detail would not change the next action

---

## Step 1 — Prefer installed default

Ask:
- is there already a clearly sufficient installed skill?
- is there a stable local default for this recurring overlap?
- does a platform-specific skill obviously beat a generic one?

If yes, use it and stop.

Core restraint:
- do not reopen discovery just because something newer might exist

---

## Step 2 — Test genuine insufficiency

Only escalate if the installed environment is actually not enough.

Minimum test:
1. Can an installed skill accept the input?
2. Can an installed skill produce the needed output?
3. Is the quality sufficient for the user’s actual purpose?

If all three are yes, stay with installed reality.
If any answer is no, discovery is justified.

---

## Step 3 — Discover only for a real gap

When discovery is justified:
- state the missing capability clearly
- keep the candidate set small
- prefer concrete candidates over broad browsing
- if `find-skills` is installed, prefer delegating discovery to it

Discovery is for insufficiency, not novelty.

---

## Step 4 — Vet unfamiliar candidates

If a candidate is unfamiliar, third-party, or broad in permissions:
- vet before recommendation
- compare scope to stated purpose
- check source accountability
- prefer caution over enthusiasm

For the deeper checklist, read `publish-safe-runtime-contract.md`.

---

## Quick reference

| Situation | Resolution |
|---|---|
| Task should just be done | No routing |
| One installed skill is clearly enough | Use it |
| Installed path is sufficient but imperfect | Use it anyway |
| Installed environment is not enough | Discover candidates |
| Candidate is unfamiliar | Vet before recommendation |
| Same overlap keeps recurring | Record a stable default |

---

## Bottom line

This file exists to clarify the main path, not to add another layer of routing ceremony.
