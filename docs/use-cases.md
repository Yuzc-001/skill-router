# Use Cases

## When Skill Router helps

### "Do we already have a skill for this?"

The user has many skills installed and cannot remember if one covers their current need. Skill Router inspects the installed environment and points to the best match — or confirms that no match exists.

### "Which skill should I use?"

Multiple installed skills could fit. Skill Router picks the strongest match based on the dominant capability and briefly explains the choice.

### Preventing unnecessary installation

A user is about to search for and install a new skill, but an installed skill already covers the need. Skill Router catches this by checking installed capabilities first.

### Safe discovery

No installed skill fits. Skill Router searches for candidates, evaluates them, and routes unfamiliar options through vetting before recommending installation.

### Forgotten skills

The user installed a skill months ago and forgot about it. Skill Router finds it during the installed-match step and routes the task there, saving a redundant installation.

---

## When Skill Router stays out of the way

### Simple tasks

"What's 2 + 2?" — No skill needed. No routing commentary.

### Obviously matched tasks

"Create a PowerPoint presentation" with `pptx` installed — one obvious match, route silently.

### User explicitly names a skill

"Use the pdf skill for this" — respect the explicit choice, no second-guessing.

### Tasks that don't need skills

A quick answer, a one-liner, a small edit — just do it. Skills add overhead to trivial tasks.

---

## Scenario walkthroughs

### Scenario 1: New task, strong installed match

> **User:** "Create a detailed report from these sales figures."
> **Installed:** docx, xlsx, pdf, pptx
> **Skill Router thinks:** Dominant capability = Document Creation. `docx` is a direct match. Enough.
> **Result:** Routes to `docx`. No commentary.

### Scenario 2: New task, no installed match

> **User:** "Deploy this app to Kubernetes with auto-scaling."
> **Installed:** docx, xlsx, pdf, pptx, frontend-design
> **Skill Router thinks:** Dominant capability = System Administration (deployment). No installed skill covers this.
> **Result:** States the gap. Proceeds to discovery. Presents candidates for review.

### Scenario 3: Multiple matches, needs disambiguation

> **User:** "Create a visual report with interactive charts from this dataset."
> **Installed:** xlsx, frontend-design, docx, pdf
> **Skill Router thinks:** Dominant capability = Data Analysis + Document Creation. `xlsx` handles data and charts. `frontend-design` handles interactive web visuals. The word "interactive" tips toward `frontend-design` for the deliverable, with `xlsx` for data processing.
> **Result:** Recommends `frontend-design` for the interactive output, notes `xlsx` for data prep. Brief explanation.

### Scenario 4: User about to redundantly install

> **User:** "Is there a skill for creating formatted PDF reports?"
> **Installed:** pdf, docx
> **Skill Router thinks:** `pdf` is already installed and handles PDF creation.
> **Result:** "You already have the `pdf` skill installed — it handles formatted PDF creation."

### Scenario 5: Discovery finds questionable candidate

> **User:** "Find me a skill for automated email outreach."
> **Installed:** (no email skills)
> **Skill Router discovers:** `email-blaster-pro` by anonymous author, requests full filesystem and network access.
> **Result:** Flags concerns during vetting. Notes the broad permissions relative to the stated purpose. Suggests looking for alternatives from known sources.
