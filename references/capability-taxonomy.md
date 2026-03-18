# Capability Taxonomy

A lightweight classification of task capabilities for routing decisions.

This is not an exhaustive ontology. It is a practical reference for identifying the **dominant capability** a task requires, so Skill Router can match it against installed skills.

---

## How to Use This File

1. Read the user's task
2. Identify which capability category best describes what the task **primarily** needs
3. Use that category to search installed skills for a match
4. If the task spans multiple categories, pick the **dominant** one — the one that determines success or failure

Do not decompose tasks into fine-grained sub-capabilities. The goal is a single routing decision, not a dependency graph.

---

## Capability Categories

### Document Creation

Producing structured output files: reports, presentations, spreadsheets, PDFs, Word documents.

**Signals:** "create a report", "make a presentation", "build a spreadsheet", file format mentions (.docx, .pptx, .xlsx, .pdf)

### Document Transformation

Converting, reformatting, merging, splitting, or restructuring existing documents.

**Signals:** "convert this to", "merge these files", "reformat", "extract from this PDF"

### Code Generation

Writing new code: applications, scripts, components, functions, configurations.

**Signals:** "build an app", "write a script", "create a component", explicit language/framework mentions

### Code Transformation

Refactoring, porting, debugging, optimizing, or migrating existing code.

**Signals:** "refactor this", "port to Python", "fix this bug", "optimize", "migrate from X to Y"

### Data Analysis

Analyzing, summarizing, visualizing, or extracting insights from structured or unstructured data.

**Signals:** "analyze this data", "what trends do you see", "summarize these results", "chart this"

### Research & Information Retrieval

Finding, synthesizing, and presenting information from various sources.

**Signals:** "research X", "find out about", "what's the latest on", "compare options for"

### Image Generation

Creating new images from text descriptions or reference images using AI generation tools.

**Signals:** "生成图片", "画一张", "文生图", "generate an image", "create an illustration", "make a picture of", "AI 作画", "画图", "图生图"

### Visual Content Production

Creating structured visual content beyond a single AI image: infographics, cover images, article illustrations, slide image decks, comics, XHS image series, and other composed visual formats.

**Signals:** "做信息图", "封面图", "小红书图文", "文章配图", "漫画", "slide 图片", "视觉内容", "图文系列", "infographic", "cover image"

Note: Distinct from Image Generation (which produces a single AI image) and Document Creation (which produces editable files). Visual Content Production outputs composed, publication-ready image sequences or structured layouts.

### Image Processing

Converting, compressing, resizing, or batch-manipulating existing images.

**Signals:** "压缩图片", "转换格式", "resize", "convert to WebP", "batch process images", "图片格式转换", "compress image"

### Video & Animation

Creating, editing, converting, or processing video and animation content. Includes GIF generation and animated diagrams.

**Signals:** "制作视频", "做动画", "GIF", "视频转换", "音频提取", "字幕", "make a video", "animate", "logic diagram GIF", "视频剪辑"

### OCR & Text Extraction

Extracting text from images, scanned documents, PDFs, or web pages.

**Signals:** "识别文字", "OCR", "提取文字", "extract text from image", "scan this document", "抓取网页内容", "fetch URL", "网页转 Markdown", "从图片读取"

### Translation

Translating text or documents between languages.

**Signals:** "翻译", "translate", "英译中", "中译英", "translate this document", "多语言", "localize"

### Communication & Writing

Drafting, editing, or refining written communications: articles, blog posts, documentation, internal comms, emails.

**Signals:** "write an email", "draft a message", "edit this text", "写公众号文章", "写博客", "写文档", "帮我写", "创作内容"

### Integration & Messaging

Sending or reading messages, notifications, or events through external platforms and services.

**Platform signals by context:**
- WeChat / 公众号: `baoyu-post-to-wechat`, `baoyu-markdown-to-html`
- Weibo / 微博: `baoyu-post-to-weibo`
- X / Twitter: `baoyu-post-to-x`
- Feishu / 飞书: `feishu-card` (send), `feishu-doc-reader` (read)
- Slack: `slack-gif-creator` (for GIFs in Slack)
- GitHub / webhook / generic API: handle directly, no dedicated skill

**General signals:** "发布到", "post to", "send a message", "notify", "create an issue", "trigger a webhook", platform name mentions

### Social Media Publishing

Publishing content (text, images, articles) to social media platforms. A specialized sub-case of Integration & Messaging where the primary deliverable is a published post.

**Signals:** "发微博", "发推", "发小红书", "post this to", "发公众号", "publish to social media"

Route based on which platform is mentioned. If no platform is specified, ask before routing.

### Workflow Automation

Orchestrating multi-step processes, integrations, or automations across tools and services.

**Signals:** "automate this", "set up a pipeline", "connect X to Y", "every time X happens, do Y", "CI/CD", "git hooks", "定时任务", "脚本"

### Development Workflow

Managing the process of software development: feature planning, implementation discipline, code review, testing, release, and multi-agent orchestration. Distinct from Code Generation (which focuses on the output) — Development Workflow focuses on how the work is organized and executed.

**Signals:** "开发新功能", "code review", "写测试", "发版本", "commit", "初始化项目", "多 agent 协作", "TDD", "并行任务", "review 我的代码"

### System Administration

Managing infrastructure, configurations, deployments, environments, and tooling.

**Signals:** "deploy this", "configure the server", "set up the environment", "install and configure"

### Planning & Strategy

Developing plans, roadmaps, strategies, or structured decision frameworks.

**Signals:** "help me plan", "what's the best approach", "create a roadmap", "prioritize these", "长期计划", "项目规划"

### Learning & Explanation

Teaching, explaining, tutoring, or creating educational content.

**Signals:** "explain how", "teach me", "what does X mean", "walk me through"

---

## Platform Context Rule

When the task mentions a specific platform (WeChat, Weibo, XHS, Feishu, X, Slack), route to the skill matching that platform even if a more generic skill could technically handle it.

> Task: "发一篇文章到公众号"
> Platform signal "公众号" → `baoyu-post-to-wechat` is the primary skill, not a generic writing skill.

If the task content and the platform are both important, the platform determines the primary routing; the content skill is secondary.

---

## When a Task Doesn't Fit

If a task doesn't clearly map to any category above, it probably doesn't need skill routing. Just do the task directly.

If a task genuinely represents a new capability category not listed here, note it — this taxonomy should grow organically based on real routing needs, not speculation.

---

## Multi-Capability Tasks

Some tasks touch multiple categories. Examples:

- "Research competitors and create a presentation" → **Document Creation** is dominant (the presentation is the deliverable; research is a means)
- "Analyze this CSV and write a report about the findings" → **Data Analysis** is dominant (analysis quality determines success)
- "Build a dashboard that pulls data from our API" → **Code Generation** is dominant (the code is the hard part)
- "Fetch this article and post it to WeChat" → **Social Media Publishing** is dominant (fetching is a means)
- "Write a WeChat article with custom illustrations" → **Communication & Writing** is dominant (illustrations are support)

The heuristic: **what determines whether the user considers the task successful?** That's your dominant capability.
