# Great Writer v2 Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace great-writer v1 (tech product articles only) with a universal, modular writing skill covering 5 writing types through a router + sub-skill architecture.

**Architecture:** Layered design — SKILL.md as router entry point, `core/` for shared capabilities (writing DNA, research protocol, humanizer, review protocol), `modes/` for type-specific templates (tech-article, marketing-copy, research-report, xiaohongshu, technical-docs). Each invocation loads only the relevant modules (~12-14KB vs ~31KB monolithic).

**Tech Stack:** Pure Markdown skill files. No runtime dependencies. Optional tool integration (Tavily, Firecrawl, WebSearch) declared but not required.

**Spec:** `docs/superpowers/specs/2026-03-28-great-writer-v2-design.md`

---

## File Structure

```
great-writer/
├── SKILL.md                          # Router + triggers + pipeline (REWRITE)
├── core/
│   ├── writing-dna.md                # CREATE — 6 universal principles
│   ├── research-protocol.md          # CREATE — 3-step pre-writing research
│   ├── humanizer.md                  # CREATE — anti-AI-slop rules
│   └── review-protocol.md            # CREATE — 3-dimension review
├── modes/
│   ├── tech-article.md               # CREATE — from v1 SKILL.md extraction
│   ├── marketing-copy.md             # CREATE — landing/social/ad
│   ├── research-report.md            # CREATE — whitepaper/competitive/brief
│   ├── xiaohongshu.md                # CREATE — 种草/干货/经验
│   └── technical-docs.md             # CREATE — README/API/changelog/guide
├── scripts/
│   └── bundle.sh                     # CREATE — concatenate into single file
├── great-writer-bundled.md           # GENERATED — single-file version
├── README.md                         # REWRITE
├── README.en.md                      # REWRITE
└── LICENSE                           # KEEP
```

## Task Dependencies

```
Task 1 (setup)
  ├→ Task 2 (writing-dna)
  ├→ Task 3 (research-protocol)
  ├→ Task 4 (humanizer)
  └→ Task 5 (review-protocol)
       ├→ Task 6 (tech-article)      ← parallelizable
       ├→ Task 7 (marketing-copy)    ← parallelizable
       ├→ Task 8 (research-report)   ← parallelizable
       ├→ Task 9 (xiaohongshu)       ← parallelizable
       └→ Task 10 (technical-docs)   ← parallelizable
            └→ Task 11 (SKILL.md router)
                 ├→ Task 12 (READMEs)
                 ├→ Task 13 (bundle script)
                 └→ Task 14 (verification)
```

Tasks 6-10 are fully independent and can be dispatched in parallel.

---

### Task 1: Project Setup

**Files:**
- Create: `core/` directory
- Create: `modes/` directory
- Create: `scripts/` directory
- Backup: current `SKILL.md` → `SKILL.v1.md` (temporary reference)

- [ ] **Step 1: Create directory structure**

```bash
cd /Users/admin/Documents/AI/skills/great-writer
mkdir -p core modes scripts
```

- [ ] **Step 2: Backup v1 SKILL.md for reference during implementation**

```bash
cp SKILL.md SKILL.v1.md
```

- [ ] **Step 3: Commit setup**

```bash
git add core/ modes/ scripts/ SKILL.v1.md
git commit -m "chore: create v2 directory structure, backup v1 SKILL.md"
```

---

### Task 2: core/writing-dna.md — Universal Writing Principles

**Files:**
- Create: `core/writing-dna.md`

This is the foundation layer. All modes inherit these 6 principles. Written in English with bilingual examples.

- [ ] **Step 1: Write core/writing-dna.md**

