# Commands | 命令

The commands you'll actually use day-to-day.

日常实际会用到的命令。

---

## Command Structure | 命令结构

```bash
openclaw <command> [subcommand] [options]
```

### Global Flags | 全局选项

| Flag | Description | 说明 |
|------|-------------|------|
| `--dev` | Use `~/.openclaw-dev` (isolated dev env) | 使用独立的开发环境 |
| `--profile <name>` | Use `~/.openclaw-<name>` | 使用指定配置文件 |
| `--no-color` | Disable colors | 禁用颜色 |
| `-V`, `--version` | Print version | 显示版本 |

---

## Essential Commands | 核心命令

### `openclaw onboard`

First-time setup wizard.

首次设置向导。

```bash
# Full interactive setup with daemon
openclaw onboard --install-daemon

# Quick setup
openclaw onboard --flow quickstart

# Advanced setup with all options
openclaw onboard --flow advanced

# Non-interactive (for automation)
openclaw onboard --non-interactive
```

### `openclaw doctor`

Health check — run this when something seems wrong.

健康检查 — 出问题时先运行这个。

```bash
openclaw doctor

# Deep check (probes running services)
openclaw doctor --deep

# Auto-fix issues
openclaw doctor --yes
```

### `openclaw status`

Quick overview of your setup.

快速查看设置状态。

```bash
openclaw status

# Include usage stats
openclaw status --usage

# JSON output
openclaw status --json
```

---

## Gateway Commands | Gateway 命令

The Gateway is the heart of OpenClaw — it connects everything.

Gateway 是 OpenClaw 的核心 — 连接一切。

### `openclaw gateway`

Start the Gateway manually.

手动启动 Gateway。

```bash
# Start with defaults
openclaw gateway

# Custom port
openclaw gateway --port 18790

# Verbose mode
openclaw gateway --verbose
```

### `openclaw gateway service`

Manage Gateway as a background service.

管理 Gateway 后台服务。

```bash
openclaw gateway status   # Check if running
openclaw gateway start    # Start service
openclaw gateway stop     # Stop service
openclaw gateway restart  # Restart service
openclaw gateway install  # Install service
openclaw gateway uninstall
```

### `openclaw logs`

View Gateway logs.

查看 Gateway 日志。

```bash
# Tail logs
openclaw logs --follow

# Last 100 lines
openclaw logs --limit 100

# JSON format
openclaw logs --json
```

---

## Messaging Commands | 消息命令

### `openclaw agent`

Talk to the AI assistant via CLI.

通过命令行与 AI 助手对话。

```bash
# Send a message
openclaw agent --message "What's the weather like?"

# Specify thinking level
openclaw agent --message "Analyze this code" --thinking high

# Target a specific channel
openclaw agent --message "Hello" --channel telegram
```

Thinking levels: `off`, `minimal`, `low`, `medium`, `high`, `xhigh`

### `openclaw message`

Send messages through channels.

通过渠道发送消息。

```bash
# Send to a phone number (WhatsApp)
openclaw message send --target +15555550123 --message "Hi there"

# Send a poll
openclaw message poll --channel discord \
  --poll-question "Lunch?" \
  --poll-option "Pizza" \
  --poll-option "Sushi"

# React to a message
openclaw message react --channel slack --emoji ":thumbsup:"
```

---

## Channel Commands | 渠道命令

### `openclaw channels`

Manage connections to messaging platforms.

管理消息平台连接。

```bash
# List configured channels
openclaw channels list

# Add a new channel
openclaw channels add

# Check health
openclaw channels status
openclaw channels status --probe  # Extra checks

# View logs
openclaw channels logs --channel whatsapp

# Login/logout
openclaw channels login --channel whatsapp
openclaw channels logout --channel telegram
```

---

## Model Commands | 模型命令

### `openclaw models`

Manage LLM models and authentication.

管理大语言模型和认证。

```bash
# List models
openclaw models list
openclaw models list --all      # Include unavailable
openclaw models list --local    # Local models only

# Check auth status
openclaw models status --check

# Set primary model
openclaw models set claude-3-opus

# Set up authentication
openclaw models auth add

# Manage fallbacks
openclaw models fallbacks list
openclaw models fallbacks add gpt-4-turbo
```

---

## Skills & Plugins | Skills 和插件

### `openclaw skills`

View available skills.

查看可用的 skills。

```bash
openclaw skills list
openclaw skills info browser-control
openclaw skills check  # Which are ready?
```

### `openclaw plugins`

Manage extensions.

管理扩展。

```bash
openclaw plugins list
openclaw plugins install ./my-plugin
openclaw plugins enable my-plugin
openclaw plugins disable my-plugin
openclaw plugins doctor  # Check for errors
```

---

## Browser Control | 浏览器控制

### `openclaw browser`

Control a browser instance.

控制浏览器实例。

```bash
# Start/stop browser
openclaw browser start
openclaw browser stop
openclaw browser status

# Navigate
openclaw browser open "https://example.com"
openclaw browser navigate "https://google.com"

# Interact
openclaw browser click "submit-button"
openclaw browser type "search-input" "hello world"
openclaw browser screenshot
openclaw browser screenshot --full-page

# List tabs
openclaw browser tabs
openclaw browser focus <targetId>
openclaw browser close <targetId>
```

---

## Scheduling | 定时任务

### `openclaw cron`

Schedule recurring tasks.

安排定时任务。

```bash
# List jobs
openclaw cron list

# Add a job
openclaw cron add --name "daily-report" --every "24h"
openclaw cron add --name "weekly-backup" --cron "0 0 * * 0"

# Manage jobs
openclaw cron enable <id>
openclaw cron disable <id>
openclaw cron rm <id>

# Run manually
openclaw cron run <id>
```

---

## In-Chat Commands | 聊天中的命令

When chatting with OpenClaw through WhatsApp, Telegram, etc., you can use these commands:

在 WhatsApp、Telegram 等平台与 OpenClaw 聊天时，可以使用这些命令：

| Command | Description | 说明 |
|---------|-------------|------|
| `/status` | Session info | 会话信息 |
| `/think [level]` | Set reasoning depth | 设置推理深度 |
| `/reset` or `/new` | Clear context | 清除上下文 |
| `/verbose on\|off` | Toggle output verbosity | 切换输出详细程度 |

---

## Utility Commands | 实用命令

```bash
# Open web dashboard
openclaw dashboard

# Open terminal UI
openclaw tui

# Search docs
openclaw docs "how to configure"

# Shell completion
openclaw completion bash >> ~/.bashrc
openclaw completion zsh >> ~/.zshrc

# Backup/restore
openclaw backup create
openclaw backup verify
```

---

## Pro Tips | 实用技巧

### Create shell aliases | 创建别名

```bash
# Add to .bashrc or .zshrc
alias oc="openclaw"
alias oca="openclaw agent --message"
alias ocs="openclaw status"
alias ocd="openclaw doctor"
```

### Quick message | 快速发消息

```bash
# One-liner
openclaw agent -m "Summarize my last 5 emails"
```

### Check everything | 全面检查

```bash
openclaw doctor --deep && openclaw status --usage
```

---

Next: [Troubleshooting](troubleshooting.md) | 下一步：[常见问题](troubleshooting.md)
