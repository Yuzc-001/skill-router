# Release Notes — v0.1.1

**Released:** 2026-03-15

Maintenance release. Improves routing coverage, tightens public guarantees, and synchronizes documentation.

---

## What changed

### Added: Integration & Messaging capability category

`references/capability-taxonomy.md` now includes an **Integration & Messaging** category covering tasks that interact with external platforms through APIs or message-passing:

- Messaging apps (Slack, Teams, Discord, WeChat)
- Developer platforms (GitHub issues, PRs, releases)
- Social media APIs (Twitter/X, Weibo)
- Email services
- Webhook triggers and event-based integrations

**Signals:** "send a Slack message", "create a GitHub issue", "post to Twitter", "trigger a webhook", "notify the team on Discord"

This closes a routing gap where tasks involving external service integrations had no clear capability category to land on.

### Added: public-surface.md

`docs/public-surface.md` defines the boundary between what Skill Router publicly guarantees and what is local-only configuration. It is now referenced in `SKILL.md`'s reference table and listed in the repository tree.

### Changed: documentation consistency

- `README.zh-CN.md` rewritten to match the current English README structure — removes outdated sections, deleted asset references, and badge markup
- `README.md` repository tree updated to list all current files
- `SKILL.md` examples tightened to avoid implying local tool names are universally available

---

## No behavior changes

Routing logic, resolution order, and all five routing behaviors are unchanged from v0.1.0. This release only adds taxonomy coverage and improves documentation accuracy.
