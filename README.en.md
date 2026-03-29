<p align="center">
  <h1 align="center">Great Writer</h1>
  <p align="center">AI writing that people actually want to read</p>
  <p align="center">
    <a href="#three-core-capabilities">Core</a> · <a href="#5-writing-modes">Modes</a> · <a href="#installation">Install</a> · <a href="./README.md">中文</a>
  </p>
</p>

---

## TL;DR

A universal AI writing skill covering **tech articles, marketing copy, research reports, Xiaohongshu notes, and technical docs** — five modes in one package. Research-driven, full-pipeline, anti-AI-slop. Bilingual (EN/ZH).

## What Problem Does It Solve

Ask AI to write something and you'll probably get this:

> "In today's rapidly evolving technological landscape, our product leverages cutting-edge AI capabilities to deliver an unprecedented experience..."

> "随着人工智能技术的快速发展，XX 产品凭借其强大的功能和出色的性能..."

**Nobody reads that.** No data, no pain point, no imagery — just AI filler. And it doesn't matter whether you're writing a blog post, a landing page, a research brief, or a product review. Without guardrails, AI output tastes the same everywhere: hollow, formulaic, obviously machine-generated.

**After loading Great Writer:**

| What you're writing | Without Great Writer | With Great Writer |
|---------------------|---------------------|-------------------|
| Tech article | "With the rapid development of cloud computing, we're proud to introduce a powerful new product..." | "Your server bill tripled last month. Not because traffic grew — because you're paying for idle compute." |
| Marketing copy | "Our product delivers powerful features and outstanding performance in a comprehensive solution..." | "3-minute deploy. Zero ops. $2,400/month saved." |
| Research report | "Based on the above analysis, this industry shows broad prospects and immense market potential..." | "$4.7B raised in this space in Q4 2025 — up 340% YoY. Three signals worth watching." |
| Xiaohongshu note | "This product is really amazing, highly recommend!" | "Used it for two weeks, here's the honest take. Bottom line: worth it, but there's one trap to avoid." |
| Technical docs | "This document aims to provide developers with a comprehensive API usage guide..." | "5 minutes to first request. Install, configure, call, handle errors, deploy to prod." |

## Three Core Capabilities

### 1. Research-Driven: No Research, No Writing

Most AI writing fails not because of bad prose but because of **thin content**. The AI writes from training data or a one-line prompt, producing generic text that could describe any product.

Great Writer enforces a three-step research protocol before any writing begins:
- **Audience targeting** — Who reads this? What's their technical level? Where will they encounter it?
- **Exclusion analysis** — Who's locked out by existing solutions? Those people are your strongest angle.
- **Deep material mining** — If search tools are available, actively find competitor data and benchmarks. No tools? Ask the user for materials. Never fabricate.

Research must be completed before drafting starts. No exceptions.

### 2. Full Pipeline: 5 Phases, Each Independently Re-runnable

```
Research → Draft → Review → Humanize → Final Check
```

| Phase | What happens | Module loaded |
|-------|-------------|---------------|
| Research | Audience analysis, exclusion analysis, material mining | `core/research-protocol.md` |
| Draft | Write first draft using mode template + writing DNA | `core/writing-dna.md` + `modes/*.md` |
| Review | Structural review + logic review + fact check | `core/review-protocol.md` |
| Humanize | Blacklist interception + rhythm reshaping | `core/humanizer.md` |
| Final Check | Run mode-specific self-check checklist; fail = fix and re-check | Checklist in each mode file |

Users can jump to any phase at any time. Say "re-research" to go back to step 1. Say "humanize" to jump straight to step 4. Each phase runs independently — no need to restart from scratch.

### 3. Anti-AI-Slop: Bilingual Blacklist + Rhythm Reshaping

**Level 1 — Hard rules: Blacklist interception**

Chinese bans: "随着...的发展", "众所周知", "在当今时代", "不言而喻", "值得一提的是", "毋庸置疑"...
English bans: "In today's rapidly evolving...", "It's worth noting...", "Game-changing", "Delve into", "Robust", "Seamless"...

Adjectives without data support are banned outright: "powerful", "outstanding", "innovative", "leading", "revolutionary"...

**Level 2 — Soft rules: Rhythm reshaping**

- Sentence length variation: short sentences carry the backbone, long ones provide breathing room — no three consecutive sentences of similar length
- Asymmetric structure: AI loves perfectly parallel three-item lists; humans don't write that way
- Concrete details replace abstractions: "many users reported" becomes "2,847 users in the first week"
- Rhetorical questions for rhythm: 1-2 per piece, no more
- Mode-specific overrides: Xiaohongshu allows more emojis and internet slang; technical docs forbid rhetorical questions and conversational asides

## 5 Writing Modes

