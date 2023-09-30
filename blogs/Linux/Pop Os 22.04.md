---
title: Pop OS 配置
date: 2023/09/29
tags:
 - PopOS22.04
categories:
 - Linux
---

# Pop OS 配置

## Firefox 常用扩展



## 使用镜像

备份配置文件

```
cp /etc/apt/sources.list.d/system.sources ~/system.sources.bk
```

修改配置文件

```
sudo nano /etc/apt/sources.list.d/system.sources
```

修改前

```
X-Repolib-Name: Pop_OS System Sources
Enabled: yes
Types: deb deb-src
URIs: http://apt.pop-os.org/ubuntu
Suites: jammy jammy-security jammy-updates jammy-backports
Components: main restricted universe multiverse
X-Repolib-ID: system
X-Repolib-Default-Mirror: http://apt.pop-os.org/ubuntu
```

修改后

```
X-Repolib-Name: Pop_OS System Sources
Enabled: yes
Types: deb deb-src
URIs: http://repo.huaweicloud.com/ubuntu
Suites: jammy jammy-security jammy-updates jammy-backports
Components: main restricted universe multiverse
X-Repolib-ID: system
X-Repolib-Default-Mirror: http://repo.huaweicloud.com/ubuntu
```

## 更新、升级

更新软件仓库

```
sudo apt update -y
```

升级软件

更新软件仓库

```
sudo apt upgrade -y
```

## 安装基础软件

```
sudo apt install wget curl zsh vim -y
```

## 输入法 fcitx5

### 安装

安装输入法

```bash
sudo apt install fcitx5 fcitx5-module-cloudpinyin -y
```

### 配置输入法

使用命令 `im-config` 设置默认输入法为 fcitx5

修改环境变量，配置输入法

```
sudo vim /etc/environment
```

在文件末尾追加

```
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
INPUT_METHOD=fcitx
SDL_IM_MODULE=fcitx
GLFW_IM_MODULE=ibus
```

使用软件 `启动应用程序` 将 fcitx5 添加到开机子启动

配置如下

名称 `fcitx5`
命令 `/usr/bin/fcitx5`
注释 `fcitx5`

### 主题配置

主题下载地址 [https://maicss.lanzoui.com/iScGart77xi](https://maicss.lanzoui.com/iScGart77xi)

```
unzip fcitx5-simple-themes.zip 

mv Simple-dark ~/.local/share/fcitx5/themes
mv Simple-white ~/.local/share/fcitx5/themes
```

### 词库配置

词库下载地址 [https://maicss.lanzoui.com/iErOirt790h](https://maicss.lanzoui.com/iErOirt790h)

```
mkdir -p  ~/.local/share/fcitx5/pinyin/dictionaries/
cp zhwiki-20210722.dict ~/.local/share/fcitx5/pinyin/dictionaries/
```

### 重启系统

重启系统后，输入法配置生效

重启之后：

1. 选择输入法主题
2. 配置 云输入法
3. 配置字体大小

## Google Chrome

Google Chrome 国内官网 [https://www.google.cn/chrome/index.html](https://www.google.cn/chrome/index.html)

```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

```
sudo dpkg -i google-chrome-stable_current_amd64.deb
```



## Flatpak

安装 Flatpak

```
sudo apt install flatpak
```
Flatpak 仓库配置

- 官方仓库 https://flathub.org/repo/flathub
- 上交大镜像 https://mirror.sjtu.edu.cn/flathub

```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```


```
flatpak remote-modify flathub --url=https://mirror.sjtu.edu.cn/flathub
```

```
wget https://mirror.sjtu.edu.cn/flathub/flathub.gpg

sudo flatpak remote-modify --gpg-import=flathub.gpg flathub 
```

## SublimeText 4152

官网下载地址 [https://download.sublimetext.com/sublime-text_build-4152_amd64.deb](https://download.sublimetext.com/sublime-text_build-4152_amd64.deb)

兰奏云下载地址 [https://wwyx.lanzout.com/idGyy1a6j8di](https://wwyx.lanzout.com/idGyy1a6j8di)

## XDM

官网下载地址 [https://github.com/subhra74/xdm/releases/download/8.0.29/xdman_gtk_8.0.29_amd64.deb](https://github.com/subhra74/xdm/releases/download/8.0.29/xdman_gtk_8.0.29_amd64.deb)

兰奏云下载地址 [https://wwyx.lanzout.com/icJG41a6jdyj](https://wwyx.lanzout.com/icJG41a6jdyj)

## Docker

```
sudo apt install docker.io
```

修复： 解决 sudo 权限问题

```
sudo usermod -aG docker $USER
```

```
newgrp docker
```

配置 Docker 镜像

```
sudo vim /etc/docker/daemon.json
```

内容如下

```json
{
  "registry-mirrors": ["http://f1361db2.m.daocloud.io"]
}
```


## V2rayA

```
docker run -d \
  --restart=always \
  --privileged \
  --network=host \
  --name v2raya \
  -e V2RAYA_ADDRESS=0.0.0.0:2017 \
  -v /lib/modules:/lib/modules:ro \
  -v /etc/resolv.conf:/etc/resolv.conf \
  -v /etc/v2raya:/etc/v2raya \
  mzz2017/v2raya
```

GitHub 免费订阅地址 freefq/free

```
https://bulinkbulink.com/freefq/free/master/v2
```

## OhMyZsh

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## 主题美化


## ToDesk

官网下载地址 [https://www.todesk.com/linux.html](https://www.todesk.com/linux.html)


## JetBrain


ToolBox 官网下载地址 [https://www.todesk.com/linux.html](https://www.todesk.com/linux.html)

最新激活补丁仓库 [https://github.com/libin9iOak/ja-netfilter-all](https://github.com/libin9iOak/ja-netfilter-all)


最新激活补丁下载地址[https://github.com/libin9iOak/ja-netfilter-all/archive/refs/heads/main.zip
](https://github.com/libin9iOak/ja-netfilter-all/archive/refs/heads/main.zip
)

最近激活码获取地址 [https://jetbra.in/5d84466e31722979266057664941a71893322460](https://jetbra.in/5d84466e31722979266057664941a71893322460 )

## 图片


自带图片查看器默认不支持 webp 格式

解决方法：

```
sudo add-apt-repository ppa:helkaluin/webp-pixbuf-loader
sudo apt update
sudo apt install webp-pixbuf-loader
```

## localsend

局域网聊天文件传输

```
cd ~/
axel -n 16 https://download.njuu.cf/localsend/localsend/releases/download/v1.11.1/LocalSend-1.11.1-linux-x86-64.deb
sudo dpkg -i ~/LocalSend-1.10.0-linux-x86-64.deb
```

## 视频播放器

```
sudo apt install vlc mpv -y
```

## node.js

```
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash
```

```
nvm install --lts
```


```
npm 
```

## GitHubDesktop

https://github.com/shiftkey/desktop

```bash
https://github.com/shiftkey/desktop/releases/download/release-3.3.1-linux1/GitHubDesktop-linux-amd64-3.3.1-linux1.deb
```

