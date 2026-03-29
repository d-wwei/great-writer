# Technical Documentation — Mode Template

This mode is for documentation and technical writing: READMEs, API documentation,
changelogs, release notes, internal guides, and decision records.

Core principle: **Clarity > Completeness > Elegance**

Activated when: README, API docs, API文档, changelog, release notes, 技术文档, 内部文档, internal guide, technical docs, decision record

---

## Humanizer Overrides

This mode applies STRICTER humanizer settings:
- **No rhetorical questions** — docs answer, they don't ask
- **No conversational asides** — every word serves a purpose
- **No emojis** — except in changelogs where category markers are useful
- **Pure clarity** — if a sentence can be shorter, make it shorter

---

## Sub-Type 1: README

### Structure

1. **One sentence: what is this**
   - No marketing. No adjectives. Just what it does.
   - ✅ "A CLI tool that converts Markdown to PDF with syntax highlighting."
   - ❌ "A powerful, comprehensive solution for all your document conversion needs."
   - ✅ 一个把 Markdown 转成 PDF 的命令行工具，支持代码高亮。
   - ❌ 一个强大的、全面的文档转换解决方案。

2. **Why you need it**
   - What problem it solves. 2-3 sentences, user perspective.
   - ✅ "Existing tools either lose formatting or can't handle code blocks. This one does both, offline, in under a second."
   - ❌ "In today's fast-paced development environment, documentation is more important than ever..."

3. **Quick start**
   - ≤5 steps from zero to working. All commands copy-pasteable.
   ```bash
   npm install -g md2pdf
   md2pdf README.md
   # → README.pdf created (0.3s)
   ```

4. **Core features**
   - Scenario-based: "You can..." not "Supports..."
   - 4-6 items max.
   - ✅ "Convert any .md file with one command"
   - ❌ "Supports Markdown file conversion functionality"

5. **Installation / Configuration**
   - Platform-specific tabs if needed (macOS / Linux / Windows)
   - Every command tested and runnable

6. **Contributing guide** — optional, link to CONTRIBUTING.md

---

## Sub-Type 2: API Documentation

### Per-Endpoint Structure

Each endpoint follows this exact format:

```markdown
### `POST /api/v1/convert`

Convert a Markdown file to PDF.

**Request:**

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| content | string | yes | Markdown content |
| format | string | no | Output format: "pdf" (default), "html" |

**Example request:**
\```bash
curl -X POST https://api.example.com/api/v1/convert \
  -H "Authorization: Bearer $TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"content": "# Hello", "format": "pdf"}'
\```

**Response (200):**
\```json
{
  "url": "https://cdn.example.com/output/abc123.pdf",
  "size_bytes": 24576,
  "pages": 1
}
\```

**Errors:**

| Code | Meaning |
|------|---------|
| 400 | Invalid Markdown or missing content field |
| 401 | Invalid or expired token |
| 413 | Content exceeds 10MB limit |
```

**Rules:**
- Examples MUST be copy-runnable. Never show a fake URL or wrong payload.
- Every error code documented with clear meaning.
- Request and response schemas match exactly.

---

## Sub-Type 3: Changelog

### Input
Git history, PRs, release notes.

### Process
1. Filter noise: skip "fix typo", "update deps", merge commits, CI changes
2. Translate to user perspective
3. Categorize and format

### Categories

| Category | Meaning | Example |
|----------|---------|---------|
| **New** | Wholly new features | "PDF export with custom themes" |
| **Improved** | Enhanced existing features | "Page load 40% faster" |
| **Fixed** | Bug fixes | "Fixed crash when file contains emoji" |
| **Breaking** | Requires user action | "API key format changed — regenerate keys" |

### Format

```markdown
## v2.1.0 (2026-03-28)

### New
- PDF export with custom themes (#234)
- Dark mode support in preview (#241)

### Improved
- Page load 40% faster via lazy-loading images (#238)
- Search now matches partial words (#235)

### Fixed
- Fixed crash when file path contains spaces (#237)
- Fixed incorrect page count for multi-section docs (#239)

### Breaking
- API key format changed from `sk-xxx` to `gw-xxx` — regenerate keys in Settings (#240)
```

**Rules:**
- User perspective: not "refactored internal module" but "page load 40% faster"
- Each entry: one sentence, user-perceivable impact
- Include PR/issue numbers for traceability
- Breaking changes get extra detail: what changed + what the user must do

---

## Sub-Type 4: Internal Docs / Guides

### Problem-Driven Structure

Every guide answers ONE question. Format: "Want to do X? Follow these steps."

```markdown
# How to Deploy to Staging

## Prerequisites
- SSH access to staging server
- Docker installed locally

## Steps
1. Build the image: `docker build -t app:staging .`
2. Push to registry: `docker push registry.internal/app:staging`
3. SSH and pull: `ssh staging 'docker pull registry.internal/app:staging && docker-compose up -d'`
4. Verify: `curl https://staging.internal/health`

## Troubleshooting
- "Connection refused" → Check VPN is connected
- "Image not found" → Verify registry login: `docker login registry.internal`
```

### Decision Records

For decisions that affect architecture or process:

```markdown
# ADR-001: Use PostgreSQL Over MongoDB

## Context
We need a database for user data. Expected 100K users, complex queries on relational data.

## Options Considered
1. **PostgreSQL** — Relational, strong query support, ACID
2. **MongoDB** — Document store, flexible schema, horizontal scaling
3. **SQLite** — Simple, embedded, no server needed

## Decision
PostgreSQL.

## Reasoning
- Our data is inherently relational (users → projects → tasks)
- We need complex joins and aggregations for reporting
- 100K users doesn't require horizontal scaling
- Team has more PostgreSQL experience
```

**Rule:** If a guide answers two questions, split it into two guides.

---

## Tone Rules

- Maximum clarity, zero ambiguity
- Short sentences. Active voice.
- No filler:
  - ❌ "Please note that..." → just state what to note
  - ❌ "It should be noted that..." → delete entirely
  - ❌ "In order to..." → "To..."
  - ❌ "It is important to remember that..." → state the thing
  - ❌ 请注意... → 直接说要注意什么
  - ❌ 需要指出的是... → 删掉

---

## Self-Check Checklist

- [ ] README first line says what it is (no adjectives)?
- [ ] Quick start is ≤5 steps and all commands work?
- [ ] API examples are copy-runnable?
- [ ] Changelog entries are user-perspective (not developer-perspective)?
- [ ] Breaking changes explain what user must do?
- [ ] Internal guides answer exactly ONE question?
- [ ] No filler phrases ("please note", "it should be noted")?
- [ ] All code blocks have language tags?
- [ ] Active voice throughout?
- [ ] A new team member could follow this without asking questions?
