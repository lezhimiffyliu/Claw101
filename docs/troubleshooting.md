# Troubleshooting | 排错

A short list of issues beginners hit first.

给新手的第一版常见问题清单。

---

## 1. First commands to run | 先跑哪些命令

If something feels off, start here:

如果感觉哪里不对，先跑这些：

```bash
openclaw status
openclaw doctor
openclaw gateway status
openclaw channels status --probe
openclaw logs --follow
```

---

## 2. `openclaw` command not found

### Cause | 原因

Your npm global bin is probably not in PATH.

大概率是 npm 全局 bin 不在 PATH 中。

### Fix | 解决

```bash
npm config get prefix
```

Then make sure `<prefix>/bin` is in PATH.

然后确认 `<prefix>/bin` 在 PATH 里。

---

## 3. Node version too old

### Check

```bash
node --version
```

OpenClaw expects Node 22+.

OpenClaw 需要 Node 22+。

---

## 4. Gateway not running

### Check

```bash
openclaw gateway status
```

### Start foreground process

```bash
openclaw gateway
# or
openclaw gateway run
```

### Start installed service

```bash
openclaw gateway start
```

---

## 5. Port conflict on 18789

### Check

```bash
lsof -i :18789
```

### Options

- stop the conflicting process
- or change the port

- 停掉冲突进程
- 或者改端口

Example:

```bash
openclaw config set gateway.port 18790
openclaw config validate
```

---

## 6. Channel problems

Start with:

```bash
openclaw channels list
openclaw channels status
openclaw channels status --probe
openclaw channels logs --channel telegram
```

If needed, re-login:

```bash
openclaw channels login --channel whatsapp
openclaw channels logout --channel whatsapp
```

---

## 7. Model auth problems

### Useful commands

```bash
openclaw models status --check
openclaw models auth add
openclaw models list --all
```

If auth is wrong, fix auth first before blaming the agent.

如果认证有问题，先修认证，再看 agent。

---

## 8. Config confusion

### Print the active config file

```bash
openclaw config file
```

### Validate after editing

```bash
openclaw config validate
```

A lot of confusion is really just “I edited the wrong file/profile.”

很多问题本质上只是“你改错了 profile 或文件”。

---

## 9. Common documentation trap | 常见文档陷阱

A command can look very believable and still be the wrong shape.

一个命令看起来很像真的，也可能还是错的。

Example:

### Less ideal beginner guidance

```bash
openclaw gateway service start
```

### Better first command to teach

```bash
openclaw gateway start
```

If unsure, always re-check with `--help`.

不确定时，永远重新看 `--help`。

---

## 10. My recommended recovery path | 我推荐的恢复路径

When a setup is messy, I would do this:

当环境已经有点乱的时候，我会这样排：

```bash
openclaw status
openclaw doctor
openclaw config file
openclaw gateway status
openclaw channels status --probe
openclaw logs --follow
```

This gets you grounded fast.

这套命令能很快帮你重新建立全局判断。
