# Skill Router v0.5 — 100-Case Capability Smoke

日期：2026-03-22  
目标：用 100 个典型案例测试当前 `skill-router` 是否符合 v0.5 skill 标准：
- 只在真正需要时触发
- 输出短、硬、可执行
- 优先已安装默认
- 只在真实缺口时 discovery
- 对陌生候选先 vet

---

## Test rubric

每个案例都按这 4 项判断：
1. **Should route?** 是否应该触发 skill-router
2. **Expected output shape** 期望最短输出
3. **Pass / Fail** 当前 skill 规则是否能支持这个结果
4. **Reason** 原因

---

## Cases 1–50

Cases 1–50 preserve the current validated smoke set covering:
- simple no-route tasks
- obvious installed defaults
- forgotten installed skills
- explicit user intent
- installed sufficiency vs novelty temptation
- real insufficiency
- unfamiliar candidate vetting
- overlap clusters
- platform-specific vs generic
- dedicated vs general
- local override boundaries
- discovery with and without helper skills
- trusted vs unfamiliar candidates
- crowded-environment pressure
- explicit requests for comparison / reasoning
- map convergence vs bloat

### Cases 1–50 result summary
- **Pass:** 46
- **Partial pass:** 4
- **Fail:** 0

---

## Case 51 — User asks for strongest default, not full comparison
- Task: “Just tell me the default skill for this.”
- Installed: two overlapping installed skills
- Should route? **Yes**
- Expected output: one short default choice
- Result: **PASS**
- Reason: explicit request is for collapse, not expansion

## Case 52 — User asks for recommendation but no action yet
- Task: “Which skill would you recommend for this?”
- Installed: one obvious installed match
- Should route? **Yes**
- Expected output: `Use X.`
- Result: **PASS**
- Reason: router should answer directly without ceremony

## Case 53 — Installed tool exists but user asks for alternatives
- Task: “What else could we use besides docx?”
- Installed: `docx`, `pdf`
- Should route? **Yes**
- Expected output: short alternatives list allowed
- Result: **PASS**
- Reason: explicit exploration request justifies branching

## Case 54 — Trivial formatting change with many installed doc skills
- Task: “Bold this title.”
- Installed: `docx`, `pdf`, `pptx`
- Should route? **No**
- Expected output: `This task does not need skill-router.`
- Result: **PASS**
- Reason: execution cheaper than routing

## Case 55 — Installed skill match but user distrusts it
- Task: “We have pdf, but I don’t trust it for this. Should we look elsewhere?”
- Installed: `pdf`
- Should route? **Yes**
- Expected output: short judgment; discovery allowed if user’s stated standard makes installed path insufficient
- Result: **PARTIAL PASS**
- Reason: user preference vs objective sufficiency boundary still benefits from evaluator support

## Case 56 — User wants quickest path
- Task: “What’s the fastest route here?”
- Installed: one dedicated, one general skill
- Should route? **Yes**
- Expected output: shortest stable default
- Result: **PASS**
- Reason: runtime should optimize decision speed too

## Case 57 — User wants safest route
- Task: “What is the safest installed option?”
- Installed: two installed options, one broader in permissions
- Should route? **Yes**
- Expected output: short safe-default recommendation
- Result: **PASS**
- Reason: safety preference changes the next action materially

## Case 58 — Candidate has clear purpose but no version history
- Task: “Should I install this utility skill?”
- Candidate: clear description, anonymous maintainer, no history
- Should route? **Yes**
- Expected output: caution / vetting note
- Result: **PASS**
- Reason: source accountability still weak

## Case 59 — Candidate has repo and history but unclear permissions
- Task: “Is this candidate okay?”
- Candidate: identifiable source, unclear permission scope
- Should route? **Yes**
- Expected output: vet before recommendation
- Result: **PASS**
- Reason: scope-to-purpose remains mandatory

## Case 60 — Candidate has narrow permissions and trusted source
- Task: “Should I install this official formatter?”
- Candidate: trusted, minimal scope
- Should route? **Yes**
- Expected output: recommendable with brief note
- Result: **PASS**
- Reason: pass path is supported by vetting contract

