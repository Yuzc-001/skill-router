# How It Works

Skill Router v0.5 works by refusing to spend routing tokens unless the routing decision will change the next real action.

It is not a taxonomy engine.
It is not a pre-task ceremony.
It is a very small runtime for reducing unnecessary skill-selection cost.

---

## The Main Path

```
Task arrives
  → Ask: is skill choice actually blocking progress?
  → If no: disappear
  → If yes: prefer the strongest installed default
  → Ask: is the current environment genuinely insufficient?
  → If no: use installed reality and stop
  → If yes: discover a small candidate set
  → If unfamiliar candidates appear: vet before recommendation
```

Every step is a gate.
The goal is to stop as early as possible.

---

## Step 0 — Decide whether routing is needed at all

This is the most important step.

Skill Router should only activate when skill choice itself is slowing or blocking progress.

If any of the following are true, Skill Router should disappear:
- the task should just be executed directly
- one installed skill is an obvious match
- the correct skill is already active
- more routing commentary would cost more than the decision
- extra classification would not change the next action

The best routing layer is often invisible.

---

## Step 1 — Prefer the strongest installed default

Before discovery, before comparison theater, before cleverness:

# look at installed reality

Ask:
- is there already a clearly sufficient skill?
- is there already a stable default for this recurring conflict?
- does one installed option obviously beat the others?

If yes, use it and stop.

This is where most wasted routing should die.

---

## Step 2 — Test real insufficiency

Discovery is expensive.
So do not trigger it unless the current environment is genuinely not enough.

Use the minimum sufficiency test:

1. Can an installed skill accept the task input?
2. Can an installed skill produce the needed output?
3. Is the quality sufficient for the user’s real purpose?

If all three are yes, stay with installed reality.
If any answer is no, discovery is justified.

---

## Step 3 — Discover only for real gaps

If the environment is genuinely insufficient:
- state what capability is missing
- keep the candidate set small
- prefer concrete candidates over broad browsing
- do not turn discovery into novelty-seeking

If `find-skills` is installed, delegate discovery to it.

The point of discovery is not to find something cooler.
It is to fill a real gap.

---

## Step 4 — Vet before admitting unfamiliar candidates

If a discovered candidate is unfamiliar, third-party, or broad in permission scope:
- vet it before recommending installation
- check whether its scope matches its stated purpose
- check whether the source is identifiable and accountable
- check whether you would be comfortable recommending it to a non-technical user

This is not a side quest.
It is part of keeping the environment from getting noisier and less trustworthy over time.

---

## What changed in v0.5

Earlier versions leaned too much toward routing doctrine:
- more ordering logic
- more taxonomy pressure
- more explanation than default change

v0.5 cuts that down hard.

The new standard is simple:

# if routing will not change the next action, routing should not speak

That is the main behavioral shift.

---

## The only conflicts that matter on the main path

Skill Router v0.5 only cares about high-value conflicts:
- installed vs discover
- dedicated vs general
- platform-specific vs generic
- recurring overlap cluster
- unfamiliar install vs safe reuse

If a distinction does not change the default next action, it does not belong on the main path.

---

## What success looks like

Skill Router is working when it causes visible reductions in:
- repeated skill discovery
- repeated skill comparison
- repeated installation
- routing token spend
- unstable defaults in crowded skill environments

If those do not go down, the system is not helping enough.

---

## In one sentence

Skill Router v0.5 works by spending almost no routing tokens until the routing decision becomes materially necessary — then giving the shortest useful default resolution possible.
