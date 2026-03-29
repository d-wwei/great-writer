# Adapt Protocol — Multi-Platform Content Adaptation

When the user has a finished piece and wants it adapted for a different platform,
this protocol handles the transformation without re-running research or full drafting.

Activated when: "转成...", "改成...版", "adapt for...", "make a ... version", "turn this into a ...", "发到..."

---

## When to Use

- After a piece is finalized in one mode, the user wants it on another platform
- User has existing content (from anywhere) and wants it reformatted for a specific platform
- User wants the same content across multiple platforms simultaneously

## When NOT to Use

- The target platform needs fundamentally different content (not just reformatting) → use the appropriate mode from scratch
- The source content is low quality → use rewrite mode first, then adapt

---

## Adaptation Matrix

From any source, adapt to these targets:

| Target Platform | Key Transformation | Length | Tone Shift |
|----------------|-------------------|--------|------------|
| **WeChat 公众号** | Add structure modules (TL;DR, comparison table), mobile-friendly paragraphs | 1200-1800 chars | Professional-casual |
| **Tech Blog** | More code blocks, deeper technical detail allowed | 1500-2500 chars | Technical but accessible |
| **小红书** | Add emojis, first-person voice, image markers, tags. Dramatic tone shift. | 300-1200 chars | Personal, enthusiastic |
| **Twitter/X Thread** | Extract 5-8 key points, each <280 chars. First tweet = hook. | 5-8 tweets | Punchy, direct |
| **LinkedIn Post** | Professional framing, credential signals, one clear takeaway | 200-300 words | Professional, insightful |
| **Email** | Lead with action/ask, strip all preamble, minimize length | 3-10 sentences | Direct, respectful |
| **Slack/内部消息** | TL;DR + bullet points, link to full version | 3-5 sentences | Casual, efficient |
| **Landing Page** | Hero headline + pain/solution pairs + CTA | 500-800 words | Urgent, benefit-focused |
| **Executive Summary** | Conclusions first, key numbers, recommendation | 200-400 words | Authoritative, concise |

---

## Adaptation Process

### Step 1: Identify Source and Target

- What is the source format? (tech article, report, email, etc.)
- What is the target platform?
- What is the core message to preserve?

### Step 2: Extract Core Content

From the source, extract:
1. **The one-sentence thesis** (what is this about?)
2. **Killer data points** (1-3 numbers that matter)
3. **Key arguments/features** (3-5 main points)
4. **CTA or desired action** (what should the reader do?)

### Step 3: Apply Target Template

Load the target platform's rules from the adaptation matrix above. Then:

1. **Restructure** — Reorder content to match target platform's expected flow
2. **Resize** — Cut or expand to target length. When cutting: remove examples first, then supporting arguments, keep core claims and data.
3. **Restyle** — Shift tone, formality, emoji usage, paragraph length per target
4. **Add platform elements** — Tags (小红书), thread numbering (Twitter), code blocks (tech blog), image markers (小红书)

### Step 4: Platform-Specific Rules

#### → 小红书 Adaptation
- Rewrite in first person: "我用了这个工具3个月"
- Add emojis as visual anchors (1-2 per paragraph)
- Add `[配图建议: ...]` markers
- Add 5-10 hashtags
- Honest tone — add a "不足之处" section if appropriate
- Internet slang OK if natural

#### → Twitter/X Thread Adaptation
- Tweet 1: Hook with data or counter-intuitive claim. Must stand alone.
- Tweets 2-6: One point per tweet. No thread-reading required for each.
- Tweet 7-8: CTA + link
- Each tweet: <280 chars, no orphan threads
- Add "🧵" to first tweet

#### → Email Adaptation
- Subject line: [Action needed] or [FYI] + one-line summary
- First sentence: the ask or the answer
- Body: bullet points for details
- Close: specific next step + deadline
- Delete all preamble ("I hope this finds you well")

#### → Executive Summary Adaptation
- First paragraph: conclusion + recommendation
- Second paragraph: 2-3 supporting data points
- Third paragraph: risks or caveats
- No background section — the reader knows the context

---

## Multi-Platform Batch

When the user says "发到所有平台" / "adapt for all platforms":

1. Produce adaptations for: WeChat, 小红书, Twitter, LinkedIn
2. Present them sequentially with clear platform labels
3. Each adaptation is independent — don't cross-reference between them

---

## Self-Check Checklist

- [ ] Core message preserved from source?
- [ ] Killer data points carried over (not lost in adaptation)?
- [ ] Length matches target platform guidelines?
- [ ] Tone shifted appropriately for the platform?
- [ ] Platform-specific elements added (tags, emojis, code blocks, etc.)?
- [ ] Not just a truncation — actually restructured for the platform?
- [ ] Humanizer applied to the adapted version?
