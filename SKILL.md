---
name: great-writer
description: >
  Universal writing skill for AI agents. 9 writing modes (tech articles, marketing copy,
  research reports, Xiaohongshu notes, technical docs, GitHub READMEs, creative writing,
  rewrite/polish, editorial review) + 9 core modules (research, core-finding, writing DNA,
  humanizer/polish, review, style learning, adaptation, SEO/GEO, writing memory,
  visualization). 6-phase pipeline with deep-thinking methodology. Bilingual (EN/ZH).
triggers:
  - /great-writer
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
  - 改写
  - 润色
  - 帮我改
  - 审稿
  - 写小说
  - 写故事
  - 写散文
  - 写演讲稿
  - 学习风格
  - 转成
  - 发到
  - SEO优化
  - 写 README
  - 仓库介绍
  - 仓库 README
  - GitHub 仓库介绍
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
  - API docs
  - changelog
  - technical docs
  - internal guide
  - release notes
  - xiaohongshu
  - rewrite
  - polish
  - improve this
  - edit this
  - editorial review
  - critique this
  - creative writing
  - fiction
  - short story
  - essay
  - speech
  - screenplay
  - learn this style
  - match this style
  - adapt for
  - turn this into
  - SEO
  - keywords
  - GitHub README
  - repo README
  - project README
  - write a README for
---

# Great Writer — Universal Writing Skill

## Stance

Thinks from the reader's position, not the writer's. Every sentence earns its place by creating value for the reader — not by documenting what the writer knows. Treats rhythm, asymmetry, and surprise as engineering parameters, not aesthetic preferences. Writes like a human: irregular, opinionated, specific.

心里放一个具体的人，写给他，不是写给"读者们"。先亮自己的弯路，再给方向——所有说服力的来源不是因为你对，而是因为你先错过。

This skill covers 9 writing modes through a modular 6-phase pipeline, with 9 core capability modules. Each piece goes through core logic (research + find core), structure design, drafting, review, polishing, and finalization before output.

---

## Red Lines

Scan all output against these constraints before delivery. Every item is mechanically checkable.

1. **No output without Research Summary** — Phase 1 Step a gate. If skipped, mark output `[⚠️ Written without research]`
2. **No unexamined core** — Phase 1 Step c gate. The core must survive an attack before expansion. An unexamined opinion, no matter how well-written, collapses at the first smart reader's question.
3. **No draft without structural outline** — Phase 2 gate. Skeleton must exist before prose
3. **No 3+ consecutive sentences of similar length** — Adjacent sentences within ±20% word count = low burstiness. Insert a short punch or a long breather
4. **No symmetrical section structure** — If all sections have the same paragraph count and internal pattern, restructure until emphasis is visible
5. **No AI-slop phrases** — Blacklist in `core/humanizer.md` Level 1 applies to all output, no exceptions
6. **No unsupported claims** — Every claim needs a data point, example, or source. "This is powerful" without evidence = delete
7. **No significance inflation** — If a paragraph ends by explaining why the thing matters when the reader can already see it, delete that sentence
8. **No swap-test failure** — If you can substitute a different subject and the piece still reads the same, it is too generic. Rewrite with specifics that only apply to this subject
9. **No translation voice** — Chinese writing only. Test: translate the sentence back to English, then back to Chinese. Still the same? → Translation voice. Rewrite with Chinese rhythm. (See writing-dna.md Translation Immunity for symptoms checklist)

---

## Acceptance Criteria

From the reader's perspective — every item testable by two independent reviewers.

1. **Actionable endpoint**: Reader can identify what to do next (CTA, changed understanding, or specific next step)
2. **Evidence density**: At least one data point, analogy, or concrete example per major section
3. **Burstiness**: Sentence length standard deviation ≥ 30% of mean sentence length across the piece
4. **Research-dependent**: The piece could NOT have been written without the specific research done in Phase 1 — remove all research findings and the piece collapses
5. **Tension**: The piece changes the reader's mind about at least one thing, or teaches something the reader did not know and would find surprising

---

## Step 1: Route to the Right Mode

Identify the writing type from the user's request and load the corresponding mode template.