| Mode | Description | Typical platforms |
|------|-------------|-------------------|
| **Tech Product Article** | Data-driven product introduction, 9-module structure, pain-first opening | WeChat, tech blogs, product launches |
| **Marketing Copy** | Conversion-focused, CTA-driven, supports landing pages / social / ads | Landing pages, social media, ad campaigns |
| **Research Report** | Deep analysis, rigorous data, actionable conclusions for decision-makers | Whitepapers, competitive analysis, industry research |
| **Xiaohongshu Note** | Useful + authentic + visually appealing, personal voice, visual formatting | Xiaohongshu / RED, review communities |
| **Technical Docs** | Clarity > completeness > elegance, 5-minute onboarding, developer-facing | READMEs, API docs, changelogs, internal guides |

## Architecture

```
great-writer/
├── SKILL.md                    # Entry point: routing + pipeline definition
├── core/                       # Shared core modules (used by all modes)
│   ├── writing-dna.md          #   6 universal writing principles
│   ├── research-protocol.md    #   Research protocol (3 steps)
│   ├── review-protocol.md      #   Review protocol (3 dimensions)
│   └── humanizer.md            #   Anti-AI-slop protocol (2 levels)
├── modes/                      # Mode-specific templates
│   ├── tech-article.md         #   Tech product article
│   ├── marketing-copy.md       #   Marketing copy
│   ├── research-report.md      #   Research report
│   ├── xiaohongshu.md          #   Xiaohongshu note
│   └── technical-docs.md       #   Technical documentation
└── README.md / README.en.md    # What you're reading
```

Layered design: `SKILL.md` handles routing and pipeline orchestration. `core/` contains the writing DNA shared across all modes. `modes/` holds structure templates and self-check checklists for each writing type. Every file is self-contained and loaded on demand.

## Installation

### Claude Code

```bash
# Clone the repo
git clone https://github.com/d-wwei/great-writer.git

# Create symlink (macOS / Linux)
ln -sf "$(pwd)/great-writer" ~/.claude/skills/great-writer
```

Once installed, Claude Code auto-loads the skill when it detects trigger words in conversation.

### Codex / agentskills.io

Great Writer uses the standard Skill directory structure (`SKILL.md` entry point + module files), compatible with the agentskills.io format. Import the repo directly.

### Other Agents

Inject the content of `SKILL.md` as a system prompt or context. Include the core module files (`core/` and `modes/`) alongside it, following the file references in `SKILL.md`.

If your agent doesn't support multi-file loading, concatenate `SKILL.md` + all `core/*.md` + the relevant `modes/*.md` into a single file.

## Usage

### Trigger Words

The skill auto-activates when these keywords appear in conversation:

| Mode | Chinese triggers | English triggers |
|------|-----------------|-----------------|
| Tech Article | 写文章, 公众号, 博客, 产品介绍 | write article, blog post, product article |
| Marketing Copy | 文案, 推广文, 产品文案 | marketing copy, ad copy, landing page |
| Research Report | 白皮书, 研究报告, 竞品分析, 投研 | whitepaper, research report, competitive analysis |
| Xiaohongshu | 小红书, 种草, 笔记 | xiaohongshu |
| Technical Docs | 技术文档, 内部文档 | README, API docs, changelog, technical docs |

### Example Dialogue

```
You: Write a blog post about our new product. Key selling points: 10x faster, 80% cheaper.
AI:  [Routes to "Tech Product Article" mode]

     Got it. Before writing, a few research questions:
     1. Who's the target reader? Developers, PMs, or executives?
     2. Main competitors?
     3. What's the "10x faster" benchmark? Any specific numbers?

You: Targeting developers. Competitors are XX and YY. Benchmark here: ...
AI:  [Completes research → drafts using 9-module structure → reviews → humanizes → final check → outputs]
```

### Phase Jumping

Want to re-run a specific phase after the first draft:

| You say | What happens |
|---------|-------------|
| "re-research" / "重新调研" | Back to research phase |
| "rewrite" / "重写" | Back to drafting phase |
| "review" / "审校" | Run review protocol |
| "humanize" / "去AI味" | Run humanizer protocol |
| "check" / "自检" | Run final check checklist |

## Compatibility

| Platform | Support level | Notes |
|----------|--------------|-------|
| Claude Code | Full support | Native Skill format, auto-trigger, multi-file on-demand loading |
| Claude (chat) | Manual load | Paste SKILL.md content at the start of conversation |
| Cursor / Windsurf | Full support | Load as rules or context files |
| ChatGPT | Manual load | Use as Custom Instructions or conversation context |
| Codex / agentskills.io | Compatible | Standard Skill directory structure |
| Other LLM agents | Manual load | Inject SKILL.md as system prompt |

## Tool Integration

Great Writer has zero hard dependencies on external tools, but works better with them:

| Capability | Available tools | Without tools |
|------------|----------------|---------------|
| Web search | Tavily, WebSearch, Brave | Guide user to provide materials |
| Content extraction | Firecrawl, WebFetch, Jina | Ask user to paste content |
| Academic citations | Scholar, Semantic Scholar | Mark as "needs verification" |

## License

MIT
