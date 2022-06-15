---
title: Ubuntu Desktop 20.04 配置指南
date: 2022-06-14 13:49:51
tags:
  - "Ubuntu Desktop 20.04"
cover: https://s1.ax1x.com/2022/06/14/X4mkwt.jpg
---

Ubuntu Desktop 20.04 安装常用软件、搭建常见的开发环境

<!-- more -->

## 换源

推荐源

- 阿里云
- 华为云
- cn99

## Sudo 免密码


使用 `sudo visudo` 打开配置文件，文件末尾追加以下内容

```
demodeom ALL=(ALL:ALL) NOPASSWD: ALL
```

demodeom 代表当前用户名，需要根据实际情况修改


`ctrl + o` 保存修改, 输入 `y` , 然后按下 `回车` 确认保存

`ctro + x` 退出文件


## 更新系统

```bash
sudo apt update
sudo apt upgrade
```

## 常用软件

```bash
sudo apt install -y git curl wget zsh axel vim
```

## UpdateHosts

[GitHub520 Host Home Page](https://raw.hellogithub.com/hosts)

```bash

```

## 终端

### OhMyZsh

[OhMyZsh Home Page](https://github.com/ohmyzsh/ohmyzsh)

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Terminator

```
sudo apt install terminator
```





## AppImageLauncher

[AppImageLauncher Download](https://github.com/TheAssassin/AppImageLauncher)

```bash
sudo dpkg -i appimagelauncher_2.2.0-travis995.0f91801.bionic_amd64.deb
```

## 下载工具

### Motrix

[Motrix Download](https://github.com/agalwood/Motrix/releases)


## 浏览器

### Firefox

FireFox 常用扩展

[划词翻译](https://addons.mozilla.org/zh-CN/firefox/addon/hcfy/)

[Gesturefy](https://addons.mozilla.org/zh-CN/firefox/addon/gesturefy/)

[LastPass: Free Password Manager](https://addons.mozilla.org/zh-CN/firefox/addon/lastpass-password-manager/)


[Tampermonkey](https://addons.mozilla.org/zh-CN/firefox/addon/tampermonkey/)

[Tampermonkey 脚本 - Github 增强](https://greasyfork.org/zh-CN/scripts/412245-github-增强-高速下载)

[Tampermonkey 脚本 - 网盘直链下载助手](https://greasyfork.org/zh-CN/scripts/436446-网盘直链下载助手)

[Tampermonkey 脚本 - Github 中文插件](https://greasyfork.org/zh-CN/scripts/435208-github-中文化插件)


### Google Chrome

[Google Chrome Download](https://www.google.cn/intl/zh-CN/chrome/)

```bash
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

### LibreWolf

```bash
distro=$(if echo " bullseye focal impish jammy uma una " | grep -q " $(lsb_release -sc) "; then echo $(lsb_release -sc); else echo focal; fi)

echo "deb [arch=amd64] http://deb.librewolf.net $distro main" | sudo tee /etc/apt/sources.list.d/librewolf.list

sudo wget https://deb.librewolf.net/keyring.gpg -O /etc/apt/trusted.gpg.d/librewolf.gpg

sudo apt update

sudo apt install -y librewolf 
```

## IDE

### Sublime Text

[Sublime Text Download](https://www.sublimetext.com/download)

```bash
sudo dpkg -i sublime-text_build-4126_amd64.deb
```

### Typora

Add apt-key

```bash
wget -qO - https://typoraio.cn/linux/public-key.asc | sudo apt-key add -
```

Add Typora's Repository

```
sudo add-apt-repository 'deb https://typoraio.cn/linux ./'
```

Apt Update

```
sudo apt update
```

Install Typora

```
sudo apt-get install typora
```

### JetBrain 全家桶

[JetBrain ToolBox Download](https://www.jetbrains.com/toolbox-app/)

**关于激活**

每个账号提供一个月的试用， 支持 JetBrain 下的所有产品，注册账号只需要邮箱即可

**关于邮箱**

每个手机号每年支持注册 10 个QQ账号，腾讯每年允许一次机会， 一键解绑所有QQ账号， 来年还可以继续注册QQ号；

每个QQ号可以至少得到两个邮箱账号， 一个是 `@qq.com` ， 一个是 `@foxmail.com`

**关于登陆**

登陆 ToolBox 即可，其它产品会自动登陆， 获取一个月试用

**注册地址**  [注册地址](https://account.jetbrains.com/login)

### Eclipse

```bash
wget https://mirrors.nju.edu.cn/eclipse//technology/epp/downloads/release/2021-12/R/eclipse-jee-2021-12-R-linux-gtk-x86_64.tar.gz

tar -xvf eclipse-jee-2021-12-R-linux-gtk-x86_64.tar.gz

mv eclipse ~/eclipse


echo '[Desktop Entry]' | sudo  tee -a /usr/share/applications/Eclipse.desktop
echo 'Version=1.0' | sudo  tee -a /usr/share/applications/Eclipse.desktop
echo 'Name=Eclipse' | sudo  tee -a /usr/share/applications/Eclipse.desktop
echo 'Comment=Eclipse' | sudo  tee -a /usr/share/applications/Eclipse.desktop
echo 'Exec=/home/wyj/eclipse/eclipse' | sudo  tee -a /usr/share/applications/Eclipse.desktop
echo 'Icon=/home/wyj/eclipse/icon.xpm' | sudo  tee -a /usr/share/applications/Eclipse.desktop
echo 'Terminal=false' | sudo  tee -a /usr/share/applications/Eclipse.desktop
echo 'Type=Application' | sudo  tee -a /usr/share/applications/Eclipse.desktop
echo 'Categories=Utility;Application;' | sudo  tee -a /usr/share/applications/Eclipse.desktop

rm ./eclipse-jee-2021-12-R-linux-gtk-x86_64.tar.gz
```



## Docker

```bash
sudo apt install -y docker.io
```

Sudo 权限问题, 命令需重新登录生效

```bash
sudo usermod -aG docker $USER
```


设置 Docker 国内镜像 [DaoColud Mirror](https://www.daocloud.io/mirror)

```bash
curl -sSL https://get.daocloud.io/daotools/set_mirror.sh | sh -s http://f1361db2.m.daocloud.io
```

## V2rayA

使用 Docker 安装 V2rayA

```bash
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

Web 管理界面地址 [http://localhost:2017](http://localhost:2017)

Free 订阅地址 [https://bulink.me/sub/m5vaa/vm](https://bulink.me/sub/m5vaa/vm)

Socks5 默认端口 `20170`




## 开发环境

### PHP

添加源仓库

```bash
sudo add-apt-repository ppa:ondrej/php
```

安装 PHP 7.3

```bash
sudo apt install php7.3-fpm php7.3-cli php7.3-mbstring php7.3-zip php7.3-mysql php7.3-xml php7.3-gd php7.3-bcmath
```

安装 PHP 7.4

```bash
sudo apt install php7.4-fpm php7.4-cli php7.4-mbstring php7.4-zip php7.4-mysql php7.4-xml php7.4-gd php7.4-bcmath php7.4-curl
```

安装 PHP 8.0

```bash
sudo apt install php8.0-cli php8.0-fpm php8.0-xml php8.0-mbstring php8.0-curl php8.0-gd
```


### Node.js

[Nvm Home](https://github.com/nvm-sh/nvm)

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

```bash
nvm install --lts
```

### Python

[Pyenv Installer Home](https://github.com/pyenv/pyenv-installer)


安装脚本

```bash
curl https://pyenv.run | bash
```

添加环境变量

```bash
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init --path)"
eval "$(pyenv virtualenv-init -)"
```

### Java JDK

[清华大学开源软件镜像站 - JDK Download](https://mirrors.tuna.tsinghua.edu.cn/Adoptium/)

```bash
tar -xvf OpenJDK11U-jdk_x64_linux_hotspot_11.0.15_10.tar.gz

cd OpenJDK11U-jdk_x64_linux_hotspot_11.0.15_10

sudo mv jdk-11.0.15+10 /opt/jdk11
```

环境变量配置

```bash
# JDK
export JAVA_HOME=/opt/jdk11
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin
```

查看 JDK 版本

```bash
java --version
```

```
openjdk 11.0.15 2022-04-19
OpenJDK Runtime Environment Temurin-11.0.15+10 (build 11.0.15+10)
OpenJDK 64-Bit Server VM Temurin-11.0.15+10 (build 11.0.15+10, mixed mode)
```


### Maven

[清华大学开源软件镜像站 - Maven Download](https://mirrors.tuna.tsinghua.edu.cn/apache/maven/)

```bash
tar -xvf apache-maven-3.8.6-bin.tar.gz
mv apache-maven-3.8.6 /opt/apache-maven-3
```

环境变量

```bash
#Maven
export MAVEN_HOME=/opt/apache-maven-3
export PATH=$MAVEN_HOME/bin:$PATH
```

Maven 版本

```bash
mvn --version
```

```
Apache Maven 3.8.6 (84538c9988a25aec085021c365c560670ad80f63)
Maven home: /opt/apache-maven-3
Java version: 11.0.15, vendor: Eclipse Adoptium, runtime: /opt/jdk11
Default locale: zh_CN, platform encoding: UTF-8
OS name: "linux", version: "5.13.0-48-generic", arch: "amd64", family: "unix"
```



### Tomcat

[清华大学开源软件镜像站 - Tomcat Download](https://mirrors.tuna.tsinghua.edu.cn/apache/tomcat/)

```bash
tar -xvf apache-tomcat-10.0.22.tar.gz
sudo mv apache-tomcat-10.0.22 /opt/apache-tomcat-10
```

环境变量

```bash
# Tomcat
export CATALINA_HOME=/opt/apache-tomcat-10
export PATH=$CATALINA_HOME/bin:$PATH
```

查看版本

```bash
/opt/apache-tomcat-10/bin/version.sh 
```

```
Using CATALINA_BASE:   /opt/apache-tomcat-10
Using CATALINA_HOME:   /opt/apache-tomcat-10
Using CATALINA_TMPDIR: /opt/apache-tomcat-10/temp
Using JRE_HOME:        /opt/jdk11
Using CLASSPATH:       /opt/apache-tomcat-10/bin/bootstrap.jar:/opt/apache-tomcat-10/bin/tomcat-juli.jar
Using CATALINA_OPTS:   
NOTE: Picked up JDK_JAVA_OPTIONS:  --add-opens=java.base/java.lang=ALL-UNNAMED --add-opens=java.base/java.io=ALL-UNNAMED --add-opens=java.base/java.util=ALL-UNNAMED --add-opens=java.base/java.util.concurrent=ALL-UNNAMED --add-opens=java.rmi/sun.rmi.transport=ALL-UNNAMED
Server version: Apache Tomcat/10.0.22
Server built:   Jun 2 2022 16:53:56 UTC
Server number:  10.0.22.0
OS Name:        Linux
OS Version:     5.13.0-48-generic
Architecture:   amd64
JVM Version:    11.0.15+10
JVM Vendor:     Eclipse Adoptium
```

## 视频播放器


### Mpv

```bash
sudo apt install -y mpv
```

### VLC

```bash
sudo apt install -y vlc
```

## 邮箱

### Mailspring


### Evolution



## DNS 缓存


Ubuntu22.04 查看 Dns 缓存、清空DNS缓存


### 查看缓存


`resolvectl statistics` 查看缓存

```
DNSSEC supported by current servers: no

Transactions              
Current Transactions: 0
  Total Transactions: 7373
                          
Cache                     
  Current Cache Size: 1
          Cache Hits: 3674
        Cache Misses: 3706
                          
DNSSEC Verdicts           
              Secure: 0
            Insecure: 0
               Bogus: 0
       Indeterminate: 0
```

### 清空缓存

`resolvectl flush-caches` 查看缓存


### 重置


`resolvectl reset-statistics`


## 美化

```bash
sudo apt install -y gnome-tweaks gnome-shell-extensions
```

```bash
mkdir ~/.icons
mkdir ~/.themes
```

























