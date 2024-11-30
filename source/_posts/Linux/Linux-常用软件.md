---
title: Linux 常用软件
date: 2024-11-30 16:32:04
tags:
	- Linux
---


<!-- more -->

## Manjaro

### 常用软件

```bash
sudo pacman -Sy vim zsh wget git curl
```

## 配置

### 终端美化

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