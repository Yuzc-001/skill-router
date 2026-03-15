# Local Overrides

How to handle user-specific routing preferences that override Skill Router's default behavior.

---

## What Are Local Overrides?

Local overrides are explicit user preferences about how tasks should be routed. They take precedence over Skill Router's default resolution order.

Examples:
- "Always use `docx` for reports, never `pdf`"
- "I prefer `frontend-design` for any web-related task"
- "Don't suggest new skills unless I explicitly ask"
- "For data tasks, always try `xlsx` first"

---

## How to Detect Them

Local overrides come from:

1. **Explicit statements** — the user directly says "always use X for Y"
2. **Repeated corrections** — the user keeps redirecting from one skill to another
3. **Environment configuration** — a local config file or memory entry specifying preferences
4. **Conversation history** — past conversations where the user established a preference

---

## How to Apply Them

### Override beats default resolution

If the user has an explicit preference, it wins. Do not run the full resolution sequence and then override at the end — skip directly to the preferred skill.

> User preference: "Always use `pdf` for reports"
> Task: "Create a quarterly report"
> Default resolution: Would route to `docx`
> With override: Route to `pdf` immediately

### Overrides are scoped

A preference for "reports" does not extend to "presentations" unless the user says so. Apply overrides narrowly.

### Overrides are revocable

If the user says "actually, let's try `docx` this time," respect that. Overrides are preferences, not laws.

---

## Storage

If the environment supports persistent memory or configuration:

- Store overrides as simple key-value pairs: `task_type → preferred_skill`
- Include the user's original statement for context
- Timestamp the override so stale preferences can be revisited

Example:

```
override: reports → pdf
  source: "Always use pdf for my reports" (2025-01-15)
  
override: web_tasks → frontend-design
  source: "I like the frontend-design skill for anything web-related" (2025-02-03)
```

---

## Conflicts

If an override conflicts with what Skill Router would choose:

1. Follow the override
2. Do not mention the conflict unless the override leads to a clearly worse outcome
3. If the outcome is clearly worse, mention it once: "I used `pdf` for this per your preference. If you'd like, `docx` might give you better table formatting for this kind of report."
4. Accept the user's decision either way

---

## Example: Full Override Flow

**Stored override:** `data_analysis → xlsx`

**Task:** "Analyze this JSON file and give me insights."

**Default resolution:** No strong installed match (JSON analysis isn't a primary skill). Might discover or route to general capability.

**With override:** Route to `xlsx`. The user prefers it for data tasks. It can read JSON and produce analysis.

**Outcome:** The override provides a clear, fast routing decision that respects the user's preference. No discovery needed.