| Signal | Mode | File |
|--------|------|------|
| 公众号, 博客, 技术博客, 产品介绍, 产品发布, 推广文, blog post, product article, tech article | Tech Product Article | `modes/tech-article.md` |
| Landing page, 广告, CTA, 社交媒体, 文案, ad copy, social post, marketing copy | Marketing Copy | `modes/marketing-copy.md` |
| 白皮书, 行业分析, 竞品报告, 投研, whitepaper, research report, competitive analysis | Research Report | `modes/research-report.md` |
| 小红书, 种草, 笔记, xiaohongshu, RED note | Xiaohongshu Note | `modes/xiaohongshu.md` |
| GitHub README, repo README, project README, 写 README, 仓库介绍, 仓库 README, write a README for | GitHub README | `modes/github-readme.md` |
| API docs, changelog, 技术文档, 内部文档, technical docs, internal guide, release notes | Technical Documentation | `modes/technical-docs.md` |
| 改写, 润色, 帮我改, polish, rewrite, improve this, edit this, make this better | Rewrite / Polish | `modes/rewrite.md` |
| 审稿, 帮我看看, 编辑审核, editorial review, critique this, review this article | Editorial Review | `modes/editorial-review.md` |
| 写小说, 写故事, 写散文, 写演讲稿, 写剧本, creative writing, fiction, essay, short story, speech | Creative Writing | `modes/creative-writing.md` |
| Ambiguous or unclear | Ask the user to clarify | — |

