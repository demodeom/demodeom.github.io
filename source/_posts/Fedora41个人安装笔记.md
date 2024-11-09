---
title: Fedora41个人安装笔记
date: 2024-11-09 15:31:41
tags:
	- Linux
	- Fedora
---

Fedora41个人安装笔记

<!-- more -->

## 系统必备

### DNS

阿里云公共的DNS

IP4

```
223.5.5.5,223.6.6.6
```

IP6

```
2400:3200::1,2400:3200:baba::1
```

### 镜像

### 常用软件

常用软件

```bash
sudo dnf install zsh git curl wget vim axel -y
```

Git 配置

```bash
# 配置默认分支名为 main
git config --global init.defaultBranch main
# 配置用户名
git config --global user.name "demo"
# 配置用户邮箱
git config --global user.email "demodeom@example.com"
```

### Oh My Zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### 软件管理

#### Flatpak

```bash
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak remote-modify flathub --url=https://mirror.sjtu.edu.cn/flathub
```

#### Gear Lever

```bash
flatpak install flathub it.mijorus.gearlever
```

## 

### Fcitx5

1. 安装输入法

```bash
sudo dnf install fcitx5  fcitx5-chinese-addons fcitx5-configtool -y
```

1. 使用 **Gnome Tweaks** 将 **fcitx5** 添加到开机自启动
2. 使用命令 **fcitx5** 启动输入法
3. 使用命令  **fcitx5-config-qt** 启动fcitx5配置， 将 **Pinyin** 添加到输入法分组
4. 重启系统生效

安装 Gnome 扩展 **Input Method Panel** 优化输入法主题

建议修改文件 **/etc/environment**

```bash
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

### Clash

Clash GitHub 下载地址 [https://github.com/clash-verge-rev/clash-verge-rev/releases](https://github.com/clash-verge-rev/clash-verge-rev/releases)

```bash
# 下载 clash
wget https://ghproxy.cn/https://github.com/clash-verge-rev/clash-verge-rev/releases/download/alpha/Clash.Verge-2.0.0-rc.5-1.x86_64.rpm
# 安装 clash
sudo rpm -i Clash.Verge-2.0.0-rc.5-1.x86_64.rpm
```

Fedora 41 可能需要以下依赖

```bash
sudo dnf install openssl libayatana-appindicator-gtk3 -y
```

三毛导航 [https://三毛导航.com](https://三毛导航.com/)

### Gnome 桌面

#### Gnome Tweaks

```bash
sudo dnf install gnome-tweaks -y
```

#### Gnome Extension Manager

```bash
flatpak install flathub com.mattjakeman.ExtensionManager
```

推荐安装扩展

- Dash To Panel
- User Themes
- Input Method Panel
- AppIndicator and KStatusNotifierItem Support
- Blur my Shell

## 下载工具

### Motrix

```bash
flatpak install flathub net.agalwood.Motrix
```

### qBittorrent

```
flatpak install flathub org.qbittorrent.qBittorrent
```

### XDM

Xtreme Download Manager [https://github.com/subhra74/xdm/releases](https://github.com/subhra74/xdm/releases)

```
https://github.com/subhra74/xdm/releases/download/8.0.29/xdman_gtk-8.0.29-1.fc36.x86_64.rpm
```

```
https://ghproxy.cn/https://github.com/subhra74/xdm/releases/download/8.0.29/xdman_gtk-8.0.29-1.fc36.x86_64.rpm
```



## 文本编辑器

### Sublime Text 4

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

```bash
flatpak install flathub io.typora.Typora
```

## 

## 浏览器

### Gecko内核

```
flatpak install flathub org.mozilla.firefox
```

```
flatpak install flathub io.gitlab.librewolf-community
```

```
flatpak install flathub net.waterfox.waterfox
```

### Blink 内核

Chrome

```
flatpak install flathub com.google.Chrome
```

Chromium

```
flatpak install flathub org.chromium.Chromium
```

brave

```
flatpak install flathub com.brave.Browser
```

Opera

```
flatpak install flathub com.opera.Opera
```

### 火狐浏览器

使用 **软件商店** 、Flatpak、DNF 等工具安装的 Firefox 浏览器， 可能会存在某些问题， 建议使用 Firefox 提供的二进制文件进行安装

下载地址

```
https://download.mozilla.org/?product=firefox-latest-ssl&os=linux64&lang=en-US
```



```bash
cd ~/Downloads
tar xjf firefox-*.tar.bz2
sudo mv firefox /opt
sudo ln -s /opt/firefox/firefox /usr/local/bin/firefox
sudo wget https://raw.githubusercontent.com/mozilla/sumo-kb/main/install-firefox-linux/firefox.desktop -P /usr/local/share/applications
```



## 开发工具

### Sublime Merge-Git可视化工具

```
flatpak install flathub com.sublimemerge.App
```

### Docker-容器

安装 docker

```bash
sudo dnf install docker -y
```

开机自启动 docker

```bash
sudo systemctl enable docker.service 
```

启动 docker

```bash
sudo systemctl start docker.service 
```

解决 sudo 权限问题（重新登录用户生效）

```bash
sudo usermod -aG docker $USER
```

[Docker/DockerHub 国内镜像源/加速列表-长期维护](https://xuanyuan.me/blog/archives/1154)

```bash
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

### Insomnia-API接口测试工具

```bash
flatpak install flathub rest.insomnia.Insomnia
```

### Flameshot-截图工具

```bash
flatpak install flathub org.flameshot.Flameshot
```

### Gcolor3-取色工具

```bash
flatpak install flathub nl.hjdskes.gcolor3
```

### LocalSend-局域网文件传输

```bash
flatpak install flathub org.localsend.localsend_app
```

### Selenium-浏览器自动化测试

Firefox Driver https://github.com/mozilla/geckodriver/releases

```bash
wget https://cors.isteed.cc/github.com/mozilla/geckodriver/releases/download/v0.35.0/geckodriver-v0.35.0-linux64.tar.gz
tar -xvf geckodriver-v0.35.0-linux64.tar.gz
sudo mv geckodriver /usr/local/bin
```

### Nvm-Node Version Manager

Node Version Manager [https://github.com/nvm-sh/nvm](https://github.com/nvm-sh/nvm)

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
source ~/.zshrc
nvm install --lts
npm install nrm  -g --registry=https://registry.npmmirror.com
```

### Pyenv-Python多版本管理

**Simple Python Version Management** [https://github.com/pyenv/pyenv](https://github.com/pyenv/pyenv)

- 安装 Pyenv

```bash
curl https://pyenv.run | bash
```

- 安装依赖: Fedora 22 and above: [https://github.com/pyenv/pyenv/wiki#suggested-build-environment](https://github.com/pyenv/pyenv/wiki#suggested-build-environment)

```bash
sudo dnf install make gcc patch zlib-devel bzip2 bzip2-devel readline-devel sqlite sqlite-devel openssl-devel tk-devel libffi-devel xz-devel libuuid-devel gdbm-libs libnsl2
```

- 追加以下内容到 **~/.zshrc** 文件末尾

```shell
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
```

- 临时生效系统环境变量

```bash
source ~/.zshrc
```

- 下载 Python 源码

```bash
mkdir ~/.pyenv/cache
cd ~/.pyenv/cache
wget https://mirrors.huaweicloud.com/python/3.10.14/Python-3.10.14.tar.xz
```

- 安装 3.10.14

```bash
pyenv install 3.10.14
```

- 设置默认Python版本

```bash
pyenv global 3.10.14
```

- 镜像配置

```bash
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
pip config set install.trusted-host pypi.tuna.tsinghua.edu.cn
```

