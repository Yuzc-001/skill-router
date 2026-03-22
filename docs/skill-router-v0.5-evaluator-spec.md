# Skill Router v0.5 — Evaluator Spec

日期：2026-03-22  
状态：draft / contract-to-evaluator bridge

---

## Purpose

This document turns `skill-router v0.5` from a document-tested contract into a repeatable evaluation target.

The goal is not to test whether the prose sounds good.
The goal is to test whether the routing behavior remains stable under realistic variation.

---

## Evaluation goals

The evaluator should verify that Skill Router:
1. activates only when skill choice actually matters
2. prefers installed reality before discovery
3. suppresses novelty-driven discovery by default
4. routes unfamiliar candidates through vetting
5. keeps outputs short unless deeper reasoning is explicitly requested
6. maintains stable decisions in crowded environments
7. handles defaults, overrides, sufficiency bars, and ambiguity boundaries consistently

---

## Evaluation unit

Each evaluation case should be represented as a structured object.

```json
{
  "id": "case-001",
  "task": "Create a PowerPoint deck from these notes.",
  "installed_skills": [
    { "name": "pptx", "description": "Create and edit PowerPoint decks." },
    { "name": "docx", "description": "Create and edit Word documents." }
  ],
  "local_defaults": [
    { "scope": "slides", "skill": "pptx" }
  ],
  "local_overrides": [],
  "candidate_skills": [],
  "user_constraints": {
    "quality_bar": "default",
    "prefer_reuse": true,
    "prefer_discovery": false,
    "explanation_depth": "minimal"
  },
  "expected": {
    "should_route": true,
    "decision_class": "use_installed",
    "allowed_skills": ["pptx"],
    "max_explanation_level": "short"
  }
}
```

---

## Core fields

### Required input fields
- `task`
- `installed_skills`
- `user_constraints`
- `expected`

### Optional input fields
- `local_defaults`
- `local_overrides`
- `candidate_skills`
- `active_skill`
- `environment_noise`
- `notes`

---

## Expected output classes

The evaluator should classify routing results into one of these contract-level classes:

- `no_route`
- `use_installed`
- `use_local_default`
- `use_override`
- `discover_candidates`
- `vet_candidate`
- `ask_one_clarification`
- `allow_reasoned_comparison`
- `allow_extended_reasoning`

These classes are more stable than exact wording and should be the main regression target.

---

## Secondary output checks

In addition to decision class, the evaluator should check:

### 1. Output shortness
Default outputs should remain within contract expectations:
- `minimal`
- `short`
- `extended` only when explicitly requested

### 2. Noise resistance
Irrelevant installed skills should not change the decision class.

### 3. Sufficiency sensitivity
Raising or lowering the quality bar should predictably affect whether the result stays installed or escalates to discovery.

### 4. Override scope discipline
Narrow overrides should not leak to unrelated task types.

### 5. Default update discipline
A new skill should replace an old default only when it materially improves the recurring decision.

---

## Pass / fail rules

### Pass
A case passes when:
- the produced decision class matches the expected class
- the chosen skill (if any) is within the expected allowed set
- the explanation level does not exceed the allowed maximum
- no forbidden escalation occurs

### Partial pass
A case is partial when:
- the decision is directionally correct but explanation exceeds the contract
- the decision is plausible but depends on under-specified ambiguity that should have triggered one clarification
- the chosen skill is acceptable but not the strongest expected default

### Fail
A case fails when:
- discovery happens when installed sufficiency should hold
- no-route cases trigger unnecessary routing
- unfamiliar candidates bypass vetting
- irrelevant noise changes the decision incorrectly
- overrides leak outside scope
- explanation becomes long when contract expects short

---

## Case families

The evaluator should group cases into reusable families.

### Family A — No-route tasks
Examples:
- trivial edits
- direct questions
- tiny direct execution tasks

### Family B — Installed-default tasks
Examples:
- obvious dedicated skill exists
- forgotten installed skill exists
- correct active skill already exists

### Family C — Sufficiency boundary tasks
Examples:
- rough / acceptable bar
- professional / production-ready bar
- technically possible but actually weak

### Family D — Discovery tasks
Examples:
- no matching installed skill
- explicit discovery request despite installed sufficiency
- discovery with and without helper skill

### Family E — Vetting tasks
Examples:
- unknown author
- trusted source + broad permissions
- narrow scope + trusted source
- self-authored candidate

### Family F — Override / default governance
Examples:
- narrow override applies
- override does not apply
- one-off instruction should not harden
- new specialist should replace old default

### Family G — Crowded environment tasks
Examples:
- 50-skill environment with 2 relevant skills
- 100-skill environment with heavy noise
- fake overlap vs real overlap

### Family H — Ambiguity / clarification tasks
Examples:
- missing destination platform
- missing quality bar
- user distrust without clear bar raise
- user asks to just pick

### Family I — Explanation-boundary tasks
Examples:
- user asks for one-line answer
- user asks why
- user asks for comparison
- user asks for full routing logic

---

## Recommended evaluator phases

### Phase 1 — Contract evaluator
Use structured synthetic cases only.
Goal: ensure the decision class remains stable.

### Phase 2 — Variation evaluator
For each base case, inject variation:
- more irrelevant installed skills
- renamed skills with same descriptions
- stricter / looser user quality bar
- explicit exploration request
- explicit no-commentary request

Goal: test invariance and sensitivity.

### Phase 3 — Drift evaluator
Re-run the full evaluator after every contract or reference change.
Goal: catch regressions in:
- no-route behavior
- novelty suppression
- override leakage
- crowded-environment stability
- vetting discipline

---

## Recommended metrics

The evaluator should report at least:
- pass / partial / fail counts
- pass rate by case family
- average explanation class by family
- false-discovery count
- false-no-route count
- false-clarification count
- override leakage count
- noise-instability count

---

## Minimal gold-set recommendation

The current repo already has enough material to define a first gold set of:
- 30 no-route / installed-default cases
- 20 sufficiency boundary cases
- 20 discovery / vetting cases
- 15 override / default-governance cases
- 15 crowded-environment / ambiguity cases

That yields a practical `100-case gold set` for the first evaluator.

The two smoke batches already created can serve as the source pool.

---

## What this evaluator is not

This evaluator is not trying to prove that Skill Router is the universally best skill-routing system.

It is trying to prove that the current contract:
- stays coherent
- stays bounded
- stays low-noise
- stays stable under realistic variation

---

## Bottom line

`skill-router v0.5` now has a contract strong enough to evaluate.

The next step is not more policy writing.
The next step is to encode this evaluator spec into a repeatable case runner or review workflow so the contract can be regression-tested instead of merely re-described.
