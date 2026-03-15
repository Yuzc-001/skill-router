# Skill Router

[English](./README.md) · [简体中文](./README.zh-CN.md) · [GitHub 仓库](https://github.com/Yuzc-001/skill-router) · [问题反馈](https://github.com/Yuzc-001/skill-router/issues) · [版本说明](./docs/release-notes-v0.1.1.md)

[![版本](https://img.shields.io/badge/version-v0.1.1-0B1738?style=flat-square)](./CHANGELOG.md)
[![类型](https://img.shields.io/badge/type-routing%20layer-4C6FFF?style=flat-square)](./SKILL.md)
[![默认策略](https://img.shields.io/badge/default-reuse--first-2FAE73?style=flat-square)](./docs/how-it-works.md)

一层低存在感的 skill 路由层，适用于 skill 数量较多的 agent 环境。

> 先选最合适的已安装 skill。只有现有 skill 明显不够时，才进入 discovery。

---

## 它做什么

Skill Router 给 skill-heavy 工作流增加五个行为：

- **reuse-first routing** — 先复用已安装 skill，不先找新的
- **installed-reality-first judgment** — 按用户真实安装环境路由，不按理想假设
- **discovery only for insufficiency** — 只有现有能力明显不足时才 discovery
- **vet before unfamiliar install** — 陌生第三方 skill 先过安全检查，再推荐安装
- **quiet-by-default guidance** — 简单任务保持安静，不打断工作流

## 它不是什么

Skill Router 不是搜索引擎、不是包管理器、不是 normal skill triggering 的替代品，也不是每个任务都要发言的 meta 层。

它是一个决策层，只在 **skill 选择本身成为问题时** 才出现。

## 它如何工作

1. 判断任务的主能力类型
2. 检查已安装的 skill 环境
3. 优先选择最强的已安装匹配
4. 应用 enough-is-enough 规则——已安装的够用就停在这里
5. 只有现有 skill 明显不足时，才进入 discovery
6. discovery 到陌生第三方候选时，先 vet 再推荐安装

**核心原则：** Installed reality beats local preference.
**操作规则：** Discovery is for insufficiency, not novelty.

## 仓库结构

```
skill-router/
├── README.md               ← 英文版
├── README.zh-CN.md         ← 你在这里
├── SKILL.md                ← skill 本体
├── VERSION                 ← 当前版本
├── CHANGELOG.md            ← 版本历史
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

## 当前版本

**v0.1.1** — 维护版本：新增 Integration & Messaging 能力分类，完善公开承诺文档。

详见 [release notes](docs/release-notes-v0.1.1.md)。

## 接着读

1. [为什么需要 Skill Router](docs/why-skill-router.md)
2. [它如何工作](docs/how-it-works.md)
3. [典型使用场景](docs/use-cases.md)
4. [有无 Skill Router 的差异](docs/with-vs-without.md)
5. [SKILL.md](SKILL.md) — skill 本体
