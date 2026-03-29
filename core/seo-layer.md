# SEO/GEO Layer — Search Optimization Extension

An OPTIONAL enhancement layer for marketing-copy and tech-article modes.
Not loaded by default — activated when user mentions SEO, search ranking, keywords,
or when the content target is a public-facing web page.

Activated when: "SEO优化", "搜索优化", "关键词", "SEO", "search optimization", "keywords", "rank for", "GEO"

---

## When to Use

- Content will be published on a website (blog, landing page, docs)
- User wants to rank for specific search terms
- User mentions keywords, search intent, or organic traffic
- Content targets generative search results (GEO — Generative Engine Optimization)

## When NOT to Use

- WeChat 公众号 articles (not indexed by search engines)
- 小红书 notes (platform has its own discovery algorithm)
- Internal documentation
- Email or Slack content

---

## SEO Checklist (Apply During Phase 5)

### Title & Meta

- [ ] **Title tag:** Contains primary keyword, ≤60 chars, compelling to click
  - Formula: `[Primary keyword] + [Benefit or number] + [Differentiator]`
  - ✅ "AI Writing Skill: 5 Modes, Zero AI Slop — Great Writer"
  - ❌ "Great Writer — A Universal Writing Skill for AI Agents"
- [ ] **Meta description:** Contains primary keyword, ≤155 chars, includes CTA
  - ✅ "One AI writing skill for tech articles, marketing copy, research reports, and more. Research-driven, anti-AI-slop. Free on GitHub."
- [ ] **H1:** Matches title tag intent, contains primary keyword
- [ ] **URL slug:** Short, keyword-rich, no filler words (`/ai-writing-skill` not `/introducing-our-new-universal-ai-writing-skill`)

### Content Optimization

- [ ] **Primary keyword** appears in: title, first paragraph, one H2, closing
- [ ] **Secondary keywords** (3-5) appear naturally throughout the body
- [ ] **Keyword density:** 1-2% for primary, <1% for each secondary (don't stuff)
- [ ] **Headers hierarchy:** H1 → H2 → H3, no skipped levels
- [ ] **Internal links:** 2-3 links to related content on same site (if applicable)
- [ ] **External links:** 1-2 authoritative outbound links (builds trust)
- [ ] **Image alt text:** Descriptive, includes keyword where natural
- [ ] **Content length:** Matches search intent (informational: 1500+ words, transactional: 500-1000)

### Search Intent Alignment

Before writing, identify the search intent behind the target keyword:

| Intent | User Wants | Content Should |
|--------|-----------|----------------|
| **Informational** | Learn about a topic | Educate, explain, compare |
| **Navigational** | Find a specific page | Be that page, clear branding |
| **Transactional** | Take an action | CTA-heavy, benefit-focused |
| **Commercial investigation** | Compare options | Comparison tables, pros/cons |

**Rule:** Content MUST match the dominant search intent. A transactional keyword needs a CTA, not a 3000-word explainer.

### GEO (Generative Engine Optimization)

For content that should appear in AI-generated search results (Google AI Overviews, Perplexity, etc.):

- [ ] **Direct answers:** Include clear, concise answers to likely questions in the first 2-3 paragraphs
- [ ] **Structured data:** Use clear headers, tables, and lists that AI can easily extract
- [ ] **Cite sources:** Include specific numbers with sources — AI search engines prefer citable content
- [ ] **FAQ section:** Add 3-5 Q&A pairs for common questions (optional but powerful for GEO)
- [ ] **Unique data:** Original research, benchmarks, or comparisons that can't be found elsewhere — this is what AI cites

---

## Keyword Research (Lightweight)

If the user hasn't provided keywords, do a quick research:

1. **Ask the user:** "What would someone search for to find this content? Give me 2-3 search phrases."
2. **If search tools available:** Verify search volume and competition for suggested keywords
3. **If no search tools:** Use common sense — the keyword should match what the content actually delivers

**Output:** Primary keyword + 3-5 secondary keywords + identified search intent

---

## A/B Title Suggestions

After the article is finalized, generate 3 alternative titles optimized for different intents:

```
## Title Options

1. **Click-optimized:** "5 种写法 1 个 Skill：AI 写作告别套话时代"
   (Emotional hook for social sharing)

2. **SEO-optimized:** "AI Writing Skill: 5 Modes for Tech Articles, Marketing, and Docs"
   (Primary keyword front-loaded)

3. **GEO-optimized:** "What Is the Best AI Writing Skill? Great Writer Covers 5 Types"
   (Question format for AI search results)
```

---

## Integration with Modes

This layer is additive — it doesn't replace any mode's structure. It adds checks AFTER the normal pipeline:

```
Phase 1-4: Normal pipeline
Phase 5: Mode-specific checklist
Phase 5+: SEO/GEO checklist (if activated)
```

### Mode-Specific SEO Notes

| Mode | SEO Considerations |
|------|-------------------|
| tech-article | Blog posts rank well — prioritize informational keywords |
| marketing-copy | Landing pages need transactional keywords and schema markup |
| research-report | Long-form content with unique data ranks for featured snippets |
| technical-docs | Documentation ranks highly — use exact tool/API names as keywords |
| xiaohongshu | Skip SEO layer — RED has its own algorithm |
| rewrite | Apply SEO only if the rewritten content goes to web |

---

## Self-Check Checklist

- [ ] Primary keyword identified and placed in title, first paragraph, H2, closing?
- [ ] Meta description written with keyword and CTA?
- [ ] Search intent identified and matched?
- [ ] Content length appropriate for intent?
- [ ] No keyword stuffing (reads naturally)?
- [ ] GEO elements present (direct answers, structured data, unique data)?
- [ ] 3 alternative title options provided?
