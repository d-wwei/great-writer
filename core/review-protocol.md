# Review Protocol — Post-Draft Review

This protocol is MANDATORY after drafting and before humanizing.
The agent runs all four review dimensions and produces a numbered fix list.
ALL fixes must be applied before proceeding to the Humanize phase.

---

## Dimension 1: Structural Review

Check the draft against the mode's template structure.

**For each section in the mode template, verify:**
1. Is the section present? If missing, add it.
2. Is it in the correct order? If not, reorder.
3. Does it meet the length guidelines? If too long, cut. If too short, expand.
4. Does it follow the format requirements? (e.g., comparison table must exist for tech-article)

5. **No example repetition** — Track every example/anecdote by its first appearance. If the same example is fully expanded in two different sections (e.g., as hook AND as scenario), collapse the second occurrence to a one-sentence callback: "回到开头那个 MBA 的例子" / "Returning to the MBA example from the opening." Structure serves reading experience — don't repeat content for structural completeness.
6. **No designer-perspective sections** — Remove sections that describe internal design decisions, constraints, or principles that don't affect user understanding or usage. Test: if you delete this section, can the reader still understand and use the product? If yes, delete it. Keep the reader on the path: problem → solution → mechanism → evidence → get started.

**Common structural issues:**
- Missing TL;DR or executive summary
- Pain point section buried after a context-setting intro (move it up)
- Feature list instead of scenario-grouped capabilities
- Missing CTA in closing
- No data comparison table when one is required
- Same example fully expanded in two different sections (dedup it)
- Internal design notes masquerading as user-facing content (remove them)

---

## Dimension 2: Logic Review

Check the argument flow for coherence and persuasion.

**Verify:**
1. **No argument jumps** — Does each section logically follow from the previous? Would a reader ask "wait, why?" at any transition?
2. **Data supports claims** — Every claim is backed by a specific number, example, or source. Flag any unsupported claims: `[⚠️ Unsupported: ...]`
3. **No self-contradictions** — Does the piece claim something in paragraph 3 that conflicts with paragraph 7?
4. **"So what?" test** — For each finding or feature, is it clear why the reader should care? If not, add the implication.
5. **Differentiation holds** — If the piece claims "we're better because X," verify X is actually different from competitors, not just described differently.

6. **Claim → Mechanism within 2-3 paragraphs** — When the article claims an unusual capability (e.g., "always-on across conversations," "zero-latency sync"), verify that the mechanism explaining HOW is present within 2-3 paragraphs of the claim. Pattern: claim → mechanism → therefore. Without mechanism, technical readers classify the claim as marketing, not fact.
7. **Self-contradiction scan** — After completing each section, check: does this section contradict any other section? Pay special attention to "constraint" and "principle" statements — if the article says "we never use X," verify the article itself doesn't use X. Also verify the article doesn't present internal design principles as user-facing constraints.
8. **"A vs B" needs structured comparison** — When the article's core argument is the difference between two concepts (e.g., "Skill vs Cognitive Base"), prose description alone is insufficient. Provide at least one structured comparison (table, side-by-side diagram, or dimension-by-dimension breakdown). The reader should be able to answer "what's different" in 10 seconds without reading full paragraphs.

**Common logic issues:**
- Claiming "faster" without benchmark data
- Pain point doesn't connect to the solution presented
- Features listed without explaining WHY they matter
- Competitor comparison that's not actually fair (comparing free tier to paid tier)
- Capability claim with no mechanism explanation (readers think it's marketing)
- Section contradicts another section (especially constraint/principle statements)
- A-vs-B argument explained only in prose without any structured comparison

---

## Dimension 3: Fact Check

Verify accuracy of all data and claims.

**Required checks:**
1. **Numbers are accurate** — Do the math. "96% reduction" means going from X to 0.04X. Is that what the data shows?
2. **Citations are real** — If a source is cited, it should exist. If search tools are available, verify URLs and claims.
3. **Dates are current** — No "as of 2024" in a 2026 article unless discussing historical context.
4. **Names and terms are correct** — Product names, company names, technical terms spelled correctly. **Critical:** Verify product/repo names are the current *public* names, not internal development names. If the user provided a repo link, check the README for the current display name. Dev names ≠ release names (e.g., "what is good job" was renamed to "results-driven").
5. **Comparisons are fair** — Same tier, same use case, same conditions.
6. **Disciplinary classifications are accurate** — When the article involves multiple academic disciplines or fields:
   - Is each discipline label correct? ("社会学" vs "认知科学" vs "行为经济学" — these are not interchangeable)
   - Are cross-discipline mappings structurally rigorous (genuine structural isomorphism) or just surface-level similarity?
   - If unsure about a classification, flag it: `[⚠️ Needs verification: discipline classification of X]`
   - Wrong discipline labels are caught immediately by expert readers and undermine the entire article's credibility.

**If search tools are available:**
- Actively verify key claims against live sources
- Check if cited products/features still exist
- Confirm pricing and performance numbers are current

**If no search tools:**
- Flag unverifiable claims: `[⚠️ Needs verification: claim about X]`
- Ask the user to confirm critical data points

---

## Dimension 4: Perspective Audit

The single most common failure mode in AI writing: **sliding into developer perspective** when the reader needs product or user perspective.

Three perspectives exist. They must not be mixed carelessly:

| Perspective | Content | Belongs in article? |
|-------------|---------|-------------------|
| **Developer** | Internal design decisions, technical constraints, implementation details, architecture trade-offs | Only when the mechanism directly explains a user-facing capability |
| **Product** | What it does, how it achieves it, how it differs from alternatives | Main body of the article |
| **User** | What changes after I install it, how to install, how to verify it works | Most important — reader must be able to extract concrete actions |

**Required check:** For each section, identify which perspective it's written from. Flag any section that is pure developer-perspective with no user/product value. Common offenders:
- Design principles that don't affect usage ("axis independence," "zero-jargon rule")
- Internal architecture details without user-perceivable implications
- Technical constraints that readers don't need to know to use the product

**The reader's path must be unbroken:** Problem → Solution → Mechanism → Evidence → Get Started. Every section should advance this path. Sections that don't (developer-perspective detours) break the reader's momentum.

---

## Output Format

After reviewing all four dimensions, produce a numbered fix list:

```
## Review Findings

### Must Fix
1. [Structural] Missing comparison table in Section 4. Add three-way comparison.
2. [Logic] Paragraph 5 claims "10x faster" but no benchmark data provided. Add source or remove claim.
3. [Fact] Competitor pricing listed as $99/mo — verify this is current.

### Should Fix
4. [Structural] Quick-start section has 7 steps — reduce to 5 or fewer.
5. [Logic] Transition from pain point to solution is abrupt. Add one bridging sentence.

### Nice to Fix
6. [Structural] Feature group 3 only has 2 items — consider merging with group 2.
7. [Perspective] Section 3 ("Design Principles") is pure developer-perspective — delete or fold into mechanism explanation.
```

**Rule:** ALL "Must Fix" items are resolved before proceeding. "Should Fix" items are resolved unless the user overrides. "Nice to Fix" items are optional.
