# Task-to-Skill Map

A maintained mapping from common task types to installed skills. This is a living document — update it as skills are installed, removed, or as routing patterns emerge.

---

## Purpose

This map accelerates routing by providing a quick lookup from task type to the most appropriate installed skill. It reduces the need to run the full resolution sequence for common, well-understood tasks.

---

## How to Use

1. Identify the task type from the user's request
2. Look up the task type in this map
3. If a mapping exists and the skill is still installed → route directly
4. If no mapping exists → run the full resolution sequence from SKILL.md
5. After a successful routing decision for a new task type → consider adding it here

---

## Map Structure

Each entry follows this format:

```
Task Type → Primary Skill [→ Secondary Skill (if commonly combined)]
  Confidence: high | medium
  Notes: any routing nuances
```

---

## Default Map

This map assumes a standard installation of common skills. Adjust based on actual installed skills.

### Document Tasks

```
Word document creation     → docx        | Confidence: high
PDF creation               → pdf         | Confidence: high
PDF reading/extraction     → pdf         | Confidence: high
Presentation creation      → pptx        | Confidence: high
Spreadsheet creation       → xlsx        | Confidence: high
Spreadsheet analysis       → xlsx        | Confidence: high
CSV processing             → xlsx        | Confidence: high
Document format conversion → (source format skill)  | Confidence: medium
  Notes: Route to the skill matching the SOURCE format; it likely handles export
```

### Code Tasks

```
Web UI / frontend creation → frontend-design  | Confidence: high
React component creation   → frontend-design  | Confidence: high
HTML/CSS layout            → frontend-design  | Confidence: high
General code generation    → (no skill needed) | Confidence: high
  Notes: Most code generation is handled directly without a skill
Code debugging             → (no skill needed) | Confidence: high
```

### Data Tasks

```
Data analysis (tabular)    → xlsx        | Confidence: high
Data visualization         → xlsx → frontend-design  | Confidence: medium
  Notes: xlsx for the analysis, frontend-design if the visualization needs
  to be interactive or web-based
Chart creation             → xlsx        | Confidence: medium
  Notes: For embedded charts in spreadsheets. For standalone web charts,
  consider frontend-design
```

### Multi-Step Tasks

```
"Read PDF + create spreadsheet"    → pdf → xlsx     | Confidence: high
"Analyze data + create report"     → xlsx → docx    | Confidence: medium
"Research + create presentation"   → (research) → pptx | Confidence: medium
  Notes: Research step may not need a skill; pptx for the deliverable
```

---

## Maintaining This Map

### When to add entries

- After a routing decision that took multiple steps to resolve
- When a user establishes a recurring pattern
- When a new skill is installed that covers common tasks

### When to remove entries

- When a skill is uninstalled
- When a mapping consistently routes to the wrong skill
- When a better routing pattern is discovered

### When to update entries

- When confidence levels change based on experience
- When notes need to capture new edge cases
- When secondary skill recommendations change

---

## Empty Map Template

If starting fresh with no installed skills, this map should be empty. Populate it as skills are installed and routing patterns emerge.

```
# Task-to-Skill Map (empty)
# Add entries as routing patterns are established.
```
