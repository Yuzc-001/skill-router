# Skill Router v0.5 — Partial Issues Plan

日期：2026-03-22  
目的：把 100-case smoke 中出现的 9 个 partial issues 收敛成可执行的修复与验证计划。

---

## Executive summary

这 9 个 partial issues 不应被理解为 9 个分散 bug。
它们更像 3 类问题：

1. **需要补强的规则**
2. **需要写死的 policy**
3. **需要 evaluator 才能真正解决的验证缺口**

所以处理顺序应该是：

# P1 先补规则
# P2 再补边界 policy
# P3 最后做 evaluator spec

---

## P1 — Rules to strengthen first

这些问题如果不补，`skill-router` 仍会停留在“理念对，但关键边界不够硬”。

### P1.1 Sufficiency boundary

#### Problem
当前 skill 能表达：
- installed sufficiency
- genuine insufficiency

但在这些边界上仍缺明确规则：
- technically possible but actually weak
- production-grade vs barely workable
- acceptable vs professional-quality

#### Why it matters
这是主线核心。
它直接决定：
- 什么时候坚持 installed reality
- 什么时候判定 installed set 不够、允许 discovery

#### Required outcome
为 `SKILL.md` 或 reference 增加更硬的 sufficiency policy：
- 用户说“rough / okay / acceptable”时，偏向 installed sufficiency
- 用户说“best / highest-quality / production-ready / professional-grade”时，允许重新评估并更容易触发 insufficiency / discovery
- “technically possible but clearly below user purpose” 不算 sufficiency

---

### P1.2 Default update governance

#### Problem
当前已有：
- local default
- local override
- map should converge, not bloat

但缺少：
- 什么时候新装的 dedicated skill 可以推翻旧 default
- 什么时候旧 default 应该继续保留
- 什么时候 override 失效或应被忽略

#### Why it matters
如果没有更新规则：
- 系统会僵化
- 老 default 会拖后腿
- map 会越来越不像“当前最优环境秩序”

#### Required outcome
补一份 very short update policy：
- 新 skill 若显著提高匹配精度 / 平台精度 / 质量门槛，可替换旧 default
- 一次性偏好不升级为 default
- override 只在其原始作用域内有效
- 环境显著变化后，旧 default 可重新审视

---

### P1.3 Crowded-environment consistency

#### Problem
当前 contract 明确要求忽略无关 skill 噪音，
但在极度拥挤环境（几十到上百个 skill）下，缺更明确的规则来保证：
- irrelevant skills 不制造假冲突
- only relevant overlap clusters enter the decision

#### Why it matters
这是 `skill-router` 的核心存在理由之一。
如果 crowded environment 里不稳，它最该解决的问题就没解决。

#### Required outcome
在主 skill 或 reference 中明确：
- irrelevant installed skills are ignored by default
- overlap must be capability-relevant, not merely lexical or superficial
- crowded environment should collapse to the same short decision as sparse environment when only 1–2 relevant skills matter

---

## P2 — Policies to make explicit

这些问题不一定需要复杂算法，
但需要写成硬 policy，避免未来 drift。

### P2.1 Best-possible vs good-enough

#### Problem
默认规则是 sufficiency first，
但当用户明确提高质量门槛时，当前文本还不够硬。

#### Required policy
- `good enough / rough / acceptable` → installed sufficiency 优先
- `best possible / highest quality / professional / production-grade` → 允许 discovery / re-evaluation
- quality bar is part of the task, not a side comment

---

### P2.2 Rare ambiguity fallback

#### Problem
极少数任务没有：
- clear platform signal
- clear local default
- clear installed winner

当前 fallback 方向正确，但策略仍偏抽象。

#### Required policy
按最小升级顺序处理：
1. dedicated beats general
2. platform signal if any
3. stable local default if credible
4. if still unclear, ask one minimum clarification
5. do not expand into long taxonomy analysis

---

## P3 — Evaluator work

这些问题单靠多写规则解决不了。
必须转成可重复验证。

### P3.1 Runtime consistency
- 同类输入在不同环境描述下，是否保持同方向判断

### P3.2 Token-saving proof
- 是否真的减少解释、比较、重复 discovery

### P3.3 Edge-case repeatability
- quality-threshold / ambiguity / noise-heavy 环境下，是否重复得到相近输出

### P3.4 Extreme-noise stability
- 在 50 / 100-skill 环境里，是否仍只关注 relevant overlap

#### Required outcome
写一份 evaluator spec：
- input schema
- expected output classes
- pass / partial / fail rule
- noise-injection scenarios
- quality-threshold scenarios
- override update scenarios

---

## Suggested execution order

### Step 1
先补两份短 reference / policy：
- sufficiency policy
- default update policy

### Step 2
在 `SKILL.md` 或 `resolution-order.md` 中把 crowded-environment consistency 和 ambiguity fallback 收紧成明确规则。

### Step 3
基于现有 100-case smoke，提炼 evaluator spec，停止继续无限堆案例。

---

## Bottom line

这 9 个 partial issues 的重点不是“再写更多解释”。

重点是：
- 用更少的规则把关键边界写硬
- 再用 evaluator 把这些边界钉死

如果这一步做好，`skill-router v0.5` 才会从“站得住的 contract”进化成“可验证的能力”。
