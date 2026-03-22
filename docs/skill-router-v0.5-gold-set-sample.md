# Skill Router v0.5 — Gold-Set Sample

日期：2026-03-22  
对象：`docs/skill-router-v0.5-gold-set-sample.json`

---

## What this file is

This is the first structured sample of gold-set cases for `skill-router v0.5`.

It is not the full gold set yet.
It is a practical starter pack that proves the schema can be instantiated as real case objects.

---

## What is included

The current sample includes 12 structured cases across these families:
- `no_route`
- `installed_default`
- `sufficiency_boundary`
- `discovery`
- `vetting`
- `crowded_environment`
- `ambiguity_clarification`
- `override_governance`
- `explanation_boundary`

This is enough to prove the schema is workable, reviewable, and extensible.

---

## Why this matters

Before this file, the project had:
- contract
- policy
- smoke cases
- evaluator spec
- gold-set schema

Now it also has:

# actual structured case data

That means the project has crossed from “evaluation design” into “evaluation substrate”.

---

## Next good step

Expand this sample into the first real 100-case gold set using the distribution defined in:
- `docs/skill-router-v0.5-gold-set-schema.md`

The current JSON file should be treated as the seed set.

---

## Related files

- `docs/skill-router-v0.5-evaluator-spec.md`
- `docs/skill-router-v0.5-gold-set-schema.md`
- `docs/skill-router-v0.5-smoke-cases.md`
- `docs/skill-router-v0.5-smoke-cases-batch-2.md`

---

## Bottom line

`skill-router v0.5` now has:
- a contract
- policy hardening
- smoke evidence
- evaluator design
- a schema
- and real structured sample cases

That is enough to begin disciplined regression evaluation.