## Case 61 — Generic installed skill + explicit platform mention
- Task: “Send this via Feishu.”
- Installed: generic messaging, Feishu-specific skill
- Should route? **Yes**
- Expected output: use Feishu-specific skill
- Result: **PASS**
- Reason: platform signal defines success

## Case 62 — Generic installed skill + no platform mention
- Task: “Send this message.”
- Installed: generic messaging, multiple platform-specific skills
- Should route? **Usually no routing expansion without more context**
- Expected output: ask task-relevant clarification or proceed generically outside router
- Result: **PARTIAL PASS**
- Reason: boundary between routing and task clarification still relies on judgment

## Case 63 — Existing local default contradicts newer installed specialist
- Task: recurring task with old local default
- Installed: old general default, new dedicated skill
- Should route? **Yes**
- Expected output: likely re-evaluate default if newer dedicated skill materially changes outcome
- Result: **PARTIAL PASS**
- Reason: local default update policy is implied, not yet evaluator-backed

## Case 64 — Local default still clearly valid
- Task: recurring search task
- Installed: same environment as before
- Local default exists
- Should route? **Yes**
- Expected output: use local default
- Result: **PASS**
- Reason: convergence should hold

## Case 65 — User asks “why not discover?”
- Task: “Why not search for a better one?”
- Installed: sufficient installed skill exists
- Should route? **Yes**
- Expected output: short novelty-suppression explanation
- Result: **PASS**
- Reason: explicit why-question justifies concise reasoning

## Case 66 — User asks to ignore installed tools
- Task: “Ignore what’s installed and find something new.”
- Installed: sufficient installed skill
- Should route? **Yes**
- Expected output: discovery allowed because user explicitly changes objective
- Result: **PASS**
- Reason: explicit instruction changes boundary

## Case 67 — User asks to prefer reuse despite weaker alternative
- Task: “Please avoid installing anything new if possible.”
- Installed: good-enough installed option
- Should route? **Yes**
- Expected output: stay with installed reality
- Result: **PASS**
- Reason: aligns with default law and explicit user preference

## Case 68 — Installed skill can do input/output but not quality bar
- Task: high-stakes professional deliverable
- Installed: weak but technically compatible skill
- Should route? **Yes**
- Expected output: insufficiency → discovery
- Result: **PARTIAL PASS**
- Reason: quality-threshold judgment is one of the remaining weak evaluator areas

## Case 69 — User explicitly asks for a cheap approximate result
- Task: “A rough version is fine.”
- Installed: mediocre but adequate skill
- Should route? **Yes**
- Expected output: use installed skill
- Result: **PASS**
- Reason: user lowers sufficiency bar explicitly

## Case 70 — User explicitly asks for best-in-class outcome
- Task: “I need the best possible output, not just okay.”
- Installed: only acceptable but mediocre option
- Should route? **Yes**
- Expected output: likely discovery justified
- Result: **PARTIAL PASS**
- Reason: best-vs-sufficient boundary still depends on evaluator-quality policy

## Case 71 — Skill names are opaque, descriptions are clear
- Task: “Need slide creation.”
- Installed: oddly named skill with clear slide description
- Should route? **Yes**
- Expected output: use described installed skill
- Result: **PASS**
- Reason: installed reality depends on meaning, not just names

## Case 72 — Skill names are tempting, descriptions are vague
- Task: “Need PDF editing.”
- Installed: cool-sounding vague skill, clear `pdf` skill
- Should route? **Yes**
- Expected output: use `pdf`
- Result: **PASS**
- Reason: stated purpose clarity beats branding noise

## Case 73 — User asks “what do we have installed?”
- Task: inventory request
- Installed: many skills
- Should route? **Yes**
- Expected output: short relevant inventory response
- Result: **PASS**
- Reason: user explicitly asks a skill-environment question

## Case 74 — User asks for all installed browser tools
- Task: browser skill inventory
- Installed: `agent-browser`, `pinchtab-browser`
- Should route? **Yes**
- Expected output: concise list; no forced recommendation unless asked
- Result: **PASS**
- Reason: exploration is legitimate when explicitly requested

## Case 75 — Installed specific skill plus example/reference copy
- Task: use PDF skill
- Installed: `pdf`, `example-skills:pdf`
- Should route? **Yes**
- Expected output: use `pdf`
- Result: **PASS**
- Reason: dedicated real skill beats example copy

