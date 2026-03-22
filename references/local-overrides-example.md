# Local Overrides

How local overrides work in Skill Router v0.5.

Local overrides are valid only when they reduce recurring routing waste.
They are not the center of the system.

---

## What a local override is

A local override is a user or environment preference that changes the default routing result.

Examples:
- “Always use X for reports.”
- “Do not suggest new skills unless I explicitly ask.”
- “For this workspace, prefer the platform-specific skill over the generic one.”

If an override does not change the next real action, it is not an override worth recording.

---

## When to record one

Record a local override when:
- the user explicitly states a stable preference
- the same correction happens repeatedly
- the environment has a durable preference that reduces recurring comparison

Do not record one-off whims as stable routing rules.

---

## How to apply one

If a valid local override exists, apply it early.
Do not run a long routing sequence and then override at the end.

The point of a local override is to shorten decisions, not lengthen them.

---

## Scope rule

Overrides should stay narrow.

A preference for reports does not automatically generalize to every document-like task.
A platform preference for one workspace does not automatically become a global rule.

Keep overrides as small as the real preference.

---

## Revocation rule

Overrides are preferences, not permanent law.

If the user changes their mind, the old override should stop applying.
If the environment changes enough that the override no longer reduces waste, remove or ignore it.

---

## Good example

```text
reports → docx | Confidence: high
Notes: user explicitly prefers docx output for recurring report work
```

Why this is good:
- it changes the next action
- it will likely recur
- it reduces repeated comparison

---

## Bad example

```text
maybe_web_task → something | Confidence: low
Notes: seemed useful once in a vague conversation
```

Why this is bad:
- it is vague
- it does not describe a stable recurring pattern
- it will not reliably reduce waste

---

## Bottom line

A good local override is a small, durable shortcut.
If it does not reliably shorten future routing, it should not be kept.
