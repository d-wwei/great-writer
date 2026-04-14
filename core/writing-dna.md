# Writing DNA — Universal Principles

These seven principles apply to ALL writing types. Every mode inherits them.
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

**Hook example rule:** If the hook uses multiple examples, they MUST be **progressive** (each reveals a new dimension or deepens the argument), NOT **parallel** (all proving the same point).

- 1 strong example > 3 parallel examples. Parallel examples consume the reader's most precious attention budget — the opening — without adding new information.
- If you have 3 examples that all argue "X is broken," keep the strongest one and compress the others into one sentence of supplementary evidence.
- Test: cover the 2nd and 3rd examples. Does the reader lose any understanding they didn't already have from the 1st? If no, they're parallel — cut them.

```
❌ 3 parallel examples all showing "Agent defaults are bad":
   Example 1: MBA decision lacks risk assessment
   Example 2: Project plan skips risk assessment  ← same point
   Example 3: Investigation doesn't verify         ← same point

✅ 1 strong example + compressed supplement:
   "你让 Agent 做一个 MBA 级别的决策…… [full example]
    类似的问题在项目规划和调查分析中同样出现。" ← one sentence, done
```

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

**Analogy quality self-check (MUST pass before using any analogy):**
- Can the target reader understand this analogy WITHOUT extra explanation?
- If the analogy comes from an internal doc or professional context, does it still work for the article's audience?
- If you need parentheses to explain the analogy, it has failed. Replace it or state the idea directly.
- When the analogy is harder to understand than the thing it explains, delete it.

```
❌ "四种方案，同一个假设：Agent 是近视的" — 读者：啥？什么近视？
✅ "四种方案，同一个假设：Agent 就是不安全的、就是危险的" — 直接说，不绕弯

❌ "Four approaches, same assumption: the Agent is nearsighted" — Reader: what?
✅ "Four approaches, same assumption: the Agent is inherently unsafe" — just say it
```

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

**Before/after scenario comparisons must focus on OUTCOME, not mechanism.**

- The summary of each scenario should describe the **user-perceivable behavior change** — what the user *sees* differently.
- Do NOT summarize scenarios by describing the product's internal mechanism ("auto-triggers without calling," "always-on without invocation").
- Test: extract the summary sentence from each scenario. If it describes how the product works internally → rewrite to describe what the user observes.

```
❌ Mechanism-focused: "三个场景，没有人调用任何 Skill，认知底座自动生效了"
✅ Outcome-focused: "三个完全不同的领域，Agent 都在做同一件事：先审计假设"

❌ "Auto-triggers across all scenarios without manual invocation"
✅ "In every scenario — career, business, content — the Agent audits assumptions first"
```

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
- **Flip their selling points.** When arguing "X's limitations," don't only list what X can't do. Also inspect what X *claims* to do — a selling point often hides a deeper flaw. "Auto-triggers intelligently" sounds good until you realize "you can never tell if it's actually active right now." The strongest limitation argument turns the opponent's strength into a weakness.

```
❌ Weak limitation: "Skill 不能覆盖所有场景" (only listing what it can't do)
✅ Strong limitation: "Skill 能自动触发——但你无法确认此刻它有没有在生效。
    Agent 的表现变成了黑盒：时好时坏。" (flipping the selling point)
```

---

## Principle 6: Describe From the Underlying Change

When describing a product's core value, distinguish the **underlying change** (what it actually transforms) from the **surface manifestation** (what users observe as a side effect). Start from the underlying change; let the surface follow as natural evidence.

- If a product claims to change "how you think," don't describe it as changing "how you talk." Expression is a surface manifestation of judgment; judgment is the underlying change.
- Test: Is your description of the product's value operating at the same depth level as the product's claim? If the product claims to change *thinking* but you're describing changes in *output format*, you've downgraded it.

```
❌ "Tacit Knowledge 改变了 Agent 怎么组织和表达它的思考" (surface: expression style)
✅ "Tacit Knowledge 改变了 Agent 的判断力本身——它注意什么、跳过什么、
    浮现什么隐性信号" (underlying: judgment quality)

❌ "Changes how the Agent organizes and presents its thinking" (surface)
✅ "Changes what the Agent notices, skips, and surfaces — judgment itself" (underlying)
```

---

## Principle 7: Audience Adaptation

Technical readers should think "that's accurate." Non-technical readers should think "I get it."

**Rule:** Use user-perceivable outcomes (accuracy, cost, speed, reliability) to bridge the gap. Implementation details are for the appendix, not the lead.

