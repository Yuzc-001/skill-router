# Changelog

All notable changes to Skill Router will be documented in this file.

## [0.3.0] — 2026-03-18

### Fixed

- **Skill Families portability** — removed hardcoded private environment family names (`baoyu-*`, `ccg:*`, `superpowers:*`) from `SKILL.md` and `references/resolution-order.md`. Replaced with generic family concepts and routing rules. Specific families are now discovered by Bootstrap Scan and recorded in the Local Map, not hardcoded in the core skill.
- **Step 0 Portable Defaults gap** — Step 0 now explicitly checks Portable Defaults as a second fast-path layer (Local Map → Portable Defaults → Step 1). Previously, Portable Defaults were described in `task-to-skill-map.md` but never referenced in the routing sequence.
- **Portable Defaults name resolution** — Step 0 Portable Defaults path now includes an explicit step to resolve the capability description to an actual installed skill name before invoking.
- **Bootstrap trigger ambiguity** — clarified that Bootstrap runs automatically once on first use (empty Local Map), and only re-runs when explicitly triggered thereafter. Previous wording implied a contradiction between "automatic" and "only when triggered".
- **Bootstrap → Step 0 sequencing gap** — Step 0 now explicitly states: if Local Map is empty, run Bootstrap Protocol first, then return to Step 0. The connection was previously implicit.
- **No invocation action after routing** — Steps 0 and 4 now specify "invoke the skill by name" as the concrete terminal action. Previously, routing decisions ended with "route there and stop" without specifying what invoking a skill means.
- **`route` vs `invoke` terminology** — unified language throughout `SKILL.md` and `references/resolution-order.md`. All routing conclusions now use "invoke".
- **`3d.` heading level** — demoted `### 3d. Tiebreaking Equal Matches` from a peer heading to a bold paragraph within Step 3. It was visually ambiguous as a sibling of `### Step 3` and `### Step 4`.
- **Step 2 skill enumeration source** — clarified that in Claude Code, the installed skill list is read from the `available-deferred-tools` section of the system reminder. Previously referenced a fictional `available_skills` variable.
- **Edge Cases duplicate tiebreaking rules** — removed a conflicting tiebreaking list from `### Multiple equally strong matches` in Edge Cases. That section now references Step 3's tiebreaking rules as the single source of truth.
- **`references/resolution-order.md` out of sync** — synchronized sequence diagram, Step 2 notes, and Step 4 conclusion with all of the above fixes.

## [0.2.1] — 2026-03-17

### Added

- **Bootstrap Protocol** in `SKILL.md` — on first use in a new environment, Skill Router scans all installed skills, maps them to capability categories, and populates the Local Map automatically. No manual configuration needed.
- **Step 0 Fast Path** in resolution sequence — checks Local Map before running full resolution. Cache hit routes immediately, skipping Steps 1–4.
- **Two-layer task-to-skill-map** — Portable Defaults (environment-agnostic, ships with the skill) + Local Map (auto-built from installed skills, empty by default). Eliminates the problem of a pre-populated map that only works for one specific environment.

### Changed

- `references/task-to-skill-map.md` — rebuilt as a two-layer structure. Removed environment-specific mappings from the portable layer. Local Map starts empty and is populated by bootstrap and self-update.
- `references/resolution-order.md` — sequence diagram updated to include Step 0 and Local Map update step.

## [0.2.0] — 2026-03-17

### Added

- **Six Routing Behaviors** — added Behavior 6: Self-Updating Map; routing table grows with use
- **Skill Families section** in `SKILL.md` — routing guidance for `baoyu-*`, `ccg:*`, `superpowers:*`, `example-skills:*` families
- **Tiebreaker rule 3d** in `SKILL.md` and `references/resolution-order.md` — four-priority conflict resolution for equal-capability skills
- **find-skills delegation** in Step 5 — if `find-skills` is installed, delegate discovery to it before manual search
- **example-skills edge case** in Guidance on Edge Cases — always prefer non-example version when duplicates exist
- **Platform Context Rule** in `references/capability-taxonomy.md` — platform signals override generic matching
- **8 new capability categories** in `references/capability-taxonomy.md`: Image Generation, Visual Content Production, Image Processing, Video & Animation, OCR & Text Extraction, Translation, Social Media Publishing, Development Workflow (total: 21 categories, up from 13)
- **60+ task-to-skill mappings** in `references/task-to-skill-map.md` — full coverage of installed skills including baoyu-\*, ccg:\*, remotion, ppocrv5, data-analysis, deepl, release-skills, and more (previously ~10 entries)
- **18 routing examples** in `references/micro-routing-examples.md` — replaced generic examples with real installed skill patterns including platform routing, pipeline routing, and tiebreaker scenarios

### Changed

- `SKILL.md` Step 2 — added skill family awareness, example-skills priority, and pipeline detection
- `SKILL.md` Step 4 — replaced subjective "materially harmed" test with concrete three-question test
- `SKILL.md` "Five Routing Behaviors" renamed to "Six Routing Behaviors"
- `references/resolution-order.md` — synchronized Step 2, 3, 4, 5 and cheat sheet with updated SKILL.md logic

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
