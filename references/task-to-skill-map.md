# Task-to-Skill Map

A two-layer routing table. The portable layer ships with Skill Router. The local layer is built automatically from your installed environment and grows through use.

---

## How to Use

1. Identify the task type from the user's request
2. Check the Local Map first — if an entry exists and the skill is installed, route directly
3. Check the Portable Defaults if no local entry exists
4. If still no match, run the full resolution sequence from SKILL.md
5. After every new routing decision, add the result to the Local Map (Behavior 6)

---

## Portable Defaults

These mappings apply in virtually any environment where these skill types exist. They use generic capability descriptions, not specific skill names.

```
Word document (.docx)          → the installed skill whose primary purpose is .docx creation
PDF creation / reading         → the installed skill whose primary purpose is .pdf work
Presentation (.pptx)           → the installed skill whose primary purpose is .pptx creation
Spreadsheet / CSV analysis     → the installed skill whose primary purpose is .xlsx/.csv work
Web UI / frontend              → the installed skill whose primary purpose is HTML/CSS/JS interfaces
Translation                    → the installed skill whose primary purpose is language translation
Image generation               → the installed skill whose primary purpose is text-to-image generation
Video / audio processing       → the installed skill whose primary purpose is video/audio manipulation
OCR / text extraction          → the installed skill whose primary purpose is extracting text from images or files
Code review                    → the installed skill whose primary purpose is reviewing code changes
Git commit message             → the installed skill whose primary purpose is generating commit messages
Project release                → the installed skill whose primary purpose is versioned releases
```

These are resolved at routing time by matching descriptions — not by hardcoding skill names. If your environment has no skill matching a description, fall through to the full resolution sequence.

---

## Local Map

Built automatically by Skill Router when running in your environment. Updated after each new routing decision (Behavior 6: Self-Updating Map).

If this section is empty, Skill Router will run a Bootstrap Scan on first invocation to populate it. See SKILL.md — Bootstrap Protocol.

```
# Local Map — populated automatically. Do not edit manually.
# Format: Task Type → Skill Name | Confidence: high | medium
#         Notes: any routing nuances

```

---

## Bootstrap Scan Output

After a Bootstrap Scan, this section is populated with discovered mappings from your installed environment. Skill Router reads each installed skill's name and description, matches it to a capability category, and adds the mapping here.

Example of what a populated Local Map looks like after bootstrap:

```
# (example — your actual map will reflect your installed skills)
# Text-to-image generation     → gemini-image          | Confidence: high
# Post to WeChat               → baoyu-post-to-wechat  | Confidence: high
# Feature development          → ccg:feat              | Confidence: high
# Data analysis (multi-format) → data-analysis         | Confidence: high
```

---

## Maintaining This Map

The Local Map is maintained automatically by Skill Router. Manual edits are valid but not required.

**Add manually when:**
- You want to override an auto-generated entry
- You have a strong preference for a specific skill over the default

**Do not add to Portable Defaults** — that section is part of the published skill and should remain environment-agnostic.