**Mixed audience strategy:**
- Lead with the outcome: "40% faster page loads"
- Follow with the mechanism (one sentence): "by lazy-loading below-the-fold images"
- Link to the deep dive: "See Architecture section for implementation details"

This applies to all writing types. A research report still needs accessible executive summaries. A README still needs to tell users WHY before HOW.

---

## Principle 8: Reader Value First

Writing exists to create value for the reader, not to document what the writer knows.

**McEnerney's test:** "Would someone who isn't already interested in this topic want to read this?" If no, the piece serves the writer's need to process, not the reader's need for information.

**The tension rule:** Every piece must create instability in the reader's current understanding — comfort confirms, tension compels. The reader should finish thinking "I was wrong about something" or "I didn't know that" or "I need to change what I'm doing."

- Writer's journey ≠ reader's article. Your research path (chronological discovery) is rarely the right reading path
- Start from what the reader lacks, not from what you know
- If the piece could be summarized as "here are some facts about X" without any tension or surprise, it has no reason to exist yet — find the angle that matters

---

## Principle 9: Asymmetry as Design

Expert writing has rhythmic irregularity within a coherent arc — like rubato in music. AI writing is metronomic: uniform paragraphs, uniform sections, uniform emphasis.

**The asymmetry principle:** Deliberately vary section weight, paragraph length, and structural density. The section that matters most gets 40% of the piece. Background context might get 5%. If everything is equally emphasized, nothing is.

- If all sections are the same length with the same internal structure → restructure until the emphasis is visible
- Compress ruthlessly what the reader already knows or can infer. Expand generously what is surprising, counterintuitive, or load-bearing
- One section should be disproportionately detailed — that's where the real value lives. The reader will forgive brief treatment of context if the core insight gets the space it deserves

---

## Principle 10: Scene-First Opening

The first sentence gives the reader a reason to continue. No warmup. No background. No "since ancient times."

The best opening is an image or a specific event — something that happened last week, something you saw this morning, something someone said. Let the core idea grow naturally out of that concrete moment.

Second best: a judgment that makes the reader stop. Place it quietly, don't explain it, let it create friction on its own.

最好的开头是一个画面或一件具体的事。从这个画面里自然地长出核心观点。次好的开头是一句让人停下来的判断——安静放着，不解释，让它自己制造摩擦。

**Relationship to Principle 2 (Pain First):** Pain-first is a subset of scene-first — a pain scenario is one type of opening scene. For product-focused writing (tech-article, marketing-copy), Principle 2 takes priority. For opinion and creative writing, Principle 10 takes priority.

---

## Principle 11: Progressive Revelation

Don't present the complete, complex version upfront. Start with a simple version the reader already understands, show where it breaks, then introduce what you really want to say. Each step crosses only one gap. The reader walks with you — not dragged by you.

One cognitive increment per paragraph — two means split it, zero means delete it. Remove any paragraph and the chain should break — if it doesn't break, the paragraph was filler.

别一上来就端出完整的复杂版本。先给读者已经懂的简单版本，展示它哪里撑不住，再引出你真正要说的。

---

## Principle 12: Scene Over Argument

Don't say "this is wrong" — construct a scene that lets the reader see it's wrong. A micro-scene with time, people, and conflict is ten times more powerful than abstract argument.

不说"这是错的"，构造一个场景让读者自己看到它是错的。有时间、有人物、有冲突的微型场景，比抽象论证有力十倍。

**Relationship to Principle 4 (Scenario-Based):** Principle 4 is about presenting product features through scenarios. Principle 12 is about replacing logical arguments with scenes — turning "persuasion" into "let the reader see for themselves."

---

## Principle 13: Concession Turns

At the strongest point of your argument, hit the brakes. "That said..." "Don't get me wrong..." "This doesn't mean..." — acknowledge the other side has a point. Then press the accelerator again.

The re-assertion after a concession is far more powerful than charging straight through, because the reader sees you as fair.

论证走到最强势的地方，踩一脚刹车。"话说回来""别误会"——承认对面有道理。然后再把油门踩下去。让步之后的再断言比一路冲到底有力得多。

---

## Principle 14: Analogy Crack Handling

Where does the analogy break down? That point is the most valuable paragraph in the piece.

Don't announce "the analogy fails here." Let the reader feel the mismatch on their own. Push through it with narrative.

An analogy that covers everything perfectly is either too vague to be useful or too neat to be honest. The crack is where insight lives.

类比在哪里撑不住了？那个点就是文章最值钱的段落。不宣布"类比失效"，让读者自己感到对不上了。用叙事推过去。

**Relationship to Principle 3 (Analogy Over Explanation):** Principle 3 teaches you to choose good analogies. Principle 14 teaches you to handle their boundaries — acknowledging the crack is stronger than hiding it.

