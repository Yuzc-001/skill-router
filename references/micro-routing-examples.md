# Micro Routing Examples

Short examples for Skill Router v0.5.

Read this file only when you need a compact pattern reminder.
If the decision is already obvious, do not read it.

---

## Pattern 1 — No route needed

**Task:** “What’s the capital of France?”

**Route:** `This task does not need skill-router.`

---

## Pattern 2 — Obvious installed default

**Task:** “Create a PowerPoint deck from these notes.”

**Installed:** `pptx`

**Route:** `Use pptx.`

---

## Pattern 3 — Forgotten installed skill

**Task:** “Do we already have a skill for PDF work?”

**Installed:** `pdf`, `docx`

**Route:** `Use the installed pdf skill.`

---

## Pattern 4 — Real insufficiency

**Task:** “I need a skill for a service none of my installed tools support.”

**Installed:** no matching skill

**Route:** `The installed set is not enough; discover candidates.`

---

## Pattern 5 — Unfamiliar candidate

**Task:** “I found this third-party skill. Should I install it?”

**Route:** `Candidate is unfamiliar; vet before recommendation.`

---

## Pattern 6 — User explicitly names the skill

**Task:** “Use the github skill for this PR.”

**Route:** `Use github.`

---

## Bottom line

If an example needs a long explanation, it probably is not a good micro-routing example.
