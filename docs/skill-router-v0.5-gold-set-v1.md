# Skill Router v0.5 — Gold Set v1

日期：2026-03-22  
对象：`docs/skill-router-v0.5-gold-set-v1.json`

---

## What this is

This is the first instantiated gold-set file for `skill-router v0.5`.

It is the first substantial gold-set file for `skill-router v0.5`.
Its purpose is to prove that the schema can be populated with real, reviewable, contract-level cases at meaningful scale.

---

## Current scope

The current v1 file contains **100 structured cases** across these families:
- `no_route`
- `installed_default`
- `sufficiency_boundary`
- `discovery`
- `vetting`
- `crowded_environment`
- `ambiguity_clarification`
- `override_governance`
- `explanation_boundary`

This is enough to serve as:
- a first real 100-case manual regression set
- a review template for future cases
- a substantial substrate for a future runner

---

## Why it matters

Before this file, the repository already had:
- a contract
- hardened policy
- 200 smoke cases
- an evaluator spec
- a gold-set schema
- a sample JSON file

Now it also has:

# a first real gold-set file

That means the repository now contains the beginning of a true regression surface.

---

## What is still missing

To reach the intended first full gold set, this file should later be expanded toward the distribution defined in:
- `docs/skill-router-v0.5-gold-set-schema.md`

Current family distribution is now broad enough for serious review, though it still does not exactly match the ideal target distribution from the schema. That is acceptable for `v1` as long as the set keeps pressure on the most failure-prone boundaries.

---

## Related files

- `docs/skill-router-v0.5-evaluator-spec.md`
- `docs/skill-router-v0.5-gold-set-schema.md`
- `docs/skill-router-v0.5-gold-set-sample.json`
- `docs/skill-router-v0.5-smoke-cases.md`
- `docs/skill-router-v0.5-smoke-cases-batch-2.md`

---

## Bottom line

`skill-router v0.5` now has its first instantiated **100-case** gold-set file.

This is the point where evaluation stops being only descriptive and starts becoming operational.
