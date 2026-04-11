# Great Writer

A writing skill for AI agents. 9 writing modes, 9 core modules, bilingual (EN/ZH).

<a href="./README.zh.md">中文</a>

---

## What Problem It Solves

You ask AI to write something. First sentence back:

> "In today's rapidly evolving technological landscape, our product leverages cutting-edge AI capabilities..."

The model isn't the problem. The missing writing system is.

| Task | Without Great Writer | With Great Writer |
|------|---------------------|-------------------|
| Tech article | "With the rapid development of cloud computing..." | "Your server bill tripled last month. Not because traffic grew." |
| Marketing copy | "Our robust, comprehensive solution empowers..." | "Deploy in 3 minutes. Zero ops. Save $2,400/mo." |
| Research report | "The industry shows tremendous growth potential..." | "Q4 funding hit $4.7B, up 340% YoY. Three signals to watch." |
| Documentation | "This document aims to provide a comprehensive guide..." | "Install. Configure. First request. Handle errors. Ship." |
| Rewrite | "Here is the revised version: [barely changed]" | "Diagnosis: 3 structural issues, 5 AI cliches, 2 logic gaps. Fixed each, changes shown." |

Great Writer loads a writing system into your AI agent: mandatory research before writing, automatic AI-slop removal after, dedicated templates for each format.

---

## Quick Start

```bash
git clone https://github.com/d-wwei/great-writer.git
```

Then load into your agent:

- **As a skill directory:** Point your agent's skill path to the cloned repo
- **As a system prompt:** Copy `great-writer-bundled.md` into your agent's system prompt or context
- **As a rules file:** Import `SKILL.md` as a rules/instructions file

Say "write article", "小红书种草", or "write a README" in conversation to trigger.

---

## What It Does

**Write 8 types of content:**

| Mode | Triggers | Use For |
|------|----------|---------|
| Tech Product Article | write article, blog post, 公众号 | WeChat, tech blogs, product launches |
| Marketing Copy | marketing copy, landing page, ad copy | Landing pages, social media, ads |
| Research Report | whitepaper, competitive analysis, 投研 | Whitepapers, competitive reports |
| Xiaohongshu Note | 小红书, 种草, xiaohongshu | Product recommendations, tutorials |
| Technical Docs | README, API docs, changelog | READMEs, API docs, internal guides |
| Rewrite / Polish | rewrite, polish, improve this | Existing drafts, emails, memos |
| Editorial Review | critique this, editorial review, 审稿 | Feedback on others' writing |
| Creative Writing | fiction, essay, speech, screenplay | Stories, essays, speeches, scripts |

**Every piece goes through a 5-phase pipeline:**

```
Research → Draft → Review → Humanize → Finalize
```

Each phase runs independently. Say "humanize" to jump straight to phase 4 without restarting.

**5 enhanced capabilities (activated on demand):**

| Capability | Trigger |
|-----------|---------|
| Style Learning | Provide reference text, say "match this style" |
| Platform Adaptation | "adapt for Twitter" or "转成小红书版" |
| Writing Memory | Persists brand names, terms, data, style across sessions |
| SEO/GEO Optimization | "SEO", suggests optimization for web-published content |
| Data Visualization | Auto-triggers for data-rich content, suggests charts |

---

## How It Works

Layered architecture. SKILL.md routes requests, core/ holds shared capabilities, modes/ holds format templates. Each invocation loads only what it needs.

```
great-writer/
├── SKILL.md                    # Router + pipeline definition
├── core/                       # Shared core (9 modules)
│   ├── writing-dna.md          # 7 writing principles
│   ├── research-protocol.md    # Pre-writing research
│   ├── review-protocol.md      # Post-draft review
│   ├── humanizer.md            # Anti-AI-slop protocol
│   ├── style-learner.md        # Style fingerprint extraction
│   ├── adapt-protocol.md       # Multi-platform adaptation
│   ├── writing-memory.md       # Cross-session persistence
│   ├── seo-layer.md            # SEO/GEO optimization
│   └── visualization.md        # Data visualization suggestions
├── modes/                      # Format templates (9 modes)
│   ├── tech-article.md         # Tech product articles
│   ├── github-readme.md        # Story-driven bilingual GitHub READMEs
│   ├── marketing-copy.md       # Marketing copy
│   ├── research-report.md      # Research reports
│   ├── xiaohongshu.md          # Xiaohongshu notes
│   ├── technical-docs.md       # Technical documentation
│   ├── rewrite.md              # Rewrite / polish
│   ├── editorial-review.md     # Editorial review
│   └── creative-writing.md     # Creative writing
├── scripts/bundle.sh           # Single-file bundler
├── great-writer-bundled.md     # Bundled version for single-file agents
├── README.md                   # English (this file)
└── README.zh.md                # 中文
```

---

## Installation

**Any agent that supports skill directories** (Claude Code, Codex, Cursor, Windsurf, etc.):

```bash
git clone https://github.com/d-wwei/great-writer.git
# Point your agent's skill/rules path to the cloned directory
```

**Single-file agents** (ChatGPT, custom LLM pipelines, etc.):

Use `great-writer-bundled.md` as your system prompt or context injection. One file, all 17 modules included.

---

## Compatibility

| Platform | Method |
|----------|--------|
| Claude Code | Symlink to `~/.claude/skills/` |
| Codex | agentskills.io format, import directly |
| Cursor / Windsurf | Load as rules file or project context |
| ChatGPT / GPT | Paste `SKILL.md` into Custom Instructions |
| Gemini CLI | Import as agent skill |
| Custom LLM pipelines | Inject `great-writer-bundled.md` as system prompt |

---

## Anti-AI-Slop

30+ bilingual blacklist rules built in. Chinese bans: "随着", "赋能", "一站式". English bans: "leverage", "delve into", "game-changing", "robust", "seamless".

The blacklist is layer one. Layer two reshapes rhythm: breaks AI's perfect parallel structures, varies sentence length, replaces "significant number of users" with "2,847 users in the first week."

---

## Tool Integration

No hard dependencies. Auto-enhances when tools are available:

| Capability | Tools | Without |
|-----------|-------|---------|
| Search | Tavily, WebSearch, Brave | Guides user to provide materials |
| Extraction | Firecrawl, WebFetch | Asks user to paste content |
| Typesetting | typeset skill | Outputs plain Markdown |

---

## License

MIT
