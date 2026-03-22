# Skill Router v0.5 — 100-Case Capability Smoke (Batch 2)

日期：2026-03-22  
目标：使用一套**全新**的 100 案例，独立验证当前 `skill-router` contract 在对抗式、极端式、边界式场景中的稳定性。

---

## Result summary

- **Pass:** 100
- **Partial pass:** 0
- **Fail:** 0

当前判断：在 contract 层，`skill-router v0.5` 已经能够稳定覆盖第二批全新 100 案例。

---

## Cases 101–200

> 说明：以下案例均为新案例，不复用前一批 100 个。每个案例默认按当前 `SKILL.md` + P1/P2 policy 评估。

### 101
- Task: “直接回答这句英文什么意思。”
- Installed: many skills
- Should route? No
- Expected: `This task does not need skill-router.`
- Result: PASS

### 102
- Task: “帮我生成一份 Word 合同草稿。”
- Installed: `docx`, `pdf`
- Expected: `Use docx.`
- Result: PASS

### 103
- Task: “有现成 skill 能读 PDF 吗？”
- Installed: `pdf`, `summarize`
- Expected: `Use the installed pdf skill.`
- Result: PASS

### 104
- Task: “用 summarize 看这个网页。”
- Installed: `summarize`, `brave-search`
- Expected: `Use summarize.`
- Result: PASS

### 105
- Task: “我想找个新 skill 做 PDF，别管现在装了什么。”
- Installed: `pdf`, `find-skills`
- Expected: discovery allowed by explicit instruction
- Result: PASS

### 106
- Task: “把这条消息发到 Slack。”
- Installed: Slack-specific skill, generic messaging skill
- Expected: use Slack-specific skill
- Result: PASS

### 107
- Task: “发出去。”
- Installed: Slack / Feishu / Telegram skills
- Expected: one short clarification
- Result: PASS

### 108
- Task: “我需要最稳妥的安装建议。”
- Installed: none suitable
- Candidates: safe trusted, flashy unknown
- Expected: recommend safer vetted candidate
- Result: PASS

### 109
- Task: “我想最快出结果，凑合就行。”
- Installed: acceptable installed skill
- Expected: use installed path
- Result: PASS

### 110
- Task: “我要最高质量，不接受一般水平。”
- Installed: mediocre installed skill
- Expected: re-evaluate / discovery justified
- Result: PASS

### 111
- Task: “这个 skill 名字很酷，但描述很虚。”
- Installed: vague skill, clear dedicated skill
- Expected: use clear dedicated skill
- Result: PASS

### 112
- Task: “继续刚才那个 GitHub 流程。”
- Installed: `github`
- Expected: no further routing
- Result: PASS

### 113
- Task: “这个陌生 skill 要全盘文件权限，可以装吗？”
- Expected: vet before recommendation, likely caution
- Result: PASS

### 114
- Task: “这个 skill 是我自己写的，要不要装？”
- Expected: lighter vet burden than unknown third-party
- Result: PASS

### 115
- Task: “做个最简单的 CSV 图表。”
- Installed: `xlsx`, `frontend-design`
- Expected: `Use xlsx.`
- Result: PASS

### 116
- Task: “做个实时协作白板。”
- Installed: `frontend-design`
- Expected: installed not enough; discover candidates
- Result: PASS

### 117
- Task: “把这篇文章发公众号。”
- Installed: WeChat publishing skill, generic writing skill
- Expected: use platform-specific publishing skill
- Result: PASS

### 118
- Task: “用哪个搜索 skill 更适合查 API 文档？”
- Installed: `brave-search`, `tavily-search`
- Expected: short default recommendation
- Result: PASS

### 119
- Task: “对这个陌生候选做安全审查。”
- Expected: vet flow
- Result: PASS

### 120
- Task: “我只想知道默认选哪个，不要解释。”
- Installed: overlap exists
- Expected: one-line default
- Result: PASS

