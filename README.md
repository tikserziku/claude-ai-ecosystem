# 🤖 Claude AI Ecosystem

<div align="center">

![Claude AI Ecosystem](https://img.shields.io/badge/Claude-AI%20Ecosystem-blueviolet?style=for-the-badge&logo=anthropic)
![MCP Servers](https://img.shields.io/badge/MCP%20Servers-39+-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Production-success?style=for-the-badge)
![Uptime](https://img.shields.io/badge/Uptime-99.9%25-brightgreen?style=for-the-badge)

**A comprehensive AI infrastructure built with Claude, featuring 39+ MCP servers, intelligent cost optimization, and autonomous task execution.**

[Features](#-features) • [Architecture](#-architecture) • [Services](#-services) • [Cost Optimization](#-cost-optimization) • [Contact](#-contact)

---

</div>

## 🎯 What is This?

This is a **production-grade AI ecosystem** that demonstrates the full potential of Claude AI and the Model Context Protocol (MCP). Built over months of iterative development, it showcases:

- **39+ MCP Servers** working in harmony
- **Intelligent AI Orchestra** that routes tasks to optimal models
- **90% cost savings** through smart model selection
- **Autonomous agents** for VM management, transcription, and more
- **Real-time monitoring** and self-healing capabilities

> 💡 **Note**: This repository serves as documentation and showcase. Core source code is proprietary, but I'm open to collaborations and discussions about the architecture.

---

## ✨ Features

### 🎼 MCP Orchestra - Intelligent Task Routing

```
┌─────────────────────────────────────────────────────────────┐
│                    USER REQUEST                              │
└─────────────────────┬───────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────────────────┐
│              🎼 MCP ORCHESTRA (Router)                       │
│  ┌─────────────────────────────────────────────────────┐    │
│  │  Task Analysis → Complexity Score → Model Selection │    │
│  └─────────────────────────────────────────────────────┘    │
└─────────────────────┬───────────────────────────────────────┘
                      │
          ┌───────────┼───────────┐
          ▼           ▼           ▼
    ┌──────────┐ ┌──────────┐ ┌──────────┐
    │ DeepSeek │ │   GROK   │ │  Claude  │
    │   80%    │ │   15%    │ │    5%    │
    │ routine  │ │ creative │ │ complex  │
    └──────────┘ └──────────┘ └──────────┘
```

**How it works:**
- Analyzes incoming tasks for complexity, creativity requirements, and domain
- Routes 80% of routine tasks to DeepSeek (cost-effective)
- Sends 15% creative/conversational tasks to GROK
- Reserves 5% complex reasoning tasks for Claude
- **Result: 90% cost reduction** while maintaining quality

### 🖥️ Oracle VM Agent v3.0

Full autonomous control over cloud infrastructure:

| Feature | Description |
|---------|-------------|
| 🔧 **Shell Execution** | Safe command execution with blocked patterns |
| 📁 **File Operations** | CRUD with backup, search, recursive operations |
| ⚙️ **Service Management** | Create, edit, delete systemd services |
| 🌐 **Network Ops** | HTTP requests, port scanning, health checks |
| 🐙 **GitHub Integration** | Auto-backup, restore, version control |
| 📊 **Monitoring** | CPU, RAM, disk, process monitoring |
| 🔔 **Telegram Alerts** | Real-time notifications |
| 📋 **19+ Recipes** | Pre-built automation workflows |

### 🎬 Video Transcriber

Automatic transcription service supporting:
- ✅ YouTube videos
- ✅ TikTok videos  
- ✅ Direct video URLs
- ✅ Multiple languages (auto-detection)
- ✅ Whisper AI integration
- ✅ Auto yt-dlp updates (nightly builds)

### 🔊 Voice AI Assistants

Personal AI assistants with voice capabilities:
- **Emilija** - Personal AI with custom personality
- **Zigminta** - Alternative assistant configuration
- Real-time speech-to-text and text-to-speech
- PWA support for mobile devices

---

## 🏗️ Architecture

```
┌────────────────────────────────────────────────────────────────────┐
│                         CLIENT LAYER                                │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐           │
│  │ Claude   │  │ Claude   │  │  Mobile  │  │   n8n    │           │
│  │ Desktop  │  │   Web    │  │   PWA    │  │ Workflows│           │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘           │
└───────┼─────────────┼─────────────┼─────────────┼──────────────────┘
        │             │             │             │
        └─────────────┴──────┬──────┴─────────────┘
                             │
┌────────────────────────────┼───────────────────────────────────────┐
│                      MCP GATEWAY                                    │
│                    (Caddy Reverse Proxy)                           │
│              visaginas360.duckdns.org:443                          │
└────────────────────────────┬───────────────────────────────────────┘
                             │
┌────────────────────────────┼───────────────────────────────────────┐
│                    ORACLE VM (Ubuntu 24)                           │
│  ┌─────────────────────────────────────────────────────────────┐  │
│  │                    SERVICE MESH                              │  │
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐           │  │
│  │  │  Admin  │ │ Portal  │ │  Voice  │ │ Monitor │           │  │
│  │  │  API    │ │ :3335   │ │ :3336   │ │ :8676   │           │  │
│  │  │  :5001  │ └─────────┘ └─────────┘ └─────────┘           │  │
│  │  └─────────┘                                                │  │
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐           │  │
│  │  │Transcr. │ │ Android │ │ Emilija │ │Zigminta │           │  │
│  │  │ :5000   │ │ :3337   │ │  PWA    │ │  PWA    │           │  │
│  │  └─────────┘ └─────────┘ └─────────┘ └─────────┘           │  │
│  └─────────────────────────────────────────────────────────────┘  │
│                                                                    │
│  ┌─────────────────────────────────────────────────────────────┐  │
│  │                    AGENT MODE v3.0                          │  │
│  │  • Shell/Python execution    • GitHub auto-backup          │  │
│  │  • File operations           • Telegram notifications      │  │
│  │  • Service management        • 19+ automation recipes      │  │
│  │  • Network operations        • Self-diagnostics            │  │
│  └─────────────────────────────────────────────────────────────┘  │
└────────────────────────────────────────────────────────────────────┘
```

---

## 📊 Services Overview

| Service | Port | Description | Status |
|---------|------|-------------|--------|
| **grok-admin-api** | 5001 | Main MCP API server | 🟢 Active |
| **grok-portal** | 3335 | Services dashboard | 🟢 Active |
| **grok-voice** | 3336 | Voice AI streaming | 🟢 Active |
| **grok-android** | 3337 | Mobile PWA | 🟢 Active |
| **grok-monitor** | 8676 | Real-time monitoring | 🟢 Active |
| **grok-emilia** | - | Personal AI assistant | 🟢 Active |
| **grok-zigminta** | - | Personal AI assistant | 🟢 Active |
| **transcriber** | 5000 | Video transcription | 🟢 Active |

---

## 💰 Cost Optimization

### Before MCP Orchestra
```
Monthly AI API costs: ~$150-200
All tasks → Claude API
```

### After MCP Orchestra
```
Monthly AI API costs: ~$15-20
Intelligent routing:
├── 80% → DeepSeek ($0.14/1M tokens)
├── 15% → GROK (included in X Premium)
└── 5%  → Claude (complex tasks only)

💰 Savings: ~90%
```

### Task Routing Logic

```python
def route_task(task):
    complexity = analyze_complexity(task)
    
    if complexity < 3:
        return "deepseek"      # Simple: translations, summaries
    elif complexity < 7:
        return "grok"          # Medium: creative, conversational
    else:
        return "claude"        # Complex: reasoning, coding, analysis
```

---

## 🛠️ MCP Servers Collection

### Core Infrastructure
- `vm-management` - Oracle VM control
- `github-backup` - Auto repository backup
- `file-operations` - File system management
- `service-manager` - Systemd service control

### AI & Processing
- `transcriber` - Video to text (YouTube, TikTok)
- `voice-stream` - Real-time voice AI
- `image-gen` - Image generation (VEO3, etc.)
- `ai-orchestra` - Multi-model routing

### Integrations
- `google-drive` - Drive sync & search
- `telegram-bot` - Notifications & commands
- `n8n-workflows` - Automation triggers
- `render-deploy` - Cloud deployment

### Utilities
- `notes-manager` - Knowledge base
- `task-tracker` - Todo management
- `news-aggregator` - AI news collection
- `tools-catalog` - AI tools database

---

## 📈 Statistics

<div align="center">

| Metric | Value |
|--------|-------|
| **Total MCP Servers** | 39+ |
| **Active Services** | 7 |
| **Uptime** | 17+ weeks |
| **Automation Recipes** | 19 |
| **Cost Savings** | ~90% |
| **Languages Supported** | RU, EN, LT |

</div>

---

## 🚀 Roadmap

- [x] MCP Orchestra v1.0 - Intelligent routing
- [x] Oracle VM Agent v3.0 - Full automation
- [x] Video Transcriber - YouTube/TikTok support
- [x] Voice AI Assistants - Emilija & Zigminta
- [ ] VEO3 Integration - AI video generation
- [ ] Claude Computer Use - Browser automation
- [ ] Public API - Limited access for testers
- [ ] Documentation - Detailed guides

---

## 🤝 Collaboration

I'm actively looking to connect with:

- **Anthropic Team** - Showcase real-world Claude implementations
- **MCP Developers** - Share best practices and patterns
- **AI Enthusiasts** - Discuss architecture and optimizations

### What I Can Share

✅ Architecture diagrams and patterns  
✅ Cost optimization strategies  
✅ MCP server design principles  
✅ Automation workflow examples  
✅ Lessons learned and best practices  

### What's Proprietary

🔒 Source code (available for serious collaborations)  
🔒 API keys and credentials  
🔒 Personal configurations  

---

## 📬 Contact

<div align="center">

**Interested in learning more or collaborating?**

[![Telegram](https://img.shields.io/badge/Telegram-@visaginas360-blue?style=for-the-badge&logo=telegram)](https://t.me/visaginas360)
[![GitHub](https://img.shields.io/badge/GitHub-tikserziku-black?style=for-the-badge&logo=github)](https://github.com/tikserziku)

</div>

---

## 📜 License

This repository contains documentation and architectural descriptions only.  
Source code is proprietary and available under separate licensing terms.

---

<div align="center">

**Built with ❤️ using Claude AI by Anthropic**

*"The best way to predict the future is to build it"*

</div>
