# Changelog

All notable changes to Skill Router will be documented in this file.

## [0.5.0] — 2026-03-22

### Changed

- **Ruthless reset of product center** — Skill Router is no longer framed primarily as a routing layer or taxonomy guide. `v0.5.0` re-centers the product on one runtime purpose: reducing unnecessary skill-selection cost in crowded skill environments.
- **North star rewritten** — the product now optimizes for lower routing waste, lower repeated comparison, lower repeated discovery, lower repeated installation, and stronger stable defaults.
- **`SKILL.md` fully rewritten** — the main skill contract now follows a much smaller runtime path: decide whether routing is needed, prefer the strongest installed default, test genuine insufficiency, discover only for real gaps, and vet unfamiliar candidates before recommendation.
- **Public contract tightened** — `docs/public-surface.md` now promises less but means it more strongly: installed reality first, discovery only for insufficiency, vet-before-admission, and silence whenever routing would not change the next real action.
- **Docs re-authored around v0.5** — `docs/how-it-works.md`, `docs/why-skill-router.md`, `docs/with-vs-without.md`, `docs/use-cases.md`, `references/resolution-order.md`, `references/task-to-skill-map.md`, `references/micro-routing-examples.md`, and `references/local-overrides-example.md` were all rewritten to match the new anti-waste runtime model.
- **Task-to-skill map demoted from center to utility** — the map is no longer presented as a growing universal routing table. It now exists only as a lightweight local-default record for recurring overlap clusters that genuinely reduce future routing waste.
- **Conflict handling narrowed** — `v0.5.0` focuses the main path on only the conflicts that materially matter: installed vs discover, dedicated vs general, platform-specific vs generic, recurring overlap clusters, and unfamiliar install vs safe reuse.
- **Output discipline hardened** — preferred output shapes are now short and executable (`Use X.`, `Installed set is not enough; discover candidates.`, `Candidate is unfamiliar; vet before recommendation.`, `This task does not need skill-router.`).
- **Release surface updated for the reset** — added `docs/skill-router-v0.5-ruthless-reset.md` and aligned repository entry points around the v0.5 reset.

### Notes

`v0.5.0` is intentionally disruptive.

It is not an incremental improvement to the old routing doctrine.
It is a cut-down-and-rebuild release.

The standard for this release is simple:

# if Skill Router does not reduce real decision waste, it does not deserve to speak

Primary reading for this release:
- `docs/skill-router-v0.5-ruthless-reset.md`
- `docs/why-skill-router.md`
- `docs/how-it-works.md`
- `docs/public-surface.md`

## [0.4.0] — 2026-03-20

### Changed

- **Product positioning sharpened** — Skill Router is now explicitly framed as a low-presence routing layer that resolves real selection conflicts **without replacing agent judgment**.
- **Boundary rule added** — introduced the explicit product rule: *when skill choice is not the problem, Skill Router should disappear*.
- **Conflict-set heuristic added** — shifted emphasis away from ever-finer taxonomy expansion and toward resolving recurring overlap clusters where default skill choice is genuinely unclear.
- **Resolution order tightened** — added a new first gate that asks whether routing is needed at all before checking maps or capabilities.
- **Non-trigger guidance strengthened** — clarified that Skill Router should not activate for simple tasks, obvious single-skill matches, already-active correct skills, or cases where more routing detail would not change the default decision.
- **Public contract clarified** — `docs/public-surface.md` now explicitly states that Skill Router reduces selection waste without replacing judgment, and that local conflict sets are not part of the public guarantee.
- **README / docs language upgraded** — repository messaging now reflects the product's actual role: a judgment-preserving, conflict-aware, low-bureaucracy routing layer.

### Notes

This release is intentionally philosophical and behavioral rather than feature-heavy. The goal is not to route more often. The goal is to route **better, less often, and with clearer boundaries**.

Dedicated release surface:
- `docs/release-notes-v0.4.0.md`
- `docs/skill-router-v0.4-product-milestone.md`

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
- **60+ task-to-skill mappings** in `references/task-to-skill-map.md` — full coverage of installed skills including baoyu-* , ccg:* , remotion, ppocrv5, data-analysis, deepl, release-skills, and more (previously ~10 entries)
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
