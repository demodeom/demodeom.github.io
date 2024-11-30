---
title: Linux 软件管理
date: 2024-11-30 16:39:35
tags:
	- Linux
	- AppImage
	- Flatpak
---

<!-- more -->

## AppImage

Gear Lever是一个可以轻松管理 AppImage 的工具！Gear Lever 将为你组织和管理 AppImage 文件，生成桌面快捷方式、更新应用程序或保留多个版本并存。

## GearLever

```bash
flatpak install flathub it.mijorus.gearlever
```

## Flatpak 镜像

镜像

配置 [上海交通大学 Flatpak 镜像]([上海交通大学 Linux 用户组 软件源镜像服务](https://mirrors.sjtug.sjtu.edu.cn/docs/flathub))

```bash
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak remote-modify flathub --url=https://mirror.sjtu.edu.cn/flathub
```

- 官方仓库 https://flathub.org/repo/flathub
  
- 上交大镜像 https://mirror.sjtu.edu.cn/flathub