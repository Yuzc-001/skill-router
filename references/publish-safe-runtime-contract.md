# Publish-Safe Runtime Contract

Guidelines for vetting third-party skill candidates before recommending installation.

---

## When This Applies

Apply this contract when Skill Router's resolution reaches Step 6 — a candidate skill has been found through discovery, and it comes from an unfamiliar or unvetted source.

This does **not** apply to:
- Skills the user created themselves
- Skills from sources the user has already trusted and used
- Built-in or first-party skills that ship with the platform

---

## The Vetting Checklist

Before recommending installation of an unfamiliar third-party skill, evaluate it against these criteria:

### 1. Stated Purpose Clarity

- Does the skill clearly state what it does?
- Is the description specific enough to understand its scope?
- Would a non-technical user understand what this skill is for?

**Red flag:** Vague descriptions like "enhances your workflow" or "does everything better" with no specifics.

### 2. Scope-to-Purpose Ratio

- Do the skill's requested permissions match its stated purpose?
- Does it access only what it needs, or does it request broad system access?
- Are there capabilities in the skill that go beyond what the description promises?

**Red flag:** A "markdown formatter" skill that requests network access or file system write permissions outside its output directory.

### 3. Source Accountability

- Is the author or organization identifiable?
- Is there a repository, website, or contact point?
- Has this author published other skills that are known and trusted?
- Is there a version history showing active maintenance?

**Red flag:** Anonymous author, no repository, no version history, no way to report issues.

### 4. Behavioral Boundaries

- Does the skill stay within its stated scope during execution?
- Does it modify files or state outside its designated workspace?
- Does it make network requests that aren't part of its core function?
- Does it attempt to access or exfiltrate user data?

**Red flag:** A skill that writes to system directories, phones home, or accesses unrelated user files.

### 5. Non-Technical User Test

Ask yourself: "Would I be comfortable recommending this skill to someone who doesn't understand what it does internally?"

If the answer is no — if the skill requires the user to understand its internals to stay safe — it fails this test.

---

## Vetting Outcomes

### Pass

The skill clearly states its purpose, requests only necessary permissions, comes from an identifiable source, stays within behavioral boundaries, and passes the non-technical user test.

**Action:** Recommend installation. Briefly note what you checked.

### Conditional Pass

The skill is mostly fine but has one area of concern that the user should know about.

**Action:** Recommend installation with a clear note about the concern. Let the user decide.

Example: "This skill looks solid, but it requests network access for update checks. That's common but worth knowing about if you prefer fully offline tools."

### Fail

The skill has one or more red flags that suggest it could be harmful, deceptive, or inappropriately scoped.

**Action:** Do not recommend installation. Explain the concern plainly. Suggest alternatives if available.

Example: "This skill requests write access to your entire home directory, which is much broader than what a markdown formatter needs. I'd recommend [alternative] instead."

---

## Principles

### Err Toward Caution

When in doubt, flag the concern and let the user decide. It is better to over-flag than to under-flag.

### Be Specific

Do not say "this skill seems suspicious." Say exactly what the concern is: "This skill requests access to X, which is unusual for a skill that claims to do Y."

### Respect User Autonomy

Vetting provides information. The user makes the final decision. If they understand the risks and want to proceed, respect that.

### Do Not Block Exploration

Vetting is not gatekeeping. The goal is informed installation, not prevented installation. A user who wants to explore and test a skill in a sandboxed environment should be supported.
