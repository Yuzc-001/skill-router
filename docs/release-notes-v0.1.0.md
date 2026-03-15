# Release Notes — v0.1.0

**Released:** 2025

This is the first public release of Skill Router.

---

## What's included

### Core routing skill (`SKILL.md`)

The routing logic itself: a six-step resolution sequence that prefers installed skills, applies an enough-is-enough rule, and falls back to discovery only when installed capabilities are genuinely insufficient.

### Five routing behaviors

1. **Reuse-first** — prefer installed skills over discovery
2. **Installed-reality-first** — route based on what exists, not what should exist
3. **Discovery only for insufficiency** — search only for real gaps
4. **Vet before unfamiliar install** — review unknown candidates before recommending
5. **Quiet by default** — no routing commentary unless it helps

### Reference documents

- **Capability taxonomy** (`references/capability-taxonomy.md`) — classification of task capabilities for routing decisions
- **Resolution order** (`references/resolution-order.md`) — detailed walkthrough with worked examples
- **Publish-safe runtime contract** (`references/publish-safe-runtime-contract.md`) — vetting checklist for third-party skills
- **Reminder policy** (`references/reminder-policy.md`) — when Skill Router speaks and when it stays quiet
- **Micro routing examples** (`references/micro-routing-examples.md`) — 13 quick-reference routing patterns
- **Local overrides** (`references/local-overrides-example.md`) — handling user-specific routing preferences
- **Task-to-skill map** (`references/task-to-skill-map.md`) — maintainable mapping from task types to skills

### Documentation

- `docs/why-skill-router.md` — product rationale
- `docs/how-it-works.md` — routing model and principles
- `docs/use-cases.md` — practical scenarios with walkthroughs
- `docs/with-vs-without.md` — before/after comparison of workflows

---

## Design decisions in this release

### Low presence over high visibility

Skill Router is designed to be invisible when things are simple. It only speaks when routing is genuinely ambiguous or when a capability gap exists.

### Installed-first over search-first

The default path is always to check what's installed before searching for anything new. This reduces installation churn and respects the user's existing setup.

### Single dominant capability over decomposition

Rather than decomposing tasks into many sub-capabilities and trying to match each one, Skill Router identifies the single most important capability and routes based on that.

### Conservative discovery

Discovery is treated as a last resort, not a default step. This prevents skill sprawl and keeps the installed environment manageable.

---

## Known limitations

- No automated matching — routing decisions rely on reading skill descriptions, not programmatic matching
- No cross-session memory of routing decisions (unless the environment provides persistent memory)
- Vetting is advisory, not enforced — the user can always override
- The capability taxonomy is intentionally small; it will grow based on real usage
- No multi-agent routing — this version assumes a single agent making routing decisions

---

## What's next

- Stronger runtime matching consistency across environments
- Cleaner public examples for mixed-skill and mixed-capability tasks
- Richer product presentation and visual identity
