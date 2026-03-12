# Claw101

A practical guide for OpenClaw users — from zero to productive.

OpenClaw 实用指南 — 从入门到上手。

---

## What is this?  这是什么？

**Claw101** is a community-driven guide for [OpenClaw](https://github.com/openclaw/openclaw), a personal AI assistant you run on your own devices. It works across WhatsApp, Telegram, Slack, Discord, Signal, iMessage, and more.

**Claw101** 是一份面向 [OpenClaw](https://github.com/openclaw/openclaw) 用户的社区指南。OpenClaw 是一个运行在你自己设备上的个人 AI 助手，支持 WhatsApp、Telegram、Slack、Discord、Signal、iMessage 等多个平台。

## Why does this exist? | 为什么要做这个？

Official docs are great, but sometimes you just want someone to tell you:
- "Here's what works"
- "Here's what doesn't"
- "Here's what nobody told me but I wish they had"

That's what Claw101 is for.

官方文档很好，但有时你只是想要有人告诉你：
- "这样做是对的"
- "那样做会出问题"
- "这些是没人告诉我但我希望早点知道的事"

这就是 Claw101 存在的意义。

## Quick Start | 快速开始

### 1. Install OpenClaw | 安装 OpenClaw

Requires Node ≥22.

需要 Node ≥22。

```bash
npm install -g openclaw@latest
```

### 2. Run the onboarding wizard | 运行引导向导

```bash
openclaw onboard --install-daemon
```

This wizard will:
- Set up the Gateway (local control plane)
- Configure your workspace
- Connect your chat channels (WhatsApp, Telegram, etc.)
- Install recommended skills

向导会帮你：
- 设置 Gateway（本地控制平面）
- 配置工作空间
- 连接聊天渠道（WhatsApp、Telegram 等）
- 安装推荐的 skills

### 3. Check that everything works | 检查是否正常

```bash
openclaw doctor
```

### 4. Send your first message | 发送第一条消息

```bash
openclaw agent --message "Hello, what can you do?"
```

That's it! You're up and running.

就这么简单！你已经可以开始了。

## Documentation | 文档

| Topic | 主题 | Link |
|-------|------|------|
| Installation | 安装 | [docs/installation.md](docs/installation.md) |
| Configuration | 配置 | [docs/configuration.md](docs/configuration.md) |
| Commands | 命令 | [docs/commands.md](docs/commands.md) |
| Troubleshooting | 常见问题 | [docs/troubleshooting.md](docs/troubleshooting.md) |

## Official Resources | 官方资源

- [GitHub](https://github.com/openclaw/openclaw)
- [CLI Reference](https://docs.openclaw.ai/cli)
- [Website](https://openclaw.ai/)

## Contributing | 贡献

Found something wrong? Know a better way? Open an issue or PR. This guide is for the community, by the community.

发现了错误？知道更好的方法？欢迎提 issue 或 PR。这份指南来自社区，服务社区。

## License

MIT
