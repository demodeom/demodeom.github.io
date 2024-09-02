---
title: Fodora 40 个人使用配置
date: 2024-09-03 06:09:49
tags:
---

Fedora（发音：英 [fɪ'dɔːrə]，美 [fɪ'dɔrə]）是一个由Fedora项目社区开发、红帽公司赞助的开源操作系统，也被称为Fedora Linux.

随着版本的更新，Fedora不断引入新技术和桌面环境。Fedora 40版本则更新了GNOME桌面至46版，并首次自带PyTorch。

<!-- more -->

## 系统配置

### 系统镜像

清华大学 Fedora 镜像文档地址 [https://mirrors.tuna.tsinghua.edu.cn/help/fedora/](https://mirrors.tuna.tsinghua.edu.cn/help/fedora/)

 Fedora 40

```bash
sudo sed -e 's|^metalink=|#metalink=|g' \
    -e 's|^#baseurl=http://download.example/pub/fedora/linux|baseurl=https://mirrors.tuna.tsinghua.edu.cn/fedora|g' \
    -i.bak \
    /etc/yum.repos.d/fedora.repo \
    /etc/yum.repos.d/fedora-modular.repo \
    /etc/yum.repos.d/fedora-updates.repo \
    /etc/yum.repos.d/fedora-updates-modular.repo
```

更新缓存

```bash
sudo dnf makecache
```

更新系统

```bash
sudo dnf update
```

系统更新升级之后， 建议重启系统

### DNS

推荐 阿里云 DNS

 阿里云 DNS IP4

```
223.5.5.5,223.6.6.6
```

 阿里云 DNS IP6

```
2400:3200::1,2400:3200:baba::1
```

DNS 修改前

```

```

DNS 修改后

```
➜  ~ ping raw.githubusercontent.com -c3
PING raw.githubusercontent.com (2606:50c0:8003::154) 56 字节的数据
64 字节，来自 2606:50c0:8003::154: icmp_seq=1 ttl=52 时间=144 毫秒
64 字节，来自 2606:50c0:8003::154: icmp_seq=2 ttl=52 时间=145 毫秒
64 字节，来自 2606:50c0:8003::154: icmp_seq=3 ttl=52 时间=165 毫秒

--- raw.githubusercontent.com ping 统计 ---
已发送 3 个包， 已接收 3 个包, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 143.506/151.331/165.299/9.900 ms
```

### 系统更新

系统镜像可能不是最新版，第一次安装完系统后，建议进行更新，

```bash
sudo dnf update
```

### 必备软件

```bash
sudo dnf install git curl wget zsh vim
```

### 终端美化、优化

oh my zsh 是一款不错的插件

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```



## 软件管理

### Flatpak

Flatpak 配置 上海交通大学 镜像

```bash
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak remote-modify flathub --url=https://mirror.sjtu.edu.cn/flathub
```



### AppImage Launcher



```bash
## 下载 AppImageLauncher
wget https://mirror.ghproxy.com/https://github.com/TheAssassin/AppImageLauncher/releases/download/v2.2.0/appimagelauncher-2.2.0-travis995.0f91801.x86_64.rpm

#安装 AppImageLauncher
sudo dnf install ./appimagelauncher-2.2.0-travis995.0f91801.x86_64.rpm
```



### Docker

Docker 官方安装文档 [https://docs.docker.com/engine/install/fedora/#install-using-the-repository](https://docs.docker.com/engine/install/fedora/#install-using-the-repository)

```bash
sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo

sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### WebAppManager



```bash
flatpak install flathub net.codelogistics.webapps
```



## Clash

作为码农，没有代理是痛苦的

百度三天可能无法搜索到的解决方法；Google + 英文 可能一分钟就找到了

Clash 只是一个跨平台的客户端代理软件，支持多种协议，代理服务器仍需自己搭建或者购买

GitHub 搜索关键字 free ，可以找到免费的代理服务，但是免费是有代价的

代理仅可可用于学习，请勿用于其他用途

Clash GitHub 下载地址 [https://github.com/clash-verge-rev/clash-verge-rev/releases](https://github.com/clash-verge-rev/clash-verge-rev/releases)

```bash
# 下载 clash
wget https://cors.isteed.cc/github.com/clash-verge-rev/clash-verge-rev/releases/download/v1.7.7/clash-verge-1.7.7-1.x86_64.rpm
# 安装 clash
sudo dnf install clash-verge-1.7.7-1.x86_64.rpm
```

推荐代理服务商

​	- 三毛导航 [https://三毛导航.com/](https://三毛导航.com/) ， 很便宜， 所以叫做 三毛

## 文本、代码编辑器

### Sublime Text 4

```bash
sudo rpm -v --import https://download.sublimetext.com/sublimehq-rpm-pub.gpg

sudo dnf config-manager --add-repo https://download.sublimetext.com/rpm/stable/x86_64/sublime-text.repo

sudo dnf install sublime-text
```

### Visual Studio Code

```bash
flatpak install flathub com.visualstudio.code
```

### Typora

```bash
flatpak install flathub io.typora.Typora
```

## 输入法 Fcitx5

安装输入法 Fcitx5

```bash
sudo dnf install fcitx5 fcitx5-chinese-addons
```

将 Fcitx5 添加到开机自启动

修改全局环境配置文件 /etc/environment

```bash
sudo vim /etc/environment
```

在文件 /etc/environment 末尾追加以下内容

```
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
INPUT_METHOD=fcitx
SDL_IM_MODULE=fcitx
GLFW_IM_MODULE=ibus
```

使用 **扩展管理** 程序安装扩展  **Input Method Panel** 优化输入法

重启系统生效
