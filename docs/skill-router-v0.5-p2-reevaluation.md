# Skill Router v0.5 — P2 Re-evaluation

日期：2026-03-22  
目的：在补完 P2 policy 之后，重新评估剩余 3 个 partial issues。

P2 已补内容：
- `references/ambiguity-fallback-policy.md`
- `references/distrust-and-clarification-policy.md`

---

## Remaining partials before P2
- rare ambiguity fallback
- user distrust vs objective insufficiency
- clarification boundary in under-specified routing tasks

---

## Case A — Rare ambiguity fallback

### Before
- Result: **PARTIAL PASS**
- Reason: fallback direction existed, but strategy was not explicit enough.

### After P2
- Result: **PASS**
- Why:
  - `ambiguity-fallback-policy.md` now defines a strict fallback order
  - it explicitly limits escalation to one minimum clarification when needed
  - it explicitly forbids taxonomy sprawl

### Updated reading
Ambiguity now has a concrete, bounded handling path.

---

## Case B — User distrust vs objective insufficiency

### Before
- Result: **PARTIAL PASS**
- Reason: distrust, raised quality bar, and vague concern were still blurred together.

### After P2
- Result: **PASS**
- Why:
  - `distrust-and-clarification-policy.md` now separates:
    - subjective distrust
    - raised quality/safety bar
    - missing task information
  - distrust alone no longer forces discovery
  - raised bar clearly justifies re-evaluation
  - vague concern now leads to one short clarification instead of routing drift

### Updated reading
This boundary is now much cleaner.

---

## Case C — Clarification boundary in under-specified routing tasks

### Before
- Result: **PARTIAL PASS**
- Reason: unclear whether the router should route, clarify, or stay silent.

### After P2
- Result: **PASS**
- Why:
  - `SKILL.md` now explicitly says that when the real problem is missing task information, ask one short clarification instead of expanding routing
  - `ambiguity-fallback-policy.md` and `distrust-and-clarification-policy.md` both reinforce the one-minimum-clarification rule

### Updated reading
Under-specification is now treated as a clarification problem, not fake routing complexity.

---

## Post-P2 score update

### Before P2 re-evaluation
- **Pass:** 97
- **Partial pass:** 3
- **Fail:** 0

### After P2 re-evaluation
- **Pass:** 100
- **Partial pass:** 0
- **Fail:** 0

---

## Bottom line

After P1 and P2, the contract-level partial issues are now effectively closed.

That does **not** mean evaluator work is unnecessary.
It means the remaining uncertainty is no longer mainly about missing contract rules.

The next frontier is no longer policy completeness.
It is evaluator design and runtime verification.
