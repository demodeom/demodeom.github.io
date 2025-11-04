---
title: Fedora43个人配置
date: 2025-10-02 03:32:03
tags:
    - Linux 
index_img: https://s21.ax1x.com/2025/10/02/pVT1Klq.png
---

Fedora43个人配置

<!-- more -->

# Fedora 个人配置

## 1. 系统配置

### 1.1 DNS

#### 1.1.1 阿里云DNS

推荐案例云公共的DNS https://alidns.com/

IP4

```
223.5.5.5,223.6.6.6
```

IP6

```
2400:3200::1,2400:3200:baba::1
```

#### 1.1.2 为什么要修改DNS

使用以下命令测试

```
ping raw.githubusercontent.com -c3
```

修改前

```
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.009 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.018 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.017 ms

--- raw.githubusercontent.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2053ms
rtt min/avg/max/mdev = 0.009/0.014/0.018/0.004 ms
```

修改后

```
PING raw.githubusercontent.com (185.199.109.133) 56(84) bytes of data.
64 bytes from cdn-185-199-109-133.github.com (185.199.109.133): icmp_seq=1 ttl=128 time=120 ms
64 bytes from cdn-185-199-109-133.github.com (185.199.109.133): icmp_seq=2 ttl=128 time=121 ms
64 bytes from cdn-185-199-109-133.github.com (185.199.109.133): icmp_seq=3 ttl=128 time=121 ms

--- raw.githubusercontent.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 120.394/120.504/120.613/0.089 ms
```

#### 1.1.3 修改DNS(Fedora42)

```

```

### 1.2 镜像

清华大学 Fedora 镜像使用

```
sudo sed -e 's|^metalink=|#metalink=|g' \
    -e 's|^#baseurl=http://download.example/pub/fedora/linux|baseurl=https://mirrors.tuna.tsinghua.edu.cn/fedora|g' \
    -i.bak \
    /etc/yum.repos.d/fedora.repo \
    /etc/yum.repos.d/fedora-updates.repo
```

修改镜像后， 建议升级更新系统，然后重启电脑

```
sudo dnf update
```

### 1.3 基础软件

#### 1.3.1 常用软件

- curl – 命令行 HTTP 请求工具（支持多种协议）。
- wget – 命令行下载工具（支持 HTTP/HTTPS/FTP）。
- zsh – 功能强大的交互式 Shell（支持插件和主题）。
- git – 分布式版本控制系统（代码管理必备）。
- vim – 高效文本编辑器（支持插件和脚本）。
- vlc – 跨平台多媒体播放器（支持多种格式）。
- mpv – 轻量级命令行视频播放器（可定制性强）。
- ffmpeg – 音视频处理工具（转码/剪辑/流媒体）。

```
sudo dnf install -y curl wget zsh git vim
```

#### 1.3.2 终端美化

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

#### 1.3.3 Git 配置

```
# 设置默认分之为 main
git config --global init.defaultBranch main

# 配置用户名
git config --global user.name "demo"

# 配置用户邮箱
git config --global user.email "demodeom@example.com"
```

### 1.4 输入法 Fcitx5

1. 安装 fcitx5

   ```
   sudo dnf install fcitx5 fcitx5-chinese-addons fcitx5-configtool
   ```

1. 使用 **gnome tweaks** 将 fcitx5 添加到 开机自启动 软件列表
2. 启动软件 **Fcitx5**
3. 启动软件 **Fcitx5 Configuration**, 将 **PinYin** 添加到 输入法分组， 点击 **应用** 按钮， 点击 **确定** 按钮
4. 重启系统

中文字体

```
sudo dnf install wqy-microhei-fonts wqy-zenhei-fonts 
```

建议修改文件 **/etc/environment**

```
sudo vim /etc/environment
```

添加以下内容

```
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
INPUT_METHOD=fcitx
SDL_IM_MODULE=fcitx
GLFW_IM_MODULE=ibus
```

### 1.5 软件管理

