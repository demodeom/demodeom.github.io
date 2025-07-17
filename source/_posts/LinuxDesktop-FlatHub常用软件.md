---
title: '[LinuxDesktop]FlatHub常用软件'
date: 2025-07-18 06:50:45
tags:
---

FlatHub 仓库中个人常用软件


<!-- more -->

##  Gnome Extension Manager

> Gnome Extension Manager 是一款用于 GNOME 桌面环境的图形化工具，方便用户安装、管理和更新 GNOME Shell 扩展。

```bash
flatpak install -y flathub com.mattjakeman.ExtensionManager
```



**推荐Gnome Desktop Extension**

- **User Themes** 用户自定义主题
- **Blur my Shell** 任务栏透明
- **Dash to Dock** 工具栏
- **Input Method Panel** fcitx5 输入法美化工具
- **AppIndicator and KStatusNotifierItem Support** 任务栏应用小图标支持

## Sublime Merge

> https://flathub.org/apps/com.sublimemerge.App 是一款高效的 Git  客户端，提供直观的用户界面和强大的功能，旨在简化版本控制的管理。它具有实时预览和语法高亮功能，方便用户查看和编辑代码变更。Sublime  Merge 还支持快速搜索、分支管理和合并冲突解决，提升开发者的工作效率。此外，作为 Sublime Text 的姊妹产品，Sublime  Merge 可以与 Sublime Text 无缝集成，适合需要高效 Git 工作流的开发者。

```bash
flatpak install -y  flathub com.sublimemerge.App
```



## Color Picker

> **Color Picker** 是一款用于拾取屏幕任意位置颜色的实用工具，支持复制色码（如 HEX、RGB）。

```bash
flatpak install -y  flathub nl.hjdskes.gcolor3
```

## GearLever

> Gear Lever是一个可以轻松管理 AppImage 的工具！Gear Lever 将为你组织和管理 AppImage 文件，生成桌面快捷方式、更新应用程序或保留多个版本并存。

```bash
flatpak install -y  flathub it.mijorus.gearlever
```

## Insomnia

> Insomnia 是一款开源的 API 客户端，专为开发人员设计，旨在简化 API 的测试和调试过程。它提供直观的用户界面，支持 REST 和 GraphQL 请求，使用户能够轻松构建、发送和管理 API 请求。Insomnia  具备丰富的功能，包括环境变量管理、请求历史记录、代码生成和响应格式化，方便用户快速分析和调试数据。此外，Insomnia  还支持插件扩展，用户可以根据需要添加功能，提升工作效率。无论是进行日常开发还是调试复杂的 API，Insomnia 都是一个理想的工具。

```bash
flatpak install -y  flathub rest.insomnia.Insomnia
```

## LocalSend

> LocalSend 是一款用于局域网内设备间文件传输的软件。无需互联网连接，用户可以通过 Wi-Fi  将文件快速传输到同一网络中的其他设备。支持多种文件格式，界面友好，操作简便，适用于各种操作系统。LocalSend  提供了高效、安全的文件共享解决方案，是局域网内设备互传文件的理想选择。

```bash
flatpak install  -y flathub org.localsend.localsend_app
```

## 下载工具

### Motrix

> Motrix 是一款开源的下载管理器，支持多种下载协议，包括 HTTP、HTTPS、FTP、BitTorrent  和磁力链接。它提供简洁直观的用户界面，方便用户快速添加和管理下载任务。Motrix  支持多线程下载，可有效提高下载速度，同时还具备断点续传、定时下载和下载分类等功能。该软件跨平台兼容，适用于 Windows、macOS 和  Linux，适合需要高效下载管理的用户。无论是大文件下载还是批量资源获取，Motrix 都能提供出色的性能和便利性。

```bash
flatpak install  -y flathub net.agalwood.Motrix
```

### Freedownloadmanager

**Free Download Manager (FDM)** 是一款免费的多功能下载加速工具，支持 **HTTP/HTTPS、FTP、BT 种子及磁力链接**，提供智能分段下载技术以提升速度。其特色功能包括：**批量下载、断点续传、带宽控制、视频抓取**（支持 YouTube 等平台），以及 **远程控制**（通过手机App管理下载任务）。界面简洁，无广告，适用于 Windows、macOS 及 Linux 系统，是替代迅雷或 IDM 的轻量化选择。

```
flatpak install flathub org.freedownloadmanager.Manager
```

###  qBittorrent

