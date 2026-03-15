# Skill Router

[English](./README.md) · [简体中文](./README.zh-CN.md) · [GitHub Repository](https://github.com/Yuzc-001/skill-router) · [Issues](https://github.com/Yuzc-001/skill-router/issues) · [Release Notes](./docs/release-notes-v0.1.1.md)

[![Version](https://img.shields.io/badge/version-v0.1.1-0B1738?style=flat-square)](./CHANGELOG.md)
[![License](https://img.shields.io/badge/license-MIT-2FAE73?style=flat-square)](./LICENSE)
[![Type](https://img.shields.io/badge/type-routing%20layer-4C6FFF?style=flat-square)](./SKILL.md)
[![Default](https://img.shields.io/badge/default-reuse--first-2FAE73?style=flat-square)](./docs/how-it-works.md)

A low-presence routing layer for skill-heavy agent environments.

> Choose the best installed skill first. Discover only when existing skills are clearly insufficient.

---

## What it does

Skill Router adds five behaviors to skill-heavy workflows:

- **Reuse-first routing** — prefer installed skills before searching for new ones
- **Installed-reality-first judgment** — route based on what is actually installed, not ideal assumptions
- **Discovery only for insufficiency** — search only when installed capabilities are clearly not enough
- **Vet before unfamiliar install** — review unknown candidates through safety checklist before recommending
- **Quiet-by-default guidance** — avoid interrupting simple tasks with unnecessary routing commentary

## What it is not

Skill Router is not a search engine, a package manager, a replacement for normal skill triggering, or a meta-layer that should speak on every task.

It is a decision layer for moments when skill *choice* itself becomes part of the problem.

## How it works

1. Identify the dominant capability the task needs
2. Inspect the installed skill environment
3. Prefer the strongest installed match
4. Apply the enough-is-enough rule — if installed is good enough, stop
5. Move to discovery only when installed skills are clearly insufficient
6. Route unfamiliar third-party candidates to vetting before installation

**Core principle:** Installed reality beats local preference.
**Operational rule:** Discovery is for insufficiency, not novelty.

## Repository structure

```
skill-router/
├── README.md               ← You are here
├── README.zh-CN.md         ← 简体中文版
├── SKILL.md                ← The routing skill itself
├── LICENSE                 ← MIT license
├── VERSION                 ← Current version
├── CHANGELOG.md            ← Release history
├── docs/
│   ├── why-skill-router.md
│   ├── how-it-works.md
│   ├── use-cases.md
│   ├── with-vs-without.md
│   ├── public-surface.md
│   └── release-notes-v0.1.0.md
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

**v0.1.1** — Maintenance release: adds Integration & Messaging capability category, tightens public surface documentation.

See [release notes](docs/release-notes-v0.1.1.md) for details.

## Read next

1. [Why Skill Router](docs/why-skill-router.md)
2. [How It Works](docs/how-it-works.md)
3. [Use Cases](docs/use-cases.md)
4. [With vs Without](docs/with-vs-without.md)
5. [SKILL.md](SKILL.md) — the routing skill itself

## Collaboration & Contact

- **Issues:** [github.com/Yuzc-001/skill-router/issues](https://github.com/Yuzc-001/skill-router/issues)
- **Email:** [zxyu24@outlook.com](mailto:zxyu24@outlook.com)

Use **Issues** for bugs, install problems, documentation gaps, and feature discussion.
Use **email** for licensing, private collaboration, or questions that should not start in a public thread.

## License

This project is licensed under the [MIT License](./LICENSE).
