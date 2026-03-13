# Commands | 命令

These are the OpenClaw commands beginners actually use most often.

这些是新手最常会用到的 OpenClaw 命令。

---

## 1. Help first | 先看 help

When in doubt, do this first:

不确定时先这样做：

```bash
openclaw help
openclaw gateway --help
openclaw config --help
openclaw channels --help
```

This sounds obvious, but it prevents a surprising number of fake or outdated commands.

这听起来很基础，但能避免很多“看起来合理、其实不对”的命令。

---

## 2. Setup and overview | 初始化和总览

### Onboarding

```bash
openclaw onboard
openclaw onboard --flow quickstart
openclaw onboard --install-daemon
```

### Status / doctor

```bash
openclaw status
openclaw doctor
openclaw doctor --deep
```

---

## 3. Gateway commands | Gateway 命令

### Run in foreground

```bash
openclaw gateway
# or
openclaw gateway run
```

### Service lifecycle

```bash
openclaw gateway status
openclaw gateway start
openclaw gateway stop
openclaw gateway restart
openclaw gateway install
openclaw gateway uninstall
```

### Probe / inspect

```bash
openclaw gateway health
openclaw gateway probe
openclaw logs --follow
```

---

## 4. Config commands | 配置命令

```bash
openclaw config file
openclaw config get gateway.port
openclaw config set gateway.port 18790
openclaw config unset gateway.tailscale
openclaw config validate
```

Interactive config:

```bash
openclaw configure
```

---

## 5. Channels | 渠道

```bash
openclaw channels list
openclaw channels add
openclaw channels login --channel whatsapp
openclaw channels status
openclaw channels status --probe
openclaw channels logs --channel telegram
openclaw channels remove --channel telegram
```

---

## 6. Models | 模型

```bash
openclaw models list
openclaw models list --all
openclaw models auth add
openclaw models status --check
```

---

## 7. Agent / message | Agent / 发消息

### One CLI agent turn

```bash
openclaw agent --message "Hello"
```

### Deliver a reply back to a target

```bash
openclaw agent --to +15555550123 --message "Summarize this" --deliver
```

### Send a channel message directly

```bash
openclaw message send --channel telegram --target @mychat --message "Hi"
```

---

## 8. Good commands to memorize | 值得记住的命令

If I had to memorize only a few:

如果只记少数几个，我会记这些：

```bash
openclaw help
openclaw status
openclaw doctor
openclaw gateway status
openclaw config file
openclaw channels status
openclaw logs --follow
```
