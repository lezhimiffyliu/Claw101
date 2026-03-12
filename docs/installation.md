# Installation | 安装

Getting OpenClaw installed on your machine.

在你的机器上安装 OpenClaw。

---

## Requirements | 前置要求

- **Node.js ≥22** (required | 必须)
- macOS, Linux, or Windows

Check your Node version:

检查 Node 版本：

```bash
node --version
# Should be v22.x.x or higher
```

If you need to upgrade Node, use [nvm](https://github.com/nvm-sh/nvm) or download from [nodejs.org](https://nodejs.org/).

如果需要升级 Node，使用 [nvm](https://github.com/nvm-sh/nvm) 或从 [nodejs.org](https://nodejs.org/) 下载。

## Installation | 安装

### npm (Recommended | 推荐)

```bash
npm install -g openclaw@latest
```

### pnpm

```bash
pnpm add -g openclaw@latest
```

## Initial Setup | 初始设置

After installing, run the onboarding wizard:

安装后，运行引导向导：

```bash
openclaw onboard --install-daemon
```

The `--install-daemon` flag installs a background service (launchd on macOS, systemd on Linux) so the Gateway stays running.

`--install-daemon` 参数会安装后台服务（macOS 上是 launchd，Linux 上是 systemd），让 Gateway 保持运行。

### What the wizard does | 向导做了什么

1. Sets up the **Gateway** (local WebSocket control plane, default port 18789)
2. Configures your **workspace** directory
3. Connects **chat channels** (WhatsApp, Telegram, Discord, Slack, etc.)
4. Installs **skills** (optional capabilities)
5. Configures **model authentication** (OpenAI, Anthropic, Mistral, etc.)

### Wizard options | 向导选项

```bash
# Quick setup with defaults
openclaw onboard --flow quickstart

# Full control over every option
openclaw onboard --flow advanced

# Non-interactive (for scripts/automation)
openclaw onboard --non-interactive
```

## Verifying Installation | 验证安装

```bash
# Check version
openclaw --version

# Run health checks
openclaw doctor

# Check Gateway status
openclaw gateway status
```

If `openclaw doctor` shows all green, you're good to go.

如果 `openclaw doctor` 全部显示绿色，说明安装成功。

## Updating | 更新

```bash
openclaw update
```

Or specify a channel:

或指定更新通道：

```bash
openclaw update --channel stable  # stable, beta, or dev
```

## Uninstalling | 卸载

```bash
# Remove service and data
openclaw uninstall --all

# Or selectively
openclaw uninstall --service    # Just the daemon
openclaw uninstall --state      # Local state
openclaw uninstall --workspace  # Workspace files
```

Then remove the npm package:

然后删除 npm 包：

```bash
npm uninstall -g openclaw
```

---

## Common Installation Issues | 常见安装问题

### "Node version too old"

```bash
# Check your version
node --version

# If using nvm, install Node 22+
nvm install 22
nvm use 22
```

### "EACCES permission denied" on npm install

Don't use `sudo`. Fix npm permissions instead:

不要用 `sudo`。修复 npm 权限：

```bash
# Option 1: Use nvm (recommended)
# Option 2: Change npm's default directory
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
# Add to PATH in .bashrc/.zshrc:
export PATH=~/.npm-global/bin:$PATH
```

### Gateway won't start

```bash
# Check if port 18789 is in use
lsof -i :18789

# Try a different port
openclaw gateway --port 18790
```

---

Next: [Configuration](configuration.md) | 下一步：[配置](configuration.md)
