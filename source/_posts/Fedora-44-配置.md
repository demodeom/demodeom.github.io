---
title: Fedora 44 配置
date: 2026-05-10 22:35:12
tags:
	- Fedora44
---

Fedora 44 

<!-- more -->

# Fedora 44 配置

## 前言

### GitHub 镜像

**推荐两个镜像**

- [https://github.akams.cn/](https://github.akams.cn/)

- [https://gh-proxy.com/](https://gh-proxy.com/)

### 搜索引擎

**推荐三个**

1. [微软搜索](https://cn.bing.com)
2. [Yandex](https://yandex.com/)
3. [百度](https://www.baidu.com/)



```bash
# 微软搜索
https://www.bing.com/search?q=搜索关键字

# Yandex
https://yandex.com/search/?text=搜索关键字

# 百度
https://www.baidu.com/s?wd=搜索关键字
```

### 代理

推荐两个软件 **FlClash**、**Clash Verge Rev**

#### Clash Verge Rev(首推)

Clash Verge Rev 可以完全兼容 Fedora 44（2026-05-02）

[GitHub 仓库地址 clash-verge-rev/clash-verge-rev](https://github.com/Clash-Verge-rev/clash-verge-rev/releases)

[GitHub Release Page](https://github.com/Clash-Verge-rev/clash-verge-rev/releases)

```bash
# 2026-05-02
https://github.com/clash-verge-rev/clash-verge-rev/releases/download/v2.4.7/Clash.Verge-2.4.7-1.x86_64.rpm
```



#### FlClash

FlClash 尚未兼容 Fedora 44（2026-05-02）

[GitHub 仓库地址 chen08209/FlClash](https://github.com/chen08209/FlClash)

[GitHub Release Page](https://github.com/chen08209/FlClash/releases)

```

```

#### 代理服务商

**推荐一个**

- [三毛导航](https://三毛导航.com/)

## 镜像

### 清华大学镜像

[清华大学开源软件镜像站 Fedora](https://mirrors.tuna.tsinghua.edu.cn/help/fedora/)

Fedora 44 清华大学镜像好像没有更新成功（2026-05-02），暂时用阿里云的

### 阿里云

[阿里云 Fedora 镜像](https://developer.aliyun.com/mirror/fedora)

```bash
# 备份
sudo mv /etc/yum.repos.d/fedora.repo /etc/yum.repos.d/fedora.repo.backup
sudo mv /etc/yum.repos.d/fedora-updates.repo /etc/yum.repos.d/fedora-updates.repo.backup

# 下载新配置
sudo wget -O /etc/yum.repos.d/fedora.repo http://mirrors.aliyun.com/repo/fedora.repo
sudo wget -O /etc/yum.repos.d/fedora-updates.repo http://mirrors.aliyun.com/repo/fedora-updates.repo
```

## 基础软件

### 更新系统

```bash
sudo dnf update
```

### 常用软件

| 软件   | 功能说明               | 主要用途                                |
| ------ | ---------------------- | --------------------------------------- |
| `curl` | 命令行 HTTP 请求工具   | API 调试、文件传输、支持多种网络协议    |
| `wget` | 命令行下载工具         | 递归下载、断点续传、支持 HTTP/HTTPS/FTP |
| `zsh`  | 功能强大的交互式 Shell | 支持插件系统、主题定制、智能补全        |
| `git`  | 分布式版本控制系统     | 代码管理、协作开发、版本追踪            |
| `vim`  | 高效文本编辑器         | 代码编辑、配置文件修改、支持插件扩展    |

```bash
sudo dnf install -y curl wget zsh git vim
```

### Git 版本控制配置

完成 Git 安装后，建议进行以下全局配置

| 配置项               | 作用             | 推荐值                   |
| -------------------- | ---------------- | ------------------------ |
| `init.defaultBranch` | 新仓库默认分支名 | main（现代标准）         |
| `user.name`          | 提交者名称       | 您的实际姓名或昵称       |
| `user.email`         | 提交者邮箱       | 与代码托管平台一致的邮箱 |
| `core.quotepath`     | 路径显示编码     | false（显示原始字符）    |

```bash
# 设置默认分支名称（新仓库默认使用 main 分支）
git config --global init.defaultBranch main

# 配置用户身份（提交记录中显示的作者信息）
git config --global user.name "您的用户名"
git config --global user.email "您的邮箱@example.com"

# 解决中文文件名显示问题
# 禁止对非ASCII字符进行转义，直接显示原始中文
git config --global core.quotepath false
```

### Oh My Zsh 

从 GitHub 安装 

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

从 GitHub 加速代理安装

```bash
sh -c "$(curl -fsSL https://gh-proxy.org/https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Fcitx5 输入法

#### 1. 安装核心组件﻿

使用 DNF 包管理器安装 Fcitx5 及其相关组件：

```bash
sudo dnf install fcitx5 fcitx5-chinese-addons fcitx5-configtool
```



各组件说明：

- fcitx5 ：输入法框架核心程序
- fcitx5-chinese-addons ：中文输入法插件包（包含拼音、五笔等输入引擎）
- fcitx5-configtool ：图形化配置工具

#### 2. 设置开机自启动﻿

为确保输入法在系统启动后自动运行，需要通过 GNOME Tweaks 工具配置开机自启：

```bash
# 如未安装 GNOME Tweaks，需先安装
sudo dnf install gnome-tweaks
```



**安装完成后：**

1. 打开 GNOME Tweaks （优化工具）
2. 导航至 开机启动程序 （Startup Applications）选项卡
3. 点击 添加 （Add）
4. 在命令栏输入 `fcitx5` ，添加名称后保存

#### 3. 首次启动与配置﻿

```bash
# 手动启动 Fcitx5 输入法框架
fcitx5

# 打开 Fcitx5 配置界面
fcitx5-configtool
```

**在配置界面中：**

1. 在 输入法 （Input Method）选项卡下，点击 添加输入法 （Add Input Method）
2. 搜索并选择 Pinyin （拼音）输入法
3. 点击 应用 （Apply）保存配置，随后点击 确定 （OK）



> 注意 ：部分应用程序需要重启系统后才能正常调用 Fcitx5 输入法。

#### 4. 解决应用程序输入法兼容性问题﻿

如果某些应用程序无法正常使用 Fcitx5 输入法，需要通过设置环境变量来解决。编辑系统环境变量配置文件：

```bash
sudo vim /etc/environment
```

在文件末尾追加以下配置：

```bash
# GTK 程序输入法支持
GTK_IM_MODULE=fcitx      # GNOME/GTK 应用（如 Gedit、Evince）
QT_IM_MODULE=fcitx       # KDE/Qt 应用（如 WPS、VLC）

# X11 传统程序支持
XMODIFIERS=@im=fcitx     # 兼容 XIM 协议的老旧应用

# 多媒体及游戏框架支持
SDL_IM_MODULE=fcitx      # SDL2 应用（游戏、模拟器）
GLFW_IM_MODULE=fcitx     # GLFW 框架应用

# 其他图形库支持
CLUTTER_IM_MODULE=fcitx  # Clutter 图形库应用
```

配置完成后，需注销并重新登录使环境变量生效。



### Gnome Desktop

#### Gnome Tweaks

```bash
sudo dnf install gnome-tweaks
```

### Gnome Extension Manager

**个人常用扩展详解﻿**

1. AppIndicator and KStatusNotifierItem Support﻿ 任务栏小图标支持

2. Dash to Panel﻿ 将 GNOME 的应用程序启动器（Dash）合并到顶部面板

3. Input Method Panel﻿ 改善 Fcitx5 输入法框架的视觉体验

4. User Themes﻿ 允许用户加载自定义 Shell 主题

5. Bilingual App Search﻿ 增强 GNOME 应用搜索功能，解决中文环境下英文应用名搜索不到的问题



### 软件管理

#### dnf



#### Flatpak

安装 Flatpak

```bash
sudo dnf install flatpak
```

配置 Flatpak 仓库

```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

#### Gear Lever

管理 **AppImage** 格式的软件



## 文本编辑器



### Sublime Text 4 

```bash
sudo rpm -v --import https://download.sublimetext.com/sublimehq-rpm-pub.gpg

sudo dnf config-manager addrepo --from-repofile=https://download.sublimetext.com/rpm/stable/x86_64/sublime-text.repo

sudo dnf install sublime-text
```



### Typora

```bash
flatpak install flathub io.typora.Typora
```



## 编辑器（JetBrain）

推荐 JetBrain 全家桶

### JetBrains Toolbox App

推荐使用 **JetBrains Toolbox App** 安装、管理 编辑器，支持常见的Linux发行版，比如 Fedora、Ubuntu、Arch 等。

[JetBrains Toolbox App 下载地址](https://www.jetbrains.com/toolbox-app/)





### 3.jetbra.in

JetBrain 全家桶激活码免费体验获取途径 [https://3.jetbra.in/](https://3.jetbra.in/)



### 安装命令

```bash
cd ~/Downloads

tar -xvf jetbrains-toolbox-3.4.3.81140.tar.gz
mv jetbrains-toolbox* ~/DevTools/jetbrains-toolbox

cp ~/DevTools/jetbrains-toolbox/bin/jetbrains-toolbox ~/.local/share/applications

unzip jetbra-*.zip(N)
mv jetbra ~/DevTools
```



### 中文乱码

最近发现出现中文乱码问题，解决方法：安装中文字体

```bash
sudo dnf install google-noto-cjk-fonts wqy-zenhei-fonts
```



### 环境变量

```bash
# JetBrains Toolbox App
echo '# JetBrains Toolbox App' >> ~/.zshrc
echo 'export PATH=$PATH:$HOME/DevTools/jetbrains-toolbox/bin' >> ~/.zshrc

# Android Studio
echo '# Android Studio' >> ~/.zshrc
echo 'export PATH=$PATH:$HOME/Android/Sdk/platform-tools' >> ~/.zshrc
```

## 开发环境

### Node.js

[GitHub nvm-sh/nvm](https://github.com/nvm-sh/nvm)



```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.4/install.sh | bash
```



```bash
source ~/.zshrc

nvm install --lts

npm install nrm -g
```



### Pyenv

[GitHub pyenv/pyenv](https://github.com/pyenv/pyenv)

[suggested build environment](https://github.com/pyenv/pyenv/wiki#suggested-build-environment)

Fedora 22 and above:

```bash
sudo dnf install make gcc patch zlib-devel bzip2 bzip2-devel readline-devel sqlite sqlite-devel openssl-devel tk-devel libffi-devel xz-devel libuuid-devel gdbm-libs libnsl2
```

下载、安装 pyenv

```bash
curl -fsSL https://pyenv.run | bash
```

环境变量配置

```bash
# Pyenv 
echo '# Pyenv' >> ~/.zshrc
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init - zsh)"' >> ~/.zshrc
```

安装 Python（不建议安装最新版本，建议小一个版本）

```bash
source  ~/.zshrc

pyenv install 3.13
```

### Java(JDK)

[Tuna Mirror Adoptium](https://mirrors.tuna.tsinghua.edu.cn/Adoptium/)

```bash
cd ~/Downloads

tar -xvf OpenJDK8U-jdk_x64_linux_hotspot_*.tar.gz(N)

mv jdk8u* ~/DevTools/jdk8

# jdk 
echo '# java' >> ~/.zshrc
echo 'export PATH=$PATH:$HOME/DevTools/jdk8/bin' >> ~/.zshrc

source ~/.zshrc
```



