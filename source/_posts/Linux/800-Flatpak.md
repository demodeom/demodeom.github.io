---
title: Linux 软件管理-Flatpak
date: 2024-10-20 16:57:44
tags:
	- Linux
sticky: 800
---

Flatpak 是一个现代化的软件包管理系统，旨在简化 Linux 应用程序的分发和安装。无论你使用哪个发行版，Flatpak 都能为你提供一致的应用体验，使软件安装变得更加便捷。

<!-- more -->

## APT

安装 Flatpak

```bash
sudo apt install flatpak -y
```

## 镜像

Flatpak 配置 上海交通大学 镜像 https://mirrors.sjtug.sjtu.edu.cn/docs/flathub

```bash
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak remote-modify flathub --url=https://mirror.sjtu.edu.cn/flathub
```

- 官方仓库 https://dl.flathub.org/repo/flathub.flatpakrepo
- 上交大镜像 https://mirror.sjtu.edu.cn/flathub


```
flatpak remote-modify flathub --url=https://dl.flathub.org/repo/flathub.flatpakrepo
```
