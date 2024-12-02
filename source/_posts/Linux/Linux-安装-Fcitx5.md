---
title: Linux 安装 Fcitx5
date: 2024-11-30 16:29:40
tags:
	- Linux
	- Fcitx5
---

释放您的输入潜力，尽在 Fcitx5！作为 Linux 用户的必备输入法框架，Fcitx5 提供多种语言支持与灵活定制，让每一次输入都流畅无阻。无论是拼音、五笔还是其他输入法，Fcitx5 都能完美满足您的需求。现代化的界面和强大的插件生态，让您的工作与娱乐更高效。选择 Fcitx5，体验无与伦比的输入乐趣，提升您的数字生活品质！立即下载，开启高效输入新体验！

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


## Ubuntu

适用于 **Ubuntu 2204** 、**Ubuntu 2404**、**Pop!_OS 2204**、**Zorin OS 17** 等

1. 安装输入法

```bash
sudo apt install fcitx5 fcitx5-module-cloudpinyin fcitx5-chinese-addons -y
```

2. 使用 **Startup Applications** 将 **fcitx5** 添加到开机自启动
3. 使用命令 **fcitx5** 启动输入法
4. 使用命令  **fcitx5-config-qt** 启动fcitx5配置， 将 **Pinyin** 添加到输入法分组
5. 重启系统生效


##  Fedora

适用于 **Fedora 40** 等

1. 安装输入法

```bash
sudo dnf install fcitx5  fcitx5-chinese-addons fcitx5-configtool -y
```

2. 使用 **Gnome Tweaks** 将 **fcitx5** 添加到开机自启动
3. 使用命令 **fcitx5** 启动输入法
4. 使用命令  **fcitx5-config-qt** 启动fcitx5配置， 将 **Pinyin** 添加到输入法分组
5. 重启系统生效

##  优化

安装 Gnome 扩展 **Input Method Panel** 优化输入法主题

## 优化

安装 Gnome 扩展 [Input Method Panel - GNOME Shell Extensions](https://extensions.gnome.org/extension/261/kimpanel/)优化输入法外观

下载 词库 [自建拼音输入法词库，百万常用词汇量](https://github.com/wuhgit/CustomPinyinDictionary)， 优化输入效果


词库下载地址 https://maicss.lanzoui.com/iErOirt790h

```bash
mkdir -p  ~/.local/share/fcitx5/pinyin/dictionaries/
cp zhwiki-20210722.dict ~/.local/share/fcitx5/pinyin/dictionaries/
```