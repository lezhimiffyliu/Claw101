# Configuration | 配置

How to set up OpenClaw the way you want it.

按你的方式配置 OpenClaw。

---

## Config File Location | 配置文件位置

OpenClaw uses a single JSON5 config file:

OpenClaw 使用单个 JSON5 配置文件：

```
~/.openclaw/openclaw.json
```

You can also use `--dev` or `--profile <name>` to isolate state:

你也可以用 `--dev` 或 `--profile <name>` 来隔离配置：

```bash
openclaw --dev gateway          # Uses ~/.openclaw-dev/
openclaw --profile work gateway # Uses ~/.openclaw-work/
```

## Interactive Configuration | 交互式配置

The easiest way to configure OpenClaw:

最简单的配置方式：

```bash
# Full interactive wizard
openclaw configure

# Or reconfigure specific parts
openclaw onboard --reset-scope
```

## Reading and Writing Config | 读写配置

### View config | 查看配置

```bash
# Get a specific value
openclaw config get gateway.port

# Print config file path
openclaw config file

# Validate config
openclaw config validate
```

### Set config | 设置配置

```bash
# Set a value
openclaw config set gateway.port 18790

# Remove a value
openclaw config unset gateway.tailscale
```

## Gateway Settings | Gateway 设置

The Gateway is the local WebSocket control plane that connects everything.

Gateway 是连接一切的本地 WebSocket 控制平面。

```json5
{
  "gateway": {
    "port": 18789,           // Default port
    "bind": "loopback",      // loopback, tailnet, lan, auto, or custom
    "auth": {
      "mode": "token"        // token or password
    },
    "tailscale": {
      "mode": "off"          // off, serve, or funnel
    }
  }
}
```

### Bind options explained | bind 选项说明

| Value | Description | 说明 |
|-------|-------------|------|
| `loopback` | Only localhost (most secure) | 仅本地访问（最安全） |
| `tailnet` | Accessible via Tailscale | 通过 Tailscale 访问 |
| `lan` | Local network | 局域网访问 |
| `auto` | Auto-detect | 自动检测 |

## Model Configuration | 模型配置

### Set up authentication | 设置认证

```bash
# Interactive setup
openclaw models auth add

# Or paste a token directly
openclaw models auth paste-token
```

### Set primary model | 设置主模型

```bash
# List available models
openclaw models list --all

# Set primary model
openclaw models set claude-3-opus

# Set image model
openclaw models set-image dall-e-3
```

### Fallbacks | 备选模型

```bash
# Add fallback models (used if primary fails)
openclaw models fallbacks add gpt-4-turbo
openclaw models fallbacks add claude-3-sonnet

# List fallbacks
openclaw models fallbacks list
```

## Channel Configuration | 渠道配置

Channels are how OpenClaw connects to messaging platforms.

渠道是 OpenClaw 连接到消息平台的方式。

```bash
# Add a new channel
openclaw channels add

# List configured channels
openclaw channels list

# Check channel health
openclaw channels status --probe
```

### Channel policies | 渠道策略

```json5
{
  "channels": {
    "whatsapp": {
      "dmPolicy": "pairing",  // pairing or open
      "allowFrom": []         // Allowlist (empty = all allowed when open)
    }
  }
}
```

| Policy | Description | 说明 |
|--------|-------------|------|
| `pairing` | Requires pairing code approval | 需要配对码批准 |
| `open` | Anyone can message (use with caution) | 任何人都可以发消息（谨慎使用） |

## Skills Configuration | Skills 配置

Skills are capabilities that extend what OpenClaw can do.

Skills 是扩展 OpenClaw 能力的模块。

```bash
# List available skills
openclaw skills list

# Check which are ready vs missing requirements
openclaw skills check

# Get info about a specific skill
openclaw skills info browser-control
```

## Secrets Management | 密钥管理

```bash
# Audit for plaintext secrets
openclaw secrets audit

# Configure secret provider
openclaw secrets configure

# Reload secrets after changes
openclaw secrets reload
```

## Useful Config Commands | 实用配置命令

```bash
# Full security audit
openclaw security audit --deep

# Fix permissions and security issues
openclaw security audit --fix

# Validate everything
openclaw config validate && openclaw doctor
```

## Pro Tips | 实用技巧

### Separate dev and prod configs | 分离开发和生产配置

```bash
# Development
openclaw --dev onboard
openclaw --dev gateway

# Production
openclaw gateway
```

### Backup your config | 备份配置

```bash
openclaw backup create
openclaw backup verify
```

### Reset if things go wrong | 出问题时重置

```bash
# Reset config only
openclaw reset --scope config

# Full reset (careful!)
openclaw reset --scope full
```

---

Next: [Commands](commands.md) | 下一步：[命令](commands.md)
