# Claw101

A practical, bilingual guide to **OpenClaw** that is checked against the **official docs** and real CLI output.

一份面向 **OpenClaw** 的中英双语实用指南，内容按**官方文档**和**真实 CLI 输出**核对。

---

## Why this repo exists | 为什么做这个仓库

OpenClaw is powerful, but a lot of beginner pain is not about installation itself.
It is about:

- command names that are easy to guess wrong
- config locations that people misremember
- older examples floating around online
- ChatGPT-style answers that sound plausible but are not exact

OpenClaw 很强，但很多新手踩坑并不是因为“装不上”，而是因为：

- 命令名字不确定
- 配置文件位置
- 网上有些示例已经过时
- 很多 AI 回答“听起来对”，但实际命令不准确

**Claw101** is meant to be a practical companion to the official docs.

**Claw101** 的定位是官方文档的实用补充。

---

## Quick Start | 快速开始

### English

Requires **Node.js 22+**, Node 24 recommended.

1. Install:

```bash
npm install -g openclaw@latest
```

2. Run onboarding:

```bash
openclaw onboard
```

3. Open the dashboard or run your first command:

```bash
openclaw dashboard
# or
openclaw agent --message "Hello"
```

### 中文

最低需要 **Node.js 22+**, 推荐Node 24。

1. 安装：

```bash
npm install -g openclaw@latest
```

2. 运行引导向导：

```bash
openclaw onboard
```

3. 打开 dashboard，或者直接跑第一条命令：

```bash
openclaw dashboard
# 或者
openclaw agent --message "Hello"
```

---

## What this repo covers | 这个仓库会写什么

### English

- installation that actually matches current OpenClaw
- verified command usage
- config file locations and editing tips
- common mistakes and how to recover
- bilingual notes for beginners

### 中文

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
