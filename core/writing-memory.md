# Writing Memory — Cross-Session Content Persistence

This module enables great-writer to remember project-specific writing context
across sessions: brand voice, key terminology, recurring data points, and style decisions.

Activated when:
- "记住这个风格" / "remember this style"
- "保存写作记忆" / "save writing memory"
- "用上次的设定" / "use last session's settings"
- Automatically after completing any writing task (offers to save useful context)

---

## What Gets Remembered

### Brand & Terminology
- **Product name** and how to refer to it (official name, abbreviations, never-use names)
- **Competitor names** and how to reference them (neutral terms, comparison framing)
- **Technical terms** and their approved definitions / analogies
- **Banned terms** — words the brand never uses

### Content Assets
- **Killer data points** — the numbers that recur across multiple pieces
- **Proven analogies** — analogies that worked well and can be reused
- **Boilerplate sections** — standard "About us", compatibility lists, quick-start instructions
- **Source materials** — links to docs, repos, datasets used in research

### Style Decisions
- **Style fingerprint** (from style-learner) — if one was created, persist it
- **Tone calibration** — any user feedback on tone ("too formal", "more casual")
- **Platform preferences** — default target platform, preferred length
- **Humanizer adjustments** — any user-approved exceptions to blacklist rules

### Audience Profile
- **Default reader persona** — who usually reads this project's content
- **Technical level** — so research protocol doesn't re-ask every time
- **Context** — where content typically appears (WeChat, blog, internal, etc.)

---

## Storage Location

Writing memory is stored per-project:

```
.great-writer/
├── memory.md          # Main memory file (key-value, human-readable)
├── styles/            # Saved style fingerprints
│   └── brand-voice.md
└── assets/            # Boilerplate sections, data tables, etc.
    └── comparison-table.md
```

If `.great-writer/` doesn't exist, offer to create it on first save.

If the project has an `.assistant/` directory (companion-bootstrap system), writing memory integrates:
- Store in `.assistant/memory/writing/` instead of `.great-writer/`
- Follow the existing memory policy for the project

---

## Memory File Format

`memory.md` uses a simple, human-editable format:

```markdown
# Writing Memory — [Project Name]

Last updated: 2026-03-28

## Brand
- Product name: Great Writer
- Short name: GW
- Never use: "GreatWriter" (no space), "great_writer"
- Competitor references: "other writing skills", "typical single-mode skills"

## Key Data
- 5 writing modes (vs industry typical 1)
- 30+ bilingual blacklist rules
- 60%+ context savings with modular loading
- 6-phase pipeline with independent re-run

## Proven Analogies
- "分诊台 + 专科医生" (for router architecture)
- "固定手册 vs 专科医生" (for skill comparison)

## Audience
- Default: AI Agent users, tech PMs, content creators
- Technical level: mixed
- Primary platform: WeChat 公众号

## Style
- Tone: professional-casual, data-driven
- Fingerprint: (see styles/brand-voice.md if exists)
- User feedback: (none yet)

## Boilerplate
- Quick start: (see assets/quick-start.md if exists)
- Compatibility list: any LLM agent (skill directory or system prompt injection)
```

---

## How Memory Is Used

### During Phase 1 (Core Logic — Research)
- Pre-fill audience targeting from memory (skip re-asking if already known)
- Load key data points as starting material
- Load competitor names and framing

### During Phase 3 (Draft)
- Apply saved style fingerprint (if exists)
- Use proven analogies where relevant
- Insert boilerplate sections where appropriate
- Use correct brand terminology

### During Phase 5 (Polish)
- Apply any user-approved polish exceptions
- Check against saved style fingerprint

### During Phase 6 (Finalize)
- Verify brand terminology consistency
- Check that key data points match saved values (no contradictions)

---

## Memory Lifecycle

### Save Triggers
After completing any writing task, offer to save useful context:

> "This session produced some reusable context (brand terms, data points, style decisions). Want me to save them to writing memory? (保存写作记忆？)"

Only save if the user agrees. Never silently write memory files.

### Update
When new content contradicts existing memory:
1. Flag the contradiction: "Memory says [X], but this draft uses [Y]. Which is correct?"
2. Update memory after user confirms
3. Never silently overwrite — always confirm

### Cleanup
When memory grows stale:
- Mark items with last-used dates
- After 30 days unused, suggest reviewing: "These memory items haven't been used in a month: [list]. Keep or remove?"
- Never auto-delete

---

## Privacy

- Writing memory is stored locally, never uploaded
- Memory files are human-readable and editable
- User can delete any memory file at any time
- Memory is project-scoped — never leaks between projects
