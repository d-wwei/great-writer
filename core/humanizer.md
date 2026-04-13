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

## Level 1.5: Structural Pattern Detection

These structural patterns betray AI authorship more reliably than word choice. Each is acceptable in isolation — what betrays AI is their **simultaneous, uniform deployment** across an entire piece. If 3+ appear in one piece, the piece needs structural editing.

| Pattern | Detection | Fix |
|---------|-----------|-----|
| **Low burstiness** | 3+ consecutive sentences within ±20% word count | Vary: insert a 4-word punch or a 30-word breather |
| **Rule-of-three compulsion** | Every list has exactly 3 items, every grouping has 3 elements | Use 2, or 4, or 5. Reserve triplets for deliberate rhetorical effect only |
| **Significance inflation** | Paragraph ends with "contributing to..." / "highlighting the importance of..." / "标志着...的重要性" | Delete the sentence. If the significance isn't obvious from the content, the content itself failed |
| **Copula avoidance** | "Serves as" / "functions as" / "acts as" / "充当" replacing "is" / "是" | Use "is" / "是". Simpler is braver |
| **Outline-as-prose** | Parallel section headers ("Challenges" / "Solutions" / "Future Prospects") with identical internal structure | Break the pattern: vary section length, nest subsections unevenly, let some sections be one paragraph and others five |
| **Hedging uniformity** | Same hedge level regardless of certainty ("research suggests" for both proven and speculative claims) | Hedge selectively: confident where you know, uncertain where you don't. Match language to actual confidence |
| **Negative parallelism** | "It's not X, it's Y" / "不是X，而是Y" pattern used more than once per piece | Use this move once for emphasis. A second time is a tic, not a technique |
| **Symmetrical section weight** | Every section has same paragraph count and internal structure | Deliberately vary: the section that matters most gets 40% of the piece, some sections are one paragraph |

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

- [ ] Zero blacklisted phrases remain (Level 1 scan)
- [ ] Structural pattern count < 3 simultaneous (Level 1.5 scan)
- [ ] No three consecutive sentences of similar length
- [ ] Section weights are visibly asymmetric (not all sections same length/structure)
- [ ] At least one rhetorical question (except technical-docs)
- [ ] Specific numbers/details replace all vague references
- [ ] Lists are not all perfectly parallel
- [ ] Opening doesn't set context — it enters the topic directly
- [ ] Closing doesn't summarize what was just said
- [ ] Hedging matches actual confidence level (not uniform)
