# 📚 Lessons Learned

Real-world insights from building and operating a production AI ecosystem.

---

## 🔌 MCP Development

### What Works
✅ **SSE over WebSocket** - More reliable for remote servers
✅ **Stdio for local** - Fast, no network overhead
✅ **Simple tool design** - One tool, one purpose
✅ **Detailed error messages** - Helps Claude self-correct

### What Doesn't Work
❌ **Complex tool chains** - Break them into smaller tools
❌ **Large payloads in tools** - Stream or paginate instead
❌ **Silent failures** - Always return explicit errors
❌ **Ambiguous tool names** - Be specific and descriptive

### Pro Tips
```python
# Good: Clear, specific tool
@server.tool("vm_restart_service")
async def restart(service: str) -> str:
    """Restart a systemd service by name"""
    
# Bad: Vague, multi-purpose tool
@server.tool("manage")
async def manage(action: str, target: str) -> str:
    """Do stuff with things"""
```

---

## 💰 Cost Optimization

### Key Insight
> 80% of AI tasks don't need the most powerful model

### Proven Strategy
1. **Analyze** - Track what tasks you actually run
2. **Classify** - Group by complexity requirements
3. **Route** - Send simple tasks to cheap models
4. **Monitor** - Track quality, adjust thresholds

### Surprising Findings
- DeepSeek handles translation better than expected
- GROK excels at creative brainstorming
- Claude is overkill for formatting tasks
- Context window matters more than model size

### Cost per Task Type
| Task | Before (Claude) | After (Optimized) | Savings |
|------|-----------------|-------------------|---------|
| Translation | $0.003 | $0.00014 | 95% |
| Summarization | $0.005 | $0.0002 | 96% |
| Code review | $0.01 | $0.01 | 0% |
| Complex analysis | $0.02 | $0.02 | 0% |

---

## 🖥️ Infrastructure

### What I'd Do Differently

1. **Start with systemd** - Don't use screen/tmux for production
2. **Use reverse proxy from day 1** - Caddy > Nginx for simplicity
3. **Automate SSL** - Let's Encrypt + Caddy auto-renewal
4. **Log everything** - You'll thank yourself later

### Architecture Decisions That Paid Off

✅ **Microservices** - Easy to update/restart individual components
✅ **Health endpoints** - Every service has `/health`
✅ **Graceful degradation** - Services handle missing dependencies
✅ **Auto-restart** - systemd `Restart=always`

### Mistakes Made
❌ **Running as root** - Security nightmare
❌ **Hardcoded ports** - Use environment variables
❌ **No rate limiting** - Got hit by bots
❌ **Manual backups** - Automate with GitHub

---

## 🔒 Security

### Essential Practices
1. **No hardcoded secrets** - Environment variables only
2. **SSH keys only** - Disable password auth
3. **Firewall first** - UFW with whitelist
4. **Update regularly** - Automate security updates

### Real Incident
> A crawler discovered an open endpoint and made 10K requests/hour.
> 
> **Solution**: Cloudflare + rate limiting + IP blocking

### Security Checklist
- [ ] SSH key auth only
- [ ] UFW enabled
- [ ] No root services
- [ ] Secrets in env vars
- [ ] Regular updates
- [ ] Monitoring alerts
- [ ] Backup verification

---

## 🐛 Debugging

### Common Issues & Solutions

#### yt-dlp Breaks
**Symptom**: Transcription fails
**Cause**: YouTube/TikTok API changes
**Fix**: Update to nightly build
```bash
VERSION=$(curl -s https://api.github.com/repos/yt-dlp/yt-dlp-nightly-builds/releases/latest | grep -oP '"tag_name": "\K[^"]+')
curl -L -o /tmp/yt-dlp "https://github.com/yt-dlp/yt-dlp-nightly-builds/releases/download/${VERSION}/yt-dlp"
sudo cp /tmp/yt-dlp /usr/local/bin/yt-dlp
```

#### Service Won't Start
**Symptom**: systemd reports failure
**Debug**:
```bash
journalctl -u service-name -n 50
python3 -m py_compile /path/to/script.py
```

#### MCP Connection Fails
**Symptom**: Claude can't connect
**Checklist**:
1. Is service running? `systemctl status`
2. Is port open? `lsof -i :PORT`
3. Is SSL valid? Check Caddy logs
4. Is URL correct in config?

---

## 📊 Monitoring

### What to Monitor
1. **Service health** - HTTP 200 from /health
2. **Port availability** - All expected ports open
3. **Resource usage** - CPU/RAM/Disk
4. **Error rates** - Log analysis
5. **Response times** - Latency tracking

### Alert Thresholds
| Metric | Warning | Critical |
|--------|---------|----------|
| CPU | 70% | 90% |
| RAM | 80% | 95% |
| Disk | 80% | 95% |
| Response time | 1s | 5s |
| Error rate | 1% | 5% |

---

## 🚀 Performance

### Quick Wins
1. **Connection pooling** - Reuse HTTP connections
2. **Async everywhere** - Don't block on I/O
3. **Caching** - Cache expensive computations
4. **Compression** - Gzip all responses

### Benchmarks
| Operation | Before | After | Improvement |
|-----------|--------|-------|-------------|
| API response | 500ms | 150ms | 3x |
| File read | 100ms | 20ms | 5x |
| DB query | 200ms | 50ms | 4x |

---

## 🤝 Working with Claude

### Effective Prompting
1. **Be specific** - "List 5 items" not "list some items"
2. **Provide context** - Include relevant background
3. **Show examples** - Demonstrate expected output
4. **Set constraints** - "In under 100 words"

### MCP Tool Design
```python
# Good tool description
"""
Restart a systemd service.

Args:
    service: Service name (e.g., 'grok-voice')
    
Returns:
    Success message with new status

Example:
    restart_service('grok-voice') 
    → '✅ grok-voice restarted, status: active'
"""

# Bad tool description
"""Restart service"""
```

### What Claude Does Best
- Complex reasoning and analysis
- Code review and debugging  
- Architecture design
- Safety-critical decisions

### What to Offload
- Simple translations
- Data formatting
- Routine queries
- Repetitive tasks

---

## 📈 Scaling

### Current Capacity
- 7 concurrent services
- ~1000 requests/day
- 24GB RAM (50% used)
- 200GB disk (50% used)

### Scaling Strategy
1. **Vertical first** - Upgrade VM specs
2. **Then horizontal** - Add more VMs
3. **Load balance** - Distribute traffic
4. **Cache aggressively** - Reduce backend load

### Bottlenecks Identified
- Whisper transcription (CPU-bound)
- Large file operations (I/O-bound)
- Concurrent API calls (connection limits)

---

## 🎯 Key Takeaways

1. **Start simple, iterate fast** - Don't over-engineer initially
2. **Automate everything** - Manual processes break
3. **Monitor proactively** - Don't wait for failures
4. **Document as you go** - Future you will thank you
5. **Use the right model** - Not every task needs Claude
6. **Security is not optional** - One incident ruins everything
7. **Backup religiously** - Test restores regularly

---

*These lessons come from 4+ months of production operation and hundreds of iterations.*
