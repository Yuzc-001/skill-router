# Distrust and Clarification Policy

Use this file when the user expresses doubt, distrust, or uncertainty about the installed path.

This file exists to separate three different things that should not be conflated:
- subjective distrust
- raised quality bar
- missing task information

---

## Core distinction

### 1. Subjective distrust
Example:
- `I don’t trust this skill.`

By itself, this does **not** automatically mean the installed path is insufficient.
It means the router should briefly check whether the user is signaling a real quality/safety concern or just preference uncertainty.

### 2. Raised quality or safety bar
Examples:
- `I need something more reliable.`
- `This has to be professional.`
- `I want the safest option.`

This **does** materially change the decision.
Treat it as part of the task bar.

### 3. Missing task information
Examples:
- `Send this message.`
- `Post this update.`

Here the problem is not distrust and not insufficiency.
The problem is that the next action is underspecified.

---

## Rule for distrust

If the user expresses distrust, do this in order:
1. check whether they are actually raising the bar (quality, reliability, safety)
2. if yes, re-evaluate sufficiency more aggressively
3. if no, do not automatically trigger discovery
4. if needed, ask one short question to clarify what the concern means

---

## Rule for under-specified tasks

If the missing detail changes the next action, ask one short clarification.

Examples:
- missing platform / destination
- missing quality threshold
- missing safety/cost preference

Do not route as if this were a skill conflict when it is really a task-specification gap.

---

## Good clarification examples

- `What’s the destination platform?`
- `Do you want the quick acceptable version or the higher-quality version?`
- `Should I optimize for safest option or fastest route?`

---

## Bad clarification examples

- long survey of all possible skills
- taxonomy-heavy reasoning dump
- asking several questions when one would decide the next action

---

## Output guidance

If distrust becomes a raised bar:
- `For that quality bar, the installed set is not enough; discover candidates.`
- or `For that safety bar, use X.`

If distrust is still vague:
- ask one short clarifying question

If the issue is just missing task specification:
- ask one short clarifying question

---

## Bottom line

Distrust is not automatically insufficiency.
Under-specification is not automatically a routing conflict.
Use one short clarification when that is what actually changes the next action.
