---
title: Ubuntu 24.04 lts 系统软件配置
date: 2024-12-15 21:16:17
tags:
---

Ubuntu 24.04 lts 系统软件配置

<!-- more -->

## DNS

推荐案例云公共的DNS [https://alidns.com/](https://alidns.com/)


IP4

```
223.5.5.5,223.6.6.6
```

IP6

```
2400:3200::1,2400:3200:baba::1
```

使用以下命令测试

```bash
ping raw.githubusercontent.com -c3
```

修改前

```.
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


## 换源

推荐阿里云源

## 更新、升级

```bash
# 更新软件源
sudo apt update

# 升级软件
sudo apt upgrade -y
```

升级完成后建议重启系统

## 必备软件

安装常用软件

```bash
sudo apt install -y curl wget zsh git vim
```

## 终端美化

> 作为最受欢迎的 Zsh 配置框架，Oh My Zsh 让您的终端界面焕然一新。丰富的主题和插件支持，让您轻松自定义环境，提升工作效率。无论是代码开发、系统管理还是日常任务，Oh My Zsh 都能让您的命令行操作更加智能化和便捷。加入数万用户的行列，立即体验 Oh My Zsh 带来的终端革命，让您的工作更高效、更愉悦！

```bash
git clone  --depth 1  https://github.com/ohmyzsh/ohmyzsh ~/.oh-my-zsh

cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc

sudo usermod --shell /bin/zsh ${USER}
```

一键安装脚本

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Git 配置

```bash
# 设置默认分之为 main
git config --global init.defaultBranch main

# 配置用户名
git config --global user.name "demo"

# 配置用户邮箱
git config --global user.email "demodeom@example.com"
```

## Flatpak

添加 **flathub** 仓库

```bash
sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

配置环境变量

```bash
echo 'export XDG_DATA_DIRS=/var/lib/flatpak/exports/share:$HOME/.local/share/flatpak/exports/share' >> ~/.zshrc
```

Flatpak 配置 [上海交通大学 镜像](https://mirrors.sjtug.sjtu.edu.cn/docs/flathub)

```bash
flatpak remote-modify flathub --url=https://mirror.sjtu.edu.cn/flathub
```

## FireFox

下载最新版的 firefox

```bash
wget https://download-installer.cdn.mozilla.net/pub/firefox/releases/133.0.3/linux-x86_64/en-US/firefox-133.0.3.tar.bz2
```

卸载 snap 版本的 firefox

```bash
sudo apt remove firefox

sudo snap remove firefox
```

安装 firefox

```bash
tar xjf ./firefox-133.0.3.tar.bz2

sudo mv firefox /opt

sudo ln -s /opt/firefox/firefox /usr/local/bin/firefox

sudo wget https://raw.githubusercontent.com/mozilla/sumo-kb/main/install-firefox-linux/firefox.desktop -P /usr/local/share/applications
```

## Fcitx5

安装 fcitx5

```bash
sudo apt install fcitx5 fcitx5-chinese-addons fcitx5-module-cloudpinyin
```

启动 fcitx5

启动 **Startup Applications** 软件，将 fcitx5 添加到开机自启动

使用命令 **im-config** 启动 **Input Method Configuration** 软件，将  fcitx5 设置为默认的输入法框架

启动 **Fcitx5 Configuration** 软件， 将 PinYin 添加到默认输入法分组

使用以下命令编辑全局环境变量文件

```bash
sudo vim
```

在 **/etc/environment** 文件 末尾追加以下内容

```
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
INPUT_METHOD=fcitx
SDL_IM_MODULE=fcitx
GLFW_IM_MODULE=ibus
```

重启系统生效

下载 词库 [自建拼音输入法词库，百万常用词汇量](https://github.com/wuhgit/CustomPinyinDictionary)， 优化输入效果


词库下载地址 https://maicss.lanzoui.com/iErOirt790h

```bash
mkdir -p  ~/.local/share/fcitx5/pinyin/dictionaries/
cp zhwiki-20210722.dict ~/.local/share/fcitx5/pinyin/dictionaries/
```

## Gnome

安装 **GnomeTweaks** 软件

```bash
sudo apt install -y gnome-tweaks
```

安装 ExtensionManager 软件

```bash
flatpak install flathub com.mattjakeman.ExtensionManager
```

**推荐Gnome Desktop Extension**

- **User Themes** 用户自定义主题
- **Blur my Shell** 任务栏透明
- **Dash to Dock** 工具栏
- **Input Method Panel** fcitx5 输入法美化工具
- **AppIndicator and KStatusNotifierItem Support** 任务栏应用小图标支持



## 文本编辑器

### Sublime Text 4


> [Sublime Text 4](https://www.sublimetext.com/) 是一款功能强大的文本编辑器，专为开发者和程序员设计。它具有快速响应的界面和丰富的功能，包括多光标编辑、强大的搜索与替换、语法高亮和代码自动完成等。Sublime Text 4 支持多种编程语言，并可以通过插件进行扩展，满足各种开发需求。其灵活的配置和简洁的设计，使其成为许多开发者的首选工具。无论是进行日常编码还是复杂的项目开发，Sublime Text 4 都能提供出色的用户体验。

```bash
cd ~/Downloads
wget https://download.sublimetext.com/sublime-text_build-4192_amd64.deb
sudo dpkg -i sublime-text_build-4192_amd64.deb
```

```json
{
	"font_size": 20,
	"save_on_focus_lost": true,
	"theme": "Default Dark.sublime-theme",
	"color_scheme": "Mariana.sublime-color-scheme",
}
```

## Sublime Merge

> [https://flathub.org/apps/com.sublimemerge.App](https://flathub.org/apps/com.sublimemerge.App) 是一款高效的 Git 客户端，提供直观的用户界面和强大的功能，旨在简化版本控制的管理。它具有实时预览和语法高亮功能，方便用户查看和编辑代码变更。Sublime Merge 还支持快速搜索、分支管理和合并冲突解决，提升开发者的工作效率。此外，作为 Sublime Text 的姊妹产品，Sublime Merge 可以与 Sublime Text 无缝集成，适合需要高效 Git 工作流的开发者。

```bash
flatpak install flathub com.sublimemerge.App
```

### Typora

> [Typora](https://flathub.org/apps/io.typora.Typora) 是一款简洁而直观的 Markdown 编辑器，提供所见即所得的写作体验。用户在编辑时可以实时预览文本格式，消除传统 Markdown 编辑器的分离感。Typora 支持多种主题和自定义样式，允许插入图片、表格和数学公式，适合学术写作、笔记和文档创作。无论是专业人士还是学生，Typora 都是一个理想的写作工具。

```bash
cd ~/Downloads

wget https://download2.typoraio.cn/linux/typora_1.9.5_amd64.deb

sudo dpkg -i ~/Downloads/typora_1.9.5_amd64.deb
```



### VsCode

```bash
cd ~/Downloads

wget https://vscode.download.prss.microsoft.com/dbazure/download/stable/138f619c86f1199955d53b4166bef66ef252935c/code_1.96.0-1733888194_amd64.deb

sudo dpkg -i ~/Downloads/code_1.96.0-1733888194_amd64.deb
```

## IDEA



## PHP

将此 PPA 添加到您的系统中

```bash
sudo add-apt-repository ppa:ondrej/php
sudo apt update
```


```bash
sudo apt install php8.0-cli php8.0-fpm php8.0-xml php8.0-mbstring php8.0-curl php8.0-gd
```

```bash
sudo apt install php8.3-cli php8.3-fpm php8.3-xml php8.3-mbstring php8.3-curl php8.3-gd php8.3-intl php8.3-zip php8.3-mysql
```

```bash
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php composer-setup.php
php -r "unlink('composer-setup.php');"
sudo mv composer.phar /usr/local/bin/composer
```

## Node.js

> NRM（NPM Registry Manager）是一个用于管理 NPM 源的命令行工具。它允许用户轻松切换不同的 NPM 源，如官方源、淘宝镜像和私有源，从而加快包的安装速度和提高开发效率。通过简单的命令，用户可以查看当前使用的源、添加新的源和设置默认源，非常方便。NRM 解决了在中国地区由于网络问题导致的 NPM 安装缓慢的问题，使开发者能够更高效地进行项目开发和依赖管理。

安装 nvm

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
```

临时生效环境变量

```bash
source ~/.zshrc
```

安装最新版 Node.js

```bash
nvm install --lts
```

个人常用的软件

```bash
npm install hexo-cli nrm -g
```

```bash
npm install nrm  -g --registry=https://registry.npmmirror.com
```

## Java

Java 使用

## Python

[Simple Python Version Management](https://github.com/pyenv/pyenv)

安装 pyenv

```bash
curl https://pyenv.run | bash
```

添加环境配置

```bash
echo '# Pyenv' >> ~/.zshrc
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
```

生效配置文件

```bash
source ~/.zshrc
```

Install Python build dependencies

```bash
sudo apt update; sudo apt install -y build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev curl git \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```

安装 3.10 版本的Python

```bash
pyenv install 3.10
```

全局设置默认版本

```bash
pyenv global 3.10
```

配置 pip 镜像为清华大学镜像

```bash
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
pip config set install.trusted-host pypi.tuna.tsinghua.edu.cn
```


## Docker

安装 Docker

```bash
sudo apt install -y docker.io
```

解决 sudo 权限问题（重新登录用户生效）

```bash
sudo usermod -aG docker $USER
```

开机自启动 docker

```
sudo systemctl enable docker.service
```

启动 docker

```
sudo systemctl start docker.service
```



Docker 镜像配置 [Docker/DockerHub 国内镜像源/加速列表-长期维护](https://xuanyuan.me/blog/archives/1154)

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

## Color Picker


```bash
flatpak install flathub nl.hjdskes.gcolor3
```

## Flameshot

> Flameshot 是一个功能强大的开源截图工具，专为 Linux 用户设计。它提供直观的界面和多种截图编辑功能，如注释、模糊处理和高亮显示。用户可以自定义快捷键、调整界面风格，并通过命令行进行自动化操作。Flameshot 支持多种图像格式，适合开发者、设计师和普通用户使用。

```bash
flatpak install flathub org.flameshot.Flameshot
```



## GearLever

> Gear Lever是一个可以轻松管理 AppImage 的工具！Gear Lever 将为你组织和管理 AppImage 文件，生成桌面快捷方式、更新应用程序或保留多个版本并存。

```bash
flatpak install flathub it.mijorus.gearlever
```



## Insomnia

> Insomnia 是一款开源的 API 客户端，专为开发人员设计，旨在简化 API 的测试和调试过程。它提供直观的用户界面，支持 REST 和 GraphQL 请求，使用户能够轻松构建、发送和管理 API 请求。Insomnia 具备丰富的功能，包括环境变量管理、请求历史记录、代码生成和响应格式化，方便用户快速分析和调试数据。此外，Insomnia 还支持插件扩展，用户可以根据需要添加功能，提升工作效率。无论是进行日常开发还是调试复杂的 API，Insomnia 都是一个理想的工具。



```bash
flatpak install flathub rest.insomnia.Insomnia
```



## LocalSend

> LocalSend 是一款用于局域网内设备间文件传输的软件。无需互联网连接，用户可以通过 Wi-Fi 将文件快速传输到同一网络中的其他设备。支持多种文件格式，界面友好，操作简便，适用于各种操作系统。LocalSend 提供了高效、安全的文件共享解决方案，是局域网内设备互传文件的理想选择。



```bash
flatpak install flathub org.localsend.localsend_app
```



## Motrix

> Motrix 是一款开源的下载管理器，支持多种下载协议，包括 HTTP、HTTPS、FTP、BitTorrent 和磁力链接。它提供简洁直观的用户界面，方便用户快速添加和管理下载任务。Motrix 支持多线程下载，可有效提高下载速度，同时还具备断点续传、定时下载和下载分类等功能。该软件跨平台兼容，适用于 Windows、macOS 和 Linux，适合需要高效下载管理的用户。无论是大文件下载还是批量资源获取，Motrix 都能提供出色的性能和便利性。

```bash
flatpak install flathub net.agalwood.Motrix
```



## MySQL

```bash
sudo apt install mysql-server
```

切换到 root 用户

```bash
su - root
```

连接 MySQL

```bash
mysql
```

创建用户

```sql
create user "demo"@"%" identified by "12345678";
grant all on *.* to "demo"@"%" with grant option;
```

退出数据库

```sql
exit;
```

退出 root 用户

```bash
exit
```



## Selenium



> Selenium 是一种用于自动化网页浏览的开源工具。它支持多种浏览器（如Chrome、Firefox）和编程语言（如Java、Python）。Selenium 主要用于测试Web应用程序，通过模拟用户操作（如点击、输入文本）来验证功能是否正常。它包括Selenium WebDriver、Selenium Grid等组件，帮助开发人员编写和执行自动化测试脚本，提高测试效率和覆盖率。

Firefox Driver [https://github.com/mozilla/geckodriver/releases](https://github.com/mozilla/geckodriver/releases)

```bash
# 下载驱动
wget https://github.com/mozilla/geckodriver/releases/download/v0.35.0/geckodriver-v0.35.0-linux64.tar.gz

# 解压
tar -xvf geckodriver-v0.35.0-linux64.tar.gz

# 环境变量配置
sudo mv geckodriver /usr/local/bin
```

Google Chrome Driver 下载地址 [https://googlechromelabs.github.io/chrome-for-testing/#stable](https://googlechromelabs.github.io/chrome-for-testing/#stable)

## 浏览器大全

### Brave

```bash
flatpak install flathub com.brave.Browser
```

### Waterfox

```bash
flatpak install flathub net.waterfox.waterfox
```

### Chrome

```
https://www.google.cn/intl/zh-CN/chrome/
```

```bash
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

## 远程桌面

### Remmina

```bash
sudo apt install remmina -y
```

### ToDesk

「ToDesk」 Linux 客户端 [https://www.todesk.com/linux.html](https://www.todesk.com/linux.html)

```bash
wget https://dl.todesk.com/linux/todesk-v4.7.2.0-amd64.deb

sudo dpkg -i todesk-v4.7.2.0-amd64.deb
```

## 音乐、视频

视频

```bash
sudo apt install mpv vlc ffmpeg -y
```

音乐

```bash
flatpak install flathub io.bassi.Amberol
```

## Navicat Premium

> Navicat Premium 是一款强大的数据库管理工具，支持多种数据库类型，包括 MySQL、PostgreSQL、SQLite、Oracle 和 Microsoft SQL Server。它提供直观的用户界面，方便用户进行数据库设计、查询和管理。Navicat Premium 具备丰富的功能，如数据建模、数据迁移、报表生成和自动化任务，能够提高开发和管理的效率。此外，Navicat Premium 还支持云数据库连接，便于用户在不同平台上进行操作。无论是开发人员还是数据库管理员，Navicat Premium 都是一个理想的选择。

下载地址 [https://www.navicat.com.cn/download/navicat-premium](https://www.navicat.com.cn/download/navicat-premium)

```bash
wget https://www.navicat.com.cn/download/direct-download?product=navicat17-premium-cs-x86_64.AppImage&location=1
```

## clash

畅享无忧网络体验，尽在 Clash！作为强大的代理工具，Clash 为您提供快速、稳定的网络连接，让您轻松绕过地域限制，享受自由上网。无论是流媒体观看、游戏加速还是安全浏览，Clash 都能满足您的需求。其直观的界面和灵活的配置选项，让您轻松管理网络流量，提升在线体验。选择 Clash，让您的网络生活更畅快无阻，尽情探索互联网的无限可能！


Clash GitHub 下载地址 [https://github.com/clash-verge-rev/clash-verge-rev/releases](https://github.com/clash-verge-rev/clash-verge-rev/releases)


### 三毛导航

三毛导航 [https://三毛导航.com](https://三毛导航.com)

```bash
# 下载 clash
wget https://github.com/clash-verge-rev/clash-verge-rev/releases/download/v2.0.2/Clash.Verge_2.0.2_amd64.deb

#安装 clash
sudo dpkg -i Clash.Verge_2.0.2_amd64.deb
```

## Flutter


```bash
echo 'export PATH=$HOME/Documents/flutter/bin:$PATH' >> ~/.zshrc
```

检查 flutter 环境

```
flutter doctor
```



```
[!] Android toolchain - develop for Android devices (Android SDK version 34.0.0)
    ! Some Android licenses not accepted. To resolve this, run: flutter doctor
      --android-licenses
```



```
flutter doctor --android-licenses
```



```
✗ clang++ is required for Linux development.
      It is likely available from your distribution (e.g.: apt install clang),
      or can be downloaded from https://releases.llvm.org/
```



```
✗ CMake is required for Linux development.
      It is likely available from your distribution (e.g.: apt install cmake),
      or can be downloaded from https://cmake.org/download/
```





```
✗ ninja is required for Linux development.
      It is likely available from your distribution (e.g.: apt install
      ninja-build), or can be downloaded from
      https://github.com/ninja-build/ninja/releases
```





```
✗ GTK 3.0 development libraries are required for Linux development.
      They are likely available from your distribution (e.g.: apt install
      libgtk-3-dev)
```



```bash
sudo apt install -y clang cmake ninja-build  libgtk-3-dev
```
