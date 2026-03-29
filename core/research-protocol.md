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
