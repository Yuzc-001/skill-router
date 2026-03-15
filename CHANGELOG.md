# Changelog

All notable changes to Skill Router will be documented in this file.

## [0.1.1] — 2026-03-15

### Added

- `docs/public-surface.md` — defines the boundary between public product guarantees and local-only configuration
- `Integration & Messaging` capability category in `references/capability-taxonomy.md` — covers messaging platforms, developer APIs, social media, email, and webhooks
- `docs/public-surface.md` referenced in `SKILL.md` reference table and `README.md` repository tree

### Changed

- `SKILL.md` examples tightened to avoid implying local-only tool names are universally installed
- Routing examples rewritten to separate shipped guarantees from local environment shortcuts
- `README.zh-CN.md` synchronized with current English README structure
- `README.md` repository tree updated to include `README.zh-CN.md` and `docs/public-surface.md`

## [0.1.0] — 2026-03-12

### Added

- Core routing skill (`SKILL.md`) with six-step resolution sequence
- Five routing behaviors: reuse-first, installed-reality-first, discovery-only-for-insufficiency, vet-before-install, quiet-by-default
- Capability taxonomy (`references/capability-taxonomy.md`)
- Resolution order reference (`references/resolution-order.md`)
- Publish-safe runtime contract (`references/publish-safe-runtime-contract.md`)
- Reminder policy (`references/reminder-policy.md`)
- Micro routing examples (`references/micro-routing-examples.md`) — 13 patterns
- Local overrides example (`references/local-overrides-example.md`)
- Task-to-skill map template (`references/task-to-skill-map.md`)
- Documentation: why, how-it-works, use-cases, with-vs-without, release notes
- README with repository structure and quick-start guide
