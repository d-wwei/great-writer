# Tech Product Article — Mode Template

This mode is for technology product articles: WeChat official accounts,
tech blogs, product launch announcements, and technical introductions.

Activated when: 公众号, 博客, 技术博客, 产品介绍, 产品发布, 推广文, blog post, product article, tech article

---

## 9-Module Structure Template

Every tech product article follows these 9 modules in order. Skipping a module weakens the piece.

### Module 1: Title

Must contain a number AND convey action or contrast.

- Length: 15-25 Chinese characters / 8-15 English words
- Formula: `[数据冲击] + [动作/方法]`

```
✅ "省下 96% Token！把飞书 1350 个接口塞进 AI Agent 的正确姿势"
✅ "3 分钟让 AI 操作飞书全平台，上下文只占 550 Token"
✅ "Cut 96% of Token Cost: The Right Way to Fit 1,350 APIs Into Your AI Agent"
❌ "一个好用的飞书 AI 工具介绍"
❌ "Introducing a Useful Feishu AI Tool"
```

The title is the article's first filter. If the number doesn't shock and the action doesn't intrigue, readers scroll past.

### Module 2: TL;DR

One sentence immediately after the title. Says what it is + core advantage. Gives the lazy reader a complete picture without scrolling.

- Format: `[产品是什么] + [核心优势一句话]`
- If you can't fit it in one sentence, you haven't figured out what the product actually does.

### Module 3: Pain Point Entry

2-3 paragraphs, 200 words max. Describe the current problem with data. Make the reader nod: "Yeah, that's exactly my situation."

**Opening formula:** `[痛点数据] + [读者能感受到的后果]`

```
✅ "你的 Agent 接入飞书后，14,000 Token 的上下文就这么没了。"
✅ "Your agent burned 14,000 tokens of context — just loading the tool list."
❌ "在当今 AI 快速发展的时代，飞书作为一款..."
❌ "With the rapid advancement of AI technology..."
```

Rules:
- Enter the pain directly. No warmup, no preamble.
- Use a specific number in the first sentence.
- The consequence must be something the reader personally feels (money wasted, time lost, things breaking).

### Module 4: Data Comparison Table

A three-way comparison table with visual markers. This is the article's evidence layer.

**Format:**

| Dimension | Old Solution A 🔴 | Old Solution B 🟡 | Our Solution 🟢 |
|-----------|-------------------|-------------------|-----------------|
| Context cost | 14,000 tokens | 3,500 tokens | 550 tokens |
| Tool coverage | 1,350 (all loaded) | 200 (curated) | 1,350 (on-demand) |
| Setup time | 30 min | 15 min | 3 min |

Rules:
- Three columns minimum: two existing approaches + ours.
- Use 🔴🟡🟢 emoji markers to create instant visual hierarchy.
- Numbers in every cell. No "fast" / "slow" / "moderate" — give the actual number.
- Pick dimensions where we win clearly. Don't include dimensions where we're equal (those are noise).

### Module 5: Architecture / Principle (Lightweight)

One analogy that explains the core design idea. 150 words max.

The bar: "技术人看到觉得'说得对'，非技术人看到觉得'我懂了'" / Technical readers think "that's accurate"; non-technical readers think "now I get it."

```
✅ "MCP 是背着 1350 件套工具箱出门，Skill 是揣一本口袋手册。"
✅ "MCP carries a 1,350-piece toolbox out the door. Skills is a pocket handbook."
```

Do NOT write a technical explainer here. One analogy, maybe two sentences of context. That's it.

### Module 5.5: Technical Differentiation

The most important persuasion module for technical products. Not every article needs it, but any product with technical depth MUST have it.

**Pattern for each differentiator:**

```
[别人怎么做] → [问题] → [我们怎么做] → [用户好处] → [类比]
[How others do it] → [Problem] → [How we do it] → [User benefit] → [Analogy]
```

Pick 3-5 key technical differentiators and expand each one using this pattern.

**Full example:**

```
❌ "支持元素标注和截图功能"
❌ "Supports element annotation and screenshot features"

✅ "大多数方案截图让 AI 猜坐标，50KB Token 消耗还经常点偏。
   我们给每个按钮编号，AI 报号就行——2KB Token，100% 准确率。
   截图猜坐标是蒙眼戳屏幕，元素标注是给按钮贴号码牌。"

✅ "Most solutions screenshot the page and let the AI guess coordinates —
   50KB token burn, still clicks the wrong button half the time.
   We label every element with a number. AI reports the number, done —
   2KB tokens, 100% accuracy.
   Screenshot guessing is blindfolded screen-poking;
   element labeling is giving buttons name tags."
```

**Rules:**
- Use a contrast tone, not an explanatory tone. You're not teaching — you're showing "we do it differently."
- If a feature "others also have" → write "we do it differently", not "we also have it."
- If you can't find a differentiator → that feature is not worth a standalone section. Fold it into a scenario example in Module 6.
- Every technical advantage MUST land on a user-perceivable result: more accurate, faster, cheaper, more stable.
- For mixed audiences: every technical point must end with what the user actually feels (not implementation details).

### Module 6: Feature Panorama

Group features by usage scenario, NOT by technical category. Each group has 4-6 capabilities with emoji labels and ends with a concrete scenario example.

```
❌ 支持文档搜索、文档创建、文档写入

✅ 🔄 办公自动化
   📄 AI 自动搜文档  ✏️ 写周报  📊 更新表格  📋 创建审批单

   🎯 场景示例：周一早上打开飞书，周报已经写好了——数据从过去 5 天的项目日志里自动拉取。
```

