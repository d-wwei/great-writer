# Review Protocol — Post-Draft Review

This protocol is MANDATORY after drafting and before humanizing.
The agent runs all three review dimensions and produces a numbered fix list.
ALL fixes must be applied before proceeding to the Humanize phase.

---

## Dimension 1: Structural Review

Check the draft against the mode's template structure.

**For each section in the mode template, verify:**
1. Is the section present? If missing, add it.
2. Is it in the correct order? If not, reorder.
3. Does it meet the length guidelines? If too long, cut. If too short, expand.
4. Does it follow the format requirements? (e.g., comparison table must exist for tech-article)

**Common structural issues:**
- Missing TL;DR or executive summary
- Pain point section buried after a context-setting intro (move it up)
- Feature list instead of scenario-grouped capabilities
- Missing CTA in closing
- No data comparison table when one is required

---

## Dimension 2: Logic Review

Check the argument flow for coherence and persuasion.

**Verify:**
1. **No argument jumps** — Does each section logically follow from the previous? Would a reader ask "wait, why?" at any transition?
2. **Data supports claims** — Every claim is backed by a specific number, example, or source. Flag any unsupported claims: `[⚠️ Unsupported: ...]`
3. **No self-contradictions** — Does the piece claim something in paragraph 3 that conflicts with paragraph 7?
4. **"So what?" test** — For each finding or feature, is it clear why the reader should care? If not, add the implication.
5. **Differentiation holds** — If the piece claims "we're better because X," verify X is actually different from competitors, not just described differently.

**Common logic issues:**
- Claiming "faster" without benchmark data
- Pain point doesn't connect to the solution presented
- Features listed without explaining WHY they matter
- Competitor comparison that's not actually fair (comparing free tier to paid tier)

---

## Dimension 3: Fact Check

Verify accuracy of all data and claims.

**Required checks:**
1. **Numbers are accurate** — Do the math. "96% reduction" means going from X to 0.04X. Is that what the data shows?
2. **Citations are real** — If a source is cited, it should exist. If search tools are available, verify URLs and claims.
3. **Dates are current** — No "as of 2024" in a 2026 article unless discussing historical context.
4. **Names and terms are correct** — Product names, company names, technical terms spelled correctly.
5. **Comparisons are fair** — Same tier, same use case, same conditions.

**If search tools are available:**
- Actively verify key claims against live sources
- Check if cited products/features still exist
- Confirm pricing and performance numbers are current

**If no search tools:**
- Flag unverifiable claims: `[⚠️ Needs verification: claim about X]`
- Ask the user to confirm critical data points

---

## Output Format

After reviewing all three dimensions, produce a numbered fix list:

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
```

**Rule:** ALL "Must Fix" items are resolved before proceeding. "Should Fix" items are resolved unless the user overrides. "Nice to Fix" items are optional.
