# Capability Taxonomy

A lightweight classification of task capabilities for routing decisions.

This is not an exhaustive ontology. It is a practical reference for identifying the **dominant capability** a task requires, so Skill Router can match it against installed skills.

---

## How to Use This File

1. Read the user's task
2. Identify which capability category best describes what the task **primarily** needs
3. Use that category to search installed skills for a match
4. If the task spans multiple categories, pick the **dominant** one — the one that determines success or failure

Do not decompose tasks into fine-grained sub-capabilities. The goal is a single routing decision, not a dependency graph.

---

## Capability Categories

### Document Creation

Producing structured output files: reports, presentations, spreadsheets, PDFs, Word documents, slide decks.

**Signals:** "create a report", "make a presentation", "build a spreadsheet", file format mentions (.docx, .pptx, .xlsx, .pdf)

### Document Transformation

Converting, reformatting, merging, splitting, or restructuring existing documents.

**Signals:** "convert this to", "merge these files", "reformat", "extract from this PDF"

### Code Generation

Writing new code: applications, scripts, components, functions, configurations.

**Signals:** "build an app", "write a script", "create a component", explicit language/framework mentions

### Code Transformation

Refactoring, porting, debugging, optimizing, or migrating existing code.

**Signals:** "refactor this", "port to Python", "fix this bug", "optimize", "migrate from X to Y"

### Data Analysis

Analyzing, summarizing, visualizing, or extracting insights from structured or unstructured data.

**Signals:** "analyze this data", "what trends do you see", "summarize these results", "chart this"

### Research & Information Retrieval

Finding, synthesizing, and presenting information from various sources.

**Signals:** "research X", "find out about", "what's the latest on", "compare options for"

### Design & Visual

Creating or editing visual artifacts: UI mockups, diagrams, illustrations, design systems.

**Signals:** "design a page", "create a mockup", "draw a diagram", "make it look better"

### Communication & Writing

Drafting, editing, or refining written communications: emails, messages, articles, documentation.

**Signals:** "write an email", "draft a message", "edit this text", "improve the writing"

### Integration & Messaging

Sending or reading messages, notifications, or events through external platforms and services. Covers messaging apps, developer platforms, social media APIs, email services, and webhook-based integrations.

**Signals:** "send a Slack message", "post to Twitter", "create a GitHub issue", "trigger a webhook", "notify the team on Discord", "check my emails", "post this to Weibo", "open a PR"

### Workflow Automation

Orchestrating multi-step processes, integrations, or automations across tools and services.

**Signals:** "automate this", "set up a pipeline", "connect X to Y", "every time X happens, do Y"

### System Administration

Managing infrastructure, configurations, deployments, environments, and tooling.

**Signals:** "deploy this", "configure the server", "set up the environment", "install and configure"

### Planning & Strategy

Developing plans, roadmaps, strategies, or structured decision frameworks.

**Signals:** "help me plan", "what's the best approach", "create a roadmap", "prioritize these"

### Learning & Explanation

Teaching, explaining, tutoring, or creating educational content.

**Signals:** "explain how", "teach me", "what does X mean", "walk me through"

---

## When a Task Doesn't Fit

If a task doesn't clearly map to any category above, it probably doesn't need skill routing. Just do the task directly.

If a task genuinely represents a new capability category not listed here, note it — this taxonomy should grow organically based on real routing needs, not speculation.

---

## Multi-Capability Tasks

Some tasks touch multiple categories. Examples:

- "Research competitors and create a presentation" → **Document Creation** is dominant (the presentation is the deliverable; research is a means to that end)
- "Analyze this CSV and write a report about the findings" → **Data Analysis** is dominant (the analysis determines quality; the report is packaging)
- "Build a dashboard that pulls data from our API" → **Code Generation** is dominant (the code is the hard part; the data display follows)

The heuristic: **what determines whether the user considers the task successful?** That's your dominant capability.