```
✅ 🔄 Office Automation
   📄 Auto-search docs  ✏️ Write weekly reports  📊 Update spreadsheets  📋 Create approvals

   🎯 Scenario: Monday morning — you open Feishu and your weekly report is already drafted,
   with data pulled from the last 5 days of project logs.
```

Rules:
- Scenario labels with emoji: 🔄, 📊, 🔍, 🛠️, etc.
- Each group ends with `🎯 场景示例：...` / `🎯 Scenario: ...` — a concrete moment the reader can picture themselves in.
- If Module 5.5 already covered technical differentiation in depth, simplify this module. Don't repeat the same points.

### Module 7: Compatibility / Universality

Emphasize that the solution is NOT locked to a specific platform. List supported agents, frameworks, and tools.

- Format: a short list or compatibility table.
- Highlight breadth: "Works with any LLM agent — Claude, GPT, Gemini, Codex, open-source models..."
- If there are integration constraints, state them honestly — credibility matters more than completeness.

### Module 8: Quick Start

5 steps or fewer. From zero to running in 3 minutes or less.

Rules:
- Code blocks must be copy-pasteable (no placeholder values that require editing, or clearly mark what to replace).
- Each step = one action + one code block or command.
- If it takes more than 5 steps, the product needs better DX, not a longer guide.

**Format example:**

```bash
# Step 1: Install
npm install feishu-mcp

# Step 2: Configure
export FEISHU_APP_ID=your_app_id
export FEISHU_APP_SECRET=your_app_secret

# Step 3: Run
npx feishu-mcp start
```

### Module 9: Closing

Callback to core data + CTA. Rational and restrained.

Rules:
- Echo the killer data from the title/TL;DR one more time.
- One clear call-to-action: GitHub star, try it, sign up, join waitlist.
- Do NOT write emotional appeals. No "让我们一起拥抱 AI 的未来" / "Let's embrace the AI future together."
- Keep it to 2-3 sentences max.

```
✅ "550 Token，1350 个接口，3 分钟上手。GitHub 链接在这里。"
✅ "550 tokens. 1,350 APIs. 3-minute setup. GitHub link below."
❌ "让我们共同期待这个项目的未来发展！"
```

---

## Length Guidelines

| Platform | Length | Notes |
|----------|--------|-------|
| WeChat (公众号) | 1200-1800 chars | Mobile reading, short paragraphs, generous whitespace |
| Tech blog | 1500-2500 chars | Can go deeper, more code blocks allowed |
| Product landing page | 500-800 chars | Ultra-concise, every sentence is a conversion point |
| Twitter/X thread | <100 chars each, 5-8 tweets | First tweet must hook — standalone value |

---

## Tone Rules

### Do

- Short sentences as backbone. Long sentences occasionally for breathing room.
- Conversational but not sloppy: "搞定" is fine, "牛逼" is not. "Get it done" is fine, "frickin' awesome" is not.
- Rhetorical questions for rhythm: "你愿意为了用不到的工具付出 25 倍代价吗？" / "You'd pay 25x more for tools you'll never use?"
- **Bold** key data and conclusions.
- Paragraphs max 3-4 lines. If longer, break it.

### Don't

- No sentimental or lyrical paragraphs.
- Exclamation marks: 3 max for the entire piece.
- Empty adjectives without data backing them up.

(Full blacklist of banned phrases and structural patterns is in `core/humanizer.md`. This mode uses the default humanizer settings.)

---

## Writing Workflow (Tech Article)

This mode follows the standard 5-phase pipeline (see `SKILL.md`). Mode-specific notes:

### Phase 1: Research
- Standard research protocol applies (`core/research-protocol.md`).
- For tech articles specifically: always do competitive differentiation research. The comparison table (Module 4) and differentiation section (Module 5.5) need real competitor data.

### Phase 2: Draft
Build the 9 modules in this order:
1. Write TL;DR first — if one sentence doesn't work, you haven't understood the product yet.
2. Write pain point + comparison table — this is the evidence layer.
3. Write technical differentiators — each key feature through the "others do X, we do Y" pattern.
4. Write feature scenarios — this is the imagination layer.
5. Add title and closing last — title needs the killer data, closing callbacks to it.

### Phase 3: Review
- Standard review protocol applies (`core/review-protocol.md`).
- Additional tech-article check: verify each Module 5.5 differentiator actually differentiates (not just described differently from competitors).

### Phase 4: Humanize
- Standard humanizer applies (`core/humanizer.md`).
- This mode uses default settings: balanced rhythm, moderate conversational tone.

### Phase 5: Finalize
- Run the self-check checklist below.

---

## Self-Check Checklist

Run through every item after the draft is complete.

### Basic Checks

- [ ] Title has a number?
- [ ] First 3 sentences can stand alone as a WeChat Moments post?
- [ ] Has a comparison table?
- [ ] Core data appears at least 3 times (title, body, closing)?
- [ ] Has a memorable analogy?
- [ ] Features shown by scenario, not as a flat feature list?
- [ ] Can be read in 3 minutes?
- [ ] No AI-slop phrases? (search for "随着", "众所周知", "In today's rapidly")
- [ ] Has a CTA?
- [ ] Would YOU share this article?

### Advanced Checks (from live retrospectives)

- [ ] Did audience analysis before writing? Who reads this, what's their technical level?
- [ ] Did exclusion analysis? Who's locked out by existing solutions?
- [ ] Did deep product research (not just the README)?
- [ ] Each key feature has "why we're better," not just "we can also do this"?
- [ ] Technical advantages translated to user-perceivable results?
- [ ] Has "others do X → problem → we do Y" comparison structure?
