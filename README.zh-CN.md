# Skill Router

[English](./README.md) · [简体中文](./README.zh-CN.md) · [GitHub 仓库](https://github.com/Yuzc-001/skill-router) · [问题反馈](https://github.com/Yuzc-001/skill-router/issues) · [版本说明](./CHANGELOG.md)

[![版本](https://img.shields.io/badge/version-v0.5.0-0B1738?style=flat-square)](./CHANGELOG.md)
[![许可](https://img.shields.io/badge/license-MIT-2FAE73?style=flat-square)](./LICENSE)
[![类型](https://img.shields.io/badge/type-runtime-4C6FFF?style=flat-square)](./SKILL.md)
[![默认策略](https://img.shields.io/badge/default-installed--first-2FAE73?style=flat-square)](./docs/how-it-works.md)

一层低存在感的 skill 运行时，用来降低 skill-heavy agent 环境里的选择浪费。

> 先走已安装环境里的稳定默认。

> 只有现有环境真的不够时，才进入 discovery。

> 只有在会改变下一步实际动作时，它才应该发言。

---

## 它现在在做什么

`skill-router v0.5` 不再试图把所有事都分类清楚。
它现在真正要做的，是降低 crowded skill environment 里的浪费。

它的核心价值是减少：
- 重复 discovery
- 重复比较
- 因为忘记已有能力而发生的重复安装
- 比决策本身还贵的 routing 说明
- 在 recurring overlap cluster 里的不稳定默认

如果这些浪费没有发生，Skill Router 就应该消失。

## 它现在是什么

现在的 Skill Router 最好理解成：

# 一个低存在感的 skill 默认决策运行时

再往强一点说：

# 一个降低 skill 环境熵的 runtime

它已经不再以 taxonomy 扩张或 routing doctrine 作为中心。
它的价值只取决于一件事：

# 有没有减少无谓决策成本

## 它不是什么

Skill Router 不是：
- 通用 taxonomy 引擎
- 包管理器
- 搜索引擎
- 执行前必须经过的一层
- 每个任务都该发言的 meta 层
- 本来一句话能说完却要长篇解释的系统

如果它变成这些，它就是失败的。

## v0.5 的 runtime 主路径

1. 先判断 routing 到底是不是必要
2. 优先走最强的已安装默认
3. 判断当前环境是不是真的不够
4. 只有真实缺口才 discovery
5. 对陌生候选先 vet，再推荐

**核心规则：** No default change, no voice.

**经济规则：** No waste reduction, no value.

**边界规则：** 如果 routing 不会改变下一步动作，Skill Router 就应该消失。

## 仓库结构

```
skill-router/
├── README.md               ← 英文版
├── README.zh-CN.md         ← 你在这里
├── SKILL.md                ← runtime skill 本体
├── LICENSE                 ← MIT 许可证
├── VERSION                 ← 当前版本
├── CHANGELOG.md            ← 版本历史
├── docs/
│   ├── why-skill-router.md
│   ├── how-it-works.md
│   ├── use-cases.md
│   ├── with-vs-without.md
│   ├── public-surface.md
│   ├── release-notes-v0.1.0.md
│   ├── release-notes-v0.4.0.md
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

## 当前版本

**v0.5.0** — 一次 ruthless reset。Skill Router 不再以 routing doctrine 或 taxonomy 扩张为中心，而是明确转向一个 runtime 目标：降低 crowded skill environment 里的无谓 skill-selection cost。

详见 [CHANGELOG](CHANGELOG.md)，或直接从 [v0.5 reset 文档](docs/skill-router-v0.5-ruthless-reset.md) 与 [v0.5.0 发布说明](docs/release-notes-v0.5.0.md) 开始。

## 接着读

1. [Skill Router v0.5 — Ruthless Reset](docs/skill-router-v0.5-ruthless-reset.md)
2. [为什么需要 Skill Router](docs/why-skill-router.md)
3. [它如何工作](docs/how-it-works.md)
4. [有无 Skill Router 的差异](docs/with-vs-without.md)
5. [SKILL.md](SKILL.md) — runtime skill 本体
6. [Partial Issues Plan](docs/skill-router-v0.5-partial-issues-plan.md)
7. [Partial Re-evaluation](docs/skill-router-v0.5-partial-reevaluation.md)
8. [Evaluator Spec](docs/skill-router-v0.5-evaluator-spec.md)
9. [Gold-Set Schema](docs/skill-router-v0.5-gold-set-schema.md)
10. [Gold-Set Sample](docs/skill-router-v0.5-gold-set-sample.md)
11. [Gold Set v1](docs/skill-router-v0.5-gold-set-v1.md)

## 协作与联系

- **Issues：** [github.com/Yuzc-001/skill-router/issues](https://github.com/Yuzc-001/skill-router/issues)
- **Email：** [zxyu24@outlook.com](mailto:zxyu24@outlook.com)

**Issues** 适合提交 bug、安装问题、文档缺口和功能讨论。
**邮箱** 适合处理授权、私下合作，或不适合在公开线程中开始的问题。

## 许可证

本项目采用 [MIT License](./LICENSE)。
