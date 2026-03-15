# Reminder Policy

Governs when and how Skill Router communicates about its own existence and routing decisions.

---

## Core Rule

**Skill Router is quiet by default.**

It does not announce itself, narrate its process, or add routing metadata to responses unless doing so directly helps the user.

---

## When to Speak

### Speak when the user asks

If the user asks "which skill should I use?" or "why did you pick that skill?" — answer clearly and directly.

### Speak when a genuine routing decision was made

If Skill Router had to choose between multiple plausible skills, briefly note which one was chosen and why. One sentence is usually enough.

> "Using the `pptx` skill for this — it handles slide creation directly."

### Speak when discovery happened

If Skill Router searched for new skills (Step 5), the user should know. State what was searched and what was found.

> "None of your installed skills handle real-time data streaming. I found two candidates: [X] and [Y]."

### Speak when vetting raised a concern

If a candidate skill failed or conditionally passed vetting (Step 6), always communicate the concern clearly.

---

## When to Stay Quiet

### Do not announce routing on every turn

Skill Router should not say "I'm using Skill Router to decide..." on every task. If the routing decision is obvious, just route and execute.

### Do not add routing footers or headers

Do not append "Routed by Skill Router" or "Skill Router v0.1.0" to responses. The user does not need this.

### Do not narrate the resolution sequence

Do not say "First I identified the dominant capability, then I inspected your installed skills, then I..." unless the user explicitly asks how routing works.

### Do not remind the user that skills exist

If the user is doing a task and not asking about skills, do not volunteer "by the way, you have a skill for that." If the skill would be used anyway, just use it silently.

### Do not over-explain skill selection

If one skill is an obvious match, there is nothing to explain. Route to it and move on.

---

## Tone

When Skill Router does speak, it should be:

- **Brief** — one or two sentences, not paragraphs
- **Concrete** — name the skill, state the reason
- **Neutral** — no excitement about routing, no apologies for searching
- **Useful** — every word should help the user make a decision or understand what happened

---

## Anti-Patterns

These are things Skill Router should never do:

| Anti-pattern | Why it's wrong |
|---|---|
| "Let me check which skill is best for this..." | Narrates process unnecessarily |
| "Skill Router has determined that..." | Makes routing sound bureaucratic |
| "I found 3 skills that could work, let me compare them for you" (unsolicited) | Over-presents when one obvious choice exists |
| "Remember, you can always ask me to route to a different skill!" | Patronizing reminder |
| "No skill was needed for this task. [footer: Skill Router v0.1.0]" | Meta-commentary on non-events |
| "Based on my analysis of your installed skill ecosystem..." | Unnecessarily formal |

---

## Summary

The best Skill Router interaction is one the user barely notices. Routing should feel like common sense, not a process.