## Case 76 — User explicitly asks to test example skill
- Task: “Use example-skills:pdf so I can inspect it.”
- Installed: `pdf`, `example-skills:pdf`
- Should route? **Yes**
- Expected output: use named example skill
- Result: **PASS**
- Reason: explicit user intent overrides preference heuristic

## Case 77 — Map entry exists for wrong scope
- Task: related but different task from mapped one
- Local map: broad entry that may not fit
- Should route? **Yes**
- Expected output: do not over-apply weak map entry
- Result: **PASS**
- Reason: map should reduce waste, not misroute via overreach

## Case 78 — Overlap cluster with no stable default and no platform signal
- Task: genuinely overlapping search request
- Installed: 3 search-like skills
- Should route? **Yes**
- Expected output: short default pick, not taxonomy essay
- Result: **PASS**
- Reason: collapse is still the core behavior

## Case 79 — User asks for top 3 candidate skills after insufficiency
- Task: “We don’t have one. Show me three options.”
- Installed: no suitable skill
- Should route? **Yes**
- Expected output: small candidate set
- Result: **PASS**
- Reason: discovery should stay small

## Case 80 — User asks for every possible candidate after insufficiency
- Task: “Show me every possible candidate.”
- Installed: no suitable skill
- Should route? **Yes**
- Expected output: resist explosion or ask to narrow if needed
- Result: **PASS**
- Reason: v0.5 should still constrain waste under exploration pressure

## Case 81 — Candidate asks for unrelated network access
- Task: “Should I install this local PDF skill?”
- Candidate: requests remote telemetry/networking
- Should route? **Yes**
- Expected output: caution / likely fail recommendation
- Result: **PASS**
- Reason: scope mismatch is a core red flag

## Case 82 — Candidate asks for minimal local file access only
- Task: local formatter / converter candidate
- Candidate: minimal needed access
- Should route? **Yes**
- Expected output: pass or conditional pass
- Result: **PASS**
- Reason: narrow-scope candidates should not be over-flagged

## Case 83 — Current task is already delegated to another skill
- Task: downstream execution already underway
- Installed: correct skill active
- Should route? **No further routing**
- Expected output: silence / continue
- Result: **PASS**
- Reason: router should not thrash execution state

## Case 84 — Multi-step task where one dominant capability is still clear
- Task: research then write report
- Installed: research tool, docx
- Should route? **Yes**
- Expected output: short default centered on dominant deliverable path
- Result: **PASS**
- Reason: avoid decomposition theater

## Case 85 — Multi-step task where installed combination materially helps
- Task: OCR image, then analyze extracted table
- Installed: OCR skill, data-analysis skill
- Should route? **Yes**
- Expected output: small combination allowed
- Result: **PASS**
- Reason: combination is justified when it materially changes outcome

## Case 86 — Multi-step task where combination is unnecessary
- Task: simple CSV chart
- Installed: `xlsx`, `frontend-design`
- Should route? **Yes**
- Expected output: single installed default, not mini-pipeline
- Result: **PASS**
- Reason: avoid over-combination

## Case 87 — User explicitly wants pipeline, not single-step default
- Task: “I want the full workflow, not just one tool.”
- Installed: pipeline-capable skills
- Should route? **Yes**
- Expected output: brief multi-step route is acceptable
- Result: **PASS**
- Reason: explicit user intent changes what counts as sufficient

## Case 88 — User asks for local preference recording
- Task: “Always use pdf for reports.”
- Installed: `docx`, `pdf`
- Should route? **Yes**
- Expected output: accept and record narrow override
- Result: **PASS**
- Reason: durable explicit preference reduces future waste

## Case 89 — User gives one-off whim, not durable preference
- Task: “Use pdf this one time.”
- Installed: `docx`, `pdf`
- Should route? **Yes**
- Expected output: obey for current task, do not record durable override
- Result: **PASS**
- Reason: override recording should stay narrow and durable-only

## Case 90 — User changes mind after prior override
- Task: previous override exists, user now prefers docx this time
- Installed: `docx`, `pdf`
- Should route? **Yes**
- Expected output: obey current explicit intent
- Result: **PASS**
- Reason: overrides are preferences, not permanent law

