# GitHub README — Mode Template

This mode is for writing GitHub repository READMEs that make developers want to star, clone, and use the project. Not dry reference docs — story-driven introductions that explain why, what, and how.

Core principle: **Story > Reference > Decoration** — A README is the project's front door. Visitors should understand WHY this exists, WHAT it does, and want to try it — in under 2 minutes.

**Anti-principle: Objective does NOT mean plain.** Factual writing must still convey value. "实事求是" means not exaggerating AND not under-selling. A README that accurately describes what a project does but fails to convey why anyone should care is just as broken as one that over-hypes. Every section should be honest AND compelling.

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

## DNA & Voice Settings

**Voice:**
- Temperature: 28°C (warm but professional)
- Posture: Builder — personal, warm, "I built this because..."
- Inner Voice: Optional — can add personality to the Why section
- Translation Immunity: Mandatory for Chinese version

**DNA Overrides:**
- P10 (Scene-First): Optional
- P11 (Progressive Revelation): Full — readers need progressive complexity
- P12 (Scene Over Argument): Optional
- P13 (Concession Turns): Optional
- P14 (Analogy Crack): Optional
- P15 (Ending as Door): Optional

**Core Finding:** Simplified — focus on Shovel 4 (what does this project *really* do?) + Shovel 2 (what assumption about existing tools is wrong?).

---

## Research Protocol Override

Before writing a single word, the agent MUST do deep research. A GitHub README written from surface-level understanding is immediately obvious to developers — it reads like marketing copy, not builder documentation.

### Step R0: Identity Check (MANDATORY — before all other research)

Determine the repository's **identity** — what kind of thing it is. This is not a label exercise; it determines the entire narrative structure.

| Identity | README centers on | Narrative shape |
|----------|-------------------|-----------------|
| **Tool / Product** | Usage, value, results | Why this? → What it does → Features → How to use |
| **Library / SDK** | API, integration, examples | What it provides → Quick start → API reference → Examples |
| **Framework** | Architecture, conventions, ecosystem | Mental model → Getting started → Core concepts → Migration |
| **Methodology / Process** | Principles, evidence, adoption | Problem → Insight → Method → Evidence → How to adopt |
| **Service / Platform** | Capabilities, pricing, getting started | Value prop → Demo → Plans → Quick start |
| **Data / Dataset** | Schema, coverage, access | What's in it → Stats → How to access → Caveats |

**The most common failure is identity confusion** — writing a methodology paper for a working tool, or writing a product pitch for a library. If you're unsure, default to the user's framing. If the user calls it "a tool that does X," write a tool README, not a methodology README.

**Gate:** State the identity in one sentence before proceeding. Example: "This is a CLI tool that generates X from Y." If you cannot state it clearly, you haven't understood the project yet — keep reading code.

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

### Step R3.5: Feature Baseline Filter (MANDATORY)

After identifying the project's features, **separate baseline from differentiators**. This prevents the most common feature-listing failure: promoting default behaviors as key features.

**Process:**

1. List ALL features/characteristics of the project
2. For each feature, ask: **"Is this something all similar projects also have?"**
   - If YES → it's **baseline**. Do not list it as a Key Feature. Mention it only in passing if at all.
   - If NO → it's a **differentiator**. This belongs in Key Features.
