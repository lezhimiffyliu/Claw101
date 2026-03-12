# Configuration | 配置

This page focuses on the config facts people most often get wrong.

这一页专门写那些最容易记错的配置事实。

---

## 1. Config file location | 配置文件位置

The active config file is usually:

当前配置文件通常在：

```text
~/.openclaw/openclaw.json
```

To print the real path on your current machine:

想打印当前机器上的真实路径：

```bash
openclaw config file
```

This is better than guessing.

这个比靠记忆猜要靠谱得多。

---

## 2. Is it JSON or JSON5? | 它到底是 JSON 还是 JSON5？

The file path is `openclaw.json`, but OpenClaw config tooling supports JSON5-style parsing in many places.

文件名是 `openclaw.json`，但 OpenClaw 的配置工具在很多地方支持 JSON5 风格解析。

Practical advice:

实用建议：

- treat the file as OpenClaw config, not “just random JSON”
- use `openclaw config validate` after edits

- 把它当成 OpenClaw 配置文件，而不是“普通 JSON”
- 改完后跑 `openclaw config validate`

---

## 3. Read config values | 读取配置

```bash
openclaw config get gateway.port
openclaw config get agents.defaults.workspace
openclaw config get channels.telegram.enabled
```

---

## 4. Set / unset config values | 修改 / 删除配置

```bash
openclaw config set gateway.port 18790
openclaw config set gateway.bind loopback
openclaw config unset gateway.tailscale
```

Then validate:

```bash
openclaw config validate
```

---

## 5. Interactive configuration | 交互式配置

If you want guided configuration later:

如果你后面还想用交互式方式重新配置：

```bash
openclaw configure
```

For first-time setup, `openclaw onboard` is still the better mental model.

第一次初始化时，还是更推荐把 `openclaw onboard` 当成主入口。

---

## 6. Gateway-related config you will care about | 最常见的 Gateway 配置

Examples:

```bash
openclaw config get gateway.port
openclaw config get gateway.bind
openclaw config get gateway.auth.mode
```

Typical values include:

常见值包括：

- `gateway.port`
- `gateway.bind`
- `gateway.auth.mode`

A common safe default is loopback bind.

比较安全的默认值通常是 loopback。

---

## 7. Profiles and isolated environments | profile 和隔离环境

OpenClaw supports isolated profiles.

OpenClaw 支持隔离 profile。

### Dev profile

```bash
openclaw --dev gateway
```

This uses a separate state directory, typically `~/.openclaw-dev/`.

这会使用单独的状态目录，通常是 `~/.openclaw-dev/`。

### Named profile

```bash
openclaw --profile work gateway
```

This uses a separate profile directory like `~/.openclaw-work/`.

这会使用类似 `~/.openclaw-work/` 的独立 profile 目录。

---

## 8. Useful verification commands | 很有用的验证命令

```bash
openclaw config file
openclaw config validate
openclaw status
openclaw gateway status
```

---

## 9. Common mistakes | 常见错误

### Mistake 1: editing the wrong profile

If you use `--dev` or `--profile`, you may not be editing the config you think you are.

如果你用了 `--dev` 或 `--profile`，你修改的可能不是你以为的那个配置。

### Mistake 2: editing config but not validating

Always run:

```bash
openclaw config validate
```

### Mistake 3: guessing config path from memory

Just run:

```bash
openclaw config file
```

---

## 10. If you are documenting OpenClaw | 如果你在写 OpenClaw 教程

Do not hardcode too many assumptions.
Prefer commands that let users inspect their own machine state.

不要把太多假设写死。
尽量用能让用户自己检查机器状态的命令。