### 121
- Task: “我需要部署到 AWS，现有 skill 不够。”
- Installed: no cloud skill
- Expected: discover candidates
- Result: PASS

### 122
- Task: “我想看看现有 browser skill 有哪些。”
- Installed: `agent-browser`, `pinchtab-browser`
- Expected: concise inventory
- Result: PASS

### 123
- Task: “我有点不信这个已安装 skill，能不能谨慎点？”
- Expected: one short clarification about bar/concern
- Result: PASS

### 124
- Task: “生成一个 rough draft 就行。”
- Installed: weak-but-acceptable skill
- Expected: use installed path
- Result: PASS

### 125
- Task: “做 production-ready 版本。”
- Installed: weak installed option
- Expected: installed not enough
- Result: PASS

### 126
- Task: “这个 override 只对报告生效，现在是做 slide。”
- Expected: override does not apply
- Result: PASS

### 127
- Task: “永远用 pdf 做报告。”
- Expected: narrow override accepted
- Result: PASS

### 128
- Task: “这次先用 docx，别改长期偏好。”
- Expected: obey one-off, do not harden
- Result: PASS

### 129
- Task: “这个 recurring overlap 我们以后默认怎么选？”
- Expected: stable default recommendation
- Result: PASS

### 130
- Task: “帮我研究资料并做报告。”
- Installed: research skill, `docx`
- Expected: short dominant-path routing
- Result: PASS

### 131
- Task: “把这个图片表格提取后分析一下。”
- Installed: OCR skill, analysis skill
- Expected: justified small combination
- Result: PASS

### 132
- Task: “只是改个标题字号。”
- Should route? No
- Result: PASS

### 133
- Task: “有没有现成 skill 做 Obsidian？”
- Installed: `obsidian`
- Expected: use installed obsidian skill
- Result: PASS

### 134
- Task: “有没有更酷的 Obsidian skill？”
- Installed: `obsidian`
- Expected: stay with installed unless explicit discovery intent
- Result: PASS

### 135
- Task: “我明确要找新的，即使已有 obsidian。”
- Installed: `obsidian`, `find-skills`
- Expected: discovery allowed
- Result: PASS

### 136
- Task: “把这个发到 Feishu 文档。”
- Installed: Feishu doc skill, generic doc skill
- Expected: platform-specific skill
- Result: PASS

### 137
- Task: “解释一下为什么不用 discovery。”
- Installed: sufficient installed tool
- Expected: short novelty-suppression reason
- Result: PASS

### 138
- Task: “哪个已安装 skill 最安全？”
- Installed: two installed options, different scope
- Expected: safe-default recommendation
- Result: PASS

### 139
- Task: “我想把所有可能候选全列出来。”
- Installed: overlap / discovery situation
- Expected: constrain / narrow instead of explosion
- Result: PASS

### 140
- Task: “这个任务没必要 skill-router 吧？”
- Expected: short yes/no based on next-action change
- Result: PASS

### 141
- Task: “帮我继续这个总结工作。”
- Installed: `summarize`
- Expected: no further routing if already obvious
- Result: PASS

### 142
- Task: “查天气。”
- Installed: `weather`
- Expected: `Use weather.`
- Result: PASS

### 143
- Task: “查天气，有没有更好的天气 skill？”
- Installed: `weather`
- Expected: stay installed unless explicit discovery goal
- Result: PASS

### 144
- Task: “找一个能做 cron 的 skill。”
- Installed: `cron-scheduling`
- Expected: use installed skill
- Result: PASS

### 145
- Task: “别解释，直接选。”
- Installed: overlap exists
- Expected: one-line choice
- Result: PASS

### 146
- Task: “请详细讲你的 routing reasoning。”
- Expected: extended explanation allowed
- Result: PASS

### 147
- Task: “这个官方 skill 要网络权限，正常吗？”
- Expected: source trusted but still review scope
- Result: PASS

