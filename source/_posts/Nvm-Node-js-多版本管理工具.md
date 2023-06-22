---
title: Nvm-Node.js 多版本管理工具
date: 2023-06-22 17:53:07
tags:
	- Ubuntu
	- Node.js
---


nvm 是node.js的版本管理器，设计为按用户安装并按 shell 调用。nvm适用于任何兼容 POSIX 的 shell（sh、dash、ksh、zsh、bash），特别是在以下平台上：unix、macOS 和windows WSL。

<!-- more -->

## 安装 nvm


```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
```

临时生效 nvm ，永久生效需要重启系统

```
source ~/.bashrc
```

## 安装 Node.js

安装最新的长期支持版

```bash
nvm install --lts
```

安装指定版本最新版

```bash
nvm install 14
```

安装指定版本

```bash
nvm install 8.17.0
```

### 查看安装 Node.js 版本

```
nvm list
```

## 切换版本

使用最新的长期支持版

```bash
nvm use --lts
```

使用指定版本最新版

```bash
nvm use 14
```

使用指定版本

```bash
nvm use 8.17.0
```

设置默认 Node.js 版本

```bash
nvm alias default 8.1.0
```