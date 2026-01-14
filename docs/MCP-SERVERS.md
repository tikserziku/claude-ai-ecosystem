# 🔌 MCP Servers Catalog

## Overview

This ecosystem includes **39+ MCP servers** organized into categories. Each server provides specific tools accessible via Claude Desktop or the Claude API.

---

## 📊 Infrastructure Servers

### vm-management
**Purpose**: Full control over Oracle VM infrastructure

| Tool | Description |
|------|-------------|
| `vm_list_services` | List all grok-* services |
| `vm_service_status` | Check service status |
| `vm_restart_service` | Restart a service |
| `vm_service_logs` | Get service logs |
| `vm_create_service` | Create new systemd service |
| `vm_edit_service` | Edit service code |
| `vm_delete_service` | Remove service |
| `vm_diagnose_service` | Full service diagnostic |
| `vm_diagnose_all` | Health check all services |

### vm-files
**Purpose**: File system operations

| Tool | Description |
|------|-------------|
| `vm_read_file` | Read file content |
| `vm_write_file` | Write/create file |
| `vm_list_files` | List directory contents |
| `vm_delete_file` | Delete file/folder |
| `vm_run_code` | Execute Python code |
| `vm_check_code` | Syntax check |

### github-backup
**Purpose**: Version control and backup

| Tool | Description |
|------|-------------|
| `vm_backup_to_github` | Backup service to GitHub |
| `vm_backup_all_to_github` | Backup all services |
| `vm_backup_project` | Full project backup |
| `vm_restore_from_github` | Restore from backup |
| `github_list_repos` | List repositories |
| `github_create_repo` | Create new repo |
| `github_create_file` | Create/update file |
| `github_get_file` | Get file content |

---

## 🎬 Media Processing Servers

### transcriber
**Purpose**: Video-to-text transcription

| Tool | Description |
|------|-------------|
| `transcribe_video` | Transcribe YouTube/TikTok video |

**Supported Sources**:
- ✅ YouTube (any video)
- ✅ TikTok (public videos)
- ✅ Direct video URLs
- ✅ Audio files

**Languages**: Auto-detection, Russian, English, Lithuanian, and more

### voice-stream
**Purpose**: Real-time voice AI

| Tool | Description |
|------|-------------|
| `voice_generate` | Text-to-speech |
| `voice_recognize` | Speech-to-text |

---

## 📝 Knowledge Management Servers

### notes-manager
**Purpose**: Personal knowledge base

| Tool | Description |
|------|-------------|
| `save_note` | Save note to database |
| `get_notes` | Retrieve notes |
| `search_notes` | Search notes |

### task-tracker
**Purpose**: Task and todo management

| Tool | Description |
|------|-------------|
| `add_task` | Create new task |
| `get_tasks` | List tasks |
| `complete_task` | Mark task complete |

### news-aggregator
**Purpose**: AI news collection

| Tool | Description |
|------|-------------|
| `add_news` | Add news item |
| `get_news` | Get latest news |

---

## 🛠️ Utility Servers

### tools-catalog
**Purpose**: AI tools database

| Tool | Description |
|------|-------------|
| `add_tool` | Add AI tool to catalog |
| `search_tools` | Search tools |
| `get_top_tools` | Get popular tools |

### stats-collector
**Purpose**: Analytics and metrics

| Tool | Description |
|------|-------------|
| `get_stats` | Get hub statistics |
| `export_all` | Export all data |

---

## 🌐 Integration Servers

### google-drive
**Purpose**: Google Drive synchronization

| Tool | Description |
|------|-------------|
| `google_drive_search` | Search Drive files |
| `google_drive_fetch` | Get document content |

### telegram-bot
**Purpose**: Telegram notifications

| Tool | Description |
|------|-------------|
| `telegram_send` | Send message |
| `telegram_alert` | Send alert |

### render-deploy
**Purpose**: Render.com deployment

| Tool | Description |
|------|-------------|
| `Render:list_services` | List services |
| `Render:create_web_service` | Deploy new service |
| `Render:get_logs` | Get deployment logs |
| `Render:get_metrics` | Performance metrics |

---

## 🎼 MCP Orchestra (Meta-Server)

**Purpose**: Intelligent task routing across AI models

### How It Works

```python
# Task comes in
task = "Translate this text to Spanish"

# Orchestra analyzes
complexity = analyze(task)  # Result: 2 (simple)

# Routes to optimal model
if complexity < 3:
    return deepseek.complete(task)  # Cost: $0.0001
elif complexity < 7:
    return grok.complete(task)       # Cost: $0
else:
    return claude.complete(task)     # Cost: $0.003
```

### Routing Rules

| Task Type | Complexity | Model | Cost/1M tokens |
|-----------|------------|-------|----------------|
| Translation | 1-2 | DeepSeek | $0.14 |
| Summarization | 2-3 | DeepSeek | $0.14 |
| Creative writing | 4-6 | GROK | Free* |
| Conversation | 3-5 | GROK | Free* |
| Code review | 5-7 | Claude | $3.00 |
| Complex reasoning | 7-10 | Claude | $3.00 |
| Architecture design | 8-10 | Claude | $3.00 |

*GROK is included with X Premium subscription

---

## 📈 Server Statistics

| Metric | Value |
|--------|-------|
| Total MCP Servers | 39+ |
| Active 24/7 | 15 |
| On-demand | 24 |
| Tools Available | 100+ |
| Average Response Time | <200ms |

---

## 🔧 Configuration Example

```json
{
  "mcpServers": {
    "oracle-vm": {
      "url": "https://visaginas360.duckdns.org/mcp/sse",
      "transport": "sse"
    },
    "transcriber": {
      "command": "python",
      "args": ["-m", "transcriber.mcp_server"],
      "transport": "stdio"
    },
    "local-files": {
      "command": "npx",
      "args": ["-y", "@anthropic/mcp-filesystem", "/home/user/docs"],
      "transport": "stdio"
    }
  }
}
```

---

## 🚀 Adding New MCP Server

1. **Define tools** in Python/Node
2. **Implement handlers** for each tool
3. **Choose transport**: stdio (local) or SSE (remote)
4. **Deploy** as service or local script
5. **Add to config** in Claude Desktop

Example minimal server:
```python
from mcp.server import Server
from mcp.types import Tool

server = Server("my-server")

@server.tool("hello")
async def hello(name: str) -> str:
    return f"Hello, {name}!"

# Run with: python -m my_server
```

---

*Documentation last updated: January 2025*
