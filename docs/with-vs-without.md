# With vs Without Skill Router

Side-by-side comparison of workflows with and without Skill Router active.

---

## Scenario 1: User needs a formatted report

### Without Skill Router

1. User: "Create a formatted report from these meeting notes."
2. Agent scans available skills... considers docx, pdf, maybe xlsx
3. Agent: "I can use the docx skill to create a Word document, or the pdf skill to create a PDF. Which would you prefer? I could also create a spreadsheet if you want tabular data..."
4. User: "Just... make a report."
5. Agent creates the report using docx.

**Problem:** Unnecessary back-and-forth. The user didn't ask for a choice — they asked for a report.

### With Skill Router

1. User: "Create a formatted report from these meeting notes."
2. Skill Router identifies dominant capability (Document Creation), matches to `docx`, confirms it's sufficient.
3. Agent creates the report using docx. No commentary about the decision.

**Result:** Same outcome, fewer steps, no cognitive overhead for the user.

---

## Scenario 2: User has forgotten an installed skill

### Without Skill Router

1. User: "I need to create some slides. Is there a good skill for that?"
2. Agent searches a skill registry
3. Agent: "I found `slide-maker-pro` and `deck-builder`. Want me to install one?"
4. User installs `slide-maker-pro`
5. User now has both `pptx` (installed months ago, forgotten) and `slide-maker-pro` (redundant)

**Problem:** Redundant installation. The user already had what they needed.

### With Skill Router

1. User: "I need to create some slides. Is there a good skill for that?"
2. Skill Router checks installed skills first. Finds `pptx`.
3. Agent: "You already have the `pptx` skill installed — it handles slide creation."

**Result:** No unnecessary installation. User rediscovers what they already have.

---

## Scenario 3: Genuine capability gap

### Without Skill Router

1. User: "Deploy this to AWS."
2. Agent tries to do it with general knowledge
3. Result is incomplete or error-prone
4. User: "Is there a skill for this?"
5. Agent searches, finds multiple candidates
6. User installs the first result without evaluation

**Problem:** No systematic capability check. No vetting of the discovered skill.

### With Skill Router

1. User: "Deploy this to AWS."
2. Skill Router checks installed skills. No match for cloud deployment.
3. Agent: "None of your installed skills handle AWS deployment. Let me find candidates."
4. Skill Router searches, finds candidates, applies vetting checklist
5. Agent presents vetted options with brief rationale

**Result:** Gap is identified immediately. Candidates are vetted before recommendation.

---

## Scenario 4: Simple task, no skill needed

### Without Skill Router (over-eager routing)

1. User: "What's the capital of France?"
2. Agent: "Let me check if there's a geography skill installed... I don't see one. Should I search for a geography knowledge skill?"
3. User: "Just answer the question."

**Problem:** Routing overhead on a trivial task.

### With Skill Router

1. User: "What's the capital of France?"
2. Skill Router: (silent — task doesn't need any skill)
3. Agent: "Paris."

**Result:** No routing overhead. Simple tasks stay simple.

---

## Scenario 5: Multiple installed skills could fit

### Without Skill Router

1. User: "Analyze this CSV and create a chart."
2. Agent: "I could use xlsx, or I could use frontend-design for a web chart, or I could use the pdf skill to create a PDF with an embedded chart. Here are the pros and cons of each..."
3. User is now making a tool decision instead of getting work done

**Problem:** The user is forced into a skill selection process they didn't ask for.

### With Skill Router

1. User: "Analyze this CSV and create a chart."
2. Skill Router identifies dominant capability (Data Analysis), routes to `xlsx`.
3. Agent: "Using `xlsx` for the analysis and chart."
4. Work proceeds.

**Result:** Quick, decisive routing. One brief note. Work starts immediately.

---

## Summary

| Situation | Without Skill Router | With Skill Router |
|---|---|---|
| Obvious single match | Works, but might over-explain | Silent, fast |
| Forgotten installed skill | Redundant installation | Rediscovery |
| Genuine capability gap | Ad-hoc, unvetted | Systematic, vetted |
| Simple task | Possible over-routing | Quiet, direct |
| Multiple plausible matches | User forced to choose | Quick pick with brief note |
