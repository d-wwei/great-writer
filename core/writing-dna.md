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
