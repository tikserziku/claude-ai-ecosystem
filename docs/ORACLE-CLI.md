# 🔮 Oracle CLI

A fast, scriptable command-line interface for Oracle VM management. Works independently of Claude - perfect for automation, cron jobs, and quick tasks.

## Installation

```bash
# The CLI is located at /home/ubuntu/oracle-cli.py
chmod +x /home/ubuntu/oracle-cli.py

# Create symlink for easy access
sudo ln -s /home/ubuntu/oracle-cli.py /usr/local/bin/oracle

# Test
oracle help
```

## Commands Reference

### Service Management

```bash
oracle status              # Show all services health status
oracle restart <service>   # Restart a service (auto-adds grok- prefix)
oracle logs <service> [n]  # Show service logs (default: 50 lines)
```

**Examples:**
```bash
oracle status
oracle restart voice       # Restarts grok-voice
oracle logs portal 100     # Last 100 lines from grok-portal
```

### Automation Recipes

```bash
oracle recipes             # List all available recipes
oracle run <recipe>        # Execute a recipe
```

**Available Recipes:**
- `fix_transcriber` - Update yt-dlp + restart transcriber
- `check_services` - Check all services status
- `restart_all_services` - Restart everything
- `system_cleanup` - Clean temp files, logs, apt cache
- `diagnose_all` - Full system diagnostic
- And 14+ more...

**Examples:**
```bash
oracle recipes
oracle run fix_transcriber
oracle run system_cleanup
```

### Changelog & Versioning

```bash
oracle add "description"   # Add feature to changelog queue
oracle pending             # Show pending features
oracle release [type]      # Release version (major/minor/patch)
oracle version             # Show current version
```

**Examples:**
```bash
oracle add "New MCP server for VEO3 integration"
oracle add "Fixed yt-dlp TikTok support"
oracle pending
oracle release minor       # v3.0.0 → v3.1.0
```

### Monitoring

```bash
oracle health              # Quick health check (API, services, ports)
oracle top                 # Top processes by CPU
```

## Use Cases

### Daily Monitoring Script

```bash
#!/bin/bash
# /home/ubuntu/daily-check.sh

echo "=== Daily Oracle VM Check ==="
date

oracle health
oracle status

echo "Done!"
```

### Cron Job for Cleanup

```bash
# Weekly cleanup at 3 AM Sunday
0 3 * * 0 /usr/local/bin/oracle run system_cleanup >> /var/log/oracle-cleanup.log 2>&1
```

### Quick Restart After Deploy

```bash
#!/bin/bash
# restart-after-deploy.sh

oracle restart admin-api
oracle restart portal
oracle restart voice

sleep 3
oracle health
```

### Auto-Track Features in Git Hook

```bash
#!/bin/bash
# .git/hooks/post-commit

MSG=$(git log -1 --pretty=%B)
oracle add "$MSG"
```

## Output Examples

### `oracle status`
```
🔧 SERVICES
  [+] grok-admin-api           active/running
  [+] grok-portal              active/running
  [+] grok-voice               active/running
  [+] grok-android             active/running
  [-] grok-test                inactive/dead

  4/5 healthy
```

### `oracle health`
```
💚 HEALTH
  API: UP
  Services: 4/5
  Transcriber: UP
  API: UP
  Portal: UP
```

### `oracle pending`
```
📋 PENDING (3)
  [minor] New MCP server for VEO3
  [patch] Fixed yt-dlp crash on TikTok
  [patch] Improved transcriber performance
```

## Integration with Other Tools

### n8n Webhook
```bash
curl -X POST http://localhost:5678/webhook/oracle \
  -d '{"action": "restart", "service": "voice"}'
```

### Telegram Bot Command
```python
@bot.command("status")
async def status(ctx):
    result = subprocess.run(["oracle", "status"], capture_output=True, text=True)
    await ctx.reply(result.stdout)
```

## Troubleshooting

### CLI not found
```bash
# Check symlink
ls -la /usr/local/bin/oracle

# Recreate if needed
sudo ln -sf /home/ubuntu/oracle-cli.py /usr/local/bin/oracle
```

### API unavailable
```bash
# Check if admin-api is running
systemctl status grok-admin-api

# Restart if needed
sudo systemctl restart grok-admin-api
```

### Permission denied
```bash
chmod +x /home/ubuntu/oracle-cli.py
```

---

## Technical Details

- **Location**: `/home/ubuntu/oracle-cli.py`
- **API Backend**: `http://localhost:5001` (grok-admin-api)
- **Dependencies**: Python 3, requests
- **No Claude required**: Works standalone

---

*Part of the [Claude AI Ecosystem](../README.md)*