**After routing:** Read the matched mode file (relative to this skill's root directory) to get the type-specific structure template, tone rules, and self-check checklist.

---

## Step 2: Run the Writing Pipeline

Every piece of writing goes through 6 phases. Each phase loads specific modules.

**Phase status output (mandatory):** When entering each phase, output a brief status line so the user can follow the process. Format:

> **Phase N: [Name]** — [one sentence: what this phase does and why]

Example status lines:
- **Phase 1: Core Logic** — Researching the audience, finding the core idea, and stress-testing it before writing a single word.
- **Phase 2: Structure Design** — Building the skeleton: a load-bearing analogy, narrative arc, and deliberate weight distribution.
- **Phase 3: Draft** — Writing the first draft with 15 principles active and mode-specific voice loaded.
- **Phase 4: Review** — Four-dimension check: structure, logic, facts, perspective. Fixing all must-fix items.
- **Phase 5: Polish** — Four passes: oral test → density → AI trace removal → anti-style check.
- **Phase 6: Finalize** — Running the mode-specific self-check. All items pass → output.

Keep it to one line. The user should know *what's happening* and *why*, not the full protocol details.

### Phase 1: Core Logic

Three steps to establish *what this piece is really about*.

**Step a — Research.** Read `core/research-protocol.md` and follow its protocol completely.

- Audience targeting, exclusion analysis, deep material mining
- Output: Research Summary with killer data points

**Step b — Think & Judge.** From the Research Summary, identify:

1. **Core tension**: What does this piece change about the reader's current understanding? If nothing — the piece has no reason to exist. Reframe until tension is found.
2. **Value carrier**: What single element would make readers share this? (A mapping table, a data comparison, an analogy, a causal chain, a key insight.) This element is **protected** — never compressed to meet length targets.

**Step c — Find Core & Attack Core.** Read `core/core-finding.md` and execute the protocol.

- Use the four shovels on the results from Step a and Step b to dig to the load-bearing idea underneath
- Attack the core: "If this is true, then why ______?"
- Three outcomes: core holds → proceed with confidence; core morphs → return to Step a with new angle; core breaks → tell the user honestly
- Output: Core Statement (one sentence) + Stress-Test Result

**Gate: Do not proceed to Phase 2 until Research Summary + Core Statement + Stress-Test Result are all produced.**

### Phase 2: Structure Design

Design the piece's skeleton around the validated core.

**Step a — Scaffold.** Find a cross-disciplinary load-bearing analogy for the core.

- Not decoration — a structural wall. If you remove it, the piece collapses.
- Search broadly across disciplines: biology, economics, physics, architecture, cooking, sports, games — prioritize domains familiar to the target reader, not just computer science.
- **Validation:** (1) Remove it and the piece collapses (load-bearing). (2) Dig one level deeper and it still maps (multi-layer). (3) The reader gets it without explanation (self-evident).

**Step b — Narrative arc & weight.** Choose the shape and assign weight deliberately.

- Arc options: problem→solution→evidence, story→principle→application, counterintuitive claim→proof→implications, chronological with twist.
- Assign weight: which section deserves 40%? Which deserves 5%? Asymmetry is a feature.

**Step c — Reader perspective check.** Step back and review the skeleton from the reader's viewpoint.

- Does the structure flow logically for someone who doesn't have your context?
- Can a reader who only skims headings still grasp the main argument?
- Present skeleton to user (unless user said "just write it" or the piece is short-form).

**Gate: Do not proceed to Phase 3 until the structure skeleton is confirmed.**

### Phase 3: Draft

Read `core/writing-dna.md` for universal writing principles (including Principles 10-15 and Density Control).
Read the matched `modes/{type}.md` for the structure template and DNA & Voice Settings.

- Apply the writing principles from writing-dna.md (check mode differentiation table for active principles)
- Follow the mode's structure template section by section
- Hang every detail back on the scaffold — the reader should always know "where this piece fits"
- Use research findings as the content foundation
- Output: Complete first draft

### Phase 4: Review

Read `core/review-protocol.md` and run all four review dimensions.

- Structural review (against mode template)
- Logic review (argument flow, data support)
- Fact check (verify numbers, citations, dates)
- Perspective audit (developer vs product vs user perspective)
- Output: Numbered fix list → apply all fixes

**Gate: Do not proceed to Phase 5 until all "Must Fix" items are resolved.**

### Phase 5: Polish

Read `core/humanizer.md` and run all four passes sequentially.

- Pass 1: Oral test — "Would you say this to a smart friend? No → rewrite." Highest priority. All subsequent passes must re-pass this test.
- Pass 2: Density / rhythm / word choice / anti-template — apply the five-dimensional compression model from writing-dna.md
- Pass 3: AI trace removal — merged blacklist interception + structural pattern detection + translation immunity check
- Pass 4: Anti-style check — 8 specific anti-patterns (explaining → show a scene, listing → keep only the strongest, etc.)
- Apply mode-specific overrides (e.g., xiaohongshu allows more emojis; technical-docs adjusts oral test to "clear and concise" standard)
- Output: Polished draft

### Phase 6: Finalize

Run the mode-specific self-check checklist (from the mode file).

- If all items pass → output final version
- If any items fail → fix and re-check
- Output: Final piece ready for publication

---

## Phase Jumping

Users can jump to any phase at any time:

| User Says | Action |
|-----------|--------|
| "重新调研" / "re-research" | Go to Phase 1 Step a |
| "重新找核" / "re-think" / "换个角度" | Go to Phase 1 Step c |
| "改大纲" / "restructure" / "改结构" | Go to Phase 2 |
| "重写" / "rewrite" | Go to Phase 3 |
| "审校" / "review" / "检查逻辑" | Go to Phase 4 |
| "打磨" / "polish" / "去AI味" / "humanize" / "润色" | Go to Phase 5 |
| "检查" / "check" / "自检" | Go to Phase 6 |

Each phase is independently re-runnable. Jumping to Phase 4 does not require re-running Phase 1-3.

---

## Tool Integration

This skill can optionally use external tools to enhance quality. Declare these as available capabilities:

| Capability | How to Use | Without Tools |
|------------|-----------|---------------|
| Web search | Use any available search tool to find current data, competitors, benchmarks | Guide user to provide materials |
| Content extraction | Use any available fetch/crawl tool to read URLs and extract content | Ask user to paste content |
| Academic citations | Use any available academic search tool for papers and citations | Mark as "needs verification" |
| Typesetting | Invoke typeset skill if available for rich formatting | Output plain Markdown |

**No hard dependencies.** The skill works fully without any tools — it just works better with them.

---

## Enhanced Capabilities

These modules activate on demand — not loaded unless triggered.

| Capability | Trigger | Module |
|-----------|---------|--------|
| **Style Learning** | "学习这个风格" / "match this style" / provide reference text | `core/style-learner.md` |
| **Platform Adaptation** | "转成小红书版" / "adapt for Twitter" / "发到所有平台" | `core/adapt-protocol.md` |
| **Writing Memory** | "记住这个风格" / "save writing memory" / auto-offered after tasks | `core/writing-memory.md` |
| **SEO/GEO Optimization** | "SEO优化" / "关键词" / "SEO" / web-published content | `core/seo-layer.md` |
| **Data Visualization** | Auto for data-rich content, or "加图表建议" / "visualize this" | `core/visualization.md` |

These extend the pipeline — they don't replace it. Style learning affects Phase 3+5, SEO adds to Phase 6, visualization enhances Phase 3, etc.

---

## Quick Reference

| Writing Type | Mode File | Best For |
|-------------|-----------|----------|
| Tech Product Article | `modes/tech-article.md` | WeChat, blogs, product launches |
| Marketing Copy | `modes/marketing-copy.md` | Landing pages, ads, social posts |
| Research Report | `modes/research-report.md` | Whitepapers, competitive analysis |
| Xiaohongshu Note | `modes/xiaohongshu.md` | 种草, tutorials, experience sharing |
| GitHub README | `modes/github-readme.md` | Story-driven bilingual repo READMEs |
| Technical Docs | `modes/technical-docs.md` | API docs, changelogs, internal guides |
| Rewrite / Polish | `modes/rewrite.md` | Improve existing drafts, emails, memos |
| Editorial Review | `modes/editorial-review.md` | Critique and feedback on others' writing |
| Creative Writing | `modes/creative-writing.md` | Fiction, essays, speeches, scripts |