---

## Principle 15: Ending as Door

The ending doesn't summarize. The ending is the last discovery, or a door — pointing toward something you didn't write but the reader will think about on their own.

Best: a short sentence with rhythm that stays in the mind. Like the last note of a song — it stops, but keeps vibrating.

结尾不总结。结尾是最后一个发现，或者一扇门——指向你没写但读者会自己去想的方向。像歌的最后一个音，收住，但还在震。

---

## Density Control

Five-dimensional compression model — run through each dimension after completing the first draft:

### Cut (砍)
Can this sentence be deleted? Can it merge with the previous one?

### Shorten (短)
If two words work, don't use four. "进行讨论" → "聊". "实现功能" → "做到". Big words don't make you sound smart — they make the reader tired.

### Layer (造)
One sentence carries two levels — surface says A, structure implies B.

### Word Choice (选词)
Every verb is a judgment. "放在" and "搁在" and "摆在" are not the same thing.

### Rhythm (节奏)
Fragments and expansions breathe in alternation —

Short sentences are hammers. "就这样。" "三个字。" "没了。" Don't hammer consecutively — two or three times per piece maximum.

Long sentences may stretch, but they must feel like they're moving forward, not circling.

Paragraphs breathe too: one-sentence impact → three-sentence expansion → one-sentence closure. The reader neither suffocates in long blocks nor loses direction in fragments.

### Anti-Template
The same sentence structure may appear at most once. Break regularity.

---

## Voice System Defaults

All modes inherit these defaults. Each mode may override via its own "DNA & Voice Settings" section.

### Temperature
Default 28°C — warm but direct. Neither cold nor sentimental.

- **Warming allowed:** When hitting something you genuinely care about. Don't add exclamation marks — let anger or excitement seep into word choice and sentence density.
- **Cooling allowed:** After the sharpest judgment, step back suddenly. "话说回来" / "别误会" — let the reader see you as fair. The re-assertion after cooling is more powerful than charging straight through.

### Inner Voice
Write out the thoughts that never get said aloud.

Not narration — real inner activity: "心想这也行？" "等等，不对" "算了不想了". Mark with quotes. The effect: an intimacy of eavesdropping on the thinking process.

### Translation Immunity (翻译腔免疫)
**Test:** Translate the sentence back to English, then back to Chinese. Still the same? → Probably translation voice.

Chinese has its own breathing rhythm. Don't let English syntax ride on top.

**Common symptoms:**
- Passive pile-up: "被认为是" → "大家觉得"
- Nouns as verbs: "实现了优化" → "快了"
- Nested clauses: "在我们讨论了这个之后我发现" → "聊完才发现"
- Adjective inflation: "非常重要的关键因素" → "关键"
- Connector overuse: "此外" / "另外" / "与此同时" → cut them, sentences connect themselves

---

## Mode Differentiation Table

Principles 1-9 apply universally. The table below specifies overrides for Principles 10-15, Density Control, and Voice parameters:

| Parameter | tech-article | marketing-copy | research-report | xiaohongshu | github-readme | technical-docs | creative-writing | rewrite | editorial-review |
|-----------|-------------|---------------|----------------|------------|--------------|---------------|-----------------|---------|-----------------|
| **P10 Scene-First** | Optional | Optional | Optional | Full | Optional | Skip | Full | Match original | N/A |
| **P11 Progressive Reveal** | Full | Simplified | Full | Simplified | Full | Skip | Full | Match original | N/A |
| **P12 Scene Over Argument** | Full | Optional | Optional | Full | Optional | Skip | Full | Match original | N/A |
| **P13 Concession Turns** | Full | Use sparingly | Full | Skip | Optional | Skip | Full | Match original | N/A |
| **P14 Analogy Crack** | Full | Skip | Optional | Skip | Optional | Skip | Full | Match original | N/A |
| **P15 Ending as Door** | Full | Skip (CTA ending) | Optional | Optional | Optional | Skip | Full | Match original | N/A |
| **Density** | High | Moderate | High | Low-moderate | Moderate | Maximum clarity | By work | Match original | N/A |
| **Temperature** | 28°C | 30°C | 22°C | 35°C | 28°C | 18°C | By work | Match original | 20°C |
| **Inner Voice** | Optional | Off | Off | Full | Optional | Off | Full | Match original | Off |
| **Translation Immunity** | Mandatory (ZH) | Recommended | Recommended | Mandatory | Mandatory (ZH ver) | N/A | Mandatory (ZH) | If ZH, mandatory | N/A |