3. For borderline cases, ask: **"Would a user be surprised if this feature were MISSING?"**
   - If YES → baseline (users expect it). Omit or mention briefly.
   - If NO → differentiator (users wouldn't assume it). Highlight it.

**Real example of this failure:**

```
❌ Listed "self-contained / distribution-ready" as a key feature of a skill creator.
   But ALL skills in this ecosystem are self-contained by default — it's the baseline.
   Meanwhile, "optional self-evolution" (genuinely rare and valuable) was buried in
   an optional section.

✅ After filtering: removed "distribution-ready" from Key Features, promoted
   "optional self-evolution" to Key Features. The README now highlights what's
   actually different.
```

**Output:** A ranked list of 4-6 genuine differentiators, with baselines explicitly excluded.

### Step R4: Standard Research Protocol

After R0-R3.5, run the standard `core/research-protocol.md` for audience targeting, exclusion analysis, and deep material mining.

---

## Pre-Draft Structure Design (MANDATORY)

After research and before writing any content, **design the README skeleton**. This prevents the most common structural failures: wrong ordering, missing value sections, redundant sections.

### Process

1. **Confirm identity** → pick the narrative shape from R0
2. **Select modules** → from the module template below, decide which to include and which to skip. Not every README needs all modules.
3. **Assign content to modules** → for each selected module, write 1-2 sentences describing what will go there. This catches structural problems before you've written 2000 words.
4. **Check for redundancy** → if GitHub's file tree already shows the project structure clearly, skip the Project Map module. If there are no direct competitors, adapt the comparison module or skip it.
5. **Present to user** → share the skeleton for approval before drafting. Format:

```
Proposed README structure:
1. Hero: "[one-line hook draft]"
2. Why This?: [2-sentence summary of the origin story / problem]
3. What It Is: [1-sentence definition]
4. Key Features: [list 4-6 differentiators by name]
5. With/Without: [confirm comparison dimensions]
6. How It Works: [list subsections]
7. Quick Start: [number of steps]
8. License
Skipping: Project Map (GitHub tree is clear enough)
```

This step adds 30 seconds and prevents 3+ rounds of structural rework.

---

## Module Structure Template

The modules below are ordered by the structure that has been proven to work through iteration. Modules marked **(conditional)** can be skipped if not applicable.

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
❌ "A methodology for building AI agent skills that are actually good" (identity confusion:
    it's a tool, not a methodology)
```

**Badges** (optional but encouraged): build status, license, version, last commit. Place on the line after the hook. Don't overdo it — 3-5 badges max.

### Module 3: Why This? (Problem + Motivation)

2-4 paragraphs. This is the emotional anchor AND intellectual hook of the README.

**This module answers TWO questions:**
1. What problem exists that motivated this project?
2. Why does this project's approach make sense?

**Pattern:** `[The pain] → [What we/others tried] → [Why it wasn't enough] → [The insight that led to this solution]`

This is NOT a corporate "About" section. It's the real story — builder voice, frustration, dead ends, the insight moment. But it's also not JUST a story. By the end of this section, the reader should understand the **problem** and the **core idea** behind the solution.

**Rules:**
- Must contain at least one **specific, concrete pain point** (Layer 3: "so everyone bought a separate Mac Mini just to run it")
- Must name the **root cause**, not just the symptom. "Output is generic" is a symptom. "Skills are designed from author intuition without studying domain experts" is a root cause.
- If the user provided the origin story, preserve their voice and emotional register
- If the origin is unknown, frame it as the problem space: what gap exists, why it matters now
- End this section with the core insight or approach — the reader should think "that makes sense" before seeing the feature list
- Keep it short. This is a hook, not a memoir. 2-4 paragraphs max.

```
✅ "We spent months building AI agent skills — over 100 across Claude Code,
    Codex, and Gemini CLI. The pattern became obvious: most skills that pass
    structural validation still produce generic output.

    We dug into why. The root cause: skill authors design from intuition or
    abstract 'best practices,' without studying how domain experts actually do
    the work. A writing skill that doesn't encode how professional writers think
    will produce AI-flavored text.

    The missing piece: before designing any constraint or workflow, go study how
    the best practitioners in the target domain actually work."

❌ "In today's rapidly evolving AI landscape, security has become a critical
    concern for agent-based systems..." (AI slop — no story, no pain, no voice)

❌ "A skill for AI agents that creates and upgrades other skills. Works on
    Claude Code, Codex, Gemini CLI, and OpenClaw." (accurate but flat — no
    problem, no motivation, no reason to care)
```

### Module 4: What It Is (Concise Definition)

1-3 short paragraphs. State **what the project IS** — identity, form factor, capabilities — in the most concise way possible.

This is NOT the "Core Value" essay. This is the "elevator definition." After reading this, someone should be able to tell another person what this project is in one sentence.

**Rules:**
- Lead with the concrete form: "X is a [CLI tool / Python library / SKILL.md file / GitHub Action] that..."
- State the primary capabilities as a short list (2-4 items max)
- If there's a key constraint or scope boundary, state it here ("works on Linux/macOS, not Windows")
- Do NOT list all features here — that's Module 5's job

```
✅ "Mojo Skill Creator is itself an AI agent skill (SKILL.md + 8 reference files,
    ~8,500 words total). Install it on any agent that supports the SKILL.md format,
    and it gains two capabilities:
    - new — 9-step guided process to create a skill from scratch
    - boost — 4-phase diagnostic and upgrade process for existing skills"

❌ "This project provides a comprehensive toolkit for AI agent skill lifecycle
    management with cross-platform compatibility and token-efficient architecture."
    (jargon soup — what IS it?)
```

### Module 5: Key Features (Bullet List)

4-6 differentiating features, each as a **bold label + 1-3 sentence explanation**.

**This module MUST use the output of Step R3.5 (Feature Baseline Filter).** Only differentiators appear here. Baseline features are either omitted entirely or mentioned in passing within other modules.

**Rules:**
- Each feature must pass the baseline filter: "Would a user of similar projects be surprised this exists?"
- Each feature needs a concrete explanation, not just a label. "Cross-platform" alone is a label. "Instructions use semantic verbs, not platform tool names — one skill package works on all four platforms without modification" is an explanation.
- Order by importance: most impactful differentiator first
- If a feature has a concrete data point (performance number, before/after metric), include it
- Do NOT pad with baseline features to make the list longer. 4 genuine differentiators > 8 mixed with baselines.

```
✅ "- **Domain research first.** Before writing any red line or workflow step,
      the creator guides you to study how the best practitioners actually do
      the task. This single step is the difference between a skill assembled
      from generic parts and one informed by real expertise."

❌ "- **Self-contained packages.** Every skill produced is self-contained."
    (This is baseline — ALL skills in this ecosystem are self-contained.
    Listing it as a feature signals you don't know what's actually special.)
```

### Module 6: With / Without (Comparison Table)

A side-by-side table showing what changes when someone uses this project vs not using it.

**This is the most effective value-communication module.** A good comparison table makes the value concrete and scannable in 10 seconds. It replaces 500 words of explanation.

**Rules:**
- 5-8 rows. Each row is one dimension of comparison.
- Left column: the status quo (without this project, or with the manual approach, or with the closest alternative)
- Right column: with this project
- Each cell: one short phrase, not a paragraph
- Dimensions should cover: starting point, process, quality, efficiency, and at least one "surprising" dimension the reader wouldn't think to compare
- Do NOT include dimensions where both columns would say the same thing — that's a baseline, not a differentiator

```
✅ | | Without Mojo | With Mojo |
   |---|---|---|
   | Starting point | Author's intuition + generic templates | Domain expert workflows + quality standards |
   | Red lines | Vague ("write clearly") or absent | Mechanically checkable, sourced from expert practice |
   | Runtime learning | Static — never improves after deployment | Optional: skill learns from usage |

❌ | Distribution | Requires setup | Easy to install |
   (Both are vague. What setup? What's "easy"? And if all skills are easy to install,
   this row is a baseline, not a differentiator.)
```

### Module 7: How It Works

The technical heart of the README. This is where developer credibility lives.

**This section MUST be written from actual code reading (Step R1), not from surface-level description.**

**Include:**
1. **Subsections per major capability** — If the project has 2-3 distinct modes/commands/features, give each one a ### subsection with its workflow or mechanism explained
2. **Architecture overview** — How the code is organized and why. A diagram is strongly encouraged.
3. **Design decisions** (as a table or subsection) — Why this approach over alternatives? What trade-offs were made? Format as `| Choice | Why |` table for scannability.

**Rules:**
- Show the actual structure, not a marketing version of it
- If there are two architecture levels (conceptual + implementation), show both with a bridging sentence
- Use code snippets from the actual repo to illustrate key points
- Keep it accessible: technical readers should think "well-designed," non-technical readers should think "I see how the pieces fit"
- Design decisions go HERE, not in a separate top-level section. They are part of "how it works."

**Format options:**
- Subsections per command/mode with step lists
- Mermaid/ASCII architecture diagram
- Step-by-step "what happens when you run X" walkthrough
- Key code snippets with explanation
- Design decisions table

### Module 8: Quick Start + Installation

From zero to running in ≤5 steps. Include platform/environment information here.

**Rules:**
- Every step = one action + one command
- Commands must be copy-pasteable (no placeholder values that aren't obvious, or clearly mark what to replace)
- Test the commands mentally: would they work on a fresh machine?
- If prerequisites exist (Node.js version, Python version, API key), state them BEFORE the steps
- If multiple platforms are supported, show a platform table AFTER the install commands
- End with a "you should see..." confirmation or a "now try..." next step so the user knows it worked

```markdown
## Quick Start

**Prerequisites:** Node.js >= 18

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

### Module 9: Project Map (CONDITIONAL)

Annotated directory tree. Shows the structure at a glance.

**When to SKIP this module:**
- The repository has a flat, obvious structure (< 10 files, clear naming)
- GitHub's file tree already makes the structure obvious
- The "How It Works" section already covers the architecture

**When to INCLUDE this module:**
- The repo has a non-obvious organization (why are there 3 config directories?)
- Important files are buried in nested directories
- The project has a plugin/extension structure users need to understand

**Rules:**
- Only show the important files/directories — not every single file
- Each entry gets a brief annotation (what it does / why it exists)
- Use the tree format readers expect

### Module 10: Community & License

Contributing, license, acknowledgments. Keep it brief.

**Include:**
- License (one line + link)
- Acknowledgments / inspirations (if applicable — shows authenticity)
- How to contribute (link to CONTRIBUTING.md if it exists, or 2-3 bullet points)
- Contact / community links (if applicable)

**Rules:**
- Don't write a 50-line contributing guide here — link to CONTRIBUTING.md
- The tone should be welcoming: "We'd love your help" not "Read the contributing guidelines before submitting"

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

### The Objectivity Trap

**Factual and compelling are not opposites.** The most common failure mode after being told "be objective" is to strip all energy from the writing. Here's the distinction:

| Exaggerated (bad) | Objective but flat (also bad) | Objective and compelling (good) |
|---|---|---|
| "Revolutionary AI skill creator that will transform how you build" | "A skill for AI agents that creates and upgrades other skills" | "A skill that creates other skills — starting from how domain experts actually work, not from generic templates" |
| "强大的 AI 技能革命" | "一个创建和升级技能的工具" | "一个用领域专家的真实工作流来创建技能的工具——不是从通用模板拼装" |

The difference: the compelling version **states the same fact** but includes the **differentiating mechanism**. It's still 100% accurate — it just includes the part that makes someone care.

**Rule:** After writing any section, re-read it and ask: "Is this accurate? Yes. Would someone who doesn't already care about this project keep reading? If no, add the mechanism or the contrast — the part that makes it interesting — without adding any claims you can't verify."

### Rhythm

- Short sentences carry the backbone. Long sentences for context.
- The opening (Modules 2-4) is punchy and fast. The middle (Modules 5-7) slows down for depth. The ending (Modules 8-10) is fast again — get them started.
- Paragraphs max 4-5 lines. README readers scan — help them.

### Chinese-Specific

- Don't write 翻译腔 (translationese). Chinese README should sound like it was written in Chinese first.
- Technical terms can stay in English if that's how the Chinese dev community uses them (e.g., "Agent", "Skill", "Token" — don't force-translate to 代理/技能/令牌 if the community doesn't).
- Use 「」for emphasis quotes in Chinese (optional, matches modern Chinese tech writing style).

---

## Writing Workflow (GitHub README)

### Phase 1: Research (EXTENDED)
- Run Steps R0-R4 from the Research Protocol Override above
- This phase takes longer than other modes — deep code reading is mandatory
- **Do not shortcut this.** A README written without understanding the code reads like marketing, and developers can tell.
- **R0 (Identity Check) is the first thing you do.** Everything downstream depends on it.

### Phase 2: Structure Design (MANDATORY)
- After research, design the README skeleton using the Pre-Draft Structure Design process above
- Present the skeleton to the user for approval
- This catches structural problems before you've written 2000 words
- **Do not skip this.** The most common README failure is structural (wrong ordering, missing value sections, redundant sections), not content-level.

### Phase 3: Draft
- Write English version first (README.md)
- Follow the approved module structure
- Apply the writing principles from writing-dna.md
- After each module, re-read and apply the Objectivity Trap check: "Accurate? Yes. Would someone keep reading? If no, add the mechanism."

### Phase 4: Review
- Standard review protocol applies (`core/review-protocol.md`)
- Additional check: every claim in "How It Works" must be verifiable from the actual codebase
- Run Perspective Audit (Dimension 4): README should be firmly in product + user perspective, minimal developer perspective
- **Feature baseline check:** scan Key Features — is any item actually a baseline that all similar projects share? If yes, demote or remove it.

### Phase 5: Polish
- Standard polish protocol applies (`core/humanizer.md`)
- This mode uses builder voice — warmer and more personal than tech-article default

### Phase 5b: Chinese Version
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

### Structure & Identity

- [ ] Identity stated clearly — reader knows what kind of thing this is (tool/library/framework/etc.) within the first 3 sentences?
- [ ] Module order follows the approved skeleton from Phase 2?
- [ ] No module is present that was marked "skip" in the skeleton?

### Content Quality

- [ ] Language selector on the very first line?
- [ ] One-line hook makes someone want to keep reading — states transformation, not technology?
- [ ] "Why This?" section present — reader understands the PROBLEM and the CORE INSIGHT?
- [ ] "What It Is" section is concise (1-3 paragraphs) — reader can explain the project to someone else?
- [ ] Key Features pass the baseline filter — every listed feature is genuinely differentiating?
- [ ] With/Without table present — value is concrete and scannable?
- [ ] "How It Works" based on actual code reading, not surface description?
- [ ] Design decisions included (as table or subsection within How It Works)?
- [ ] Quick Start is ≤5 steps and copy-pasteable?
- [ ] Project Map included ONLY if the structure is non-obvious from GitHub's file tree?

### Anti-Patterns

- [ ] No AI-slop phrases? (search for "随着", "旨在", "In today's rapidly", "aims to", "comprehensive", "robust")
- [ ] No baseline features promoted as key features? (ask: "do all similar projects also have this?")
- [ ] Not a methodology paper disguised as a tool README? (check: does it describe what you DO with it, or what it THINKS about?)
- [ ] Not flat/plain despite being accurate? (check: does each section include the mechanism or contrast that makes it interesting?)
- [ ] No redundant information that GitHub already shows? (file tree, commit history, contributor list)

### Bilingual Quality

- [ ] Chinese version feels native (not translated)?
- [ ] Code blocks, commands, URLs identical in both files?
- [ ] Analogies work in both languages (different analogies OK)?
- [ ] Sync marker present in Chinese file?
- [ ] Would a developer star this repo after reading?
