# 🤖 Claude AI Ecosystem

<div align="center">

![Claude AI Ecosystem](https://img.shields.io/badge/Claude-AI%20Ecosystem-blueviolet?style=for-the-badge&logo=anthropic)
![MCP Servers](https://img.shields.io/badge/MCP%20Servers-39+-blue?style=for-the-badge)
![Version](https://img.shields.io/badge/Version-3.0.0-green?style=for-the-badge)
![Uptime](https://img.shields.io/badge/Uptime-99.9%25-brightgreen?style=for-the-badge)

**A comprehensive AI infrastructure built with Claude, featuring 39+ MCP servers, intelligent cost optimization, and autonomous task execution.**

[Features](#-features) • [Tools](#-tools) • [Architecture](#-architecture) • [Documentation](#-documentation) • [Contact](#-contact)

---

</div>

## 🎯 What is This?

This is a **production-grade AI ecosystem** that demonstrates the full potential of Claude AI and the Model Context Protocol (MCP). Built over months of iterative development, it showcases:

- **39+ MCP Servers** working in harmony
- **Intelligent AI Orchestra** that routes tasks to optimal models
- **90% cost savings** through smart model selection
- **Autonomous agents** for VM management, transcription, and more
- **CLI tools** for scriptable automation
- **Real-time monitoring** and self-healing capabilities

> 💡 **Note**: This repository serves as documentation and showcase. Core source code is proprietary, but I'm open to collaborations and discussions about the architecture.

---

## ✨ Features

### 🎼 MCP Orchestra - Intelligent Task Routing

Routes tasks to the most cost-effective AI model:

| Task Complexity | Model | Cost | Use Case |
|----------------|-------|------|----------|
| Simple (1-3) | DeepSeek | $0.14/1M | Translation, formatting |
| Medium (4-6) | GROK | Free* | Creative, conversational |
| Complex (7-10) | Claude | $3/1M | Reasoning, coding |

**Result: 90% cost reduction** while maintaining quality.

### 🖥️ Oracle VM Agent v3.0

Full autonomous control over cloud infrastructure with 19+ automation recipes.

### 🔮 Oracle CLI

Fast, scriptable command-line interface:

```bash
oracle status              # All services health
oracle restart voice       # Restart service
oracle run fix_transcriber # Run automation recipe
oracle add "New feature"   # Track changelog
oracle release minor       # Release v3.1.0
```

### 📝 Changelog Agent

Automatic feature tracking with semantic versioning:

```bash
# Auto-detect from natural language
"Добавил новый MCP сервер" → [minor] New MCP server

# Trigger words: добавил, исправил, улучшил, fix, new feature...
```

---

## 🛠️ Tools

| Tool | Description | Docs |
|------|-------------|------|
| **Oracle CLI** | Command-line VM management | [📖 Docs](docs/ORACLE-CLI.md) |
| **Changelog Agent** | Auto versioning & tracking | [📖 Docs](docs/CHANGELOG-AGENT.md) |
| **Agent Mode v3.0** | Autonomous task execution | [📖 Docs](docs/ARCHITECTURE.md) |
| **MCP Servers** | 39+ specialized tools | [📖 Docs](docs/MCP-SERVERS.md) |

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                      CLIENT LAYER                            │
│   Claude Desktop │ Claude Web │ Mobile PWA │ Oracle CLI     │
└────────────────────────┬────────────────────────────────────┘
                         │
┌────────────────────────┼────────────────────────────────────┐
│                   MCP GATEWAY                                │
│             visaginas360.duckdns.org:443                    │
└────────────────────────┬────────────────────────────────────┘
                         │
┌────────────────────────┼────────────────────────────────────┐
│                 ORACLE VM (Ubuntu 24)                        │
│  ┌────────────────────────────────────────────────────────┐ │
│  │ grok-admin-api │ grok-portal │ grok-voice │ transcriber│ │
│  └────────────────────────────────────────────────────────┘ │
│  ┌────────────────────────────────────────────────────────┐ │
│  │        Agent Mode v3.0  │  Changelog Agent             │ │
│  └────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

---

## 📚 Documentation

| Document | Description |
|----------|-------------|
| [Architecture](docs/ARCHITECTURE.md) | System design & infrastructure |
| [MCP Servers](docs/MCP-SERVERS.md) | All 39+ servers catalog |
| [Cost Optimization](docs/COST-OPTIMIZATION.md) | 90% savings strategy |
| [Oracle CLI](docs/ORACLE-CLI.md) | Command-line interface |
| [Changelog Agent](docs/CHANGELOG-AGENT.md) | Auto versioning |
| [Lessons Learned](docs/LESSONS-LEARNED.md) | Best practices |
| [Changelog](docs/CHANGELOG.md) | Version history |

---

## 📊 Statistics

| Metric | Value |
|--------|-------|
| MCP Servers | 39+ |
| Active Services | 7 |
| Uptime | 17+ weeks |
| Automation Recipes | 19 |
| Cost Savings | ~90% |
| CLI Commands | 15+ |

---

## 🚀 Roadmap

- [x] MCP Orchestra v1.0 - Intelligent routing
- [x] Oracle VM Agent v3.0 - Full automation
- [x] Oracle CLI v1.0 - Scriptable commands
- [x] Changelog Agent v1.0 - Auto versioning
- [x] Video Transcriber - YouTube/TikTok
- [ ] VEO3 Integration - AI video generation
- [ ] Public API - Limited access
- [ ] Browser Automation - Claude Computer Use

---

## 🤝 Collaboration

Looking to connect with:
- **Anthropic Team** - Real-world Claude implementations
- **MCP Developers** - Best practices sharing
- **AI Enthusiasts** - Architecture discussions

### What I Share
✅ Architecture patterns  
✅ Cost optimization strategies  
✅ MCP design principles  
✅ Automation workflows  

### What's Proprietary
🔒 Source code (available for collaborations)  
🔒 API credentials  

---

## 📬 Contact

<div align="center">

[![Telegram](https://img.shields.io/badge/Telegram-@visaginas360-blue?style=for-the-badge&logo=telegram)](https://t.me/visaginas360)
[![GitHub](https://img.shields.io/badge/GitHub-tikserziku-black?style=for-the-badge&logo=github)](https://github.com/tikserziku)

**[Request Access](GET-ACCESS.md)** for demos and collaborations

</div>

---

<div align="center">

**Built with ❤️ using Claude AI by Anthropic**

*Current Version: 3.0.0*

</div>
