# How It Works

Skill Router follows a simple resolution sequence to make skill selection decisions.

## The Resolution Sequence

```
Task arrives
  → Identify the dominant capability the task needs
  → Inspect the installed skill environment
  → Find the strongest installed match
  → Apply the enough-is-enough rule
  → (only if needed) Discover new skills
  → (only if needed) Vet unfamiliar candidates before recommending installation
```

Each step is a gate. Stop at the first one that produces a sufficient result.

## The Key Decisions

### What is the dominant capability?

Every task has one primary capability that determines success. A "research and present" task is primarily about the presentation — research is a means, not the end. Skill Router identifies this single dominant capability and routes based on it, rather than decomposing tasks into long lists of sub-capabilities.

### What's already installed?

Before searching for anything new, Skill Router reads the full list of installed skills. This is the reality it works with. The installed environment is the primary constraint.

### Is the installed match good enough?

The enough-is-enough rule: if the best installed skill can complete the task to a reasonable standard — where the user would not be materially harmed or meaningfully slowed — that skill is the answer. No further searching.

### When does discovery happen?

Only when the installed set genuinely cannot handle the dominant capability. Not when something "better" might exist. Not when a shinier option is available. Only for real capability gaps.

### What happens with unfamiliar skills?

Third-party skills from unknown sources go through a vetting checklist before Skill Router recommends installation. The checklist evaluates: stated purpose clarity, scope-to-permission ratio, source accountability, behavioral boundaries, and whether a non-technical user would be safe using it.

## Operating Principles

1. **Installed reality beats local preference** — route based on what exists, not what should exist
2. **Discovery is for insufficiency, not novelty** — search only for real gaps
3. **Quiet by default** — no routing commentary unless it helps the user
4. **Reuse over rediscovery** — always prefer what's already installed
5. **Vet before trust** — unknown sources get reviewed before recommendation

## What It Looks Like in Practice

**Simple task, obvious match:**
Skill Router is invisible. The right skill is used silently.

**Multiple plausible matches:**
Skill Router picks the best one and briefly notes the choice. One sentence.

**Genuine capability gap:**
Skill Router states the gap, searches for candidates, and presents options with rationale.

**Unfamiliar candidate found:**
Skill Router applies the vetting checklist and communicates any concerns before recommending installation.

For detailed examples, see `references/micro-routing-examples.md`.
