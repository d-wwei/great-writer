[English](README.md) | [中文](README.zh.md)

# Great Writer

A writing system for AI agents. Not a prompt template — a 6-phase pipeline that forces your agent to think before it writes, then strips every trace of AI from the output.

9 writing modes. 15 writing principles. 4-pass polish. Bilingual (EN/ZH).

---

## Why This?

You ask an AI agent to write something. First sentence back:

> *"In today's rapidly evolving technological landscape, our product leverages cutting-edge AI capabilities..."*

Sound familiar? The model isn't broken. What's missing is a writing *system*.

Most AI writing tools hand you a better template — a fancier recipe card. The output improves a little, but it still reads like AI. The sentences are all the same length. The structure is perfectly symmetrical. Every list has exactly three items. Readers can smell it.

The real problem isn't formatting. It's that the AI never *thought* about what it was writing. It skipped straight from your prompt to polished prose, with nothing in between — no research, no questioning, no stress-testing the core idea.

Great Writer fixes this by adding the parts that professional writers actually spend most of their time on: figuring out what's really worth saying (and attacking that idea until it holds up), then systematically removing every pattern that screams "a machine wrote this."

Think of it as the difference between a recipe collection and chef training. Recipe collections produce standardized dishes. Chef training teaches you *why* — why this cut, why this heat, why this timing for this ingredient. That's the kind of difference we're after.

---

## What It Is

Great Writer is a single skill you install on any AI agent (Claude Code, Codex, Cursor, Windsurf, Gemini CLI — anything that loads SKILL.md or system prompts).

It gives your agent:

- **9 writing modes** — tech articles, marketing copy, research reports, Xiaohongshu notes, GitHub READMEs, technical docs, rewrite/polish, editorial review, creative writing
- **A 6-phase pipeline** — research → find core → structure → draft → review → polish → finalize
- **A 4-pass polish system** — oral test, density control, AI trace removal, anti-style check

One skill directory (~20 files). Or one bundled file if your agent doesn't support directories.

---

## Key Features

**Find Core → Attack Core.** Before writing, the agent digs for the one idea the piece is actually about — using four "shovels" (invert the claim, chase the premise, chase the emotion, flip the definition). Then it attacks that idea: "If this is true, then why ______?" If the core breaks, it tells you honestly instead of writing an essay defending a weak idea. No other writing tool does this.

**4-pass polish that merges two methodologies.** Pass 1: oral test ("would you say this to a friend?"). Pass 2: density compression across five dimensions. Pass 3: AI trace removal (bilingual blacklist with 30+ banned phrases and structures, 8 structural pattern detectors, translation immunity for Chinese). Pass 4: anti-style check (explaining? → show a scene. listing? → keep only the strongest).

**Mode-specific voice tuning.** Each writing mode has its own temperature, posture, and active principles. A Xiaohongshu note runs at 35°C with full inner voice and "empathy first." A technical doc runs at 18°C with zero rhetorical questions. The same skill produces genuinely different voices — not one template with minor tweaks.

**Forced research with 3-layer pain depth.** The agent can't start writing until it produces a Research Summary. Pain points must reach Layer 3 — not just "the problem exists" (L1) or "here's the consequence" (L2), but "here's the absurd thing people do to work around it" (L3). This is what makes the output specific instead of generic.

**15 writing principles, mechanically checkable.** Not vague advice like "write clearly." Rules like: no 3+ consecutive sentences of similar length. No paragraph ending with significance inflation. No same sentence structure repeated. Each principle has a test — pass or rewrite.

---

## With / Without

| | Without Great Writer | With Great Writer |
|---|---|---|
| **Before writing** | Agent jumps straight to prose | Agent researches audience, finds core, stress-tests it |
| **Core idea** | Whatever the prompt implies | Dug out with four shovels, attacked, verified it holds |
| **Structure** | AI's default: intro → body → conclusion | Deliberate: 40% on what matters, 5% on background |
| **First draft** | 15 principles applied? Zero | 15 principles active, mode-specific voice loaded |
| **AI smell** | Hope the reader doesn't notice | 4-pass system: bilingual blacklist, 8 structural patterns, oral test |
| **Chinese quality** | 翻译腔 everywhere | Translation immunity: symptom checklist + back-translation test |
| **Reuse** | Start from scratch every time | Writing memory: brand terms, data, style persist across sessions |

---

## How It Works

### The 6-Phase Pipeline

Every piece of writing — regardless of mode — goes through the same pipeline:

```
Phase 1          Phase 2          Phase 3       Phase 4      Phase 5       Phase 6
Core Logic  →  Structure    →    Draft    →   Review   →   Polish   →   Finalize
                Design
    │               │               │            │            │             │
    ├─ Research     ├─ Scaffold     │            │            ├─ Oral test  │
    ├─ Think/Judge  ├─ Arc/Weight   │            │            ├─ Density    │
    └─ Find+Attack  └─ Reader check │            │            ├─ AI removal │
        Core                        │            │            └─ Anti-style │
                                    │            │                          │
                              writing-dna    review-       humanizer     mode
                              + mode file    protocol      (4-pass)     checklist
```

**Phase 1: Core Logic** — The agent researches your audience, identifies the core tension ("what does this piece change about the reader's understanding?"), then digs for the core idea using four shovels and stress-tests it. If the core breaks under attack, the agent says so instead of writing a flawed essay. Output: Research Summary + Core Statement.

