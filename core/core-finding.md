# Core Finding — Find and Stress-Test the Core

Before structuring any piece of writing, find the one thing it's really about. Surface-level topics produce surface-level writing. This protocol digs to the load-bearing idea underneath.

Applied in Phase 1 Step c of the pipeline. The output — a one-sentence core statement and its stress-test result — feeds directly into Phase 2 (Structure Design).

---

## Step 1: Find the Core (找核)

What you think you want to say and what's actually worth saying are rarely the same thing. Dig one level deeper.

**Four shovels — use any combination until you hit something that resists:**

### Shovel 1: Invert (反转)
Flip the judgment. State the opposite. If the opposite is obviously absurd ("bad code is good"), the original is too obvious to write about — keep digging.

If the opposite is a position someone could genuinely hold, you've found tension. That's where the article lives.

| Original | Inverted | Verdict |
|----------|----------|---------|
| "Code review improves quality" | "Code review doesn't improve quality" | Opposite is defensible → tension exists ✓ |
| "Security matters" | "Security doesn't matter" | Obvious nonsense → original is too bland, dig deeper |

### Shovel 2: Chase the Premise (追问前提)
What assumption does this judgment stand on? The premise is often more worth writing about than the conclusion.

Ask: "This is true... but only if _____ is also true." Fill the blank. That blank is your real topic.

### Shovel 3: Chase the Emotion (追问情绪)
Why does this topic make people uncomfortable, excited, or confused? Emotion points to unspoken cognitive conflict.

If nobody feels anything about it, it's not an article — it's a textbook entry.

### Shovel 4: Flip the Definition (翻转定义)
Take a common word and ask what it really means.

| Surface | Flipped | Article potential |
|---------|---------|-------------------|
| "Taste" | = accumulated experience | High — challenges the "taste is innate" assumption |
| "Harmony" | = conflict avoidance | High — reframes a virtue as a weakness |
| "Busy" | = afraid to stop | High — names what people won't say |

When a flip lands, the entire piece crystallizes around it.

**Validation:** Can you state the core in one sentence? If not → you have multiple cores → keep only one. If you can't dig further → the idea has no depth → tell the user honestly.

---

## Step 2: Attack the Core (攻核)

Once you have a core, stress-test it. Ask the one question that could blow it up:

**"If this is true, then why ______?"**

Find the strongest counter-evidence, the most obvious objection, the fact that shouldn't exist if your core is correct.

**Three outcomes:**

| Result | Action |
|--------|--------|
| **Core holds** | The objection has an answer. Proceed with higher confidence — you've earned your thesis. |
| **Core morphs** | The objection reveals a better version of the idea. Return to Step 1 with the morphed core. |
| **Core breaks** | The idea doesn't survive scrutiny. Tell the user: "This core doesn't hold. Here's what I found instead: ______." |

**Skipping this step = expanding an unexamined opinion.** The article may sound good but won't survive a smart reader's first question.

---

## Step 3: Output

Produce two things before moving to Phase 2:

1. **Core Statement** — One sentence. If it takes two, you haven't finished finding.
2. **Stress-Test Result** — Held / Morphed (state what changed) / Broken (state what replaced it)

---

## Mode-Specific Simplification

Not every writing type needs the full four-shovel treatment. Match depth to purpose:

| Mode | Strategy |
|------|----------|
| tech-article | Full four shovels. Product articles: focus on Shovel 4 (what does this product *really* change?). Design stories: focus on Shovel 2 (what assumption drove the design?). |
| marketing-copy | Full four shovels. Focus on Shovel 3 (what emotion does the reader feel about this problem?). |
| research-report | Full four shovels. Focus on Shovel 2 (what premise does the market assume?). |
| xiaohongshu | Full four shovels. Focus on Shovel 3 (what emotion triggers sharing?). |
| creative-writing | Full four shovels. All four equally important. |
| github-readme | Simplified: Shovel 4 (what does this project *really* do?) + Shovel 2 (what assumption about existing tools is wrong?). |
| technical-docs | Simplified: "What is the core purpose of this document?" + "What is the reader's core confusion?" Two questions, direct answers. |
| rewrite | Diagnose first: does the original have a core? If yes, verify it holds. If no, run the full protocol. |
| editorial-review | Evaluate: does the submitted piece have a clear, defensible core? Report findings without finding your own. |
