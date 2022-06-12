---
title: Ubuntu22.04 安装 JDK
date: 2022-05-21 22:40:23
cover: https://blog.image.codedemo.vip/Ubuntu22.04%2Fce9580e478bb294a04469b4eb7caddd7.jpeg
tags:
	- Ubuntu22.04
---

Ubuntu22.04 安装、配置 JDK

<!-- more -->

## 下载

Oracle 下载速度比较慢，目前下载 JDK 还需要登陆 Oracle 账号


JDK [清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/Adoptium/) 


以 [JDK 11](https://mirrors.tuna.tsinghua.edu.cn/Adoptium/11/jdk/x64/linux/) 为例


## 配置

解压

```bash
tar -xvf OpenJDK11U-jdk_x64_linux_hotspot_11.0.15_10.tar.gz
```

复制到指定目录

```bash
sudo cp -r jdk-11.0.15+10 /opt
```

环境变量配置 `sudo vim /etc/profile`

```
export JAVA_HOME=/opt/jdk-11.0.15+10
export PATH=$JAVA_HOME/bin:$PATH
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
```

重启系统生效