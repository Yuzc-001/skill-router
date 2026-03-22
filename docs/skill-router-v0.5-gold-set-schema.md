# Skill Router v0.5 — Gold-Set Schema

日期：2026-03-22  
状态：draft / first practical evaluator substrate

---

## Purpose

This document turns the evaluator spec into a concrete gold-set format.

It answers:
- what a case object must contain
- what outputs are allowed
- what counts as pass / fail at the schema level
- how the first gold set should be distributed

This is the bridge between:
- policy / contract
- smoke cases
- future runner or review workflow

---

## Gold-set philosophy

A gold set should not try to encode every possible task.

It should encode the smallest set of cases that can reliably catch:
- routing overreach
- false discovery
- missing vetting
- override leakage
- instability under environment noise
- wrong sufficiency judgments
- ambiguity sprawl

The point is regression pressure, not exhaustive enumeration.

---

## Case object schema

Each case should use this shape.

```json
{
  "id": "sr-v0.5-001",
  "family": "installed_default",
  "task": "Create a PowerPoint deck from these notes.",
  "installed_skills": [
    {
      "name": "pptx",
      "description": "Create and edit PowerPoint decks.",
      "trusted": true,
      "scope": "slides"
    },
    {
      "name": "docx",
      "description": "Create and edit Word documents.",
      "trusted": true,
      "scope": "docs"
    }
  ],
  "active_skill": null,
  "local_defaults": [],
  "local_overrides": [],
  "candidate_skills": [],
  "user_constraints": {
    "quality_bar": "default",
    "prefer_reuse": true,
    "prefer_discovery": false,
    "prefer_safest": false,
    "prefer_fastest": false,
    "prefer_cheapest": false,
    "explanation_depth": "minimal",
    "allow_clarification": true,
    "explicit_skill_name": null
  },
  "environment": {
    "noise_level": "low",
    "notes": []
  },
  "expected": {
    "decision_class": "use_installed",
    "allowed_skills": ["pptx"],
    "forbidden_classes": ["discover_candidates", "vet_candidate", "ask_one_clarification"],
    "max_explanation_class": "short"
  }
}
```

---

## Required fields

### Top-level required
- `id`
- `family`
- `task`
- `installed_skills`
- `user_constraints`
- `expected`

### Optional but recommended
- `active_skill`
- `local_defaults`
- `local_overrides`
- `candidate_skills`
- `environment`

---

## Normalized enums

### `family`
Allowed values:
- `no_route`
- `installed_default`
- `sufficiency_boundary`
- `discovery`
- `vetting`
- `override_governance`
- `crowded_environment`
- `ambiguity_clarification`
- `explanation_boundary`
- `combination_path`

### `quality_bar`
Allowed values:
- `low`
- `default`
- `high`
- `production`

### `explanation_depth`
Allowed values:
- `minimal`
- `why`
- `compare`
- `full`

### `noise_level`
Allowed values:
- `low`
- `medium`
- `high`
- `extreme`

---

## Decision classes

Allowed `decision_class` values:
- `no_route`
- `use_installed`
- `use_active_skill`
- `use_local_default`
- `use_override`
- `discover_candidates`
- `vet_candidate`
- `ask_one_clarification`
- `allow_reasoned_comparison`
- `allow_extended_reasoning`
- `use_combination`

These are the stable regression surface.
Do not make wording the primary target.

---

## Explanation classes

Allowed explanation classes:
- `none`
- `short`
- `reasoned`
- `extended`

### Contract expectation
- default cases should be `none` or `short`
- `reasoned` only when the user asks why / compare
- `extended` only when the user explicitly asks for full logic

---

## Skill object schema

Each installed or candidate skill should minimally expose:

```json
{
  "name": "github",
  "description": "Interact with GitHub issues, PRs, runs, and API.",
  "trusted": true,
  "scope": "github"
}
```

Optional extensions:
- `platform`
- `permissions`
- `source_type` (`self`, `trusted_registry`, `third_party_unknown`)
- `family`
- `notes`

---

## Override object schema

```json
{
  "scope": "reports",
  "skill": "pdf",
  "source": "explicit_user_preference",
  "durable": true
}
```

Required semantics:
- overrides are narrow
- one-off instructions are not durable overrides
- override scope must be testable

---

## Default object schema

```json
{
  "scope": "search_api_docs",
  "skill": "brave-search",
  "confidence": "high"
}
```

Required semantics:
- defaults represent recurring convergence
- defaults may update when materially improved
- defaults should not be stored for one-off tasks

---

## Expected section rules

The `expected` block must include:
- exactly one primary `decision_class`
- optional `allowed_skills`
- optional `forbidden_classes`
- one `max_explanation_class`

Optional additions:
- `requires_clarification_on_missing_field`
- `must_ignore_noise`
- `must_not_update_default`
- `must_update_default`
- `must_not_escalate_to_discovery`

---

## Pass rules at schema level

A case passes when all are true:
1. actual `decision_class` == expected `decision_class`
2. selected skill is inside `allowed_skills` when provided
3. no forbidden class is triggered
4. explanation class does not exceed `max_explanation_class`
5. schema-specific flags are satisfied

---

## Partial pass rules at schema level

Use `partial` only when:
- the decision class is close but one clarification should have happened first
- explanation is slightly too verbose without changing the core decision
- one of several allowed default skills is chosen, but the strongest expected one was not

Partial should be rare.
If it becomes common, the gold set or contract is underspecified.

---

## Fail rules at schema level

A case fails when any of these happen:
- `discover_candidates` appears when installed sufficiency should hold
- `no_route` appears when a real skill-choice conflict exists
- unfamiliar candidates bypass `vet_candidate`
- an override leaks outside scope
- irrelevant noise changes the decision class
- explanation class violates contract strongly
- a one-off instruction becomes a stored default/override behaviorally

---

## First gold-set distribution

Recommended first practical gold set: **100 cases**.

### Distribution
- `no_route`: 15
- `installed_default`: 20
- `sufficiency_boundary`: 15
- `discovery`: 10
- `vetting`: 10
- `override_governance`: 10
- `crowded_environment`: 8
- `ambiguity_clarification`: 7
- `explanation_boundary`: 3
- `combination_path`: 2

This is enough to create pressure without turning the set into maintenance theater.

---

## Variation rules

Every gold-set family should later receive controlled variations:
- add irrelevant installed skills
- rename skills while preserving descriptions
- raise / lower quality bar
- add / remove local defaults
- add / remove overrides
- change explanation depth requested by the user
- introduce candidate trust and permission differences

The evaluator should confirm that only the intended axes change the result.

---

## Minimal review form

Even before a full runner exists, each case can be reviewed with this form:

```text
Case ID:
Actual decision class:
Actual selected skill:
Actual explanation class:
Pass / Partial / Fail:
Reason:
```

This is enough to begin manual regression review with discipline.

---

## Source pool

The initial gold set should be sourced from:
- `docs/skill-router-v0.5-smoke-cases.md`
- `docs/skill-router-v0.5-smoke-cases-batch-2.md`
- `docs/skill-router-v0.5-partial-reevaluation.md`
- `docs/skill-router-v0.5-p2-reevaluation.md`

The smoke cases are not the gold set directly.
They are the source pool from which a tighter 100-case evaluator set should be extracted.

---

## Bottom line

The gold-set schema gives `skill-router v0.5` a concrete regression surface.

From here, the next real step is simple:
- instantiate the first 100-case gold set
- review it manually or build a lightweight runner
- stop arguing about the contract abstractly and start checking whether it still holds
