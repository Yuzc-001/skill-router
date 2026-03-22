# Ambiguity Fallback Policy

Use this file when routing is genuinely needed but the task is still under-specified.

This file exists to prevent Skill Router from turning ambiguity into taxonomy theater.

---

## Core rule

When the task is ambiguous, escalate as little as possible.

Do not expand into long category analysis.
Do not compare many skills just because the task is underspecified.

---

## Fallback order

When routing is needed but the default path is unclear, use this order:

1. **Platform signal** — if the task names a platform or destination, prefer it
2. **Dedicated beats general** — if one installed skill is more directly aligned with the task shape
3. **Credible local default** — if a narrow stable default exists for this real overlap
4. **One minimum clarification** — if the next action is still materially unclear
5. **Short fallback choice** — if a harmless stable default exists and the user asked to just pick

---

## One minimum clarification rule

If clarification is necessary, ask only the smallest question that changes the next action.

Good examples:
- `Which platform should this go to?`
- `Do you want the rough version or the high-quality version?`
- `Should I optimize for speed or for safest install?`

Bad examples:
- long decomposition of categories
- multiple-option surveys before any action
- open-ended framework questions that cost more than the routing problem itself

---

## When not to clarify

Do not ask clarification questions when:
- one installed default is already clearly sufficient
- the user explicitly asked you to just pick
- the ambiguity does not materially change the next action

In those cases, collapse to the shortest useful default.

---

## Output guidance

When clarification is needed:
- ask one short question

When it is not:
- `Use X.`
- or `This task does not need skill-router.`

---

## Bottom line

Ambiguity should lead to either one short clarification or one short default.
It should not lead to routing sprawl.