#### 1.5.1 Flatpak

```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak remote-modify flathub --url=https://mirror.sjtu.edu.cn/flathub
```

#### 1.5.2 Gear Lever

```
flatpak install flathub it.mijorus.gearlever
```

### 1.6 安装完整的 ffmpeg

```bash
# 启用 RPM Fusion 仓库
sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm

# 更新并安装 FFmpeg
sudo dnf update
sudo dnf install ffmpeg ffmpeg-devel --allowerasing
```

**Fedora 默认仓库的 FFmpeg特点：**

- **软件包名**：通常是 `ffmpeg` 或 `ffmpeg-free`
- **编解码器支持**：只包含开源、无专利争议的编解码器
- **限制**：
  - 不支持 H.264、H.265、MP3 等有专利的编解码器
  - 缺少 AAC、MP3 编码支持
  - 没有 NVIDIA CUDA 等硬件加速支持
- **法律合规**：完全符合 Fedora 的严格开源政策

**RPM Fusion 仓库的 FFmpeg 特点：**

- **软件包名**：`ffmpeg`（来自 rpmfusion-free 和 nonfree）
- **编解码器支持**：包含完整编解码器支持
- **优势**：
  - 支持 H.264、H.265/HEVC 编解码
  - 支持 MP3、AAC 音频编解码
  - 包含硬件加速支持（CUDA、VAAPI等）
  - 支持更多视频格式和容器

### 1.7 视频播放器

```bash
sudo dnf install vlc mpv
```



## 2. 代理    

### 2.1 三毛导航

**便宜机场**

