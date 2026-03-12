# Troubleshooting | 常见问题

When things go wrong, check here first.

遇到问题时，先看这里。

---

## Quick Diagnostics | 快速诊断

Before diving into specific issues, run these:

在深入具体问题之前，先运行这些：

```bash
# Health check (always start here!)
openclaw doctor

# Deep health check
openclaw doctor --deep

# Check Gateway status
openclaw gateway status

# Check channel connections
openclaw channels status --probe

# View recent logs
openclaw logs --limit 50
```

---

## Common Issues | 常见问题

### "command not found: openclaw"

**Cause**: npm global bin not in PATH

**原因**: npm 全局 bin 目录不在 PATH 中

**Fix | 解决**:

```bash
# Find where npm installs global packages
npm config get prefix

# Add to PATH (in .bashrc or .zshrc)
export PATH="$(npm config get prefix)/bin:$PATH"

# Reload shell
source ~/.bashrc  # or ~/.zshrc
```

---

### "Node version too old"

**Cause**: OpenClaw requires Node ≥22

**原因**: OpenClaw 需要 Node ≥22

**Fix | 解决**:

```bash
# Check your version
node --version

# Using nvm
nvm install 22
nvm use 22
nvm alias default 22

# Verify
node --version  # Should be v22.x.x+
```

---

### Gateway won't start / port in use

**Cause**: Port 18789 is already in use

**原因**: 端口 18789 已被占用

**Fix | 解决**:

```bash
# Check what's using the port
lsof -i :18789

# Kill the process if it's a stale Gateway
kill <PID>

# Or use a different port
openclaw gateway --port 18790
openclaw config set gateway.port 18790
```

---

### "Cannot connect to Gateway"

**Cause**: Gateway not running or wrong address

**原因**: Gateway 未运行或地址错误

**Fix | 解决**:

```bash
# Check if Gateway is running
openclaw gateway status

# Start it if not running
openclaw gateway

# Or start the service
openclaw gateway service start

# Check Gateway health
openclaw health --verbose
```

---

### Channel won't connect (WhatsApp, Telegram, etc.)

**Cause**: Session expired or not logged in

**原因**: 会话过期或未登录

**Fix | 解决**:

```bash
# Check channel status
openclaw channels status --probe

# View channel logs
openclaw channels logs --channel whatsapp

# Re-login
openclaw channels login --channel whatsapp

# If that doesn't work, remove and re-add
openclaw channels remove --channel whatsapp
openclaw channels add
```

---

### "Authentication failed" for models

**Cause**: Missing or invalid API key

**原因**: API 密钥缺失或无效

**Fix | 解决**:

```bash
# Check auth status
openclaw models status --check

# Re-add authentication
openclaw models auth add

# Or paste token directly
openclaw models auth paste-token

# Test connectivity
openclaw models status --probe
```

---

### Skills not working

**Cause**: Missing dependencies

**原因**: 缺少依赖

**Fix | 解决**:

```bash
# Check which skills are ready vs missing requirements
openclaw skills check

# Get details on a specific skill
openclaw skills info <skill-name>

# Run doctor to identify issues
openclaw doctor
```

---

### Browser control not working

**Cause**: Browser not started or connection lost

**原因**: 浏览器未启动或连接断开

**Fix | 解决**:

```bash
# Check browser status
openclaw browser status

# Reset browser profile
openclaw browser reset-profile

# Restart browser
openclaw browser stop
openclaw browser start
```

---

### Config file errors

**Cause**: Invalid JSON5 syntax

**原因**: JSON5 语法错误

**Fix | 解决**:

```bash
# Validate config
openclaw config validate

# Find config file location
openclaw config file

# Common JSON5 mistakes:
# - Trailing commas are OK in JSON5 (but check for other issues)
# - Single quotes are allowed
# - Comments are allowed (// or /* */)

# If corrupted, reset config
openclaw reset --scope config
```

---

### Everything is broken | 一切都坏了

Nuclear option — reset everything:

核弹选项 — 重置一切：

```bash
# First, backup what you can
openclaw backup create

# Reset to fresh state
openclaw reset --scope full

# Reinstall service
openclaw uninstall --service
openclaw onboard --install-daemon
```

---

## Debug Mode | 调试模式

When you need more information:

当你需要更多信息时：

```bash
# Run Gateway with verbose logging
openclaw gateway --verbose

# Follow logs in real-time
openclaw logs --follow

# Deep diagnostic
openclaw doctor --deep

# Full security audit
openclaw security audit --deep
```

---

## Getting Help | 获取帮助

If you're still stuck:

如果你还是卡住了：

### 1. Search the docs | 搜索文档

```bash
openclaw docs "your problem"
```

### 2. Gather diagnostic info | 收集诊断信息

```bash
# Version
openclaw --version

# Status (share this with others)
openclaw status --json

# Doctor output
openclaw doctor --deep
```

### 3. Ask for help | 寻求帮助

- [GitHub Issues](https://github.com/openclaw/openclaw/issues)
- [GitHub Discussions](https://github.com/openclaw/openclaw/discussions)

When asking:
- Describe what you expected vs what happened
- Include the commands you ran
- Share `openclaw doctor --deep` output
- Share relevant logs (remove sensitive data!)

提问时：
- 描述你期望的行为和实际发生的情况
- 包含你运行的命令
- 分享 `openclaw doctor --deep` 输出
- 分享相关日志（删除敏感信息！）

---

## Pro Tips | 实用技巧

### Create a debug alias | 创建调试别名

```bash
alias ocdebug='openclaw gateway --verbose 2>&1 | tee openclaw-debug.log'
```

### Isolate issues with dev mode | 用开发模式隔离问题

```bash
# Test in isolated environment
openclaw --dev onboard
openclaw --dev gateway
```

### Regular maintenance | 定期维护

```bash
# Weekly check
openclaw doctor && openclaw update
```

---

Still having issues? The community is here to help!

还有问题？社区在这里帮助你！

---

## Official Resources | 官方资源

- [CLI Reference](https://docs.openclaw.ai/cli)
- [GitHub](https://github.com/openclaw/openclaw)
- [Website](https://openclaw.ai/)
