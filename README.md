# Skill Router

[English](./README.md) · [简体中文](./README.zh-CN.md) · [GitHub Repository](https://github.com/Yuzc-001/skill-router) · [Issues](https://github.com/Yuzc-001/skill-router/issues) · [Release Notes](./CHANGELOG.md)

[![Version](https://img.shields.io/badge/version-v0.5.0-0B1738?style=flat-square)](./CHANGELOG.md)
[![License](https://img.shields.io/badge/license-MIT-2FAE73?style=flat-square)](./LICENSE)
[![Type](https://img.shields.io/badge/type-runtime-4C6FFF?style=flat-square)](./SKILL.md)
[![Default](https://img.shields.io/badge/default-installed--first-2FAE73?style=flat-square)](./docs/how-it-works.md)

A low-presence runtime for reducing skill-selection waste in skill-heavy agent environments.

> Use installed defaults first.

> Discover only when the current environment is genuinely insufficient.

> Speak only when routing changes the actual next action.

---

## What it does

Skill Router v0.5 is not trying to classify everything.
It is trying to reduce waste in crowded skill environments.

Its core job is to reduce:
- repeated skill discovery
- repeated skill comparison
- repeated installation caused by forgetting what already exists
- routing commentary that costs more than the decision itself
- unstable defaults in recurring overlap clusters

If none of those are happening, Skill Router should disappear.

## What it is now

Skill Router is now best understood as:

# a low-presence skill default resolver

and, at its strongest:

# a runtime for reducing skill-environment entropy

It is not a taxonomy-first product anymore.
It is a runtime whose value depends on whether it lowers unnecessary decision cost.

## What it is not

Skill Router is not:
- a universal taxonomy engine
- a package manager
- a search engine
- a mandatory pre-step before execution
- a meta-layer that deserves to speak on every task
- a long-form explainer for decisions that should be one line

If it becomes any of those, it has failed.

## The v0.5 runtime path

1. Decide whether routing is actually needed at all
2. Prefer the strongest installed default
3. Test whether the current environment is genuinely insufficient
4. Discover only for a real gap
5. Vet unfamiliar candidates before recommendation

**Core rule:** No default change, no voice.

**Economic rule:** No waste reduction, no value.

**Boundary rule:** If routing does not change the next action, Skill Router should disappear.

## Repository structure

```
skill-router/
├── README.md               ← You are here
├── README.zh-CN.md         ← 简体中文版
├── SKILL.md                ← The runtime skill itself
├── LICENSE                 ← MIT license
├── VERSION                 ← Current version
├── CHANGELOG.md            ← Release history
├── docs/
│   ├── why-skill-router.md
│   ├── how-it-works.md
│   ├── use-cases.md
│   ├── with-vs-without.md
│   ├── public-surface.md
│   ├── release-notes-v0.1.0.md
│   ├── release-notes-v0.4.0.md
│   ├── release-notes-v0.5.0.md
│   ├── skill-router-v0.4-product-milestone.md
│   └── skill-router-v0.5-ruthless-reset.md
└── references/
    ├── capability-taxonomy.md
    ├── resolution-order.md
    ├── publish-safe-runtime-contract.md
    ├── reminder-policy.md
    ├── micro-routing-examples.md
    ├── local-overrides-example.md
    └── task-to-skill-map.md
```

## Current release

**v0.5.0** — Ruthless reset. Skill Router is no longer centered on routing doctrine or taxonomy expansion. It is now centered on one runtime purpose: reducing unnecessary skill-selection cost in crowded environments.

See [CHANGELOG](CHANGELOG.md) for full details, or start with the dedicated [v0.5 reset document](docs/skill-router-v0.5-ruthless-reset.md).

## Read next

1. [Skill Router v0.5 — Ruthless Reset](docs/skill-router-v0.5-ruthless-reset.md)
2. [Why Skill Router](docs/why-skill-router.md)
3. [How It Works](docs/how-it-works.md)
4. [With vs Without](docs/with-vs-without.md)
5. [SKILL.md](SKILL.md) — the runtime skill itself
6. [Partial Issues Plan](docs/skill-router-v0.5-partial-issues-plan.md)
7. [Partial Re-evaluation](docs/skill-router-v0.5-partial-reevaluation.md)
8. [Evaluator Spec](docs/skill-router-v0.5-evaluator-spec.md)
9. [Gold-Set Schema](docs/skill-router-v0.5-gold-set-schema.md)
10. [Gold-Set Sample](docs/skill-router-v0.5-gold-set-sample.md)
11. [Gold Set v1](docs/skill-router-v0.5-gold-set-v1.md)

## Collaboration & Contact

- **Issues:** [github.com/Yuzc-001/skill-router/issues](https://github.com/Yuzc-001/skill-router/issues)
- **Email:** [zxyu24@outlook.com](mailto:zxyu24@outlook.com)

Use **Issues** for bugs, install problems, documentation gaps, and feature discussion.
Use **email** for licensing, private collaboration, or questions that should not start in a public thread.

## License

This project is licensed under the [MIT License](./LICENSE).
