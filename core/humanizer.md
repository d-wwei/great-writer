# Humanizer — 4-Pass Polish Protocol

This protocol turns a draft into writing that feels human. Applied in Phase 5 of the pipeline, after review.

Four passes run sequentially. Each pass has a clear scope. Pass 1 (oral test) is the highest-priority gate — all changes from later passes must still pass the oral test.

---

## Pass 1: Oral Test (口语检验)

**The supreme rule:** "Would you say this to a smart friend? No → rewrite."

Read every paragraph aloud (or simulate reading aloud). If a sentence feels unnatural in speech, it's wrong on the page.

**Keep alive connectors** — "but," "so," "like," "不过," "所以," "就像" are the natural sound of thought turning a corner. These stay.

**Kill mechanical connectors** — "Furthermore," "Additionally," "此外," "另外," "值得注意的是" are filing-cabinet words. Nobody talks like this. Cut them.

**Priority:** This pass outranks all others. If Pass 2-4 produce changes that fail the oral test, roll back. If you compress a sentence for density and it no longer sounds speakable, undo.

**Failure examples:**
| Written | Spoken equivalent |
|---------|-------------------|
| "在某种程度上来说" | "多少算是" |
| "对此进行了深入的探讨" | "聊透了" |
| "It is worth noting that the system provides" | "The system also gives you" |
| "This fundamentally transforms the paradigm of" | "This changes how you" |

---

## Pass 2: Density & Rhythm (密度与节奏)

Run the five-dimensional compression model from `writing-dna.md` (Density Control section):

**Cut (砍):** Can this sentence be deleted? Can it merge with the previous one?

**Shorten (短):** If two words work, don't use four. "进行讨论"→"聊". "实现功能"→"做到".

**Layer (造):** Can this sentence carry a second meaning underneath the surface?

**Word Choice (选词):** Is each verb the precise one? "放在" ≠ "搁在" ≠ "摆在".

**Rhythm (节奏):**
- Short sentences are hammers — 2-3 per piece maximum, not consecutive
- Long sentences stretch forward, never circling
- Paragraph breathing: impact (1 sentence) → expansion (3-4 sentences) → closure (1 sentence)
- **No three consecutive sentences of similar length** (within ±20% word count)

**Anti-template:** The same sentence structure appears at most once. Break regularity.

After compression, re-run Pass 1. If it no longer sounds speakable, roll back.

---

## Pass 3: AI Trace Removal (AI痕迹清除)

Four sub-passes. If 3+ structural patterns from 3b appear in one piece, the piece needs structural editing.

### 3a: Vocabulary Layer — Blacklist Interception

If ANY of these patterns appear, they MUST be rewritten. No exceptions.

**Chinese Blacklist:**

Banned phrases:
- 随着...的发展 / 随着...的兴起 / 随着...的普及
- 众所周知
- 在当今时代 / 在当今社会
- 不言而喻
- 总而言之 / 综上所述
- 值得一提的是
- 毋庸置疑

Banned adjectives (without supporting data):
- 强大的、优秀的、出色的、卓越的
- 创新的、领先的、前沿的
- 赋能、引领、颠覆、革命性的
- 无缝的、全方位的、一站式的

Banned structures:
- Opening with context-setting ("随着 AI 技术的发展...")
- Closing with empty call-to-action ("让我们拭目以待")
- Exclamation marks > 3 per piece (exception: xiaohongshu allows up to 5)

**English Blacklist:**

Banned phrases:
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

Banned structures:
- Three-paragraph loop: [point] → [expand] → [summarize], repeated
- Perfect parallel structure in every list
- Excessive em-dashes (more than 2 per 500 words)
- Every paragraph starting with a transition word
- Vague attribution: "experts say," "studies show," "research indicates" (without citing which)

### 3b: Structural Layer — Pattern Detection

Each pattern is acceptable in isolation. What betrays AI is their **simultaneous, uniform deployment**:

| Pattern | Detection | Fix |
|---------|-----------|-----|
| **Low burstiness** | 3+ consecutive sentences within ±20% word count | Vary: insert a 4-word punch or a 30-word breather |
| **Rule-of-three compulsion** | Every list has exactly 3 items, every grouping has 3 elements | Use 2, or 4, or 5. Reserve triplets for deliberate rhetorical effect only |
| **Significance inflation** | Paragraph ends with "contributing to..." / "highlighting the importance of..." / "标志着...的重要性" | Delete the sentence. If the significance isn't obvious from the content, the content itself failed |
| **Copula avoidance** | "Serves as" / "functions as" replacing "is" | Use "is". Simpler is braver |
| **Outline-as-prose** | Parallel section headers with identical internal structure | Break the pattern: vary section length, nest unevenly |
| **Hedging uniformity** | Same hedge level regardless of certainty | Hedge selectively: confident where you know, uncertain where you don't |
| **Negative parallelism** | "It's not X, it's Y" / "不是X，而是Y" used more than once per piece | Use once for emphasis. A second time is a tic |
| **Symmetrical section weight** | Every section has same paragraph count and internal structure | Deliberately vary: most important section gets 40% of the piece |

