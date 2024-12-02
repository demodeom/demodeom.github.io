---
title: Linux 常用软件
date: 2024-11-30 16:32:04
tags:
	- Linux
	- 常用软件
---


<!-- more -->

## Manjaro

### 常用软件

```bash
sudo pacman -Sy vim zsh wget git curl
```

## 配置

### 终端美化

提升您的命令行体验，尽在 Oh My Zsh！作为最受欢迎的 Zsh 配置框架，Oh My Zsh 让您的终端界面焕然一新。丰富的主题和插件支持，让您轻松自定义环境，提升工作效率。无论是代码开发、系统管理还是日常任务，Oh My Zsh 都能让您的命令行操作更加智能化和便捷。加入数万用户的行列，立即体验 Oh My Zsh 带来的终端革命，让您的工作更高效、更愉悦！

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Git

```bash
# 配置默认分支名
git config --global init.defaultBranch main

# 配置用户名
git config --global user.name "demo"

# 配置用户邮箱
git config --global user.email "demodeom@example.com"
```