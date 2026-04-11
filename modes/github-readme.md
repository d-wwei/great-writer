# GitHub README — Mode Template

This mode is for writing GitHub repository READMEs that make developers want to star, clone, and use the project. Not dry reference docs — story-driven introductions that explain why, what, and how.

Core principle: **Story > Reference > Decoration** — A README is the project's front door. Visitors should understand WHY this exists, WHAT it does, and want to try it — in under 2 minutes.

Activated when: GitHub README, repo README, project README, write a README, 写 README, 仓库介绍, 仓库 README, GitHub 仓库介绍

---

## Bilingual Output (Mandatory)

Every GitHub README produced by this mode outputs **two files**:

| File | Language | Content |
|------|----------|---------|
| `README.md` | English | Primary — most GitHub traffic is English |
| `README.zh.md` | Chinese (Simplified) | Full Chinese version, not a translation |

### Bilingual Rules

1. **Both files open with a language selector** on the very first line:
   - In README.md: `[English](README.md) | [中文](README.zh.md)`
   - In README.zh.md: `[English](README.md) | [中文](README.zh.md)`

2. **Each version must feel native to its language.** The Chinese version is not a machine translation of the English — it's rewritten to sound natural in Chinese. Sentence structures, idioms, and emphasis may differ. The information is the same; the expression adapts.

3. **What stays identical across both files:**
   - Code blocks, commands, CLI examples
   - Variable names, function names, file paths
   - Badge URLs and image links
   - Architecture diagrams (labels can be translated if in text form)
   - GitHub links, installation commands

4. **What gets rewritten (not translated):**
   - Section headings
   - All prose and explanations
   - Analogy choices (a great analogy in English may not land in Chinese — find a better one)
   - The hook / one-liner

5. **Sync marker:** Add an HTML comment at the top of `README.zh.md` for sync tracking:
   ```html
   <!-- Synced with README.md as of [date] -->
   ```

---

## Research Protocol Override

Before writing a single word, the agent MUST do deep research. A GitHub README written from surface-level understanding is immediately obvious to developers — it reads like marketing copy, not builder documentation.

### Step R1: Read the Actual Code

Do NOT write the README from the existing README, docs, or user prompt alone. Use Glob, Grep, and Read tools to:

1. **Map the entry points** — What files does the user interact with first? (`main.py`, `index.ts`, `SKILL.md`, `Makefile`, etc.)
2. **Trace the core logic** — Follow the main execution path. What happens when someone runs the project? What are the key transformations?
3. **Identify architectural decisions** — How is the code organized? Why this structure and not another? What patterns are used?
4. **Find hidden gems** — Non-obvious features, clever implementations, design constraints that shaped the architecture.

**Output:** A mental model of how the project actually works, not just what it claims to do.

### Step R2: Identify the Origin Story

Ask the user (if not already provided):
- "Why did you build this? What problem hit you hard enough to start coding?"
- "Was there a specific moment or frustration that triggered it?"
- "What existing solutions did you try first, and why weren't they enough?"

If the user doesn't want to share a personal story, the origin can be framed as the problem space: what gap exists, why it matters.

### Step R3: Find the Unique Value

Ask (if not obvious from code reading):
- "What does this project do that nothing else does?"
- "If someone asks 'why not just use X instead?', what's your answer?"

The unique value must be **concrete and verifiable**, not marketing fluff. "50x faster" is concrete. "Better developer experience" is fluff unless you explain exactly how.

### Step R4: Standard Research Protocol

After R1-R3, run the standard `core/research-protocol.md` for audience targeting, exclusion analysis, and deep material mining.

---

## 10-Module Structure Template

### Module 1: Language Selector

The very first line of the file. No blank lines before it.

```markdown
[English](README.md) | [中文](README.zh.md)
```

### Module 2: Hero Section

Project name (H1) + one-line hook + optional badge row.

**The hook** is the single most important sentence in the README. It should:
- State what the project does in terms of the **transformation** it creates, not the technology it uses
- Be specific enough to filter: the right reader thinks "I need this," the wrong reader moves on
- Avoid generic claims ("powerful," "flexible," "easy-to-use")

```
✅ "Turn any thinking framework into an installable cognitive base for AI agents —
    change how they think, not just what they can do."

✅ "One skill file that gives any AI agent 9 writing modes, bilingual output,
    and anti-AI-slop protection."

❌ "A powerful and flexible tool for AI agents"
❌ "一个强大的 AI 工具"
```

**Badges** (optional but encouraged): build status, license, version, last commit. Place on the line after the hook. Don't overdo it — 3-5 badges max.

### Module 3: Origin Story (Why This Exists)

2-4 paragraphs. This is the emotional anchor of the README.

**Pattern:** `[The pain] → [What we tried] → [Why it wasn't enough] → [The moment we decided to build this]`