**qBittorrent** 是一款免费、开源的 **BitTorrent 客户端**，以轻量高效、无广告著称。采用 **Qt 框架**开发，支持 **Windows/macOS/Linux**，提供与 **μTorrent** 类似的功能（如磁力链接、种子制作、IP 过滤），但完全 **去商业化**。其特色包括 **内置搜索引擎**、**RSS 订阅下载**、**远程控制**（Web UI）及 **加密传输**，是注重隐私和简洁体验用户的理想选择。

```
flatpak install flathub org.qbittorrent.qBittorrent
```

## Gecko 内核浏览器

###  Firefox

**Firefox** 是由 Mozilla 开发的开源浏览器，采用自主研发的 **Gecko 引擎**，强调隐私保护与网络中立性。它默认拦截追踪器，支持丰富扩展（如 uBlock Origin），并提供独立于 Chromium 生态的替代选择。Firefox 以透明数据政策、跨平台同步及高效内存管理著称，适合注重安全和自由的用户。其移动版（Android）同样基于 Gecko，而 iOS 版因苹果限制改用 WebKit。


```bash
flatpak install -y flathub org.mozilla.firefox
```

### Waterfox

**Waterfox** 是一款基于 Firefox 开源代码的高性能浏览器，专注于速度、隐私和自定义体验。它保留了经典的 Firefox 扩展兼容性（如 XUL 插件），同时优化了 64 位系统性能，适合技术爱好者和老用户。Waterfox 默认减少数据收集，支持用户自主控制隐私设置，并提供独立的 G5 分支（基于新版 Firefox）和 Classic 分支（延续旧版特性）。适用于追求轻量化且重视扩展自由度的用户群体。

```bash
flatpak install  -y flathub net.waterfox.waterfox
```

### LibreWolf

**LibreWolf** 是一款基于 Firefox 的隐私强化型开源浏览器，专为抵制在线追踪和数据收集而设计。它移除了 Firefox 的遥测、数据收集和商业绑定功能，并预装 **uBlock Origin** 等隐私扩展，强制启用 **HTTPS-Only 模式** 和 **严格追踪保护**。通过独立更新维护，提供更快的安全补丁，支持 Linux、Windows 和 macOS。适合技术用户和隐私至上主义者，是 Firefox 的“去谷歌化”替代品，强调透明性与用户自主权。

```bash
flatpak install flathub io.gitlab.librewolf-community
```

## Chromium 内核浏览器 


###  Chromium

**Chromium** 是 Google 主导开发的开源浏览器项目，作为 **Chrome** 和其他主流浏览器（如 Edge、Opera、Brave）的技术基础。它采用 **Blink 渲染引擎** 和 **V8 JavaScript 引擎**，提供高速网页加载和强大的性能。相比 Chrome，Chromium 移除了 Google 专有服务（如自动更新、DRM），更透明且可定制，适合开发者或隐私优先用户。支持跨平台（Windows/macOS/Linux），是浏览器生态的核心驱动之一。

```
flatpak install -y flathub org.chromium.Chromium
```


###  Google Chrome

**Google Chrome** 是由 Google 开发的一款主流网页浏览器，采用 Chromium 开源内核，以快速、简洁和稳定著称。它支持多平台同步（书签/历史/扩展）、丰富的扩展生态（Chrome 网上应用店）、沙盒安全机制及内置翻译等功能，同时集成 Google 搜索和服务。尽管因资源占用较高和隐私数据收集策略存在争议，其兼容性和性能仍使其成为全球使用最广泛的浏览器之一。

```bash
flatpak install flathub com.google.Chrome
```


### Brave

> **Brave 浏览器** 是一款基于 Chromium 的开源浏览器，主打隐私保护与高效浏览体验。它默认屏蔽广告、追踪器和恶意软件，显著提升页面加载速度并减少数据消耗。其特色功能包括内置的隐私保护工具（如 Tor 私密标签页）、加密货币奖励系统（通过 Brave Rewards 支持内容创作者）以及低资源占用设计。支持 Chrome 扩展，适用于桌面和移动端，适合注重安全性和性能的用户。

```bash
flatpak install  -y flathub com.brave.Browser
```




###  Opera

**Opera** 是一款注重效率与创新的跨平台浏览器，以轻量化设计和内置实用工具著称。其特色功能包括：原生集成免费 **VPN**（流量加密）、**广告拦截器**、**快照工具**（页面截图标注）、**Workspaces**（多工作区管理）以及 **AI 助手 Aria**（智能搜索与问答）。采用 Chromium 内核保障兼容性，同时通过 **Flow** 实现设备间文件/笔记即时同步，并支持 **加密货币钱包**。兼顾低资源占用与流畅体验，适合追求生产力提升和隐私保护的用户。

```bash
flatpak install flathub com.opera.Opera
```

