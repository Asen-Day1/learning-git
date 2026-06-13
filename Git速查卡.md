# Git & GitHub 5 分钟速查卡

> 别被术语吓到。Git 就是一个**自动帮你记代码变化**的工具，真正用的命令不超过 10 个。

---

## 🧠 先搞懂三个概念

```
你的电脑                     GitHub 云端
┌─────────────┐             ┌──────────────┐
│ 工作目录     │  git add   │              │
│ (写代码)  ──→ 暂存区     │  git commit  │  远程仓库
│            ←── (Stage) ──→ 本地仓库 ────→ (GitHub)
│  git restore│             │  git push    │
└─────────────┘             └──────────────┘
```

| 区域 | 是什么 | 记法 |
|------|--------|------|
| **工作目录** | 你正在写的代码 | 桌面上的草稿 |
| **暂存区 (Stage)** | 准备提交的文件清单 | 购物车 |
| **本地仓库 (Repo)** | 已存档的所有版本 | 保险柜 |
| **远程仓库 (GitHub)** | 云端备份 + 协作 | 云端网盘 |

---

## ⚡ 日常 5 步循环（你每天就干这些）

```bash
# 1. 看看改了啥（随时用，最安全的命令）
git status

# 2. 加入购物车（把修改加到暂存区）
git add .

# 3. 确认存档（提交到本地仓库）
git commit -m "feat: 添加了登录功能"

# 4. 上传云端
git push origin main

# 5. 下载别人的更新
git pull origin main
```

---

## 🌿 分支协作（两人以上必看）

```bash
# 创建并切换到新分支
git checkout -b feature-新功能名

# ... 在上面写代码、add、commit ...

# 推送到 GitHub，然后去网页创建 Pull Request
git push -u origin feature-新功能名

# 合并完成后，切回 main 并同步
git checkout main
git pull origin main
git branch -d feature-新功能名     # 删除本地分支
```

> 🎯 **精髓**：main 分支永远保持稳定。开发都在 feature 分支上做，做完合并回去。

---

## 🔧 救命四招（搞砸了怎么办）

```bash
# 1. 文件改坏了，想回到上次 commit 的状态
git restore 文件名

# 2. 不小心 git add 了，想撤回
git restore --staged 文件名

# 3. commit 信息写错了，想改
git commit --amend -m "新的提交信息"

# 4. 想回到过去看一眼（不破坏历史）
git checkout <commit-id>
git checkout main    # 看完回到最新
```

---

## 📋 命令速查表

| 命令 | 作用 | 频率 |
|------|------|------|
| `git status` | 查看当前状态 | 🔥🔥🔥🔥🔥 |
| `git add .` | 暂存所有修改 | 🔥🔥🔥🔥🔥 |
| `git commit -m "..."` | 提交 | 🔥🔥🔥🔥🔥 |
| `git push origin main` | 推送到 GitHub | 🔥🔥🔥🔥 |
| `git pull origin main` | 从 GitHub 拉取 | 🔥🔥🔥🔥 |
| `git log --oneline --graph` | 看提交历史 | 🔥🔥🔥 |
| `git checkout -b 分支名` | 新建并切换分支 | 🔥🔥🔥 |
| `git checkout main` | 切换回主分支 | 🔥🔥🔥 |
| `git merge 分支名` | 合并分支 | 🔥🔥 |
| `git clone 地址` | 克隆远程仓库 | 🔥🔥 |
| `git diff` | 查看具体改了啥 | 🔥🔥 |
| `git restore 文件` | 撤销修改 | 🔥 |

---

## 🆘 最常见报错

| 报错 | 原因 | 解决 |
|------|------|------|
| `Permission denied (publickey)` | SSH 密钥没配 | 重新配置 SSH 密钥 |
| `failed to push` | 远端有你的本地没有的更新 | 先 `git pull` 再 `git push` |
| `merge conflict` | 你和别人改了同一个地方 | 手动选择保留谁的，然后 add + commit |
| `detached HEAD` | 你切到了某个历史 commit | `git checkout main` 回到正常状态 |

---

## ✅ 一次性配置（新电脑只需做一次）

```bash
# 1. 告诉 Git 你是谁
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"

# 2. 生成 SSH 密钥（一路回车）
ssh-keygen -t ed25519 -C "你的邮箱"

# 3. 复制公钥，粘贴到 GitHub → Settings → SSH Keys
cat ~/.ssh/id_ed25519.pub

# 4. 测试
ssh -T git@github.com
```

---

> 📖 需要详细教程？看同目录下的 `Git学习指南.md`
>
> 💡 **最重要的习惯**：随时敲 `git status`，它永远安全，永远不会搞坏东西。
