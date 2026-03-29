# Great Writer v2 — Universal Writing Skill Design Spec

**Date:** 2026-03-28
**Status:** Approved
**Replaces:** great-writer v1 (tech product articles only)

---

## Overview

Great Writer v2 is a universal writing skill for AI agents. It covers four writing types through a modular router + sub-skill architecture, with three shared capability pillars: research-driven workflow, full-pipeline processing, and AI-slop elimination.

### Goals

- **Universal**: handle tech articles, marketing copy, research reports, Xiaohongshu notes, and technical docs
- **Bilingual**: SKILL.md in English for internationalization; built-in rules and examples for both Chinese and English
- **Modular**: router dispatches to type-specific modes; shared capabilities live in core/
- **Research-driven**: no writing without research first
- **Anti-AI-slop**: every writing type passes through humanizer layer
- **Tool-aware**: integrates with search/crawl tools when available, degrades gracefully without them

### Non-goals

- Creative fiction / novel writing (out of scope for v2)
- Real-time collaboration / multi-agent orchestration (single skill, single agent)
- WYSIWYG formatting / typesetting (separate concern; can chain with typeset skill)

---

## Architecture

### Layered Design

```
great-writer/
├── SKILL.md                    # Router + triggers + overview
├── core/
│   ├── writing-dna.md          # Universal writing principles
│   ├── research-protocol.md    # Pre-writing research protocol
│   ├── humanizer.md            # Anti-AI-slop rules
│   └── review-protocol.md      # Post-draft review protocol
├── modes/
│   ├── tech-article.md         # Tech product articles
│   ├── marketing-copy.md       # Marketing copy & ads
│   ├── research-report.md      # Deep content & research reports
│   ├── xiaohongshu.md          # Xiaohongshu / RED notes
│   └── technical-docs.md       # Documentation & technical writing
├── README.md
├── README.en.md
└── LICENSE
```

### Layer Responsibilities

| Layer | Contains | Loaded When |
|-------|----------|-------------|
| SKILL.md | Trigger rules, routing logic, pipeline overview, tool integration declarations | Always (entry point) |
| core/ | Cross-type shared capabilities | Per-phase (only the relevant core module) |
| modes/ | Type-specific structure templates, tone rules, checklists | After routing (only the matched type) |

---

## SKILL.md — Router

### Trigger Rules

**Chinese:** 写文章, 公众号, 博客, 技术博客, 产品介绍, 产品文案, 推广文, 发布文, 文案, Landing Page, 白皮书, 研究报告, 竞品分析, 行业分析, 投研, README, API文档, Changelog, 技术文档, 内部文档, 小红书, 种草, 笔记, write article

**English:** write article, blog post, product article, marketing copy, landing page, ad copy, social media post, whitepaper, research report, competitive analysis, industry report, README, API docs, changelog, technical docs, internal guide, release notes, xiaohongshu, RED note

### Routing Logic

| Signal | Route To |
|--------|----------|
| 公众号/博客/产品发布/技术介绍/product article/blog post | `modes/tech-article.md` |
| Landing page/广告/CTA/社交媒体/文案/ad copy/social post | `modes/marketing-copy.md` |
| 白皮书/行业分析/竞品报告/投研/whitepaper/research report | `modes/research-report.md` |
| 小红书/种草/笔记/xiaohongshu/RED note | `modes/xiaohongshu.md` |
| README/API docs/Changelog/内部文档/technical docs/guide | `modes/technical-docs.md` |
| Ambiguous | Ask user to clarify |

### Pipeline (All Types)

```
Phase 1: Research    → core/research-protocol.md
Phase 2: Draft       → core/writing-dna.md + modes/{type}.md
Phase 3: Review      → core/review-protocol.md
Phase 4: Humanize    → core/humanizer.md
Phase 5: Finalize    → Type-specific checklist + output
```

Phase 5 uses the checklist embedded at the bottom of each mode file (e.g., `modes/tech-article.md` ends with its own self-check checklist).

Each phase is independently re-runnable. User can jump to any phase:
- "重新调研" / "re-research" → Phase 1
- "重写" / "rewrite" → Phase 2
- "审校" / "review" → Phase 3
- "去AI味" / "humanize" / "润色" → Phase 4
- "检查" / "check" → Phase 5

### Tool Integration

Declared as optional capabilities in SKILL.md:

| Capability | Example Tools | Degraded Behavior |
|------------|--------------|-------------------|
| Web search | Tavily, WebSearch, Brave | Guide user to provide materials manually |
| Content extraction | Firecrawl, WebFetch, Jina | Ask user to paste content |
| Academic citations | Scholar, Semantic Scholar | Mark as "needs manual verification" |
| Typesetting | typeset skill | Output plain Markdown |

No hard dependencies. Auto-enhance when tools are available, degrade gracefully without.