- 三毛导航 [https://三毛导航.com](https://三毛导航.com/)



### Flclash



```
sudo dnf install ~/Downloads/FlClash-0.8.90-linux-amd64.rpm
```



### 2.2 Clash Verge Rev

**最新版本下载地址**

- GitHub https://github.com/clash-verge-rev/clash-verge-rev/releases
- GitHub 镜像 bgithub.xyz  https://bgithub.xyz/clash-verge-rev/clash-verge-rev/releases

以 v2.4.2 为例

```
#!/bin/bash

# 定义版本号变量
VERSION="2.4.2"

# 构造下载 URL
URL="https://bgithub.xyz/clash-verge-rev/clash-verge-rev/releases/download/v${VERSION}/Clash.Verge-${VERSION}-1.x86_64.rpm"

# 使用 wget 下载文件
wget ${URL}

# 安装 Clash Verge Rev
sudo dnf install -y  Clash.Verge-${VERSION}-1.x86_64.rpm
```

## 3. Firefox 常用扩展

**常用扩展**

- [划词翻译](https://addons.mozilla.org/zh-CN/firefox/addon/hcfy/)
- [uBlock Origin](https://addons.mozilla.org/zh-CN/firefox/addon/ublock-origin/)
- [Gesturefy](https://addons.mozilla.org/zh-CN/firefox/addon/gesturefy/)
- [LastPass: Free Password Manager](https://addons.mozilla.org/zh-CN/firefox/addon/lastpass-password-manager/)
- [Tampermonkey](https://addons.mozilla.org/zh-CN/firefox/addon/tampermonkey)

**常用 Tampermonkey 脚本**

- [LinkSwift](https://greasyfork.org/zh-CN/scripts/449291-linkswift) ~~作者已删除~~
- [知乎美化](https://greasyfork.org/en/scripts/412212-知乎美化)
- [Github 增强](https://greasyfork.org/zh-CN/scripts/412245-github-增强-高速下载)
- [CSDN 人性化脚本优化](https://greasyfork.org/zh-CN/scripts/378351-持续更新-csdn广告完全过滤-人性化脚本优化-不用再登录了-让你体验令人惊喜的崭新csdn)

## 4. Gnome

### gnome tweaks

```
sudo dnf install gnome-tweaks
```

### ExtensionManager

```
flatpak install -y flathub com.mattjakeman.ExtensionManager
```

**个人常用扩展**

- **AppIndicator and KStatusNotifierItem Support** 任务栏软件小图标支持
- **Dash to Panel** dash 面板
- **Input Method Panel** 输入法主题优化
- **User Themes** 用户主题

## 开发软件

### Typora

```
flatpak install flathub io.typora.Typora
```

### Scrcpy(安卓投屏)

GitHub 地址 https://github.com/Genymobile/scrcpy

GitHub 镜像地址 https://bgithub.xyz/Genymobile/scrcpy

```bash
# 定义版本号
SCRCPY_VERSION="v3.3.3"

cd ~/Downloads

# 下载 scrcpy
wget "https://gh-proxy.com/https://github.com/Genymobile/scrcpy/releases/download/${SCRCPY_VERSION}/scrcpy-linux-x86_64-${SCRCPY_VERSION}.tar.gz"

# 解压并删除安装包
tar -xvf "scrcpy-linux-x86_64-${SCRCPY_VERSION}.tar.gz" && rm "scrcpy-linux-x86_64-${SCRCPY_VERSION}.tar.gz"

# 将软件安装到 /opt 目录
mv "scrcpy-linux-x86_64-${SCRCPY_VERSION}" $HOME/DevTools/scrcpy

# 修改图标文件权限
sudo chmod 644 $HOME/DevTools/scrcpy/icon.png

# 创建快捷方式
DESKTOP_FILE="$HOME/.local/share/applications/scrcpy.desktop"
echo "[Desktop Entry]" > "$DESKTOP_FILE"
echo "Version=1.0" >> "$DESKTOP_FILE"
echo "Type=Application" >> "$DESKTOP_FILE"
echo "Name=Scrcpy" >> "$DESKTOP_FILE"
echo "Comment=Android screen mirroring" >> "$DESKTOP_FILE"
echo "Exec=$HOME/DevTools/scrcpy/scrcpy" >> "$DESKTOP_FILE"
echo "Icon=$HOME/DevTools/scrcpy/icon.png" >> "$DESKTOP_FILE"
echo "Terminal=false" >> "$DESKTOP_FILE"
echo "Categories=Utility;" >> "$DESKTOP_FILE"
```

## 开发环境

### Android Studio

#### 环境变量配置

```
echo 'export PATH=$PATH:$HOME/Android/Sdk/platform-tools' >> ~/.zshrc
```

## 下载工具

### Motrix

```
flatpak install flathub net.agalwood.Motrix
```

### qBittorrent

```
flatpak install flathub org.qbittorrent.qBittorrent
```

### XDM

Xtreme Download Manager https://github.com/subhra74/xdm/releases

```
https://github.com/subhra74/xdm/releases/download/8.0.29/xdman_gtk-8.0.29-1.fc36.x86_64.rpm
https://ghproxy.cn/https://github.com/subhra74/xdm/releases/download/8.0.29/xdman_gtk-8.0.29-1.fc36.x86_64.rpm
```

## 文本编辑器

### Sublime Text 4

[Sublime Text 4 官网安装文档](https://www.sublimetext.com/docs/linux_repositories.html#dnf)

```bash
# Install the GPG key: 
sudo rpm -v --import https://download.sublimetext.com/sublimehq-rpm-pub.gpg

# Select the stable channel to use
sudo dnf config-manager addrepo --from-repofile=https://download.sublimetext.com/rpm/stable/x86_64/sublime-text.repo

# Update dnf and install Sublime Text
sudo dnf install sublime-text
```



```bash
wget https://download.sublimetext.com/sublime-text-4180-1.x86_64.rpm
sudo rpm -i sublime-text-4180-1.x86_64.rpm

```

Sublime Text 4 个人配置

```json
{
   "font_size": 20,
   "save_on_focus_lost": true,
   "theme": "Default Dark.sublime-theme",
   "color_scheme": "Mariana.sublime-color-scheme",
}
```

Sublime Text 4 个人扩展

### Typora

```
flatpak install flathub io.typora.Typora
```

## 开发工具

### Sublime Merge-Git可视化工具

```
flatpak install flathub com.sublimemerge.App
```

### Docker-容器

安装 docker

```
sudo dnf install docker -y
```

开机自启动 docker

```
sudo systemctl enable docker.service 
```

启动 docker

```
sudo systemctl start docker.service 
```

解决 sudo 权限问题（重新登录用户生效）

```
sudo usermod -aG docker $USER
```

[Docker/DockerHub 国内镜像源/加速列表-长期维护](https://xuanyuan.me/blog/archives/1154)

```
# 创建配置文件目录
sudo mkdir -p /etc/docker
# 创建配置文件
sudo tee /etc/docker/daemon.json <<EOF
{
    "registry-mirrors": [
        "https://dockerproxy.cn",
        "https://docker.rainbond.cc",
        "https://docker.udayun.com",
        "https://docker.211678.top"
    ]
}
EOF
# 重启服务
sudo systemctl daemon-reload
sudo systemctl restart docker
```

### Selenium-浏览器自动化测试

Firefox Driver https://github.com/mozilla/geckodriver/releases

```
wget https://cors.isteed.cc/github.com/mozilla/geckodriver/releases/download/v0.35.0/geckodriver-v0.35.0-linux64.tar.gz
tar -xvf geckodriver-v0.35.0-linux64.tar.gz
sudo mv geckodriver /usr/local/bin
```

### Nvm-Node Version Manager

Node Version Manager https://github.com/nvm-sh/nvm

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
source ~/.zshrc
nvm install --lts
npm install nrm  -g --registry=https://registry.npmmirror.com
```

### Pyenv-Python多版本管理

**Simple Python Version Management** https://github.com/pyenv/pyenv

- 安装 Pyenv

```
curl https://pyenv.run | bash
```

- 安装依赖: Fedora 22 and above: https://github.com/pyenv/pyenv/wiki#suggested-build-environment

```
sudo dnf install make gcc patch zlib-devel bzip2 bzip2-devel readline-devel sqlite sqlite-devel openssl-devel tk-devel libffi-devel xz-devel libuuid-devel gdbm-libs libnsl2
```

- 追加以下内容到 **~/.zshrc** 文件末尾

```
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
```

- 临时生效系统环境变量

```
source ~/.zshrc
```

- 下载 Python 源码

```
mkdir ~/.pyenv/cache
cd ~/.pyenv/cache
wget https://mirrors.huaweicloud.com/python/3.10.14/Python-3.10.14.tar.xz
```

- 安装 3.10.14

```
pyenv install 3.10.14
```

- 设置默认Python版本

```
pyenv global 3.10.14
```

- 镜像配置

```
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
pip config set install.trusted-host pypi.tuna.tsinghua.edu.cn
```

## 虚拟机

### Virtual Box

下载地址 https://www.virtualbox.org/wiki/Linux_Downloads

```
sudo rpm -i ~/Downloads/VirtualBox-7.1-7.1.4_165100_fedora40-1.x86_64.rpm
```

可能需要以下依赖

```
sudo dnf install gtk2 kernel-devel
```

可能需要将当前用户添加到 vboxusers 分组

```
sudo usermod -aG vboxusers $USER
```

### 火狐浏览器

使用 **软件商店** 、Flatpak、DNF 等工具安装的 Firefox 浏览器， 可能会存在某些问题， 建议使用 Firefox 提供的二进制文件进行安装

下载地址 https://www.firefox.com.cn/download/#product-desktop-release

```
https://download.mozilla.org/?product=firefox-latest-ssl&os=linux64&lang=en-US
cd ~/Downloadstar xjf firefox-*.tar.bz2sudo mv firefox /optsudo ln -s /opt/firefox/firefox /usr/local/bin/firefoxsudo wget https://raw.githubusercontent.com/mozilla/sumo-kb/main/install-firefox-linux/firefox.desktop -P /usr/local/share/applications
```