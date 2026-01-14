# 📝 Changelog Agent

Automatic feature tracking and semantic versioning for the Claude AI Ecosystem.

## Overview

The Changelog Agent monitors development activity and automatically:
- Detects new features from natural language
- Categorizes changes (features, fixes, improvements)
- Determines version bump type (major/minor/patch)
- Updates CHANGELOG.md
- Pushes to GitHub

## How It Works

```
┌─────────────────────────────────────────────────────────────┐
│                    YOUR MESSAGE                              │
│         "Добавил новый MCP сервер для VEO3"                 │
└─────────────────────────┬───────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────┐
│                  CHANGELOG AGENT                             │
│                                                              │
│  1. Detect trigger words: "добавил" → feature               │
│  2. Extract description: "новый MCP сервер для VEO3"        │
│  3. Detect category: MCP → 🔌 Integrations                  │
│  4. Determine bump: new feature → minor                     │
│  5. Add to queue                                            │
└─────────────────────────┬───────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────┐
│                   QUEUE (pending)                            │
│                                                              │
│  • [minor] New MCP server for VEO3                          │
│  • [patch] Fixed yt-dlp crash                               │
│  • [patch] Improved transcriber                             │
└─────────────────────────┬───────────────────────────────────┘
                          │
                          ▼ (on release)
┌─────────────────────────────────────────────────────────────┐
│                    RELEASE v3.1.0                            │
│                                                              │
│  → Generate CHANGELOG entry                                  │
│  → Update VERSION.json                                       │
│  → Commit to GitHub                                          │
│  → Push                                                      │
└─────────────────────────────────────────────────────────────┘
```

## Trigger Words

### Features (→ minor bump)
- `добавил`, `создал`, `реализовал`
- `new feature:`, `added`, `implemented`, `created`

### Fixes (→ patch bump)
- `исправил`, `пофиксил`, `fix:`
- `fixed`, `bugfix`, `resolved`

### Improvements (→ patch bump)
- `улучшил`, `оптимизировал`
- `improved`, `optimized`, `enhanced`

### Breaking Changes (→ major bump)
- `breaking`, `rewrite`, `v2`, `v3`
- `architecture change`

## Categories

| Category | Keywords |
|----------|----------|
| 🚀 New Features | feature, new, add, implement |
| 🔧 Improvements | improve, optimize, enhance |
| 🐛 Bug Fixes | fix, bugfix, resolve |
| 📚 Documentation | docs, readme, guide |
| 🏗️ Infrastructure | infra, deploy, service |
| 🔌 Integrations | mcp, api, integration |
| 💰 Cost Optimization | cost, saving, efficient |

## Usage

### CLI Commands

```bash
# Add feature manually
python3 changelog_agent.py add "New MCP server for VEO3"

# Auto-detect from message
python3 changelog_agent.py track "Добавил интеграцию с Google Drive"

# Show pending features
python3 changelog_agent.py pending

# Release new version
python3 changelog_agent.py release minor

# Show stats
python3 changelog_agent.py stats

# Show current version
python3 changelog_agent.py version
```

### Via Oracle CLI

```bash
oracle add "New feature description"
oracle pending
oracle release minor
oracle version
```

### API Endpoints

```bash
# Add feature
curl -X POST http://localhost:5001/changelog/add \
  -H "Content-Type: application/json" \
  -d '{"description": "New MCP server"}'

# Auto-track
curl -X POST http://localhost:5001/changelog/track \
  -H "Content-Type: application/json" \
  -d '{"message": "Добавил новый сервис"}'

# Get pending
curl http://localhost:5001/changelog/pending

# Release
curl -X POST http://localhost:5001/changelog/release \
  -H "Content-Type: application/json" \
  -d '{"bump": "minor"}'

# Get version
curl http://localhost:5001/changelog/version
```

## Semantic Versioning

```
MAJOR.MINOR.PATCH

MAJOR - Breaking changes, rewrites
MINOR - New features, capabilities  
PATCH - Bug fixes, small improvements
```

### Examples

```
v3.0.0 → v3.0.1 (patch: fixed bug)
v3.0.1 → v3.1.0 (minor: new feature)
v3.1.0 → v4.0.0 (major: architecture rewrite)
```

## Generated Output

### CHANGELOG.md Entry

```markdown
## [3.1.0] - January 15, 2025

### 🚀 New Features
- New MCP server for VEO3 video generation
- Google Drive integration

### 🐛 Bug Fixes
- Fixed yt-dlp crash on TikTok links

### 🔧 Improvements
- Improved transcriber performance
```

### VERSION.json

```json
{
  "major": 3,
  "minor": 1,
  "patch": 0,
  "released": "2025-01-15"
}
```

## Files

| File | Location | Purpose |
|------|----------|---------|
| `changelog_agent.py` | `/home/ubuntu/` | Main agent |
| `VERSION.json` | `/home/ubuntu/claude-ai-ecosystem/` | Version tracker |
| `CHANGELOG.md` | `/home/ubuntu/claude-ai-ecosystem/docs/` | Change log |
| `features_queue.json` | `/home/ubuntu/logs/` | Pending features |

## Integration with Claude

When talking to Claude, simply mention your changes naturally:

> "Добавил новый MCP сервер для транскрипции"

Claude can then run:
```python
changelog.auto_track("Добавил новый MCP сервер для транскрипции")
# → Automatically adds to queue
```

Or via Oracle CLI:
```bash
oracle add "New transcription MCP server"
```

---

*Part of the [Claude AI Ecosystem](../README.md)*