### Sub-file Loading Mechanism

SKILL.md instructs the agent to read sub-files using explicit `Read` directives within the pipeline instructions. Example:

```
When entering Phase 1, read the file `core/research-protocol.md` (relative to this skill's directory) and follow its protocol.
```

For Claude Code: sub-files are referenced via relative paths from the skill root. The agent uses its Read tool to load them on demand.
For Codex/other agents: the same relative-path references work. If the agent cannot resolve relative paths, use the bundled single-file version.

---

## Core Modules

### core/writing-dna.md — Universal Writing Principles

Six principles inherited by all writing types:

1. **Data as anchors** — Every piece must have quantifiable core data. Reject vague adjectives.
   - ✅ "Cut 96% of tokens" / "25x difference" / "550 vs 14,000"
   - ❌ "Significantly improved efficiency" / "Greatly reduced costs"

2. **Pain/problem first** — Open with the core tension. No warmup, no preamble.
   - ✅ "Your server bill tripled last month. Not because traffic grew."
   - ❌ "With the rapid development of cloud computing..."

3. **Analogy over explanation** — One good analogy beats three paragraphs of technical description.
   - ✅ "MCP is carrying a 1,350-piece toolbox; Skills is a pocket handbook."
   - ❌ "MCP protocol requires injecting all tool JSON schemas into context at startup..."

4. **Scenario-based presentation** — Group by use case, not by feature list.
   - ✅ "AI auto-searches docs, writes weekly reports, updates spreadsheets"
   - ❌ "Supports doc search, doc creation, doc writing"