This is NOT a corporate "About" section. It's the real story. Builder voice — frustration, dead ends, the "screw it, I'll build it myself" moment.

**Rules:**
- Must contain at least one **specific, concrete pain point** (Layer 3 from the pain point framework: "so everyone bought a separate Mac Mini just to run it")
- If the user provided the origin story, preserve their voice and emotional register
- If the origin is unknown, frame it as the problem space: what gap exists, why it matters now
- Keep it short. This is a hook, not a memoir. 2-4 paragraphs max.

```
✅ "We were building AI agents that could execute shell commands, read files,
    access networks. Then we realized: these agents are exactly as dangerous
    as they are capable. Our first instinct was to look at how others solved it.
    Four projects later, we found the same answer everywhere — sandbox it,
    restrict it, hope for the best. That wasn't good enough."

❌ "In today's rapidly evolving AI landscape, security has become a critical
    concern for agent-based systems..." (AI slop — no story, no pain, no voice)
```

### Module 4: Core Value (What It Actually Does)

1-2 paragraphs + optional diagram. State the **fundamental transformation**, not a feature list.

**Rules:**
- Describe from the underlying change, not the surface manifestation (writing-dna Principle 6)
- One sentence should capture what 80% of users need to know
- If the project has a key data point (performance gain, cost reduction, etc.), anchor it here
- A good architecture diagram or flow chart here is worth 500 words

```
✅ "Cognitive bases are meta-cognitive rules written into the agent's identity
    file (CLAUDE.md, AGENTS.md). They change HOW the agent thinks — across
    every conversation, every project, without being called."

    The core shift: from "tools the agent uses" to "how the agent thinks."

❌ "This project provides a set of configurable rules that can be installed
    into various AI agent platforms to modify their behavior." (accurate but dead)
```

### Module 5: How It Works

The technical heart of the README. This is where developer credibility lives.

**This section MUST be written from actual code reading (Step R1), not from surface-level description.**

**Include:**
1. **Architecture overview** — How the code is organized and why. A diagram is strongly encouraged.
2. **Core mechanism** — The key technical insight that makes it work. Walk through the main execution path.
3. **Design decisions** — Why this approach over alternatives? What trade-offs were made?

**Rules:**
- Show the actual structure, not a marketing version of it
- If there are two architecture levels (conceptual + implementation), show both with a bridging sentence
- Use code snippets from the actual repo to illustrate key points
- Keep it accessible: technical readers should think "well-designed," non-technical readers should think "I see how the pieces fit"

**Format options:**
- Directory tree with annotations
- Mermaid/ASCII architecture diagram
- Step-by-step "what happens when you run X" walkthrough
- Key code snippets with explanation

### Module 6: What Makes It Different

Direct comparison with alternatives. Not vague claims — concrete, verifiable differences.

**Pattern:** For each differentiator: `[How others do it] → [The problem with that] → [How we do it] → [The result]`

**Rules:**
- Name the alternatives explicitly. "Other tools" is not a comparison — "LangChain's approach" is.
- If there are no direct alternatives, compare with the "manual approach" — what would someone do without this project?
- Use a comparison table if there are 3+ dimensions of difference
- Every claimed advantage must be verifiable from the code or measurable in use

### Module 7: See It In Action

Demos, examples, or before/after comparisons.

**Options (pick the most compelling for this project):**
- Before/after output comparison
- Screenshot or GIF of the tool in action
- Minimal code example that produces a visible result
- "Try it in 30 seconds" sandbox link

**Rules:**
- At least ONE concrete example must be present. A README with no demo is asking readers to trust on faith.
- Code examples must be copy-pasteable and actually work
- If the project produces visible output, show the actual output
- If screenshots/GIFs don't exist yet, add placeholder with instruction: `<!-- TODO: Add screenshot of [specific thing] -->`

### Module 8: Quick Start

From zero to running in ≤5 steps.

