# Claw101

A practical, bilingual guide to **OpenClaw** that is checked against the **official docs** and real CLI output.

一份面向 **OpenClaw** 的中英双语实用指南，内容会尽量按**官方文档**和**真实 CLI 输出**核对，而不是凭印象乱写命令。

---

## Why this repo exists | 为什么做这个仓库

OpenClaw is powerful, but a lot of beginner pain is not about installation itself.
It is about:

- command names that are easy to guess wrong
- config locations that people misremember
- older examples floating around online
- ChatGPT-style answers that sound plausible but are not exact

OpenClaw 很强，但很多新手踩坑并不是因为“装不上”，而是因为：

- 命令名字很容易猜错
- 配置文件位置容易记混
- 网上有些示例已经过时
- 很多 AI 回答“听起来对”，但实际命令不准确

**Claw101** is meant to be a practical companion to the official docs, not a replacement.

**Claw101** 的定位是官方文档的实用补充，不是替代品。

---

## Principles | 原则

This repo tries to follow three rules:

1. **Prefer official docs first**
2. **Only recommend commands that are verified**
3. **Call out common wrong commands explicitly**

这个仓库尽量遵守三条原则：

1. **优先以官方文档为准**
2. **只推荐已经核实过的命令**
3. **把常见错命令直接指出来**

---

## Quick Start | 快速开始

### 1. Install OpenClaw | 安装 OpenClaw

Requires **Node.js 22+**.

需要 **Node.js 22+**。

```bash
npm install -g openclaw@latest
```

### 2. Run onboarding | 跑引导向导

```bash
openclaw onboard
```

Common variants:

```bash
openclaw onboard --flow quickstart
openclaw onboard --install-daemon
```

常见变体：

```bash
openclaw onboard --flow quickstart
openclaw onboard --install-daemon
```

### 3. Check your setup | 检查当前状态

```bash
openclaw status
openclaw doctor
openclaw gateway status
```

### 4. Fastest way to try it | 最快开始体验

```bash
openclaw dashboard
```

This opens the Control UI and is usually the fastest first interaction.

这个命令会打开 Control UI，通常是最快的第一次上手方式。

---

## What this repo covers | 这个仓库会写什么

- installation that actually matches current OpenClaw
- verified command usage
- config file locations and editing tips
- common mistakes and how to recover
- bilingual notes for beginners

- 与当前 OpenClaw 对得上的安装流程
- 已核实的命令用法
- 配置文件位置和修改方式
- 常见错误和恢复方法
- 面向新手的中英双语说明

---

## Docs in this repo | 仓库内文档

- [docs/installation.md](docs/installation.md) — installation + first setup
- [docs/commands.md](docs/commands.md) — commands you will actually use
- [docs/configuration.md](docs/configuration.md) — config file location and edits
- [docs/troubleshooting.md](docs/troubleshooting.md) — common mistakes and fixes

---

## Official references | 官方参考

- OpenClaw docs: <https://docs.openclaw.ai>
- OpenClaw repo: <https://github.com/openclaw/openclaw>

If Claw101 and the official docs disagree, trust the official docs first.

如果 Claw101 和官方文档冲突，请优先相信官方文档。

---

## Contributing | 贡献

PRs that improve correctness are especially welcome.

尤其欢迎修正命令、路径、配置细节的 PR。

## License

MIT
