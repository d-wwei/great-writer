<p align="center">
  <h1 align="center">Great Writer</h1>
  <p align="center">Make AI write tech articles people actually want to share</p>
  <p align="center">
    <a href="#installation">Installation</a> · <a href="#what-problem-does-it-solve">Why</a> · <a href="./README.md">中文</a>
  </p>
</p>

---

## TL;DR

**An AI writing protocol that kills "AI slop" in tech product articles.** Data-driven, scenario-based, rhythm-aware — the output reads like a human wrote it, not a language model.

## What Problem Does It Solve

Ask AI to write a tech product article and you'll likely get:

> "In today's rapidly evolving technological landscape, our product leverages cutting-edge AI capabilities to deliver an unprecedented experience..."

**Nobody wants to read that.** No data, no pain point, no imagery — pure AI filler.

Great Writer is a writing protocol (Skill) that forces AI to follow a proven framework:

| Problem | Great Writer's Fix |
|---------|-------------------|
| Empty fluff | Every article needs 1-2 "killer stats" as anchors |
| AI slop | Built-in blocklist for cliché phrases |
| Feature dumps | Mandatory scenario-based grouping with use case examples |
| Unreadable | Pain-first opening, short paragraphs, rhetorical questions for rhythm |
| Jargon-heavy | Analogies over explanations |

## Core Framework

### 4 Iron Rules

1. **Data is the anchor** — "Save 96% of tokens" vs "significantly improve efficiency" — the former gets quoted, the latter doesn't
2. **Open with pain** — First paragraph hits the reader's problem. No warm-up.
3. **Analogies over explanations** — "MCP is carrying a 1350-piece toolbox out the door" beats three paragraphs of protocol specs
4. **Show scenarios, not features** — "AI auto-searches docs and writes reports" instead of "supports document search and creation"

### 9-Module Article Structure

```
Title (must contain a number)
  → TL;DR (one line of value)
    → Pain point (data + consequences)
      → Comparison table (3-way, 🔴🟡🟢)
        → Architecture analogy (one memorable metaphor)
          → Feature panorama (grouped by scenario + examples)
            → Compatibility
              → Quick start (≤5 steps)
                → Closing (callback to data + CTA)
```

### Self-Check Checklist

Run through after writing:

- [ ] Does the title contain a number?
- [ ] Can the first 3 sentences stand alone as a social media post?
- [ ] Does the killer stat appear at least 3 times?
- [ ] Is there one memorable analogy?
- [ ] Are features shown by scenario or listed as a dry catalog?
- [ ] Any AI slop phrases left?
- [ ] Would you share this article yourself?

## Supported Formats

| Platform | Word Count |
|----------|-----------|
| WeChat / Blog | 1,200–1,800 words |
| Technical Blog | 1,500–2,500 words |
| Product Landing Page | 500–800 words |
| Twitter/X Thread | <100 words per tweet, 5–8 tweets |

## Installation

### Claude Code

```bash
# macOS / Linux
git clone https://github.com/d-wwei/great-writer.git
ln -sf "$(pwd)/great-writer/skill" ~/.claude/skills/great-writer
```

### Other Agents

Inject the content of `SKILL.md` as a system prompt or context. The core is the writing protocol — it's framework-agnostic.

## Usage

Once installed, these trigger words auto-activate the skill:

> "写文章", "公众号", "技术博客", "write article", "blog post", "product intro"

Example:

```
You: Write a blog post about our new product. Key selling points: 10x faster, 80% cheaper.
AI: [auto-loads great-writer skill, outputs article following the 9-module structure]
```

## Before vs After

**Without Great Writer:**

> In the rapidly evolving landscape of cloud computing, we are proud to introduce a powerful new product...

**With Great Writer:**

> Your server bill tripled last month. Not because traffic grew — because you're paying for compute you never use.

## License

MIT
