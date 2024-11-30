---
title: Linux 安装 Fcitx5
date: 2024-11-30 16:29:40
tags:
	- Linux
	- Fcitx5
---

Linux 安装 Fcitx5

<!-- more -->

## Manjaro24

### 安装 Fcitx5

```bash
sudo pacman -Sy fictx5 fcitx5-chinese-addons fcitx5-configtool
```

### 配置 Fcitx5

使用软件 **Tweaks** ， 将 Fcitx5 添加到开机自启动软件列表

启动 Fcitx5 输入法

启动 Fcitx5 Configuration ,将 **Pinyin** 输入法添加到默认分组

创建环境变量文件

```bash
sudo vim /etc/profile.d/my-fcitx5.sh
```

环境变量文件内容如下

```
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
INPUT_METHOD=fcitx
SDL_IM_MODULE=fcitx
GLFW_IM_MODULE=ibus
```

重启系统生效

## 优化

安装 Gnome 扩展 [Input Method Panel - GNOME Shell Extensions](https://extensions.gnome.org/extension/261/kimpanel/)优化输入法外观

下载 词库 [自建拼音输入法词库，百万常用词汇量](https://github.com/wuhgit/CustomPinyinDictionary)， 优化输入效果