```markdown
# Writing DNA — Universal Principles

These six principles apply to ALL writing types. Every mode inherits them.
The agent MUST internalize these before drafting.

---

## Principle 1: Data as Anchors

Every piece of writing must have 1-2 quantifiable "killer data points" — numbers the reader will remember and retell. Reject vague adjectives.

**Rule:** If you can't put a number on it, find one or don't claim it.

| Do | Don't |
|----|-------|
| "Cut 96% of tokens" | "Significantly improved efficiency" |
| "25x cost difference" | "Much more affordable" |
| "550 vs 14,000 tokens" | "Greatly reduced resource usage" |
| "3 minutes to deploy" | "Quick and easy setup" |
| 省下 96% Token | 大幅提升效率 |
| 25 倍差距 | 便宜很多 |
| 从 2M 涨到 3M DAU | 用户增长了很多 |

**Anchor placement:** Title, TL;DR, comparison table, closing. Repeat the same core number at least 3 times throughout the piece.

---

## Principle 2: Pain/Problem First

The first paragraph enters the reader's pain. No warmup. No preamble. No context-setting.

**Opening formula:** [Pain data] + [Consequence the reader feels]

| Do | Don't |
|----|-------|
| "Your server bill tripled last month. Not because traffic grew — because you're paying for idle compute." | "With the rapid development of cloud computing, costs have become an important consideration for businesses..." |
| "14,000 tokens of context — gone. Just to load the tool list." | "As AI agents become more sophisticated, context management has become increasingly important..." |
| 你的 Agent 接入飞书后，14,000 Token 的上下文就这么没了。 | 随着 AI 技术的快速发展，飞书作为一款... |
| 上个月你的服务器账单涨了 3 倍。不是流量涨了——是你在为空转算力买单。 | 在当今云计算蓬勃发展的时代... |

---

## Principle 3: Analogy Over Explanation

One good analogy beats three paragraphs of technical description. Analogies compress complexity into something the reader already understands.

**Rule:** Before writing a technical explanation, try to find an analogy first. If the analogy works, delete the explanation.

| Do | Don't |
|----|-------|
| "MCP is carrying a 1,350-piece toolbox out the door. Skills is a pocket handbook." | "MCP protocol requires injecting all tool JSON schemas into the LLM context at startup, which consumes significant token budget..." |
| "Screenshot-based navigation is blindfolded screen-poking. Element labeling is giving every button a number tag." | "Our approach assigns unique identifiers to interactive elements rather than relying on coordinate-based interaction derived from visual processing..." |
| MCP 是背着 1350 件套工具箱出门，Skill 是揣一本口袋手册。 | MCP 协议要求在启动时将所有工具的 JSON Schema 注入到上下文中... |

---

## Principle 4: Scenario-Based Presentation

Features are not "we support X" — they are "you can do Y with it." Group capabilities by use case, not by technical category.

| Do | Don't |
|----|-------|
| "AI auto-searches docs, writes weekly reports, updates spreadsheets, creates approval forms" | "Supports document search, document creation, document writing, form generation" |
| 🔄 办公自动化：AI 自动搜文档、写周报、更新表格、创建审批单 | 支持文档搜索、文档创建、文档写入、表单生成 |

**Rule:** Each feature group gets a scenario label and ends with a concrete example:
`🎯 Scenario: "Monday morning — you open Slack and your weekly report is already drafted, with data pulled from the last 5 days of JIRA tickets."`

---

## Principle 5: Differentiation > Feature Lists

Listing features is the weakest form of persuasion. Readers don't care that you "support X" — they care WHY your way is better.

**Differentiation pattern (use for every key feature):**

```
[How others do it]
  → [What's wrong with that]
    → [How we do it]
      → [User-perceived benefit]
        → [One-line analogy]
```

**Example:**

| Don't | Do |
|-------|-----|
| "Supports element annotation and screenshot features" | "Most solutions screenshot the page and let the AI guess coordinates — 50KB token burn, still clicks the wrong button half the time. We label every element with a number. AI reports the number, done — 2KB tokens, 100% accuracy. Screenshot guessing is blindfolded screen-poking; element labeling is giving buttons name tags." |

**Rules:**
- If a feature "others also have" → don't write "we also have it"; write "we do it differently"
- If you can't find a differentiator → the feature isn't worth a standalone section; fold it into a scenario example
- Technical advantages MUST translate to user-perceivable results: faster, cheaper, more accurate, more reliable

---

## Principle 6: Audience Adaptation

Technical readers should think "that's accurate." Non-technical readers should think "I get it."

**Rule:** Use user-perceivable outcomes (accuracy, cost, speed, reliability) to bridge the gap. Implementation details are for the appendix, not the lead.

**Mixed audience strategy:**
- Lead with the outcome: "40% faster page loads"
- Follow with the mechanism (one sentence): "by lazy-loading below-the-fold images"
- Link to the deep dive: "See Architecture section for implementation details"

This applies to all writing types. A research report still needs accessible executive summaries. A README still needs to tell users WHY before HOW.
```

- [ ] **Step 2: Verify file covers all 6 principles from spec**

Checklist:
- Data as anchors ✓
- Pain/problem first ✓
- Analogy over explanation ✓
- Scenario-based presentation ✓
- Differentiation > feature lists ✓
- Audience adaptation ✓
- Bilingual examples in all principles ✓

- [ ] **Step 3: Commit**

```bash
git add core/writing-dna.md
git commit -m "feat: add core/writing-dna.md — 6 universal writing principles"
```

---

### Task 3: core/research-protocol.md — Pre-Writing Research

**Files:**
- Create: `core/research-protocol.md`

Mandatory pre-writing protocol. Three steps + tool integration logic.

- [ ] **Step 1: Write core/research-protocol.md**

```markdown
# Research Protocol — Pre-Writing Research

This protocol is MANDATORY before any writing begins. No research, no writing.
The agent MUST complete all three steps before moving to the Draft phase.

---

## Why This Exists

Most AI writing fails not because of bad prose, but because of thin content. The agent writes from its training data or a brief user prompt, producing generic text that could describe any product. Research forces the agent to find specific, non-obvious material that makes the writing worth reading.

---

## Step 1: Audience Targeting

Before anything else, answer these questions explicitly. Do not assume.

**Required answers:**
1. **Who will read this?** (developers? product managers? executives? mixed?)
2. **What is their technical level?** (can read code? understands concepts? needs everything explained?)
3. **In what context will they encounter this?** (WeChat feed? HN front page? search result? forwarded by colleague? 小红书推荐流?)

**If mixed audience:** Use user-perceivable outcomes (accuracy, cost, speed) to translate technical advantages. Technical people see it and think "that's right." Non-technical people see it and think "I get it."

**Output:** 2-3 sentences defining the target reader persona.

---

## Step 2: Exclusion Analysis

Existing solutions always leave someone out. Find those people — they are your most powerful angle.

**Required answers:**
1. **Who is excluded by current solutions?** (price? platform lock-in? technical barrier? permissions? language? region?)
2. **How large is this excluded group?** (rough estimate)
3. **What workarounds do they currently use?** (manual process? inferior alternative? nothing?)
4. **How does our solution open the door for them?**

**Why this matters:** Excluded people = most eager potential users = most compelling pain point.

```
❌ Weak: "AI browser plugins aren't flexible enough" (too vague, anyone could say this)
✅ Strong: "Official plugins require a subscription; third-party API users are completely locked out" (specific group, specific reason)

❌ 弱: "AI 浏览器插件操作不够灵活"（太泛）
✅ 强: "官方插件绑定订阅，第三方 API 用户全被挡在门外"（有人群、有原因）
```

**Output:** 2-3 sentences describing the excluded group and the opportunity angle.

---

## Step 3: Deep Material Mining

Do NOT start writing after reading just the README or user prompt. Dig deeper.

**Required actions:**
1. **Study implementation details** — architecture, design decisions, technical trade-offs
2. **Find competitive differences** — how do others solve the same problem? What's different here?
3. **Extract killer data** — performance numbers, cost comparisons, accuracy metrics, user counts
4. **Identify non-obvious advantages** — things that look similar on the surface but work completely differently underneath

**If search/crawl tools are available** (Tavily, WebSearch, Firecrawl, Jina, etc.):
- Actively search for competitor products, pricing, benchmarks
- Fetch recent articles, reviews, or discussions about the topic
- Verify any claims or data points the user provided
- Look for the latest stats and market data

**If no search tools are available:**
- Ask the user to provide raw materials: docs, competitor links, data
- Mine insights from whatever materials are given
- Flag any claims that need external verification: `[⚠️ Needs verification: ...]`

**Output:** Research summary containing:
- Target audience definition (from Step 1)
- Exclusion analysis angle (from Step 2)
- 1-2 killer data points the entire piece will anchor on
- 3-5 key differentiators or insights
- List of sources/materials reviewed

---

## Protocol Enforcement

The agent MUST produce the Research Summary output before proceeding to the Draft phase. If the user says "just write it" or "skip research," the agent should:

1. Acknowledge the request
2. Explain briefly: "Research prevents generic output — 2 minutes of research saves 20 minutes of rewrites"
3. Offer a compromise: "I'll do a quick version — 3 targeted questions instead of the full protocol"
4. If the user still insists: proceed, but mark the draft as `[⚠️ Written without research — quality may vary]`
```

- [ ] **Step 2: Verify against spec**

Checklist:
- Audience targeting ✓
- Exclusion analysis ✓
- Deep material mining ✓
- Tool integration (search/crawl) with degraded behavior ✓
- Research summary output format ✓
- Enforcement mechanism ✓

- [ ] **Step 3: Commit**

```bash
git add core/research-protocol.md
git commit -m "feat: add core/research-protocol.md — mandatory pre-writing research"
```

---

### Task 4: core/humanizer.md — Anti-AI-Slop Protocol

**Files:**
- Create: `core/humanizer.md`

Two-level system: hard blacklist + soft rhythm reshaping. Bilingual rules.

- [ ] **Step 1: Write core/humanizer.md**

```markdown
# Humanizer — Anti-AI-Slop Protocol

This protocol eliminates AI writing patterns that make text feel machine-generated.
Applied in Phase 4 of the pipeline, after drafting and review.

Two levels: Level 1 catches obvious AI tells. Level 2 reshapes rhythm and structure.

---

## Level 1: Blacklist Interception (Hard Rules)

If ANY of these patterns appear in the draft, they MUST be rewritten. No exceptions.

### Chinese Blacklist

**Banned phrases:**
- 随着...的发展 / 随着...的兴起 / 随着...的普及
- 众所周知
- 在当今时代 / 在当今社会
- 不言而喻
- 总而言之 / 综上所述
- 值得一提的是
- 毋庸置疑

**Banned adjectives (when used without supporting data):**
- 强大的、优秀的、出色的、卓越的
- 创新的、领先的、前沿的
- 赋能、引领、颠覆、革命性的
- 无缝的、全方位的、一站式的

**Banned structures:**
- Opening with context-setting ("随着 AI 技术的发展...")
- Closing with empty call-to-action ("让我们拭目以待")
- Exclamation marks > 3 per piece (exception: xiaohongshu mode allows up to 5)

### English Blacklist

**Banned phrases:**
- "In today's rapidly evolving..."
- "It's worth noting that..." / "It's important to note..."
- "In conclusion" / "To summarize" / "In summary"
- "Furthermore" / "Moreover" / "Additionally" (as paragraph openers)
- "Excited to announce" / "Thrilled to share"
- "Game-changing" / "Groundbreaking" / "Revolutionary"
- "Delve into" / "Dive deep into"
- "Leverage" / "Utilize" (use "use")
- "Cutting-edge" / "State-of-the-art" / "Best-in-class"
- "Robust" / "Seamless" / "Comprehensive" / "Holistic"
- "It goes without saying"
- "At the end of the day"

**Banned structures:**
- Three-paragraph loop: [point] → [expand] → [summarize], repeated
- Perfect parallel structure in every list (AI loves symmetry; humans don't)
- Excessive em-dashes (more than 2 per 500 words)
- Every paragraph starting with a transition word
- Vague attribution: "experts say," "studies show," "research indicates" (without citing which)

---

## Level 2: Rhythm Reshaping (Soft Rules)

These are guidelines, not hard bans. The goal is text that FEELS human-written.

### Sentence Length Variation

Short sentences carry the backbone. Long sentences appear occasionally for breathing room.

```
❌ AI pattern: Every sentence is 15-25 words. Uniform. Predictable. Monotonous.

✅ Human pattern: Short punch. Then a longer sentence that unwinds a bit,
   adds context, takes its time. Then short again. Varies.
```

**Target:** Mix of 5-word punches, 10-15 word workhorses, and occasional 25+ word breathers. No three consecutive sentences of similar length.

### Conversational Tone (Calibrated by Mode)

| Register | Example (EN) | Example (ZH) | Used In |
|----------|-------------|---------------|---------|
| Professional-casual | "get it done" ✅ / "frickin' awesome" ❌ | "搞定" ✅ / "牛逼" ❌ | tech-article, marketing |
| Authoritative-accessible | "the data tells a clear story" ✅ | "数据说明了一切" ✅ | research-report |
| Friendly-personal | "trust me on this one" ✅ | "姐妹们听我说" ✅ | xiaohongshu |
| Precise-minimal | "Returns 404 if not found." ✅ | "未找到时返回 404。" ✅ | technical-docs |

### Rhetorical Questions

Use sparingly to create rhythm and engage the reader. 1-2 per piece for most types.

```
✅ "You'd pay 25x more for tools you'll never use?"
✅ 你愿意为了用不到的工具付出 25 倍代价吗？

❌ Don't chain multiple rhetorical questions (AI pattern)
❌ Don't use rhetorical questions as section openers (overused)
```

### Specific Details Over Abstractions

Replace every vague reference with a concrete one.

```
❌ "in a recent meeting" → ✅ "in last Wednesday's 3pm standup"
❌ "a significant number of users" → ✅ "2,847 users in the first week"
❌ "很多用户反馈" → ✅ "上线第一周 2,847 个用户"
❌ "在一次会议中" → ✅ "上周三下午 3 点的站会上"
```

### Asymmetric Structure

AI loves perfectly balanced lists (3 items, each 2 sentences). Humans don't write that way.

- Some bullet points are one word
- Others might ramble a bit, adding a secondary thought that the writer couldn't resist including, because that's how people actually think — in messy, uneven chunks
- Medium length here

### Imperfect Openings

Occasionally start mid-thought, the way humans do in conversation.

```
✅ "So here's the thing about context windows..."
✅ "14,000 tokens. Gone. Just to load the tool list."
✅ 14,000 Token。没了。就为了加载工具列表。
```

---

## Mode-Specific Overrides

Some modes override the default humanizer settings:

| Mode | Override |
|------|----------|
| xiaohongshu | Emojis ENCOURAGED. Exclamation marks up to 5. Internet slang OK in moderation (绝绝子, yyds). |
| technical-docs | Stricter: no rhetorical questions, no conversational asides, no emojis. Pure clarity. |
| marketing-copy | More urgency allowed. Sentence fragments OK for impact. |
| research-report | More formal. Data precision paramount. No sentence fragments. |
| tech-article | Default settings — balanced rhythm, moderate casualness. |

---

## Application Checklist

After humanizing, verify:

- [ ] Zero blacklisted phrases remain (search for them)
- [ ] No three consecutive sentences of similar length
- [ ] At least one rhetorical question (except technical-docs)
- [ ] Specific numbers/details replace all vague references
- [ ] Lists are not all perfectly parallel
- [ ] Opening doesn't set context — it enters the topic directly
- [ ] Closing doesn't summarize what was just said
```

- [ ] **Step 2: Verify against spec**

Checklist:
- Chinese blacklist ✓
- English blacklist ✓
- Structural blacklist ✓
- Sentence length variation ✓
- Conversational tone calibration ✓
- Rhetorical questions ✓
- Specific details ✓
- Asymmetric structure ✓
- Imperfect openings ✓
- Mode-specific overrides (xiaohongshu, technical-docs) ✓
- Application checklist ✓

- [ ] **Step 3: Commit**

```bash
git add core/humanizer.md
git commit -m "feat: add core/humanizer.md — anti-AI-slop protocol with bilingual blacklists"
```

---

### Task 5: core/review-protocol.md — Post-Draft Review

**Files:**
- Create: `core/review-protocol.md`

Three-dimension review: structural, logical, factual.

- [ ] **Step 1: Write core/review-protocol.md**

```markdown
# Review Protocol — Post-Draft Review

This protocol is MANDATORY after drafting and before humanizing.
The agent runs all three review dimensions and produces a numbered fix list.
ALL fixes must be applied before proceeding to the Humanize phase.

---

## Dimension 1: Structural Review

Check the draft against the mode's template structure.

**For each section in the mode template, verify:**
1. Is the section present? If missing, add it.
2. Is it in the correct order? If not, reorder.
3. Does it meet the length guidelines? If too long, cut. If too short, expand.
4. Does it follow the format requirements? (e.g., comparison table must exist for tech-article)

**Common structural issues:**
- Missing TL;DR or executive summary
- Pain point section buried after a context-setting intro (move it up)
- Feature list instead of scenario-grouped capabilities
- Missing CTA in closing
- No data comparison table when one is required

---

## Dimension 2: Logic Review

Check the argument flow for coherence and persuasion.

**Verify:**
1. **No argument jumps** — Does each section logically follow from the previous? Would a reader ask "wait, why?" at any transition?
2. **Data supports claims** — Every claim is backed by a specific number, example, or source. Flag any unsupported claims: `[⚠️ Unsupported: ...]`
3. **No self-contradictions** — Does the piece claim something in paragraph 3 that conflicts with paragraph 7?
4. **"So what?" test** — For each finding or feature, is it clear why the reader should care? If not, add the implication.
5. **Differentiation holds** — If the piece claims "we're better because X," verify X is actually different from competitors, not just described differently.

**Common logic issues:**
- Claiming "faster" without benchmark data
- Pain point doesn't connect to the solution presented
- Features listed without explaining WHY they matter
- Competitor comparison that's not actually fair (comparing free tier to paid tier)

---

## Dimension 3: Fact Check

Verify accuracy of all data and claims.

**Required checks:**
1. **Numbers are accurate** — Do the math. "96% reduction" means going from X to 0.04X. Is that what the data shows?
2. **Citations are real** — If a source is cited, it should exist. If search tools are available, verify URLs and claims.
3. **Dates are current** — No "as of 2024" in a 2026 article unless discussing historical context.
4. **Names and terms are correct** — Product names, company names, technical terms spelled correctly.
5. **Comparisons are fair** — Same tier, same use case, same conditions.

**If search tools are available:**
- Actively verify key claims against live sources
- Check if cited products/features still exist
- Confirm pricing and performance numbers are current

**If no search tools:**
- Flag unverifiable claims: `[⚠️ Needs verification: claim about X]`
- Ask the user to confirm critical data points

---

## Output Format

After reviewing all three dimensions, produce a numbered fix list:

```
## Review Findings

### Must Fix
1. [Structural] Missing comparison table in Section 4. Add three-way comparison.
2. [Logic] Paragraph 5 claims "10x faster" but no benchmark data provided. Add source or remove claim.
3. [Fact] Competitor pricing listed as $99/mo — verify this is current.

### Should Fix
4. [Structural] Quick-start section has 7 steps — reduce to 5 or fewer.
5. [Logic] Transition from pain point to solution is abrupt. Add one bridging sentence.

### Nice to Fix
6. [Structural] Feature group 3 only has 2 items — consider merging with group 2.
```

**Rule:** ALL "Must Fix" items are resolved before proceeding. "Should Fix" items are resolved unless the user overrides. "Nice to Fix" items are optional.
```

- [ ] **Step 2: Verify against spec**

Checklist:
- Structural review ✓
- Logic review ✓
- Fact check ✓
- Tool integration for verification ✓
- Numbered fix list output format ✓
- Fix priority levels ✓

- [ ] **Step 3: Commit**

```bash
git add core/review-protocol.md
git commit -m "feat: add core/review-protocol.md — 3-dimension post-draft review"
```

---

### Task 6: modes/tech-article.md — Tech Product Articles

**Files:**
- Create: `modes/tech-article.md`
- Reference: `SKILL.v1.md` (extract and refine from v1)

This is the most mature mode — directly evolved from great-writer v1. Extract the 9-module structure, tone rules, and checklists. Remove anything that now lives in `core/` (writing principles, research protocol, general humanizer rules). Keep only what's tech-article-specific.

- [ ] **Step 1: Write modes/tech-article.md**

Extract from v1 SKILL.md: the 9-module structure template, tech-article-specific tone rules, length guidelines, and self-check checklist. Remove all content that now lives in core/ (the 5 core principles, general writing rules, research steps, humanizer blacklists). What remains is the TYPE-SPECIFIC template.

The file should contain:
- Header: mode name, description, when this mode is activated
- 9-module structure template with format rules for each module (title formula, TL;DR format, pain point constraints, data table format, architecture analogy constraints, differentiation pattern, feature panorama grouping rules, quick-start constraints, closing formula)
- Length guidelines per platform: WeChat 1200-1800 chars, tech blog 1500-2500 chars, Twitter thread 5-8 tweets (<100 chars each)
- Tone rules specific to tech articles (pragmatic, rhythmic, conversational but not casual)
- Self-check checklist (10+ items from v1 spec, both basic and advanced checks)
- Each module section should include ✅/❌ examples from v1

Key content to port from v1:
- Title formula: `[数据冲击] + [动作/方法]`, 15-25 chars, must contain number
- Module 5.5 technical differentiation: `别人怎么做 → 问题 → 我们怎么做 → 用户好处 → 类比`
- Module 6 feature panorama: grouped by scenario with `🎯 场景示例` markers
- Module 8 quick start: ≤5 steps, code blocks, copy-pasteable, 0 to running in 3 minutes
- All ✅/❌ examples from v1 for each module

- [ ] **Step 2: Verify no duplication with core/**

Check that tech-article.md does NOT contain:
- General writing principles (→ core/writing-dna.md)
- Research protocol steps (→ core/research-protocol.md)
- AI blacklist phrases (→ core/humanizer.md)
- Review dimensions (→ core/review-protocol.md)

- [ ] **Step 3: Commit**

```bash
git add modes/tech-article.md
git commit -m "feat: add modes/tech-article.md — 9-module tech product article template"
```

---

### Task 7: modes/marketing-copy.md — Marketing Copy

**Files:**
- Create: `modes/marketing-copy.md`

Three sub-types: landing page, social media post, ad copy. Data-driven + anti-cliche DNA from great-writer applied to marketing formats.

- [ ] **Step 1: Write modes/marketing-copy.md**

The file should contain:
- Header: mode name, description, when this mode is activated
- Three sub-type templates:

**Landing Page template (6 sections):**
1. Hero headline: one-sentence value prop with number or specific result. Formula: `[Specific outcome] + [How/in what timeframe]`
   - ✅ "Cut your API costs by 80% — in one line of code"
   - ❌ "The powerful solution for your API needs"
2. Sub-headline: explains the how, ≤20 words
3. Pain → Solution pairs: 3 groups, each one sentence, side by side
4. Social proof: data points, user quotes, or client logos
5. Feature blocks: 3-4, scenario-based (what you can DO, not what the product HAS)
6. CTA: specific action verb. Never "Learn more" / "Get started" / "了解更多". Use "Start free trial" / "See pricing" / "Deploy in 3 minutes" / "立即部署" / "查看定价"

**Social Media Post template:**
- Hook formula: `[Data or counter-intuitive fact] + [One-sentence impact]`
- Body: problem → solution → result, ≤200 words
- CTA: one clear, specific action
- Platform-specific length: Twitter ≤280 chars, LinkedIn ≤300 words, WeChat Moments ≤200 chars

**Ad Copy template (AIDA variant):**
- Attention: data shock or surprising claim (1 sentence)
- Interest: pain resonance — reader recognizes their problem (1-2 sentences)
- Desire: scenario imagery — reader imagines the outcome (1-2 sentences)
- Action: low-friction CTA with specific next step (1 sentence)
- Total: ≤100 words

- Length guidelines per sub-type
- Tone: more direct and urgent than tech articles, more rhetorical questions and contrasts, ban "赋能/empowering", "引领/leading", "颠覆/disrupting"
- Self-check checklist specific to marketing copy

Each sub-type section must include ✅/❌ bilingual examples.

- [ ] **Step 2: Commit**

```bash
git add modes/marketing-copy.md
git commit -m "feat: add modes/marketing-copy.md — landing page, social, and ad templates"
```

---

### Task 8: modes/research-report.md — Deep Content & Research Reports

**Files:**
- Create: `modes/research-report.md`

8-section structure. Depth + readability. Enforced source citation.

- [ ] **Step 1: Write modes/research-report.md**

The file should contain:
- Header: mode name, description, when this mode is activated
- 8-section structure template:

1. **Executive Summary** (≤300 words, conclusions first, key numbers up front)
   - Formula: [Main finding] + [Key data] + [Top recommendation]
   - This section must be readable as a standalone brief
2. **Background & Problem Definition** (why research this? market size, impact scope, urgency)
   - Must answer: "Why should anyone care about this topic right now?"
3. **Methodology** (data sources, analytical framework, time period, limitations)
   - Honesty is mandatory: state what data you DIDN'T have access to
4. **Core Findings** (3-5 findings, each with: data + visualization suggestion + one-sentence takeaway)
   - Each finding must end with a "So what?" line — what it means for the reader
   - Data must have context: "grew 50%" → "grew from 2M to 3M DAU between Q1 and Q3 2026"
5. **Competitive/Comparative Analysis** (table + narrative)
   - Table: structured comparison across defined dimensions
   - Narrative: explains WHY the differences matter, not just WHAT they are
6. **Trends & Predictions** (data-based extrapolation)
   - Each prediction must state confidence level: High/Medium/Low
   - Base predictions on data shown in Findings, not speculation
7. **Recommendations/Action Items** (specific, actionable, prioritized)
   - Each recommendation: [Action] + [Expected impact] + [Effort level]
8. **Appendix/References** (sources, methodology details, raw data links)

- Length guidelines: whitepaper 3000-6000 words, competitive report 1500-3000 words, industry brief 800-1500 words
- Tone: authoritative but not pedantic, data-dense but rhythmic, every finding lands on "so what"
- Special requirement: research phase enhanced — mandatory search tool usage if available
- Citation format: inline `[Source: Name, Date]` with full references in appendix
- Self-check checklist specific to research reports

- [ ] **Step 2: Commit**

```bash
git add modes/research-report.md
git commit -m "feat: add modes/research-report.md — 8-section deep content template"
```

---

### Task 9: modes/xiaohongshu.md — Xiaohongshu / RED Notes

**Files:**
- Create: `modes/xiaohongshu.md`

Platform-native writing for 小红书. Three sub-types: 种草, 干货教程, 经验分享.

- [ ] **Step 1: Write modes/xiaohongshu.md**

The file should contain:
- Header: mode name, description, when this mode is activated
- Humanizer override declaration: emojis encouraged, exclamation marks up to 5, internet slang OK in moderation
- Three sub-type templates:

**种草笔记 (Product Recommendation):**
1. Title: emoji-rich hook, ≤20 chars. Formula: `[emoji] + [result/claim] + [emoji]`
   - ✅ "🔥 用了3个月，这个工具让我效率翻倍 💻"
   - ❌ "推荐一个好用的效率工具"
2. Opening hook: first-person experience or counter-intuitive fact (1-2 sentences)
3. Pain point: brief, relatable. Pattern: "你是不是也..." or "每次...是不是都..."
4. Product/solution intro: what it is (one sentence, no jargon)
5. Core benefits: 3-5 points, each as `emoji + **bold keyword** + one-sentence explanation`
6. Personal experience/proof: specific details (dates, numbers, before/after)
7. Practical tips: how to get the most out of it (2-3 tips)
8. Tags: 5-10 relevant hashtags. Mix popular + niche.

**干货教程 (How-to / Tutorial):**
1. Title: `[emoji] + "教你..." or "X个方法..." or "看完就会..." + [emoji]`
2. Opening: establish credibility or promise outcome (1-2 sentences)
3. Steps: numbered, each = `emoji + **bold action** + 1-2 sentence explanation`
4. Common mistakes/pitfalls (optional but adds value and engagement)
5. Summary: bullet-point recap of key takeaways
6. Tags

**经验分享 (Experience / Story):**
1. Title: personal angle, emotional hook
2. Background: brief context (who you are, what happened, 1-2 sentences)
3. Key learnings: 3-5 points, structured
4. Honest assessment: pros AND cons (authenticity is currency on RED)
5. Actionable takeaway for reader
6. Tags

- Formatting rules:
  - Emojis: mandatory, 1-2 per paragraph, as visual anchors not decoration
  - Paragraph length: 2-3 lines max, heavy line breaks for scanability
  - Bold: key terms and takeaways
  - Lists: numbered or emoji-bulleted, never wall-of-text
  - Image notes: `[配图建议: ...]` markers for cover + 2-6 content images
- Length: 种草 300-800 chars, 干货 500-1200 chars, 经验 400-1000 chars
- Tone: first-person, conversational, like telling a friend. "姐妹们"/"家人们" OK if natural.
- Specificity rule: "用了3个月" > "用了很久", "省了2000块" > "省了不少钱"
- Anti-patterns: no 随着 (instant unfollow), no ad tone ("本产品采用先进技术" = death), no generic praise without specifics, no text without image guidance, no undelivered clickbait
- Self-check checklist specific to xiaohongshu

- [ ] **Step 2: Commit**

```bash
git add modes/xiaohongshu.md
git commit -m "feat: add modes/xiaohongshu.md — 种草/干货/经验 templates for RED"
```

---

### Task 10: modes/technical-docs.md — Documentation & Technical Writing

**Files:**
- Create: `modes/technical-docs.md`

Four sub-types: README, API docs, changelog, internal docs/guides. Clarity above all.

- [ ] **Step 1: Write modes/technical-docs.md**

The file should contain:
- Header: mode name, description, when this mode is activated
- Humanizer override: no rhetorical questions, no conversational asides, no emojis, pure clarity
- Core principle: **Clarity > Completeness > Elegance**
- Four sub-type templates:

**README:**
1. One sentence: what is this (no marketing, no adjectives)
2. Why you need it: what problem it solves (2-3 sentences, user perspective)
3. Quick start: ≤5 steps from zero to working, all commands copy-pasteable
4. Core features: scenario-based ("You can..." not "Supports..."), 4-6 items
5. Installation/configuration: platform-specific tabs if needed
6. Contributing guide: optional, link to CONTRIBUTING.md

**API Documentation (per endpoint):**
- One-sentence description of what this endpoint does
- Request format: method, URL, headers, body (with types)
- Response format: status codes, body schema, example
- Example: complete, copy-runnable `curl` or code snippet
- Error codes: table of possible errors with descriptions
- Rule: examples MUST be tested and runnable. Never show a 404 URL or wrong payload.

**Changelog:**
- Input: git history, PRs, release notes
- Noise filter: skip "fix typo", "update deps", merge commits
- User perspective: not "refactored internal module" but "page load 40% faster"
- Categories: **New** (wholly new features), **Improved** (enhanced existing), **Fixed** (bugs), **Breaking** (requires action)
- Format: `- **Category:** Description (PR #123)` or `- **类别：** 描述`
- Each entry: one sentence, user-perceivable impact

**Internal Docs / Guides:**
- Problem-driven structure: "Want to do X? Follow these steps:"
- Decision records: Context → Options considered → Decision → Reasoning
- Each guide answers ONE question. If it answers two, split it.
- Link to related guides, don't duplicate content

- Tone: maximum clarity, zero ambiguity, short sentences, active voice, no filler ("please note" → just state it, "it should be noted that" → delete)
- Self-check checklist specific to technical docs

- [ ] **Step 2: Commit**

```bash
git add modes/technical-docs.md
git commit -m "feat: add modes/technical-docs.md — README/API/changelog/guide templates"
```

---

### Task 11: SKILL.md — Router Entry Point

**Files:**
- Rewrite: `SKILL.md`

This is the main entry point. Contains frontmatter, routing logic, pipeline definition, tool declarations, and phase-jump commands. References sub-files via Read directives.

- [ ] **Step 1: Write the new SKILL.md**

The file must contain:

**Frontmatter:**
```yaml
---
name: great-writer
description: >
  Universal writing skill for AI agents. Covers tech articles, marketing copy,
  research reports, Xiaohongshu notes, and technical docs. Research-driven,
  full-pipeline, anti-AI-slop. Bilingual (EN/ZH).
triggers:
  # Chinese
  - 写文章
  - 公众号
  - 博客
  - 技术博客
  - 产品介绍
  - 产品文案
  - 推广文
  - 发布文
  - 文案
  - 白皮书
  - 研究报告
  - 竞品分析
  - 行业分析
  - 投研
  - 技术文档
  - 内部文档
  - 小红书
  - 种草
  - 笔记
  # English
  - write article
  - blog post
  - product article
  - marketing copy
  - landing page
  - ad copy
  - social media post
  - whitepaper
  - research report
  - competitive analysis
  - industry report
  - README
  - API docs
  - changelog
  - technical docs
  - internal guide
  - release notes
  - xiaohongshu
---
```

**Body structure:**
1. One-line description of the skill
2. Routing table: signal → mode file mapping (exactly as in spec)
3. Pipeline definition: 5 phases with Read directives for each sub-file
4. Phase-jump commands: user phrases that skip to a specific phase
5. Tool integration declarations: optional capabilities table
6. Sub-file loading instructions: explicit Read directives with relative paths

Key implementation detail: each phase instruction must tell the agent to read the relevant sub-file. Example:
```
## Phase 1: Research
Read the file `core/research-protocol.md` (relative to this skill's root directory) and follow its protocol completely. Do not proceed to Phase 2 until the Research Summary is produced.
```

- [ ] **Step 2: Verify routing covers all 5 modes**

- tech-article ✓
- marketing-copy ✓
- research-report ✓
- xiaohongshu ✓
- technical-docs ✓
- Ambiguous → ask user ✓

- [ ] **Step 3: Verify pipeline references all 4 core modules**

- core/writing-dna.md in Phase 2 ✓
- core/research-protocol.md in Phase 1 ✓
- core/humanizer.md in Phase 4 ✓
- core/review-protocol.md in Phase 3 ✓

- [ ] **Step 4: Commit**

```bash
git add SKILL.md
git commit -m "feat: rewrite SKILL.md as v2 router with 5-mode pipeline"
```

---

### Task 12: README.md + README.en.md

**Files:**
- Rewrite: `README.md` (Chinese)
- Rewrite: `README.en.md` (English)

Update both READMEs to reflect v2 architecture, all 5 writing types, installation for multiple platforms, and before/after examples.

- [ ] **Step 1: Rewrite README.md**

Structure:
- Project title + one-line description
- What problem it solves (before/after comparison, like v1 but expanded to show multiple modes)
- Architecture diagram (the layered file tree)
- 5 writing modes listed with one-line descriptions
- Core capabilities (3 pillars: research-driven, full-pipeline, anti-AI-slop)
- Installation: Claude Code (`ln -sf`), Codex (agentskills.io format), other agents (single-file bundled version)
- Usage examples: one trigger example per mode
- Compatibility table
- License

- [ ] **Step 2: Rewrite README.en.md**

Same structure as README.md but in English. Not a word-for-word translation — adapt naturally.

- [ ] **Step 3: Commit**

```bash
git add README.md README.en.md
git commit -m "docs: rewrite READMEs for v2 — 5 modes, layered architecture, bilingual"
```

---

### Task 13: Bundle Script + Bundled Output

**Files:**
- Create: `scripts/bundle.sh`
- Generate: `great-writer-bundled.md`

Simple concatenation script that merges all modules into a single file for agents that can't load multiple files.

- [ ] **Step 1: Write scripts/bundle.sh**

```bash
#!/bin/bash
# Bundle all great-writer modules into a single file
# Usage: ./scripts/bundle.sh

set -euo pipefail

SCRIPT_DIR="$(cd "$(dirname "$0")" && pwd)"
ROOT_DIR="$(dirname "$SCRIPT_DIR")"
OUTPUT="$ROOT_DIR/great-writer-bundled.md"

cat > "$OUTPUT" << 'HEADER'
# Great Writer — Universal Writing Skill (Bundled Version)

> This is the single-file version of great-writer, for agents that cannot load
> multiple files. For the modular version, see the individual files in core/ and modes/.
> Generated by scripts/bundle.sh — do not edit directly.

HEADER

# Append router (SKILL.md body, skip frontmatter)
echo "---" >> "$OUTPUT"
echo "" >> "$OUTPUT"
echo "# Router" >> "$OUTPUT"
echo "" >> "$OUTPUT"
sed -n '/^---$/,/^---$/!p' "$ROOT_DIR/SKILL.md" | tail -n +2 >> "$OUTPUT"

# Append core modules
for f in writing-dna research-protocol humanizer review-protocol; do
  echo "" >> "$OUTPUT"
  echo "---" >> "$OUTPUT"
  echo "" >> "$OUTPUT"
  cat "$ROOT_DIR/core/$f.md" >> "$OUTPUT"
done

# Append mode modules
for f in tech-article marketing-copy research-report xiaohongshu technical-docs; do
  echo "" >> "$OUTPUT"
  echo "---" >> "$OUTPUT"
  echo "" >> "$OUTPUT"
  cat "$ROOT_DIR/modes/$f.md" >> "$OUTPUT"
done

echo ""
echo "Bundled to: $OUTPUT"
echo "Size: $(wc -c < "$OUTPUT" | tr -d ' ') bytes"
```

- [ ] **Step 2: Make executable and run**

```bash
chmod +x scripts/bundle.sh
./scripts/bundle.sh
```

Expected: `great-writer-bundled.md` generated, ~31KB.

- [ ] **Step 3: Commit**

```bash
git add scripts/bundle.sh great-writer-bundled.md
git commit -m "feat: add bundle script and single-file version for portable use"
```

---

### Task 14: Final Verification + Cleanup

**Files:**
- Delete: `SKILL.v1.md` (temporary backup)
- Verify: all files present and non-empty

- [ ] **Step 1: Verify all files exist and are non-empty**

```bash
cd /Users/admin/Documents/AI/skills/great-writer

echo "=== File check ==="
for f in \
  SKILL.md \
  core/writing-dna.md \
  core/research-protocol.md \
  core/humanizer.md \
  core/review-protocol.md \
  modes/tech-article.md \
  modes/marketing-copy.md \
  modes/research-report.md \
  modes/xiaohongshu.md \
  modes/technical-docs.md \
  scripts/bundle.sh \
  great-writer-bundled.md \
  README.md \
  README.en.md; do
  if [ -s "$f" ]; then
    echo "✅ $f ($(wc -c < "$f" | tr -d ' ') bytes)"
  else
    echo "❌ $f MISSING OR EMPTY"
  fi
done
```

- [ ] **Step 2: Verify no core/ content is duplicated in modes/**

Spot-check: search for blacklisted phrases that should only appear in core/humanizer.md:

```bash
grep -l "随着.*的发展" modes/*.md
# Expected: no results (this phrase should only appear as an example in core/humanizer.md)
```

- [ ] **Step 3: Verify router references are correct**

```bash
grep -c "core/" SKILL.md
# Expected: 4 (one reference per core module)

grep -c "modes/" SKILL.md
# Expected: 5 (one reference per mode)
```

- [ ] **Step 4: Remove v1 backup**

```bash
rm SKILL.v1.md
```

- [ ] **Step 5: Final commit**

```bash
git add -A
git commit -m "chore: final verification pass, remove v1 backup"
```
