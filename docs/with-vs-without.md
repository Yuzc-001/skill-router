# With vs Without Skill Router

This file compares environments with and without Skill Router v0.5.

The goal is not to show that routing always helps.
The goal is to show where a routing runtime actually reduces waste — and where it should stay out of the way.

---

## Scenario 1: The task should just proceed

### Without Skill Router
User asks for a small direct task. The agent either does it directly or wastes a few turns thinking about tools.

### With Skill Router
Skill Router stays silent because no routing decision is needed.

### What improved
- zero routing tokens spent
- zero extra decision ceremony
- simple task stays simple

---

## Scenario 2: A good installed skill is forgotten

### Without Skill Router
The agent starts searching for a new skill, or asks the user which one to use, even though a sufficient installed skill already exists.

### With Skill Router
Skill Router checks installed reality first and returns the shortest useful resolution:

`Use the installed skill.`

### What improved
- no redundant discovery
- no redundant installation
- faster return to execution

---

## Scenario 3: Overlapping installed skills create friction

### Without Skill Router
Two or three installed skills all seem plausible. The agent starts comparing them, explaining tradeoffs, and consuming tokens before work starts.

### With Skill Router
Skill Router applies a stable default for the overlap cluster and moves on.

### What improved
- comparison cost collapses
- repeated overlap converges instead of re-opening every time
- user is not forced into tool selection unless they asked for it

---

## Scenario 4: Installed reality is good enough, not perfect

### Without Skill Router
The agent may start searching for a theoretically better option somewhere else.

### With Skill Router
Skill Router applies the sufficiency test and stays with the installed path.

### What improved
- less novelty-seeking
- less discovery overhead
- stronger default reuse

---

## Scenario 5: The environment is genuinely insufficient

### Without Skill Router
Discovery can happen late, chaotically, or after failed attempts with the wrong installed tools.

### With Skill Router
Skill Router states the gap early, then keeps discovery small and focused.

### What improved
- earlier recognition of true gaps
- less random exploration
- smaller candidate set

---

## Scenario 6: The candidate is unfamiliar

### Without Skill Router
A candidate may be recommended or installed before anyone asks whether it is trustworthy or over-scoped.

### With Skill Router
Skill Router inserts one explicit admission gate:

`Candidate is unfamiliar. Vet before recommendation.`

### What improved
- safer expansion of the environment
- less entropy introduced by bad installs
- clearer boundary between finding and trusting

---

## Summary

| Situation | Without Skill Router | With Skill Router v0.5 |
|---|---|---|
| Simple task | Possible overthinking | Silence |
| Forgotten installed skill | Redundant discovery/install | Reuse installed reality |
| Overlap cluster | Repeated comparison | Stable default |
| Good enough installed option | Novelty-seeking | Stay with sufficiency |
| Real capability gap | Late / messy discovery | Early focused discovery |
| Unfamiliar candidate | Trust too early | Vet before recommendation |

---

## Bottom line

Skill Router v0.5 is useful only where it reduces waste.

If a given scenario would not benefit from a default decision, discovery check, or vetting gate, the correct behavior is not “more routing”.

The correct behavior is disappearance.
