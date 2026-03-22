# Skill Router v0.5 — Partial Re-evaluation After P1

日期：2026-03-22  
目的：在补完 P1 核心 policy 之后，重新评估原先的 partial issues 是否已经被规则层补强。

P1 已补内容：
- `references/sufficiency-policy.md`
- `references/default-update-policy.md`
- `references/crowded-environment-policy.md`

---

## Re-evaluated partial set

这里重判的 9 个 partial 问题，覆盖三类核心缺口：
- sufficiency boundary
- default update governance
- crowded-environment consistency

---

## Case 20 — Interactive dashboard with live collaboration

### Before
- Result: **PARTIAL PASS**
- Reason: `frontend-design` technically plausible, but evaluator lacked a hard rule for quality bar / collaboration constraints.

### After P1
- Result: **PASS**
- Why:
  - `sufficiency-policy.md` now explicitly says technical possibility alone is not sufficiency
  - `real-time / collaborative` is listed as a raised quality bar
  - static frontend for real-time collaboration is explicitly a non-sufficient pattern

### Updated expected output
`The installed set is not enough; discover candidates.`

---

## Case 30 — Rare ambiguity requiring fallback reference

### Before
- Result: **PARTIAL PASS**
- Reason: fallback existed, but still depended heavily on human judgment.

### After P1
- Result: **PARTIAL PASS**
- Why:
  - P1 improved nearby boundaries, but this case still primarily depends on the not-yet-hardened ambiguity fallback policy
  - this belongs more to P2 than P1

### Current reading
Still improved, but not fully resolved.

---

## Case 40 — Generic automation skill for production-grade Kubernetes deployment

### Before
- Result: **PARTIAL PASS**
- Reason: technically possible vs actually weak was not hard enough.

### After P1
- Result: **PASS**
- Why:
  - `sufficiency-policy.md` explicitly covers `production-grade` as a raised bar
  - it also explicitly rejects technically-possible-but-actually-weak paths
  - generic automation for production-grade Kubernetes is now clearly insufficient by contract

### Updated expected output
`The installed set is not enough; discover candidates.`

---

## Case 50 — Extreme crowding with 100 installed skills

### Before
- Result: **PARTIAL PASS**
- Reason: principles implied stability, but crowded-environment behavior was not explicit enough.

### After P1
- Result: **PASS**
- Why:
  - `crowded-environment-policy.md` now explicitly states that a crowded environment should collapse to the same decision as a sparse one when only a few skills are relevant
  - irrelevant installed skills are now explicitly defined as noise, not conflict

### Updated expected output
Short stable choice only.

---

## Case 55 — User distrusts the installed skill

### Before
- Result: **PARTIAL PASS**
- Reason: unclear boundary between subjective distrust and objective insufficiency.

### After P1
- Result: **PARTIAL PASS**
- Why:
  - P1 clarifies sufficiency relative to the user’s real bar
  - but simple distrust is still not automatically the same as a raised quality threshold
  - this still needs a tighter policy on user-stated concern vs objective bar

### Current reading
Improved, but still not fully nailed.

---

## Case 63 — Existing local default contradicted by a newer specialist

### Before
- Result: **PARTIAL PASS**
- Reason: default update behavior was implied, not explicit.

### After P1
- Result: **PASS**
- Why:
  - `default-update-policy.md` now explicitly says defaults should update when a new option materially improves match precision, platform precision, quality threshold, or repeatability
  - “newer” alone is not enough, but “newer and materially better recurring default” now clearly is

### Updated expected output
`Use Y.`
Optionally: `Y is now the stronger recurring default for this task.`

---

## Case 68 — Weak installed path under a high-stakes professional bar

### Before
- Result: **PARTIAL PASS**
- Reason: quality-threshold judgment not hard enough.

### After P1
- Result: **PASS**
- Why:
  - `sufficiency-policy.md` now explicitly makes the user’s quality bar part of the task
  - acceptable technical compatibility is no longer enough when the bar is clearly professional/high-stakes

### Updated expected output
`The installed set is not enough; discover candidates.`

---

## Case 70 — User asks for best possible output

### Before
- Result: **PARTIAL PASS**
- Reason: “best possible” vs “good enough” boundary was too soft.

### After P1
- Result: **PASS**
- Why:
  - `sufficiency-policy.md` now explicitly treats `best possible` and `highest quality` as raised-bar signals
  - this justifies re-evaluation and possible discovery even when an installed path is merely acceptable

### Updated expected output
Discovery or re-evaluation is allowed by contract.

---

## Case 100 — Maximum crowding stress test

### Before
- Result: **PARTIAL PASS**
- Reason: extreme-noise stability was implied but not explicitly codified.

### After P1
- Result: **PASS**
- Why:
  - `crowded-environment-policy.md` now explicitly rejects irrelevant-skill noise and fake overlap
  - environment size alone is no longer a reason to expand routing detail

### Updated expected output
Short stable choice only, based on the 1–2 relevant skills.

---

## Post-P1 score update

### Before re-evaluation
- **Pass:** 91
- **Partial pass:** 9
- **Fail:** 0

### After re-evaluation
- **Pass:** 97
- **Partial pass:** 3
- **Fail:** 0

---

## What remains partial

The remaining partial issues are now more clearly concentrated in places that P1 did not fully target:

1. **Rare ambiguity fallback**
   - belongs mainly to P2
2. **User distrust vs objective insufficiency**
   - needs a slightly harder policy for interpreting subjective distrust
3. **Clarification boundary in under-specified routing tasks**
   - also belongs mainly to P2

---

## Bottom line

P1 materially improved the contract.

It did not just add more prose.
It converted most of the previously weak partial areas into explicit pass conditions.

That means `skill-router v0.5` is now significantly stronger at the contract level, and the remaining uncertainty is much more concentrated and intelligible than before.
