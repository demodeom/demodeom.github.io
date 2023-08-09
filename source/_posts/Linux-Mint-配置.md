---
title: Linux Mint 配置
date: 2023-08-09 08:57:47
tags:
---

体验 Linux Mint 发行版，记录配置过程和常用软件安装步骤

<!-- more -->

# Linux Mint

## Welcome


## Hosts

DNS 查询网站

国内站长工具 [https://tool.chinaz.com/dns?type=a&ip=9.9.9.9](https://tool.chinaz.com/dns?type=a&ip=9.9.9.9)

```bash
185.199.108.133	raw.githubusercontent.com
192.30.255.112	github.com
192.30.255.112	www.github.com
```


## 输入法


1. 安装小企鹅输入法

```bash
sudo apt install fcitx5 fcitx5-chinese-addons fcitx5-material-color
```

2. 使用命令 `im-config` 配置默认输入法框架为 fcitx5

3. 将 `/usr/bin/fcitx5` 命令添加到开机启动程序

4. 重启系统

5. 配置输入法：字体大小(14)、主题、云拼音(百度)


## 软件管理

部分常用软件可以在系统自带软件管理器下载 (虽然安装方便，但是安装速度真让人着急)


### Sublime Text

```bash
sudo apt install sublime-text
```

### Google Chrome

```bash
cd ~ 
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb 
sudo dpkg -i ~/google-chrome-stable_current_amd64.deb
sudo apt install -f
```

### docker

```bash
sudo apt install docker.io
```

修复： 解决 sudo 权限问题

```
sudo usermod -aG docker $USER
```

重启永久生效

终端临时生效方法命令 `newgrp docker`

国内镜像

```
sudo vim /etc/docker/daemon.json
```

内容如下

```json
{
  "registry-mirrors": ["http://f1361db2.m.daocloud.io"]
}
```

### brave

```bash
sudo apt install curl

sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg] https://brave-browser-apt-release.s3.brave.com/ stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list

sudo apt update

sudo apt install brave-browser
```

### V2rayA

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

GitHub 免费订阅地址 [freefq/free](https://github.hscsec.cn/freefq/free)

```
https://bulinkbulink.com/freefq/free/master/v2
```

三毛机场订阅地址 

```
https://dy.jimao.icu/api/v1/client/subscribe?token=0f267133d220a53283d4016b4e2b4658
```

### localsend

```bash
cd ~/
axel -n 16 https://github.com/localsend/localsend/releases/download/v1.10.0/LocalSend-1.10.0-linux-x86-64.deb
sudo dpkg -i ~/LocalSend-1.10.0-linux-x86-64.deb
```

### ohmyzsh

```bash
sudo apt install zsh
```

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### qbittorrent

```bash
sudo apt install qbittorrent
```




