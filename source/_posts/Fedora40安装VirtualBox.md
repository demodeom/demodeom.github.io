---
title: Fedora40安装VirtualBox
date: 2024-09-09 21:43:04
tags:
---

为什么安装 VirtualBox ？ 因为 VMware Workstation Pro 太难安装了，需要解决各种错误。

<!-- more -->

## 安装 kernel-devel

```bash
sudo dnf install kernel-devel -y
```

## 下载 rpm 安装包

```bash

```

## 安装 rpm 安装包

```bash
sudo dnf install VirtualBox-7.0-7.0.20_163906_fedora40-1.x86_64.rpm
```

## 错误

#### 错误1

```
Failed to enumerate host USB devices.
VirtualBox is not currently allowed to access USB devices. You can change this by adding your user to the 'vboxusers' group. Please see the user manual for a more detailed explanation.
```
解决方法

```bash
sudo usermod -aG vboxusers $USER
```

需要重启系统







