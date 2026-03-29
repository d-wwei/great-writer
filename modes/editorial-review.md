# Editorial Review — Mode Template

This mode is for reviewing and critiquing existing content written by others (or by AI).
Not rewriting — providing structured editorial feedback like a professional editor.

Core principle: **Be specific, be actionable, be honest.**

Activated when: 审稿, 帮我看看这篇, 编辑审核, review this article, editorial feedback, critique this, 给个意见, 评价一下

---

## Review Framework

### Layer 1: First Impression (30-second scan)

Before reading in detail, capture:

- **Hook:** Did the first 3 sentences make you want to keep reading? (Yes/No + why)
- **Scanability:** Can you get the gist by scanning headings and bold text? (Yes/No)
- **Length feel:** Does it feel right, too long, or too short for what it's trying to do?
- **Immediate red flags:** Any AI-slop phrases visible? Obvious structural problems?

Output as a brief "First Impression" paragraph.

### Layer 2: Structural Analysis

| Check | What to Look For |
|-------|-----------------|
| **Opening** | Does it earn the reader's attention in the first paragraph? Or does it waste time on context? |
| **Flow** | Does each section logically lead to the next? Any "wait, why?" moments? |
| **Evidence** | Are claims backed by data, examples, or sources? Or just asserted? |
| **Pacing** | Are there sections that drag? Parts that rush through important points? |
| **Closing** | Does it end with purpose (CTA, callback, clear takeaway)? Or just... stop? |
| **Missing pieces** | Is anything obviously missing that the reader would expect? |

### Layer 3: Content Quality

| Check | What to Look For |
|-------|-----------------|
| **Thesis clarity** | Can you state the main argument in one sentence? If not, the piece doesn't know what it's about. |
| **Data quality** | Are numbers specific and contextualized? Or vague ("many users", "significant growth")? |
| **Differentiation** | If it's about a product/idea, does it explain why it's different? Or just what it does? |
| **"So what?" test** | For each major point: is it clear why the reader should care? |
| **Audience fit** | Is the language and depth appropriate for the intended reader? |

### Layer 4: Writing Craft

| Check | What to Look For |
|-------|-----------------|
| **AI smell** | Run the humanizer blacklist mentally. Any banned phrases? Structural AI patterns? |
| **Sentence variety** | All same length? Monotonous? Or varied rhythm? |
| **Word precision** | Vague words that could be more specific? ("thing", "stuff", "various", "very") |
| **Active voice** | Passive constructions that should be active? |
| **Redundancy** | Saying the same thing twice in different words? |
| **Clichés** | Overused phrases that add no value? |

---

## Output Format

### Summary Card

```
## Editorial Review Summary

**Verdict:** [Publish-ready / Needs targeted edits / Needs major revision / Needs rewrite]

**Strongest aspect:** [One thing done well — always start with a positive]
**Biggest issue:** [One thing that most needs fixing]
**AI smell score:** [Clean / Mild / Noticeable / Heavy]

**Reading time:** ~X minutes
**Target audience fit:** [Good / Partial / Poor]
```

### Detailed Findings

Organize by priority:

```
### Must Address (blocks publishing)
1. **[Issue]** — [Specific location] — [Why it matters] — [Suggested fix]
2. ...

### Should Address (improves quality)
3. **[Issue]** — [Specific location] — [Why it matters] — [Suggested fix]
4. ...

### Consider (nice-to-haves)
5. **[Issue]** — [Specific location] — [Suggested fix]
6. ...
```

### Inline Annotations (Optional)

If the user wants line-by-line feedback, use this format:

```
> "Original sentence from the text"
→ [Issue]: [explanation]. Suggested: "[revised version]"
```

---

## Tone of Feedback

- **Honest but constructive** — don't soften real problems, but always offer solutions
- **Specific, never vague** — "paragraph 3 lacks data" not "could use more evidence"
- **One positive per review** — always identify what works, even in weak pieces
- **No condescension** — the writer is a peer, not a student
- **Actionable** — every critique comes with a suggested fix or direction

---

## Mode-Specific Reviews

When the content type is identifiable, apply mode-specific checklist:

| Content Type | Additional Checks |
|-------------|------------------|
| Tech article | Has comparison table? Data in title? Scenario-based features? |
| Marketing copy | CTA specific? Hero headline has number? No buzzword filler? |
| Research report | Executive summary standalone? Sources cited? Confidence levels on predictions? |
| 小红书 | Title has emojis? Image guidance? Personal voice? |
| Technical docs | Commands runnable? Active voice? One topic per guide? |

If the content type is not one of the 5 modes, use the general framework only.

---

## Self-Check Checklist

- [ ] Captured honest first impression?
- [ ] Structural analysis covers opening, flow, evidence, pacing, closing?
- [ ] Content quality assessed (thesis, data, differentiation, "so what?")?
- [ ] Writing craft checked (AI smell, rhythm, word precision)?
- [ ] Findings organized by priority (Must / Should / Consider)?
- [ ] Every critique has a suggested fix?
- [ ] Started with something positive?
- [ ] Feedback is specific (with locations), not generic?
