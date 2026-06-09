### 1、如何使用Git和Git-Hub
##### 1、什么是Git&Git-Hub
Git 是一个分布式版本控制系统，由 Linux 之父 Linus Torvalds 于 2005 年创建。

```
核心特点
本地运行：不需要网络，在你自己电脑上就能使用
版本管理：记录文件的每一次修改，可以随时回退到任何历史版本
分支功能：支持创建独立分支进行开发，最后再合并
分布式：每个开发者的电脑上都有完整的代码仓库
```

```
git init          # 初始化仓库
git add .         # 添加文件到暂存区
git commit -m "说明" # 提交到本地仓库
git log           # 查看提交历史
git branch        # 查看分支
git merge         # 合并分支
Git-Hbu 代码托管平台(远程仓库) 
```
GitHub 是一个基于 Git 的代码托管平台，成立于 2008 年，2018 年被微软收购。
```
核心特点
云端存储：将本地 Git 仓库上传到云端
协作平台：多人可以同时开发同一个项目
社交编程：可以关注、Star、Fork 别人的项目
项目管理：提供 Issues、Projects、Wiki 等功能
CI/CD：GitHub Actions 实现自动化测试和部署
```
```
功能	           说明
Repository      代码仓库
Fork	       复制别人的仓库到自己的账号
Pull Request     向原仓库提交代码合并请求
Issues	        问题跟踪和讨论
Actions	        自动化工作流
```

##### 2、git 与Git-Hub关联
步骤 1：安装 Git
Windows：下载 Git for Windows
Mac：brew install git 或下载安装包
Linux：sudo apt install git

```
配置用户信息：
bash
git config --global user.name "你的GitHub用户名"
git config --global user.email "你的GitHub邮箱"
```

步骤 2：注册 GitHub 账号
访问 github.com 注册


步骤 3：生成并配置 SSH 密钥（推荐）
```
生成密钥：
bash
ssh-keygen -t ed25519 -C "你的邮箱@example.com"
# 一路回车，使用默认设置
```

```
查看公钥：
bash
cat ~/.ssh/id_ed25519.pub
```

添加到 GitHub：
```
GitHub → Settings → SSH and GPG keys
New SSH Key → 粘贴公钥 → Add
```

测试连接：
```bash
ssh -T git@github.com
# 看到 "Hi 用户名! You've successfully authenticated..." 即成功
```

步骤 4：创建仓库并关联
方法一：从本地推送到 GitHub

```
bash
# 1. 本地已有项目
cd 你的项目文件夹
git init
git add .
git commit -m "首次提交"

# 2. GitHub 上新建空仓库（不要勾选初始化README）

# 3. 关联远程仓库
git remote add origin git@github.com:你的用户名/仓库名.git

# 4. 推送代码
git push -u origin main
```

方法二：从 GitHub 克隆到本地
```
bash
# 1. GitHub 上创建仓库（可勾选添加 README）
# 2. 克隆到本地
git clone git@github.com:你的用户名/仓库名.git
# 3. 进入目录开始开发
cd 仓库名
```

步骤 5：日常协作流程
```
bash
# 拉取最新代码
git pull origin main
# 本地修改后
git add .
git commit -m "描述修改内容"
# 推送到 GitHub
git push origin main
```


五、常见问题
Q：用 HTTPS 还是 SSH？
SSH（推荐）：配置一次，后续免密码

HTTPS：每次 push 需要输入账号密码（可用 token）

Q：push 时要求输入密码？
GitHub 已停用密码认证，需要：

使用 SSH 方式

或创建 Personal Access Token（Settings → Developer settings → Personal access tokens）