**Rules:**
- Every step = one action + one command
- Commands must be copy-pasteable (no placeholder values that aren't obvious, or clearly mark what to replace)
- Test the commands mentally: would they work on a fresh machine?
- If prerequisites exist (Node.js version, Python version, API key), state them BEFORE the steps
- End with a "you should see..." confirmation so the user knows it worked

```markdown
## Quick Start

**Prerequisites:** Node.js ≥ 18

\```bash
# 1. Install
npm install -g cognitive-base-creator

# 2. Generate a base from any framework
cbc generate "first principles thinking" --output first-principles.md

# 3. Install into your agent
cp first-principles.md ~/.claude/

# You should see the cognitive base loaded on next Claude Code session.
\```
```

### Module 9: Project Map

Annotated directory tree. Shows the structure at a glance.

**Rules:**
- Only show the important files/directories — not every single file
- Each entry gets a brief annotation (what it does / why it exists)
- Use the tree format readers expect

```markdown
## Project Structure

\```
project/
├── SKILL.md              # Router — maps user intent to writing mode
├── core/                 # Shared modules (loaded by all modes)
│   ├── writing-dna.md    # 7 universal writing principles
│   ├── research-protocol.md  # Pre-writing research protocol
│   ├── review-protocol.md    # Post-draft 4-dimension review
│   └── humanizer.md      # Anti-AI-slop protocol
├── modes/                # One file per writing type
│   ├── tech-article.md   # WeChat, blogs, product launches
│   ├── github-readme.md  # GitHub READMEs (this mode)
│   └── ...
└── scripts/
    └── bundle.sh         # Generates single-file version
\```
```

### Module 10: Community

Contributing, license, acknowledgments. Keep it brief but welcoming.

**Include:**
- How to contribute (link to CONTRIBUTING.md if it exists, or 2-3 bullet points)
- License (one line + link)
- Acknowledgments / inspirations (if applicable)
- Contact / community links (if applicable)

**Rules:**
- Don't write a 50-line contributing guide here — link to CONTRIBUTING.md
- The tone should be welcoming: "We'd love your help" not "Read the contributing guidelines before submitting"
- If the project has a specific acknowledgment or inspiration, include it — it shows authenticity

---

## Tone Rules

### Voice

**Builder voice** — the README is written by someone who built this thing and is proud of it. Not marketing copy, not academic paper, not corporate documentation.

| Do | Don't |
|----|-------|
| "We built this because we were sick of..." | "This project aims to address..." |
| "The key insight: X and Y are the same structure" | "Our innovative approach leverages..." |
| "Install it. Run it. See what changes." | "Please refer to the installation guide for setup instructions." |
| 我们受够了每次都要…… | 本项目旨在解决…… |
| 核心洞察：X 和 Y 本质上是同一个结构 | 我们的创新方案充分利用了…… |

### Rhythm

- Short sentences carry the backbone. Long sentences for context.
- The opening (Modules 2-4) is punchy and fast. The middle (Modules 5-6) slows down for depth. The ending (Modules 8-10) is fast again — get them started.
- Paragraphs max 4-5 lines. README readers scan — help them.

### Chinese-Specific

- Don't write 翻译腔 (translationese). Chinese README should sound like it was written in Chinese first.
- Technical terms can stay in English if that's how the Chinese dev community uses them (e.g., "Agent", "Skill", "Token" — don't force-translate to 代理/技能/令牌 if the community doesn't).
- Use 「」for emphasis quotes in Chinese (optional, matches modern Chinese tech writing style).

---

## Writing Workflow (GitHub README)

### Phase 1: Research (EXTENDED)
- Run Steps R1-R4 from the Research Protocol Override above
- This phase takes longer than other modes — deep code reading is mandatory
- **Do not shortcut this.** A README written without understanding the code reads like marketing, and developers can tell.

### Phase 2: Draft
- Write English version first (README.md)
- Follow the 10-module structure in order
- Apply the 7 writing principles from writing-dna.md

### Phase 3: Review
- Standard review protocol applies (`core/review-protocol.md`)
- Additional check: every claim in "How It Works" and "What Makes It Different" must be verifiable from the actual codebase
- Run Perspective Audit (Dimension 4): README should be firmly in product + user perspective, minimal developer perspective

### Phase 4: Humanize
- Standard humanizer applies (`core/humanizer.md`)
- This mode uses builder voice — warmer and more personal than tech-article default

### Phase 5: Chinese Version
- Rewrite (not translate) the English README into Chinese
- Verify all bilingual rules are followed
- Run humanizer again on the Chinese version specifically (Chinese AI-slop patterns differ from English)

### Phase 6: Finalize
- Run the self-check checklist below on BOTH files
- Verify cross-links work
- Verify code blocks are identical across both files

---

## Self-Check Checklist

Run through every item after both README files are complete.

### Both Files

- [ ] Language selector on the very first line?
- [ ] One-line hook makes someone want to keep reading?
- [ ] Origin story present — reader understands WHY this project exists?
- [ ] Core value stated as transformation, not feature list?
- [ ] "How it works" section based on actual code reading, not surface description?
- [ ] Unique value articulated concretely — what makes this different?
- [ ] At least one demo/example present?
- [ ] Quick start is ≤5 steps and copy-pasteable?
- [ ] Project structure annotated?
- [ ] No AI-slop phrases? (search for "随着", "旨在", "In today's rapidly", "aims to")
- [ ] Would a developer star this repo after reading?

### Bilingual Quality

- [ ] Chinese version feels native (not translated)?
- [ ] Code blocks, commands, URLs identical in both files?
- [ ] Analogies work in both languages (different analogies OK)?
- [ ] Sync marker present in Chinese file?
