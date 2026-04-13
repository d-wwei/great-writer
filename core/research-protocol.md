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

### Content Strategy Check

If the article covers a product series or multiple components/modules, **do NOT assume "complete = better."** Ask the user before writing:

- "All components in one article, or select representative ones?"
- "Is this a one-time comprehensive introduction, or the first in a series?"

N components released one-by-one = N content events with sustained attention. N components dumped in one article = one event with diluted impact. Content strategy comes before writing execution.

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

## Step 2.5: Pain Point Depth Check

Pain points have three layers. Most AI writing stops at Layer 1. Tech articles MUST reach Layer 3.

| Layer | Description | Example | Strength |
|-------|-------------|---------|----------|
| 1 | Problem exists | "Agent 安全是个问题" / "Agent security is a problem" | Weakest — anyone can write this |
| 2 | Consequences | "你可能泄露 API key / 损失 X 小时" / "You'll waste X hours or leak credentials" | Medium |
| 3 | Absurd/painful behaviors people adopt | "所以大家只好单独买一台 mac mini 来装 Agent" / "So everyone buys a separate mac mini just to run the Agent" | Strongest — this is real pain |

**Rules:**
- Layer 3 is what makes readers nod: "Yeah, that's exactly my situation."
- Layer 3 describes a **specific, concrete behavior** — something people actually do to cope with the problem.
- If the source material doesn't contain a Layer 3 example, **ask the user**: "What's the most absurd thing people do to work around this problem?"
- Do NOT fabricate Layer 3 examples. They must be real.

---

## Step 3: Deep Material Mining

Do NOT start writing after reading just the README or user prompt. Dig deeper.

**Required actions:**
1. **Study implementation details** — architecture, design decisions, technical trade-offs
2. **Find competitive differences** — how do others solve the same problem? What's different here?
3. **Extract killer data** — performance numbers, cost comparisons, accuracy metrics, user counts
4. **Identify non-obvious advantages** — things that look similar on the surface but work completely differently underneath

**If search/crawl tools are available:**
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
- **Reader tension statement**: One sentence answering "What does this piece change about the reader's current understanding?" If you cannot write this sentence, the piece has no angle yet — keep researching or reframe
- List of sources/materials reviewed

---

## Protocol Enforcement

The agent MUST produce the Research Summary output before proceeding to the Draft phase. If the user says "just write it" or "skip research," the agent should:

1. Acknowledge the request
2. Explain briefly: "Research prevents generic output — 2 minutes of research saves 20 minutes of rewrites"
3. Offer a compromise: "I'll do a quick version — 3 targeted questions instead of the full protocol"
4. If the user still insists: proceed, but mark the draft as `[⚠️ Written without research — quality may vary]`