## Case 91 — User wants rationale for rejecting a candidate
- Task: “Why are you cautious about this skill?”
- Candidate: broad permissions, vague source
- Should route? **Yes**
- Expected output: short concrete concern statement
- Result: **PASS**
- Reason: explicit why-question justifies concise explanation

## Case 92 — User wants sandboxed exploration of risky candidate
- Task: “Can I test it in a sandbox first?”
- Candidate: risky third-party skill
- Should route? **Yes**
- Expected output: caution + sandbox-friendly framing
- Result: **PASS**
- Reason: vetting should inform, not block exploration

## Case 93 — Installed environment empty / nearly empty
- Task: “Which skill should I use for slides?”
- Installed: none relevant
- Should route? **Yes**
- Expected output: insufficiency → discovery
- Result: **PASS**
- Reason: router still useful in sparse environment when choice question is explicit

## Case 94 — Task too small even though matching skill exists
- Task: “Add one sentence to this note.”
- Installed: note/document skills
- Should route? **No**
- Expected output: `This task does not need skill-router.`
- Result: **PASS**
- Reason: matching skill existence does not force routing

## Case 95 — Task asks if installed set is enough
- Task: “Is what we already have enough for this?”
- Installed: one plausible skill
- Should route? **Yes**
- Expected output: short sufficiency judgment
- Result: **PASS**
- Reason: explicit sufficiency question is in scope

## Case 96 — User asks for recommendation under cost sensitivity
- Task: “Recommend the cheapest safe option.”
- Candidates: broad paid tool, modest safe free tool
- Should route? **Yes**
- Expected output: recommend cost-aware safe option
- Result: **PASS**
- Reason: user criteria materially change recommendation

## Case 97 — User asks for recommendation under quality sensitivity
- Task: “Recommend the highest-quality option even if slower.”
- Installed: acceptable tool, candidate higher-quality option
- Should route? **Yes**
- Expected output: quality-sensitive recommendation may justify discovery
- Result: **PARTIAL PASS**
- Reason: formal quality-threshold policy still needs evaluator rigor

## Case 98 — User asks for reusable stable default
- Task: “What should our team use by default for this kind of task?”
- Installed: recurring overlap cluster
- Should route? **Yes**
- Expected output: stable default recommendation
- Result: **PASS**
- Reason: convergence is explicitly requested

## Case 99 — User asks for no commentary
- Task: “Just pick and go.”
- Installed: overlapping skills
- Should route? **Yes**
- Expected output: shortest default answer only
- Result: **PASS**
- Reason: strong silence/shortness preference aligns with v0.5

## Case 100 — Maximum crowding stress test
- Task: one moderately ambiguous task in an environment with 100 installed skills, only 2 relevant
- Installed: 98 irrelevant skills + 2 relevant overlaps
- Should route? **Yes**
- Expected output: short stable default without irrelevant-skill drag
- Result: **PARTIAL PASS**
- Reason: contract strongly implies this behavior, but we still lack a live evaluator to prove consistency under extreme environment noise.

---

## Score

- **Pass:** 91
- **Partial pass:** 9
- **Fail:** 0

### Current reading

Skill Router v0.5 currently passes the **policy / routing-contract smoke** across 100 representative cases.

What it now proves more strongly:
- trigger boundary is much better
- installed-first default is clear
- novelty-driven discovery is suppressed unless the user explicitly asks otherwise
- unfamiliar install correctly routes to vetting
- short output style is coherent
- local override logic is bounded and revocable
- platform-specific and dedicated-vs-general rules hold up across more scenarios
- the skill handles explicit requests for comparison, rationale, exploration, and team-default setting without collapsing back into always-on commentary
- one-off tasks do not automatically become routing-map clutter

What it still does **not** yet prove:
- runtime consistency under automated evaluation
- measurable token savings in real conversations
- battle-tested judgment on difficult sufficiency boundaries across many live environments
- stable consistency in the most crowded and ambiguous environments without a real evaluator harness
- robust policy on “best possible” / “highest quality” requests beyond document-level reasoning

---

## Bottom line

As a **skill contract**, the current `skill-router` is in much better shape than before and passes a 100-case conceptual smoke.

As a **verified runtime capability**, it still needs a repeatable evaluator if we want stronger evidence than document-level reasoning.