5. **Differentiation > feature lists** — "Why better" matters 10x more than "what it does."
   - Pattern: [How others do it] → [What's wrong] → [How we do it] → [User-perceived benefit] → [One-line analogy]

6. **Audience adaptation** — Technical readers think "that's right"; non-technical readers think "I get it."

All principles written in English with bilingual (EN/ZH) examples and ✅/❌ contrasts.

### core/research-protocol.md — Research-Driven Protocol

Mandatory before writing. Three steps:

**Step 1: Audience Targeting**
- Who will read this? What's their technical level? In what context will they see it?
- If mixed audience: translate technical advantages into user-perceivable results (accuracy, cost, speed)

**Step 2: Exclusion Analysis**
- Who is excluded by existing solutions? Why? (Price? Platform lock-in? Technical barrier? Permissions?)
- How large is this excluded group? What workarounds do they use?
- How does our solution open the door?
- Excluded people = most eager potential users = strongest pain point angle

**Step 3: Deep Material Mining**
- Don't just read the README. Dig into implementation details, data, competitor comparisons.
- Find non-obvious advantages: what can't others do, or what do others do poorly?
- If search/crawl tools are available: actively use them to gather real data, latest stats, competitor info.
- If no tools: guide user to provide raw materials, then mine insights from what's given.
- Output: research summary + 1-2 killer data points that the entire piece will anchor on.

### core/humanizer.md — Anti-AI-Slop Protocol

Two levels:

**Level 1: Blacklist Interception (Hard Rules)**

Chinese blacklist:
- "随着...的发展", "众所周知", "在当今时代", "不言而喻", "总而言之"
- "强大的", "优秀的", "出色的", "赋能", "引领", "颠覆"
- Exclamation marks > 3 per piece

English blacklist:
- "In today's rapidly evolving...", "It's worth noting that...", "This powerful/robust solution..."
- "In conclusion", "Furthermore", "Moreover", "leverage", "utilize", "cutting-edge"
- "Excited to announce", "Game-changing", "Delve into"

Structural blacklist:
- Three-paragraph loop (point-expand-summarize repeated)
- Excessive dashes
- Vague attribution ("experts say", "studies show" without specifics)
- Perfect parallel lists (AI loves symmetry; humans don't)

**Level 2: Rhythm Reshaping (Soft Rules)**
- Sentence length variation: short sentences as backbone, occasional long for breathing room
- Conversational but not sloppy: "搞定" ✅ / "牛逼" ❌ / "get it done" ✅ / "frickin' awesome" ❌
- Rhetorical questions for rhythm
- Specific details over abstract generalizations ("Wednesday 3pm standup" > "in a meeting")
- Asymmetric structure (avoid AI's beloved perfectly balanced lists)
- Imperfect openings (start mid-thought occasionally, like humans do)

### core/review-protocol.md — Review Protocol

Mandatory after drafting. Three dimensions:

1. **Structural review** — Does it match the type template? Correct module order? Missing sections?
2. **Logic review** — Argument jumps? Data supports conclusions? Self-contradictions?
3. **Fact check** — Data sources reliable? Citations accurate? If search tools available, actively verify.

Output: numbered fix list. Each item fixed before proceeding to Humanize phase.

---

## Mode Modules

### modes/tech-article.md — Tech Product Articles

Inherited from great-writer v1. The most mature module.

**9-Module Structure:**
1. Title (must contain number + action/contrast, 15-25 chars ZH / 8-15 words EN)
2. TL;DR (one sentence: what + core advantage)
3. Pain point entry (data + consequence, ≤200 words)
4. Data comparison table (three-way, 🔴🟡🟢)
5. Architecture/principle (one analogy, ≤150 words)
6. Technical differentiation (others→problem→us→benefit→analogy pattern)
7. Feature panorama (grouped by scenario + examples)
8. Quick start (≤5 steps, copy-pasteable)
9. Closing (callback core data + CTA, rational and restrained)

**Length:** WeChat 1200-1800 chars / Tech blog 1500-2500 chars / Twitter thread 5-8 tweets

**Tone:** Pragmatic, rhythmic, conversational but not casual.

### modes/marketing-copy.md — Marketing Copy

Great-writer's "data-driven + anti-cliche" DNA applied to marketing formats.

**Sub-types:**

**Landing Page:**
1. Hero headline (one-sentence value prop with number or specific result)
2. Sub-headline (explains how, ≤20 words)
3. Pain → Solution pairs (3 groups, one sentence each)
4. Social proof (data/quotes/client logos)
5. Feature blocks (3-4, scenario-based not feature-based)
6. CTA (specific action verb, never "Learn more")

**Social Media Post:**
- Hook formula: [Data/counter-intuitive fact] + [one-sentence impact]
- Body: problem → solution → result, ≤200 words
- CTA: one clear action

**Ad Copy (AIDA variant):**
- Attention (data shock) → Interest (pain resonance) → Desire (scenario imagery) → Action (low-friction CTA)

**Length:** Landing page 500-800 words / Social post ≤200 words / Ad ≤100 words

**Tone:** More direct and urgent than tech articles. More rhetorical questions and contrasts. Ban empty buzzwords: "赋能/empowering", "引领/leading", "颠覆/disrupting".

### modes/research-report.md — Deep Content & Research Reports

Content Research Writer depth + great-writer readability. Core principle: **depth ≠ obscurity, rigor ≠ boring**.

**Structure:**
1. Executive Summary (≤300 words, conclusions first)
2. Background & Problem Definition (why research this? Market size/impact scope)
3. Methodology (data sources, analytical framework, limitations — honest and transparent)
4. Core Findings (3-5, each with: data + chart suggestion + one-sentence takeaway)
5. Competitive/Comparative Analysis (table + differentiation narrative)
6. Trends & Predictions (data-based extrapolation, confidence levels marked)
7. Recommendations/Action Items (specific, actionable, prioritized)
8. Appendix/References

**Length:** Whitepaper 3000-6000 words / Competitive report 1500-3000 words / Industry brief 800-1500 words

**Tone:** Authoritative but not pedantic. Data-dense but rhythmic. Every finding lands on "so what" — what it means for the reader.

**Special requirements:**
- Research phase enhanced: mandatory use of search tools (if available) for latest data
- Citations must include sources
- Data must have context ("grew 50%" is meaningless; "grew from 2M to 3M DAU" is meaningful)

### modes/xiaohongshu.md — Xiaohongshu / RED Notes

Platform-native writing for Xiaohongshu (小红书). Core principle: **有用 + 真实 + 好看**. The platform rewards genuinely helpful, personal-voice content with visual structure.

**Sub-types:**

**种草笔记 (Product Recommendation):**
1. Title: emoji-rich hook, ≤20 chars, must contain a number or strong claim. Formula: [emoji] + [result/claim] + [emoji]
   - ✅ "🔥 用了3个月，这个工具让我效率翻倍 💻"
   - ❌ "推荐一个好用的效率工具"
2. Opening hook: first-person experience or counter-intuitive fact (1-2 sentences)
3. Pain point (brief, relatable, "你是不是也..." pattern)
4. Product/solution intro (what it is, one sentence)
5. Core benefits (3-5 points, each as: emoji + bold keyword + one-sentence explanation)
6. Personal experience / proof (specific details: dates, numbers, before/after)
7. Practical tips (how to get the most out of it)
8. Tags: 5-10 relevant hashtags

**干货教程 (How-to / Tutorial):**
1. Title: [emoji] + "教你..." or "X个方法..." or "看完就会..." + [emoji]
2. Opening: establish credibility or promise outcome
3. Steps: numbered, each step = emoji + bold action + 1-2 sentence explanation
4. Common mistakes / pitfalls (optional, adds value)
5. Summary: bullet-point recap of key takeaways
6. Tags

**经验分享 (Experience / Story):**
1. Title: personal angle, emotional hook
2. Background: brief context (who you are, what happened)
3. Key learnings (3-5 points, structured)
4. Honest assessment (pros AND cons — authenticity is currency on RED)
5. Actionable takeaway for reader
6. Tags

**Formatting rules (platform-specific):**
- Emojis: mandatory, 1-2 per paragraph, used as visual anchors (not decoration)
- Paragraph length: 2-3 lines max, heavy line breaks for scanability
- Bold: use for key terms and takeaways
- Lists: numbered or emoji-bulleted, never wall-of-text
- Image notes: include `[配图建议: ...]` markers for each visual slot (cover + 2-6 content images)
- Total length: 300-800 chars for 种草, 500-1200 chars for 干货, 400-1000 chars for 经验

**Tone:**
- First-person, conversational, like telling a friend
- Genuine enthusiasm allowed (this is the one mode where energy is good), but never fake-hype
- "姐妹们" / "家人们" opening is OK if natural, but don't force it
- Specific > vague: "用了3个月" > "用了很久", "省了2000块" > "省了不少钱"
- Honest about limitations — RED users can smell ads instantly

**Anti-patterns (RED-specific):**
- No "随着...的发展" (instant unfollow)
- No obvious advertising tone ("本产品采用先进技术..." = death)
- No generic praise without specifics ("真的很好用" without saying WHY = zero engagement)
- No text-only posts without image guidance
- No clickbait that the content doesn't deliver on

**Humanizer override for this mode:**
- Emojis are ENCOURAGED (overrides the general restraint in other modes)
- More exclamation marks allowed (up to 5, vs 3 for other modes)
- Informal language / internet slang OK in moderation: "绝绝子", "yyds", "救命好用" — but only if contextually natural, never forced

### modes/technical-docs.md — Documentation & Technical Writing

Core principle: **Clarity > Completeness > Elegance**.

**Sub-types:**

**README:**
1. One sentence: what is this
2. Why you need it (what problem it solves)
3. Quick start (≤5 steps to working)
4. Core features (scenario-based, not API listing)
5. Installation/configuration
6. Contributing guide (optional)

**API Documentation:**
- Per endpoint: one-sentence description → request format → response format → example → error codes
- Examples must be copy-runnable

**Changelog:**
- Extracted from git history/PRs, noise filtered
- User perspective (not "refactored internal module" but "page load 40% faster")
- Categories: New / Improved / Fixed / Breaking

**Internal Docs / Guides:**
- Problem-driven: "Want to do X? Follow these steps"
- Decision records: Context → Options → Decision → Reasoning

**Tone:** Maximum clarity, zero ambiguity. Short sentences. Active voice. No "please note" filler — just state what to note.

---

## Compatibility

| Platform | Support Level |
|----------|-------------|
| Claude Code | Full — standard skill format, auto-loads sub-files |
| Codex / agentskills.io | Full — SKILL.md contains router + sub-file references |
| Other agents | Bundled mode — `great-writer-bundled.md` merges all modules into single file |

### Bundled Mode

A concatenation script (`scripts/bundle.sh`) produces `great-writer-bundled.md` by concatenating:
1. Router logic (from SKILL.md, with file-loading directives replaced by inline content)
2. All core modules (writing-dna → research-protocol → humanizer → review-protocol)
3. All mode modules (tech-article → marketing-copy → research-report → technical-docs)

Each section is separated by a clear `---` delimiter and header. The bundled file is regenerated on each release.

For agents that cannot load multiple files. Trade-off: larger context usage (~28KB vs ~12-14KB) but full functionality.

---

## File Inventory

| File | Purpose | Approx Size |
|------|---------|-------------|
| `SKILL.md` | Router, triggers, pipeline, tool declarations | ~3KB |
| `core/writing-dna.md` | 6 universal principles with bilingual examples | ~2KB |
| `core/research-protocol.md` | 3-step pre-writing research | ~2KB |
| `core/humanizer.md` | Blacklists + rhythm rules | ~2.5KB |
| `core/review-protocol.md` | 3-dimension review | ~1.5KB |
| `modes/tech-article.md` | 9-module structure + checklist | ~3KB |
| `modes/marketing-copy.md` | Landing/social/ad templates | ~2.5KB |
| `modes/research-report.md` | 8-section report structure | ~2.5KB |
| `modes/xiaohongshu.md` | 种草/干货/经验 templates | ~3KB |
| `modes/technical-docs.md` | README/API/Changelog/Guide templates | ~2.5KB |
| `README.md` | Chinese documentation | ~3KB |
| `README.en.md` | English documentation | ~3KB |
| **Total** | | **~31KB** |

Per-invocation context load: SKILL.md (~3KB) + relevant core modules (~6-8KB) + one mode (~2.5-3KB) = **~12-14KB** typical. Much lighter than loading a monolithic 31KB file every time.
