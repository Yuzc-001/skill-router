# Why Skill Router

## The problem changes as skill collections grow

Early on, the problem with skills is simple: **not enough capability**. You don't have a skill for presentations. You don't have a skill for spreadsheets. Every gap is obvious and the fix is clear — install more skills.

But at some point, the bottleneck shifts. You have 10, 20, 50 skills installed. The problem is no longer missing capability. It becomes:

- **Too many possible skills.** Three skills could handle this task. Which one?
- **Too much rediscovery.** You search for "a skill that does X" and install something new, forgetting that you already had one that does X.
- **Too much repeated installation.** Skills pile up because nobody remembers what's already there.
- **Too much cognitive overhead.** The question "which skill should I use?" becomes harder than the task itself.

This is the selection overhead problem. Skill Router is built for this stage.

## What Skill Router is not

Skill Router is not a search engine, a package manager, or a meta-layer that should speak on every task. It is not a reason to install more skills.

It is a **low-presence decision layer** for the specific moment when skill choice itself becomes part of the problem.

## The core design decisions

### Installed reality beats local preference

Skill Router routes based on what you actually have installed — not what an ideal setup would look like. If you have a `pdf` skill and it can handle the task, Skill Router uses it. It does not suggest that you install a "better" PDF skill.

### Discovery is for insufficiency, not novelty

Skill Router only searches for new skills when the installed set genuinely cannot handle the task. "There might be something better" is never a reason to search.

### Quiet by default

The best Skill Router interaction is one you barely notice. It should not announce itself, narrate its process, or add routing commentary to simple tasks. It speaks only when a genuine routing decision was made that matters to you.

### Vet before unfamiliar install

When new skills are found through discovery, Skill Router reviews them before recommending installation — especially when they come from unfamiliar sources. This is not gatekeeping. It is informed installation.

## Who this is for

Skill Router is for anyone operating in an environment where multiple skills are installed and the question "which one should I use?" comes up regularly. This includes:

- Developers with large toolkits
- Teams sharing skill collections
- Anyone who has accumulated enough skills that they sometimes forget what they have

If you have 2–3 skills and always know which one to use, you probably don't need Skill Router yet. When you do, it will be here.