### 3c: Deep Filter Layer

Additional filters that catch what blacklists miss:

- **Kill filler** — crutch words ("非常," "确实," "实际上"), inflated symbolism ("标志着," "见证了"), propaganda tone ("充满活力," "开创性的")
- **Break formulas** — negation-style parallelism: max 2 per piece. Three-part lists: change to 2 or 4 items.
- **Vary rhythm** — long and short sentences alternate. No more than one em-dash per paragraph.
- **Trust the reader** — skip softening ("似乎," "可能," "也许" when you actually know) and over-explanation
- **Kill quotable lines** — if a sentence sounds like it belongs on a motivational poster, rewrite it. Over-polished sentences break the texture of honest writing.

### 3d: Translation Immunity (翻译腔清除) — Chinese content only

**Test:** Translate the sentence to English, then back to Chinese. Still the same? → Translation voice.

**Symptom checklist:**
- Passive pile-up: "被认为是" → "大家觉得"
- Nouns as verbs: "实现了优化" → "快了"
- Nested clauses: "在我们讨论了这个之后我发现" → "聊完才发现"
- Adjective inflation: "非常重要的关键因素" → "关键"
- Connector overuse: "此外" / "另外" / "与此同时" → cut, sentences connect themselves

---

## Pass 4: Anti-Style Check (反风格检查)

Eight specific anti-patterns. Scan the entire piece against each:

| If you're... | Then... |
|-------------|---------|
| **Explaining** | Replace with a scene the reader can see |
| **Listing** | Cut to only the single most powerful item |
| **Inventing frameworks** | Delete the acronym and matrix. Say it in one sentence |
| **Chasing trends** | Write something that holds up in three years |
| **Sounding translated** | Move the verb forward, cut subordinate clauses, rewrite with Chinese rhythm |
| **Covering everything** | One point per piece. Say it. Stop. |
| **Repeating a point** | If the same argument appears twice in different words, strengthen the first occurrence and delete the repeat |
| **Writing something any assistant could write** | Rewrite or delete. If it's generic enough for any AI to produce, it adds nothing |

**Surprise test:** During the process of writing this piece, did you discover something you didn't think of before? If yes → make sure it's prominent in the text. If no → the core wasn't attacked hard enough (return to Phase 1 Step c).

---

## Mode-Specific Overrides

| Mode | Override |
|------|----------|
| xiaohongshu | Pass 3a: emojis ENCOURAGED, exclamation marks up to 5, internet slang OK in moderation. Pass 4: "covering everything" rule relaxed for tutorials. |
| technical-docs | Pass 1: oral test standard changes to "clear and concise" rather than "like talking to a friend." Pass 2: density maximized for clarity. Pass 4: skipped entirely. No rhetorical questions, no conversational asides, no emojis. |
| marketing-copy | Pass 2: sentence fragments OK for impact. Pass 4: "chasing trends" rule relaxed for timely campaigns. |
| research-report | Pass 1: oral test standard changes to "professional but readable." Pass 4: "covering everything" rule relaxed — reports may need breadth. |
| creative-writing | Pass 3b: intentional repetition and parallel structure allowed for literary effect. Pass 4: significantly relaxed — creative choices override anti-patterns. |
| tech-article | Default settings — balanced across all passes. |

---

## Application Checklist

After all four passes, verify:

- [ ] Every sentence passes the oral test (Pass 1)
- [ ] No three consecutive sentences of similar length (Pass 2)
- [ ] Section weights are visibly asymmetric (Pass 2)
- [ ] Zero blacklisted phrases remain (Pass 3a)
- [ ] Structural pattern count < 3 simultaneous (Pass 3b)
- [ ] No filler words, no quotable-poster sentences (Pass 3c)
- [ ] Chinese text passes translation immunity test (Pass 3d)
- [ ] No explaining where a scene would work (Pass 4)
- [ ] No repeated arguments in different words (Pass 4)
- [ ] Specific numbers/details replace all vague references
- [ ] Opening enters the topic directly — no context-setting
- [ ] Closing doesn't summarize what was just said
