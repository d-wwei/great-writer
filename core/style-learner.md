# Style Learner — Style Guide Extraction Protocol

When the user provides a reference text, brand guidelines, or says "match this style" / "用这个风格" / "学习这个风格", this protocol activates.

It extracts a reusable style fingerprint that subsequent writing phases will follow.

---

## When to Activate

- User provides a reference article and says "write like this" / "用这个风格写"
- User provides brand guidelines or a style guide document
- User says "learn my style" / "学习我的写作风格" and provides 2+ samples
- User references a previous output and says "keep this style" / "保持这个风格"

---

## Step 1: Analyze the Reference

Read the provided text and extract these dimensions:

### Sentence Structure
- **Average sentence length:** short (<10 words), medium (10-20), long (20+), or mixed
- **Sentence variety:** uniform or varied (short punches + long breathers)
- **Paragraph length:** 1-2 lines, 3-4 lines, or 5+ lines
- **Fragment usage:** none, occasional, frequent

### Tone & Voice
- **Formality:** casual / professional-casual / professional / academic
- **Person:** first person (I/we), second person (you), third person, or mixed
- **Emotional register:** neutral, enthusiastic, authoritative, conversational, provocative
- **Humor:** none, subtle, moderate, frequent

### Vocabulary
- **Technical density:** low (no jargon), medium (some terms explained), high (assumes knowledge)
- **Recurring phrases or patterns:** extract 3-5 signature phrases or constructions
- **Banned patterns:** note any patterns the reference consistently avoids

### Structural Habits
- **Opening pattern:** data-first, anecdote, question, direct statement
- **Transition style:** explicit connectors, implicit flow, abrupt jumps
- **Closing pattern:** CTA, summary, callback, open-ended
- **List style:** numbered, bulleted, inline, or avoided entirely
- **Emphasis style:** bold, italics, ALL CAPS, or none

### Language-Specific (if Chinese)
- **Register:** 书面语 vs 口语化
- **四字成语 usage:** frequent, occasional, never
- **Emoji usage:** none, minimal, moderate, heavy
- **Internet slang:** none, occasional, frequent

---

## Step 2: Produce the Style Fingerprint

Output a structured style card:

```
## Style Fingerprint: [Name or Source]

**Sentence:** [short/medium/long/mixed], [uniform/varied], paragraphs [1-2/3-4/5+] lines
**Tone:** [formality level], [person], [emotional register]
**Vocabulary:** [technical density], avoids [patterns]
**Structure:** opens with [pattern], closes with [pattern]
**Signature moves:** [3-5 distinctive patterns]
**Language notes:** [if applicable]

### Rules for this style:
1. [Specific rule extracted from analysis]
2. [Specific rule]
3. [Specific rule]
4. [Specific rule]
5. [Specific rule]
```

---

## Step 3: Apply During Writing

When a style fingerprint is active:

1. **Phase 3 (Draft):** Apply the fingerprint rules alongside the mode template. Fingerprint overrides default tone rules where they conflict.
2. **Phase 5 (Polish):** Use the fingerprint as the target voice, not just "avoid AI patterns." The polish passes should push toward the learned style, not just away from AI.
3. **Phase 6 (Finalize):** Add a style-match check: "Does this read like the reference? If not, what's off?"

### Conflict Resolution

If the style fingerprint conflicts with the mode template:
- **Fingerprint wins** on: tone, sentence length, vocabulary, formality
- **Mode template wins** on: structural requirements (e.g., tech-article must have comparison table)
- **Humanizer always runs** — even if the reference style uses some blacklisted patterns, the humanizer still removes obvious AI tells

---

## Step 4: Persist (Optional)

If the user wants to reuse the style across sessions:
- Save the style fingerprint to a file (e.g., `styles/brand-voice.md`)
- Future sessions can load it: "use the brand voice style" / "用品牌风格"
- Multiple fingerprints can coexist — user picks which one to apply

---

## Examples

**User:** "Here's our last 3 blog posts. Learn this style and write the next one."

**Agent:**
1. Analyzes all 3 posts
2. Extracts common patterns (short paragraphs, data-heavy, rhetorical questions, casual-professional tone)
3. Produces style fingerprint
4. Applies it to the new article alongside the tech-article mode template

**User:** "用这篇公众号的风格写下一篇"

**Agent:**
1. 分析参考文章
2. 提取风格指纹（短段落、数据密集、反问句、口语化但不随意）
3. 后续写作自动对齐