**Phase 2: Structure Design** — Find a cross-disciplinary analogy that acts as the piece's structural backbone (not decoration — remove it and the piece collapses). Then choose a narrative arc and assign weight deliberately (the important section gets 40%, background gets 5%). The skeleton is presented for your approval before any writing begins.

**Phase 3: Draft** — Load the 15 writing principles from writing-dna.md and the mode-specific template. Write section by section, hanging every detail back on the scaffold so the reader always knows where they are.

**Phase 4: Review** — Four dimensions: structure (does it match the template?), logic (does each claim have evidence?), facts (are the numbers right?), perspective (is it written for the reader, not the builder?). Output: numbered fix list. All "must fix" items resolved before moving on.

**Phase 5: Polish** — Four passes, run sequentially. Pass 1 (oral test) is highest priority — everything must sound like something you'd say to a smart friend. Pass 2 compresses density across five dimensions. Pass 3 removes AI traces using merged blacklists, structural pattern detection, and Chinese translation immunity. Pass 4 runs eight anti-style checks.

**Phase 6: Finalize** — Run the mode-specific self-check checklist. All items pass → output. Any fail → fix and re-check.

### Architecture

```
great-writer/
├── SKILL.md                    # Router + 6-phase pipeline definition
├── core/                       # Shared modules (10)
│   ├── writing-dna.md          # 15 writing principles + density + voice
│   ├── core-finding.md         # Find Core + Attack Core methodology
│   ├── research-protocol.md    # Pre-writing research (3-layer pain depth)
│   ├── review-protocol.md      # 4-dimension post-draft review
│   ├── humanizer.md            # 4-pass polish protocol
│   ├── style-learner.md        # Style fingerprint extraction
│   ├── adapt-protocol.md       # Multi-platform content adaptation
│   ├── writing-memory.md       # Cross-session brand/style persistence
│   ├── seo-layer.md            # SEO/GEO optimization (optional)
│   └── visualization.md        # Data visualization suggestions
├── modes/                      # Format templates (9)
│   ├── tech-article.md         # WeChat, blogs, product launches
│   ├── github-readme.md        # Story-driven bilingual READMEs
│   ├── marketing-copy.md       # Landing pages, ads, social posts
│   ├── research-report.md      # Whitepapers, competitive analysis
│   ├── xiaohongshu.md          # Xiaohongshu (RED) notes
│   ├── technical-docs.md       # API docs, changelogs, internal guides
│   ├── rewrite.md              # Improve existing drafts
│   ├── editorial-review.md     # Critique and feedback
│   └── creative-writing.md     # Fiction, essays, speeches, scripts
├── scripts/bundle.sh           # Concatenates everything into one file
└── great-writer-bundled.md     # Single-file version (~175KB)
```

### Design Decisions

| Decision | Choice | Why |
|----------|--------|-----|
| Find core before structuring | Separate Phase 1 and Phase 2 | You can't structure a piece until you know what it's really about. Most AI writing tools skip this — that's why the output is structurally correct but intellectually empty |
| 4-pass polish (not 2-level) | Merged two independent anti-AI systems | The oral test (from ljg-writes) catches what blacklists miss. Blacklists catch what oral tests miss. Together they cover more ground than either alone |
| Mode-specific voice temperature | Each mode has its own °C setting | A Xiaohongshu note at 18°C reads like a textbook. A technical doc at 35°C reads like a blog. Same skill, different voice — because the reader expectation is different |
| 15 principles, not 9 | Added scene-first, progressive revelation, concession turns, etc. | The original 9 were product-writing oriented. The new 6 (from ljg-writes methodology) add depth for opinion pieces, creative writing, and Chinese writing specifically |
| Forced research gate | Phase 1 cannot be skipped | Without research, AI writing is generic by definition. The agent has no specific data, no audience understanding, no unique angle. The gate makes this non-negotiable |

---

## Quick Start

```bash
git clone https://github.com/d-wwei/great-writer.git
```

**Option A — Skill directory** (Claude Code, Codex, Cursor, Windsurf):
Point your agent's skill path to the cloned directory.

**Option B — Single file** (ChatGPT, custom pipelines):
Copy `great-writer-bundled.md` into your system prompt or context.

Then just talk to your agent:

```
"写一篇公众号文章，关于我们的新产品"
"Write a blog post about our launch"
"帮我润色这篇文章"
"Write a README for this repo"
```

The skill auto-detects the writing type and loads the right mode.

---

## Enhanced Capabilities

These modules activate on demand — say the trigger phrase and they load:

| Capability | Trigger | What It Does |
|-----------|---------|-------------|
| Style Learning | "match this style" / provide reference text | Extracts a reusable style fingerprint from any sample |
| Platform Adaptation | "转成小红书版" / "adapt for Twitter" | Converts one piece into 8+ platform formats |
| Writing Memory | Auto-offered after tasks | Persists brand terms, data, style across sessions |
| SEO/GEO | "SEO" / web-published content | Search engine + AI search optimization |
| Visualization | Auto for data-rich content | Chart and diagram suggestions |

---

## License

MIT

---

*Built by humans who got tired of reading AI-flavored text. Powered by a synthesis of [ljg-writes](https://github.com/ljg) methodology and battle-tested writing principles.*
