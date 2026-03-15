# Micro Routing Examples

Quick reference for common routing patterns. Each example shows the task, the installed environment, and the correct routing decision.

---

## Pattern 1: Direct Match — Route Silently

**Task:** "Create a Word document summarizing these meeting notes."

**Installed:** `docx`, `pdf`, `xlsx`, `pptx`

**Route:** `docx` — direct match for Word document creation. Say nothing about routing.

---

## Pattern 2: Secondary Match — Still Good Enough

**Task:** "I need to analyze the data in this CSV and tell me what's interesting."

**Installed:** `xlsx`, `pdf`, `frontend-design`

**Route:** `xlsx` — its primary purpose is spreadsheet work, but it reads and analyzes CSVs well. This is a strong secondary match. Good enough. No discovery needed.

---

## Pattern 3: No Skill Needed

**Task:** "What's the capital of France?"

**Installed:** `docx`, `pdf`, `xlsx`, `pptx`, `skill-router`

**Route:** No skill. Answer directly. This task does not require any skill.

---

## Pattern 4: User Names a Skill

**Task:** "Use the pdf skill to convert this document."

**Installed:** `docx`, `pdf`, `xlsx`

**Route:** `pdf` — user explicitly named it. Do not second-guess or suggest alternatives.

---

## Pattern 5: Obvious Single Match

**Task:** "Make me a slide deck about our Q3 results."

**Installed:** `pptx`, `docx`, `pdf`

**Route:** `pptx` — only one skill handles presentations. Route silently.

---

## Pattern 6: Two Plausible Matches — Pick and Note

**Task:** "Create a formatted report of our sales data with charts."

**Installed:** `docx`, `xlsx`, `pdf`

**Route:** Multiple skills could contribute. Dominant capability is Document Creation (the report is the deliverable). Route to `docx` for the report, pulling in `xlsx` only if the data analysis step is complex enough to warrant it.

**Speak briefly:** "Using `docx` for the report. I'll handle the data analysis inline."

---

## Pattern 7: Genuine Gap — Discovery

**Task:** "Deploy this application to AWS with auto-scaling."

**Installed:** `docx`, `pdf`, `xlsx`, `pptx`, `frontend-design`

**Route:** No installed skill handles cloud deployment. This is a genuine capability gap.

**Speak:** "None of your installed skills handle cloud deployment. Let me search for something that fits."

Then proceed to discovery (Step 5).

---

## Pattern 8: Discovery Finds Unfamiliar Candidate — Vet First

**Task:** "I need a skill that can handle Kubernetes deployments."

**Discovered candidate:** `k8s-deployer` by unknown-author-42 on a third-party registry.

**Route:** Do not recommend installation immediately. Apply vetting checklist.

**Speak:** "I found `k8s-deployer`, but it's from an unfamiliar source. Let me check a few things before recommending it."

---

## Pattern 9: Small Combination — Worth It

**Task:** "Read this PDF, extract the financial data, and create a spreadsheet with charts."

**Installed:** `pdf`, `xlsx`

**Route:** Combination of `pdf` (extraction) + `xlsx` (spreadsheet creation). This combination materially changes the outcome — neither skill alone covers both steps well.

**Speak briefly:** "Using `pdf` to extract the data, then `xlsx` for the spreadsheet."

---

## Pattern 10: Small Combination — Not Worth It

**Task:** "Summarize this PDF."

**Installed:** `pdf`, `docx`

**Route:** `pdf` alone. No need to combine with `docx` — the user asked for a summary, not a formatted document. The `pdf` skill (or even no skill) can handle summarization.

---

## Pattern 11: Enough-Is-Enough in Action

**Task:** "Create a beautiful, interactive data dashboard."

**Installed:** `frontend-design`, `xlsx`

**Route:** `frontend-design` — it creates web interfaces. The result won't be a full production dashboard, but it will be a functional, styled interactive page. That's good enough unless the user specifies otherwise.

Do not search for a specialized "dashboard builder" skill. What's installed is sufficient.

---

## Pattern 12: User Exploring — Support Without Pushing

**Task:** "What skills do I have installed? Are there any good ones for data science?"

**Installed:** `xlsx`, `pdf`, `docx`, `pptx`, `frontend-design`

**Route:** This is an exploration query, not a task. List the installed skills. Note which ones touch data work (`xlsx`). Do not push the user toward installing new skills — they're browsing, not requesting.

---

## Pattern 13: Conflicting Signals — Follow Dominant Capability

**Task:** "I need to write some Python code that processes Excel files."

**Installed:** `xlsx`

**Route:** The dominant capability is Code Generation (writing Python code). The `xlsx` skill handles Excel files but its purpose is spreadsheet creation/editing, not writing Python scripts. The code generation can be done directly without a skill. The `xlsx` skill might be useful as a reference for Excel file handling patterns.

**Decision:** Do the code generation directly. Consult `xlsx` only if specific Excel format knowledge is needed.
