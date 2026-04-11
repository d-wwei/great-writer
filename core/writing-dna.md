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
