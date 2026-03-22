# Sufficiency Policy

Use this file when the hardest question is not “is there an installed skill?” but:

# is the installed path actually sufficient for the user’s real bar?

This file exists because `technically possible` is not always the same as `sufficient`.

---

## Core rule

An installed path is sufficient only if it is strong enough for the user’s actual purpose.

Do not treat mere technical possibility as sufficiency.

---

## Minimum test

The installed path is sufficient only if all three are true:
1. it can accept the task input
2. it can produce the needed output type
3. its quality is strong enough for the user’s stated bar

If any of the three fail, the installed environment is insufficient.

---

## Quality bar policy

### Prefer installed sufficiency when the user signals:
- rough
- okay
- acceptable
- quick draft
- good enough
- simple version

These lower the quality threshold.

### Re-evaluate aggressively when the user signals:
- best possible
- highest quality
- professional
- polished to a high standard
- production-ready
- enterprise-grade
- real-time / collaborative / high-reliability constraints

These raise the quality threshold.

---

## Technically possible but actually weak

Do **not** count an installed path as sufficient if it is only barely compatible while clearly below the user’s real purpose.

Examples:
- a static frontend skill for a real-time collaborative product
- a generic automation skill for production-grade Kubernetes deployment
- a weak formatter for a professional publishing workflow

If the skill can technically produce *something* but clearly misses the actual bar, treat it as insufficient.

---

## User intent beats abstract quality guesses

If the user explicitly lowers the bar:
- prefer the installed path

If the user explicitly raises the bar:
- discovery or re-evaluation is allowed, even if the installed path is merely acceptable

The user’s stated bar is part of the task.
It is not side commentary.

---

## Output guidance

When sufficiency is clear:
- `The installed set is sufficient; use X.`

When insufficiency is clear:
- `The installed set is not enough; discover candidates.`

When the bar is the real issue:
- briefly name the bar, not a long theory

Example:
- `For a rough version, the installed path is sufficient; use X.`
- `For production-grade output, the installed path is not enough; discover candidates.`

---

## Bottom line

Sufficiency is about the user’s real bar, not just technical possibility.