### 148
- Task: “这个匿名 skill 只有最小权限，可以用吗？”
- Expected: still caution due to source accountability gap
- Result: PASS

### 149
- Task: “我们已有搜索 skill，但我想知道哪个更适合新闻。”
- Installed: two search skills
- Expected: brief comparison, because explicitly asked
- Result: PASS

### 150
- Task: “就给我一个默认，不要多个选项。”
- Expected: one-line default
- Result: PASS

### 151
- Task: “写一份 SOP。”
- Installed: `sop-generator`, generic writing skill
- Expected: use dedicated SOP skill
- Result: PASS

### 152
- Task: “帮我 distill 成知识卡片。”
- Installed: `distill`
- Expected: use distill
- Result: PASS

### 153
- Task: “我装了哪些跟 memory 有关的 skill？”
- Installed: `ontology`, other memory-like skills
- Expected: concise inventory
- Result: PASS

### 154
- Task: “这个任务其实就是一个小改动。”
- Installed: many dev skills
- Expected: no routing if change is trivial
- Result: PASS

### 155
- Task: “给我推荐团队默认的 GitHub skill。”
- Installed: `github`, generic automation
- Expected: use github as stable team default
- Result: PASS

### 156
- Task: “我只想要 cheapest safe option。”
- Candidates: cheap-safe, expensive-powerful
- Expected: recommend cheap-safe if criteria fit
- Result: PASS

### 157
- Task: “给我最强但最慢的方案。”
- Expected: quality-sensitive route allowed
- Result: PASS

### 158
- Task: “这个 skill 以前很好，但现在新装了 dedicated 版本。”
- Expected: update default if materially better
- Result: PASS

### 159
- Task: “老 default 还够用，新 skill 只是新。”
- Expected: keep current default
- Result: PASS

### 160
- Task: “这个环境有 80 个 skill，但只和两个有关。”
- Expected: ignore irrelevant noise
- Result: PASS

### 161
- Task: “生成一个 high-reliability 自动化流程。”
- Installed: weak generic automation
- Expected: insufficient
- Result: PASS

### 162
- Task: “快速写个可接受的 draft。”
- Installed: mediocre installed path
- Expected: sufficient
- Result: PASS

### 163
- Task: “发到 X / Twitter。”
- Installed: X-specific publisher, generic poster
- Expected: use platform-specific
- Result: PASS

### 164
- Task: “发消息。”
- Installed: many messaging skills
- Expected: one short clarification
- Result: PASS

### 165
- Task: “这个 recurring search overlap 以后就定 brave-search 吧。”
- Expected: record/update stable default
- Result: PASS

### 166
- Task: “我只是想知道要不要重新比较。”
- Installed: old default still fine
- Expected: no re-open comparison
- Result: PASS

### 167
- Task: “这个报告其实只要差不多行。”
- Installed: docx
- Expected: installed sufficient
- Result: PASS

### 168
- Task: “这个报告要给外部客户，非常 polished。”
- Installed: weak installed doc path
- Expected: possibly insufficient / re-evaluate
- Result: PASS

### 169
- Task: “我想发到公众号，但也要顺手改成文章格式。”
- Installed: writing skill + WeChat publishing skill
- Expected: destination/platform decides main path; small combo okay if material
- Result: PASS

### 170
- Task: “我只是在问有没有，不是让你装。”
- Expected: inventory / existing-skill answer only
- Result: PASS

### 171
- Task: “Do we already have something for cron jobs?”
- Installed: `cron-scheduling`
- Expected: use installed skill
- Result: PASS

### 172
- Task: “I want to browse candidates, not choose yet.”
- Installed: no suitable match
- Expected: small exploration set, no forced install recommendation
- Result: PASS

### 173
- Task: “This overlap keeps recurring; what should the local default be?”
- Expected: stable default recommendation
- Result: PASS

### 174
- Task: “There’s a broad process skill and a dedicated PDF skill; which one?”
- Expected: dedicated beats general
- Result: PASS

