# Use Cases

Skill Router v0.5 is for the moments when skill choice itself is creating waste.

Not every task needs it.
Only the tasks below are worth the routing layer.

---

## High-value use cases

### 1. “Do we already have a skill for this?”
The user suspects the environment may already contain what they need, but does not want to waste turns rediscovering it.

### 2. “Which installed skill should be the default here?”
More than one installed skill looks plausible, and the overlap is recurring enough that unstable choice is becoming a cost.

### 3. “Is the current environment actually insufficient?”
Before discovery, the agent needs a disciplined check that the installed set is truly not enough.

### 4. “Should this new candidate even enter the environment?”
A new skill has been found, but it is unfamiliar or high-scope. Skill Router adds the admission gate before recommendation.

### 5. “This overlap keeps coming back.”
The same conflict cluster keeps reopening. Skill Router is useful here because a stable default can reduce future comparison cost.

---

## Low-value cases where Skill Router should stay out

### 1. Simple direct tasks
If the task should just be done, do it.

### 2. Obvious single-skill matches
If one installed skill is clearly enough, use it without narration.

### 3. Tasks where the user explicitly named the skill
Respect explicit intent. Do not reopen selection.

### 4. Tasks where more routing detail would not change the next action
If the answer would still be the same, the routing layer adds no value.

---

## Short examples

### Example A — reuse beats discovery
User: “Do we already have a skill for making slides?”

Good use of Skill Router:
- check installed reality first
- return the installed slide skill if it already exists
- avoid discovery if the installed path is sufficient

### Example B — overlap should converge
User: “Analyze this data and give me a chart.”
Installed environment has two or three plausible options.

Good use of Skill Router:
- apply the stable default for this overlap cluster
- start execution
- do not make the user choose unless they asked

### Example C — insufficiency justifies discovery
User: “I need a skill for a capability none of my installed tools cover.”

Good use of Skill Router:
- say the gap clearly
- keep discovery small
- recommend only a few candidates

### Example D — unfamiliar candidate needs admission control
User: “I found this third-party skill. Should I install it?”

Good use of Skill Router:
- do not treat discovery as trust
- apply vetting before recommendation

---

## Bottom line

Skill Router v0.5 helps when it reduces:
- rediscovery
- repeated comparison
- repeated installation
- unstable defaults
- unnecessary routing tokens

Outside those cases, it should vanish.
