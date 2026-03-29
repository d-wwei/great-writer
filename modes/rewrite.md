# Rewrite / Polish — Mode Template

This mode is for improving existing text: drafts, emails, memos, meeting notes,
reports, articles, or any content the user wants made better.

Core principle: **Diagnose first, then treat.** Don't blindly rewrite — understand what's wrong.

Activated when: 改写, 润色, 改一下, 帮我改, polish, rewrite, improve this, make this better, edit this, 优化这段

---

## Humanizer Note

This mode always applies the full humanizer protocol. If the input text has AI-slop patterns, they WILL be removed regardless of other instructions.

---

## Step 1: Receive & Diagnose

Read the input text and produce a diagnosis across 5 dimensions:

### Diagnosis Dimensions

| Dimension | What to Check | Severity |
|-----------|--------------|----------|
| **Structure** | Is there a clear flow? Missing sections? Wrong order? | High if chaotic |
| **Data** | Claims without numbers? Vague assertions? | High if empty |
| **AI Smell** | Blacklisted phrases? Three-paragraph loops? Perfect symmetry? | High if obvious |
| **Clarity** | Ambiguous sentences? Jargon without explanation? Wall of text? | Medium |
| **Rhythm** | Monotonous sentence length? No variation? Reads like a textbook? | Medium |

### Diagnosis Output

```
## Diagnosis

**Overall:** [1-2 sentence summary of the main issues]

**Issues found:**
1. [Critical] ...
2. [Critical] ...
3. [Important] ...
4. [Minor] ...

**Recommendation:** [Full rewrite / Targeted edits / Light polish]
```

**Severity determines approach:**
- 3+ Critical issues → Full rewrite (rebuild structure, keep core ideas)
- 1-2 Critical + some Important → Targeted edits (fix specific sections)
- Only Minor issues → Light polish (rhythm, word choice, tightening)

---

## Step 2: Confirm Approach with User

Before rewriting, tell the user what you found and what you plan to do:

> "I found 3 issues: [brief list]. I recommend [full rewrite / targeted edits / light polish]. Want me to proceed, or focus on specific areas?"

If the user says "just fix it" → proceed with recommended approach.
If the user specifies areas → focus only on those.

---

## Step 3: Rewrite

### Full Rewrite
- Identify the core message and key data from the original
- Choose the appropriate mode template (tech-article, marketing, etc.) or use a general structure if no mode fits
- Rebuild from scratch using the original's content as research material
- Run through Phase 3 (Review) + Phase 4 (Humanize) after rewriting

### Targeted Edits
- Keep the original structure intact
- Fix only the identified issues:
  - Replace AI-slop phrases with natural alternatives
  - Add missing data/numbers
  - Fix structural gaps (add missing TL;DR, fix paragraph order)
  - Clarify ambiguous sentences
- Show changes as tracked edits when possible (original → revised)

### Light Polish
- Tighten sentences (remove unnecessary words)
- Vary sentence length for rhythm
- Replace vague words with specific ones ("a lot of users" → "2,847 users")
- Fix tone inconsistencies
- Remove any remaining AI patterns

---

## Step 4: Show Changes

After rewriting, show what changed and why:

```
## Changes Made

1. **[What changed]** — [Why]
   - Before: "Our solution leverages cutting-edge AI technology..."
   - After: "Our tool reads your codebase and generates docs in 30 seconds."

2. **[What changed]** — [Why]
   - Before: (3 paragraphs explaining background)
   - After: (1 sentence of context, straight to the point)
```

This transparency helps the user learn and gives them the option to revert specific changes.

---

## Special Rewrite Types

### Email Rewrite
- Strip filler ("I hope this email finds you well" → delete)
- Lead with the ask or the answer
- One email = one topic. If multiple topics, suggest splitting.
- Max 5 sentences for routine emails, 10 for complex ones.

### Meeting Notes → Summary
- Extract: decisions made, action items (who + what + when), open questions
- Delete: discussion that didn't lead to decisions
- Format: bullet points, not prose

### Academic / Report → Blog
- Cut length by 50-70%
- Replace jargon with analogies
- Add a "so what?" after each finding
- Convert passive voice to active

### 中文改写
- 删"随着""众所周知"等套话
- 长句拆短句
- 抽象说法换成具体数字
- 书面语降级为口语化（根据目标平台）
- 加粗关键结论

---

## Self-Check Checklist

- [ ] Diagnosed before rewriting (not blind rewrite)?
- [ ] Confirmed approach with user?
- [ ] Core message preserved from original?
- [ ] All critical issues addressed?
- [ ] No new AI-slop introduced?
- [ ] Changes shown with before/after?
- [ ] Result is shorter or same length (not longer)?
- [ ] Would the user recognize their voice in the result?