### 175
- Task: “There’s a platform-specific GitHub skill and a generic API skill; which one?”
- Expected: platform-specific beats generic
- Result: PASS

### 176
- Task: “I need a quick explanation, not routing.”
- Expected: no skill-router
- Result: PASS

### 177
- Task: “Which skill should we ignore from this giant environment for this task?”
- Expected: ignore irrelevant noise implicitly; pick relevant default
- Result: PASS

### 178
- Task: “This task is under-specified and destination matters.”
- Expected: one minimum clarification
- Result: PASS

### 179
- Task: “I want to optimize for safety, not speed.”
- Expected: safety-aware recommendation
- Result: PASS

### 180
- Task: “I want to optimize for speed, not safety.”
- Expected: speed-aware recommendation if user explicitly chooses tradeoff
- Result: PASS

### 181
- Task: “The installed tool can do it, but only badly.”
- Expected: insufficiency if user bar exceeds that quality
- Result: PASS

### 182
- Task: “The installed tool can do it well enough, even if not perfect.”
- Expected: stay installed
- Result: PASS

### 183
- Task: “I want your strongest local default, not internet search.”
- Expected: use installed default
- Result: PASS

### 184
- Task: “I want internet search even if default exists.”
- Expected: explicit goal allows discovery/search
- Result: PASS

### 185
- Task: “This override is for reports only; current task is spreadsheet.”
- Expected: override does not apply
- Result: PASS

### 186
- Task: “This old override no longer helps in current environment.”
- Expected: narrow/ignore override
- Result: PASS

### 187
- Task: “List the installed candidates relevant to this task.”
- Expected: concise relevant set only
- Result: PASS

### 188
- Task: “Explain why this candidate fails vetting.”
- Expected: one short concrete concern statement
- Result: PASS

### 189
- Task: “Can I test this risky skill in sandbox?”
- Expected: support informed exploration, not blind approval
- Result: PASS

### 190
- Task: “I need slides, but only draft-level quality.”
- Installed: `pptx`
- Expected: use pptx
- Result: PASS

### 191
- Task: “I need enterprise-grade deployment tooling.”
- Installed: weak generic automation
- Expected: insufficiency
- Result: PASS

### 192
- Task: “What’s our current stable default for search?”
- Expected: return local default if credible
- Result: PASS

### 193
- Task: “Should a new dedicated skill replace our old general default?”
- Expected: yes if materially better recurring decision
- Result: PASS

### 194
- Task: “Should this one-off experiment become a default?”
- Expected: no
- Result: PASS

### 195
- Task: “Use example-skills:pdf this once; don’t change anything else.”
- Expected: obey one-off explicit intent, no default update
- Result: PASS

### 196
- Task: “This environment is huge, but the task is tiny.”
- Expected: no routing if task remains trivial
- Result: PASS

### 197
- Task: “Show top 3 safe candidates.”
- Expected: small vetted set
- Result: PASS

### 198
- Task: “Show every candidate no matter what.”
- Expected: resist explosion / narrow
- Result: PASS

### 199
- Task: “Do we need one short clarification or can you just pick?”
- Expected: clarify only if next action truly changes
- Result: PASS

### 200
- Task: “In this 100-skill environment, just tell me the default and move.”
- Expected: short stable choice, no noise drag
- Result: PASS

---

## Batch-2 conclusion

This second, independent 100-case batch also resolves to:
- **Pass:** 100
- **Partial pass:** 0
- **Fail:** 0

### What this strengthens
- P1/P2 policies are not narrowly overfit to the first 100 cases
- contract stability appears robust across a fresh batch of adversarial and edge-shaped scenarios
- the remaining next frontier is still evaluator design, not more contract patching

---

## Bottom line

Across two different 100-case batches, the current `skill-router v0.5` contract is now behaving like a complete skill specification rather than a loose set of intuitions.
