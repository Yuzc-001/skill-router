# Micro Routing Examples

Quick reference for common routing patterns. Each example shows the task, the installed environment, and the correct routing decision.

---

## Pattern 1: Direct Match — Route Silently

**Task:** "Create a Word document summarizing these meeting notes."

**Installed:** `docx`, `pdf`, `xlsx`, `pptx`

**Route:** `docx` — direct match for Word document creation. Say nothing about routing.

---

## Pattern 2: Platform Signal Overrides Generic Match

**Task:** "帮我把这篇文章发到公众号。"

**Installed:** `baoyu-post-to-wechat`, `baoyu-post-to-weibo`, `baoyu-post-to-x`

**Route:** `baoyu-post-to-wechat` — "公众号" is an unambiguous platform signal. Route to the platform-specific skill without asking which platform.

---

## Pattern 3: Two Same-Capability Skills — Apply Tiebreaker

**Task:** "把这段文字翻译成英文。"

**Installed:** `deepl`, `baoyu-translate`

**Route:** Both handle translation. Apply tiebreaker: `deepl` for format-preserving document translation; `baoyu-translate` for article/content translation. This task is a short text snippet — either works. Pick `baoyu-translate` (more recently used context, or either if unknown). Do not present a comparison.

---

## Pattern 4: example-skills Conflict — Always Prefer Non-Example

**Task:** "Read this PDF and extract the key points."

**Installed:** `pdf`, `example-skills:pdf`

**Route:** `pdf` — the non-example version always takes priority. The `example-skills:` prefix marks a reference copy, not a preferred installation.

---

## Pattern 5: No Skill Needed

**Task:** "What's the capital of France?"

**Installed:** `docx`, `pdf`, `xlsx`, `pptx`, `skill-router`

**Route:** No skill. Answer directly. This task does not require any skill.

---

## Pattern 6: User Names a Skill

**Task:** "Use the pptx skill to create slides about our Q3 results."

**Installed:** `pptx`, `baoyu-slide-deck`

**Route:** `pptx` — user explicitly named it. Do not second-guess or suggest `baoyu-slide-deck` as an alternative.

---

## Pattern 7: Visual Content vs Image Generation — Different Categories

**Task:** "做一套小红书图文，介绍我们的产品。"

**Installed:** `gemini-image`, `baoyu-xhs-images`, `baoyu-image-gen`

**Route:** `baoyu-xhs-images` — dominant capability is Visual Content Production (structured image series), not Image Generation (single AI image). `gemini-image` and `baoyu-image-gen` produce individual images; `baoyu-xhs-images` produces a composed XHS-format series.

---

## Pattern 8: ccg:* Pipeline — Single Step vs Full Pipeline

**Task:** "帮我做一个 code review。"

**Installed:** `ccg:review`, `ccg:workflow`, `ccg:commit`

**Route:** `ccg:review` — the user asked for a single step (review), not the full pipeline. Do not start `ccg:workflow`. Note briefly: "Using `ccg:review` for the review."

---

## Pattern 9: ccg:* Pipeline — Full Development Task

**Task:** "帮我开发一个新功能：用户登录模块。"

**Installed:** `ccg:feat`, `ccg:workflow`, `ccg:plan`

**Route:** `ccg:feat` — this is a full feature development task, not a single step. `ccg:feat` covers the research → plan → execute pipeline. Note briefly: "Using `ccg:feat` for this — it will go through planning and implementation."

---

## Pattern 10: Genuine Gap — Delegate to find-skills

**Task:** "我需要一个能连接 Notion 的 skill。"

**Installed:** `find-skills`, `docx`, `pdf`, `baoyu-post-to-wechat`

**Route:** No installed skill handles Notion integration. Delegate discovery: "None of your installed skills handle Notion. Delegating to `find-skills` to search for candidates."

Then invoke `find-skills`.

---

## Pattern 11: Genuine Gap — Manual Discovery (no find-skills)

**Task:** "Deploy this application to AWS with auto-scaling."

**Installed:** `docx`, `pdf`, `xlsx`, `pptx`, `frontend-design`

**Route:** No installed skill handles cloud deployment. State the gap: "None of your installed skills handle AWS deployment. Let me search for candidates." Then proceed to manual discovery via web search.

---

## Pattern 12: OCR Task

**Task:** "这张图片里的表格数据帮我提取出来。"

**Installed:** `ppocrv5`, `data-analysis`, `xlsx`

**Route:** `ppocrv5` — dominant capability is OCR & Text Extraction. `data-analysis` and `xlsx` are for analysis, not extraction. Use `ppocrv5` first, then optionally `xlsx` for the extracted data.

---

## Pattern 13: Data Analysis — data-analysis vs xlsx

**Task:** "分析这个 CSV 文件，告诉我有什么规律。"

**Installed:** `data-analysis`, `xlsx`

**Route:** `data-analysis` — preferred over `xlsx` for analysis tasks. It has token-safe exploration for large files and handles mixed formats. `xlsx` is for spreadsheet creation and editing; `data-analysis` is for insights.

---

## Pattern 14: Multi-Step Composition

**Task:** "抓取这个 URL 的文章，整理成公众号格式发出去。"

**Installed:** `baoyu-url-to-markdown`, `wechat-article`, `baoyu-post-to-wechat`

**Route:** Three-step pipeline: `baoyu-url-to-markdown` (fetch + convert) → `wechat-article` (rewrite for WeChat format) → `baoyu-post-to-wechat` (publish). Speak briefly: "Fetching with `baoyu-url-to-markdown`, rewriting with `wechat-article`, then publishing with `baoyu-post-to-wechat`."

---

## Pattern 15: Enough-Is-Enough — 3-Question Test

**Task:** "Create a professional-looking slide deck with custom animations."

**Installed:** `pptx`

**Route test:**
1. Can `pptx` accept the task's input? Yes.
2. Can `pptx` produce slide deck output? Yes.
3. Is quality sufficient for stated purpose (professional deck)? Yes — animation support is limited, but the user asked for "professional-looking", not "fully animated."

All three yes → `pptx` is enough. Do not search for a specialized animation tool.

---

## Pattern 16: Enough-Is-Enough — Fails the Test

**Task:** "Build a real-time collaborative whiteboard with live cursors."

**Installed:** `frontend-design`

**Route test:**
1. Can `frontend-design` accept the input? Yes.
2. Can it produce a web interface? Yes.
3. Is quality sufficient? No — real-time collaboration and live cursors require WebSocket infrastructure that a static frontend skill cannot provide.

Fails question 3 → proceed to discovery.

---

## Pattern 17: Video vs Animation — Routing Disambiguation

**Task:** "把这段逻辑流程做成动画 GIF。"

**Installed:** `remotion`, `remotion-video`, `ffmpeg-usage`

**Route:** `remotion` — dominant capability is animated diagram/GIF, not full video production. `remotion-video` is for full video projects; `ffmpeg-usage` is for processing existing video. `remotion` is the right tool for logic diagrams and animated GIFs.

---

## Pattern 18: User Exploring — Support Without Pushing

**Task:** "我装了哪些 skill？有适合做数据分析的吗？"

**Installed:** `data-analysis`, `xlsx`, `pdf`, `docx`, `pptx`, `frontend-design`

**Route:** This is an exploration query, not a task. List installed skills relevant to data work: `data-analysis` (primary), `xlsx` (spreadsheet analysis). Do not push toward installing new skills — the user is browsing, not requesting.
