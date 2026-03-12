# Installation | 安装

A minimal install guide that stays close to the real OpenClaw CLI.

尽量贴近真实 OpenClaw CLI 的最小安装指南。

---

## 1. Requirements | 前置要求

OpenClaw currently expects **Node.js 22+**.

OpenClaw 目前要求 **Node.js 22+**。

Check:

```bash
node --version
```

If needed, upgrade Node first.

如果版本太低，先升级 Node。

---

## 2. Install the CLI | 安装 CLI

### npm

```bash
npm install -g openclaw@latest
```

### pnpm

```bash
pnpm add -g openclaw@latest
```

Then verify:

```bash
openclaw --version
openclaw help
```

---

## 3. Run onboarding | 运行引导向导

The safest default is just:

最稳妥的默认做法就是：

```bash
openclaw onboard
```

Useful variants:

```bash
openclaw onboard --flow quickstart
openclaw onboard --install-daemon
openclaw onboard --flow manual
```

### What onboarding does | onboard 会做什么

It can help you configure:

- Gateway
- workspace
- model authentication
- channels (Telegram / WhatsApp / Discord / etc.)
- optional skills

它会帮你配置：

- Gateway
- workspace
- 模型认证
- 渠道（Telegram / WhatsApp / Discord 等）
- 可选 skills

---

## 4. Verify that it works | 验证是否正常

These are the first commands worth running:

```bash
openclaw status
openclaw doctor
openclaw gateway status
```

If you want a broad overview, `openclaw status` is a great starting point.

如果你想快速看全局状态，`openclaw status` 很有用。

---

## 5. Fastest first interaction | 最快的首次体验方式

A lot of people expect a magical chat command first.
In practice, the easiest first step is often:

很多人一开始会找一个“直接聊天”的命令。
实际上，最快上手通常是：

```bash
openclaw dashboard
```

That opens the Control UI.

它会打开 Control UI。

You can also run one CLI turn with:

你也可以用下面这个命令跑一轮 CLI agent：

```bash
openclaw agent --message "Hello"
```

---

## 6. Gateway basics | Gateway 基础

There are two common modes people confuse:

很多人会混淆两种模式：

### Run in foreground | 前台运行

```bash
openclaw gateway
# or
openclaw gateway run
```

### Manage the installed service | 管理已安装的后台服务

```bash
openclaw gateway status
openclaw gateway start
openclaw gateway stop
openclaw gateway restart
```

> Common mistake: many people write `openclaw gateway service start`.
> That is not the command form you should teach beginners first.

> 常见错误：很多人会写成 `openclaw gateway service start`。
> 这不是最适合教新手的命令形式。

---

## 7. Config file location | 配置文件位置

The active config file is usually:

当前配置文件通常在：

```text
~/.openclaw/openclaw.json
```

To print the exact path on your machine:

想打印你机器上的准确路径：

```bash
openclaw config file
```

---

## 8. Recommended sanity check list | 推荐的自检清单

After install, I would personally check these in order:

安装完后，我会按这个顺序检查：

```bash
openclaw --version
openclaw status
openclaw doctor
openclaw config file
openclaw gateway status
```

---

## 9. A few easy-to-miss pitfalls | 几个很容易踩的坑

### Pitfall 1: PATH problem

If `openclaw` is not found after install, your npm global bin is probably not in PATH.

如果安装后找不到 `openclaw`，大概率是 npm 全局 bin 不在 PATH 里。

### Pitfall 2: Guessing commands from memory

OpenClaw has a lot of subcommands. If unsure, prefer:

OpenClaw 的子命令很多，不确定时优先：

```bash
openclaw help
openclaw gateway --help
openclaw config --help
openclaw channels --help
```

### Pitfall 3: Mixing up onboarding and configuration

- `openclaw onboard` = setup wizard / initial guided setup
- `openclaw configure` = interactive configuration later

- `openclaw onboard` = 初始化引导
- `openclaw configure` = 后续交互式配置

---

## 10. If something feels wrong | 如果感觉哪里不对

Start with:

```bash
openclaw doctor
openclaw status
openclaw logs --follow
```

Then read the official docs before trusting random generated commands.

然后优先看官方文档，不要先相信随机生成的命令。
