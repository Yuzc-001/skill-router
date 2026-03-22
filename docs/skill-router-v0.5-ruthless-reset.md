# Skill Router v0.5 — Ruthless Reset

日期：2026-03-21  
状态：重塑草案 / 新中轴

---

## 先把旧问题说死

如果 `skill-router` 只是：
- 多一层 skill 选择说明
- 多一层 taxonomy
- 多一层“该用哪个 skill”的分析
- 多一层听起来很对的 meta 话术

那它就是：

# 无效中间层

它会消耗：
- token
- 注意力
- 决策回合
- 本该直接执行的任务节奏

如果它不能明显减少这些浪费，它就不该存在。

---

## v0.5 的新北极星

`skill-router v0.5` 不再以“帮助选择 skill”为目标。

它的新目标是：

# 降低 skill-heavy agent 环境中的无谓决策成本

更直接一点：

# 降低 skill 环境熵

它要解决的不是“能不能讲清楚怎么选 skill”，
而是：

- 为什么明明装了 skill 还在反复 discovery
- 为什么多个 skill 长期重叠却没有稳定默认
- 为什么 skill 越多，agent 越容易在选择上浪费判断力
- 为什么本来该做事，却被拖进工具比较

只有当它真的减少这些浪费时，它才有存在理由。

---

## v0.5 的四条铁律

### 1. 不改变默认决策，就不允许发言
如果 `skill-router` 的输出不会改变接下来实际调用哪个 skill，
它就不该出现。

### 2. 不减少重复浪费，就不算能力
不能减少以下任一类浪费的逻辑，不配进 v0.5：
- 重复 discovery
- 重复安装
- 重复比较
- 重复解释
- 重复犹豫

### 3. 只处理高价值冲突
v0.5 只保留真正高价值的选择冲突：
- installed vs discover
- dedicated vs general
- platform-specific vs generic
- recurring overlap clusters
- unfamiliar install vs safe reuse

除此之外，不展开，不分类表演。

### 4. 输出必须极短、极硬、极可执行
理想输出形态应该接近：
- 直接用 X
- 现有不够，去发现 Y 类 skill
- 候选陌生，先 vet
- 这个任务不需要 skill-router

而不是长篇 routing 分析。

---

## 旧体系哪些东西要砍

以下内容不再作为产品中心：

### 1. taxonomy 扩张
继续细分能力分类，除非它真的改变默认决策，否则一律视为噪音。

### 2. routing explanation theater
如果输出主要价值是“解释自己为什么存在”，那就是失败。

### 3. 全任务覆盖冲动
`skill-router` 不是所有任务前都该出现的总入口。

### 4. 哲学先于机制
理念可以保留，但 v0.5 只接受能改变默认行为的机制。

---

## v0.5 应该重塑成什么

不是：
- routing memo
- taxonomy guide
- skill selection explainer

而是：

# 一个极低存在感的 skill default resolver

更进一步，如果做强：

# 一个降低 skill 环境熵的 runtime layer

它的职责不是“多说”，而是：
- 让默认更稳定
- 让复用更强
- 让 discovery 更少但更准
- 让冲突集有收敛结果
- 让 agent 少把 token 烧在工具犹豫上

---

## v0.5 只保留的核心问题

### Problem A — 这个任务到底需不需要 routing？
如果不需要，立刻消失。

### Problem B — 当前已安装环境里，默认该走哪条最短 skill path？
不是最佳宇宙答案，而是当前环境最稳默认。

### Problem C — 现有 skill 是否真的不够？
只有真的不够，才允许 discovery。

### Problem D — 新候选是否值得进入环境？
陌生来源先 vet，再决定是否纳入默认秩序。

这四个问题之外的内容，默认不进主线。

---

## v0.5 的新结构

### Layer 1 — Need-to-route gate
先判断 routing 是否必要。
不必要就彻底静默。

### Layer 2 — Installed default resolver
在当前已安装环境中给出最短默认路径。

### Layer 3 — Insufficiency detector
只在现有能力真的不够时打开 discovery。

### Layer 4 — Candidate admission gate
候选 skill 必须先过 vet / risk / fit 判断，才能进入默认环境。

这四层比旧体系更小，但更硬。

---

## 判断 v0.5 是否成立的标准

`skill-router v0.5` 只有在下面这些真的改善时才算成立：

- agent 更少重复问“该用哪个 skill”
- 已安装 skill 的复用率更高
- discovery 次数更少但更准
- 重复安装减少
- 冗长 routing 解释显著减少
- 多 skill 环境里的默认判断更稳定

如果这些没有改善，v0.5 就不算成功。

---

## Bottom line

v0.5 不是升级版说明书。

v0.5 必须是一次删掉无效中间层、只保留真实 runtime value 的重塑。

如果做不到降低决策成本，
那 `skill-router` 就应该被砍掉，
而不是被继续包装。
