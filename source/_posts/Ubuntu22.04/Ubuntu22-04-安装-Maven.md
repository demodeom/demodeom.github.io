---
title: Ubuntu22.04 安装 Maven
date: 2022-05-21 22:57:14
tags:
	- Ubuntu22.04
cover: https://blog.image.codedemo.vip/Ubuntu22.04%2Fmaven-logo-black-on-white.png

---

Ubuntu22.04 安装、配置 Maven

<!-- more -->


## 下载


[Maven 下载地址](https://maven.apache.org/download.cgi)

解压

```bash
tar -xvf apache-maven-3.8.5-bin.tar.gz
```

复制到指定目录


```bash
sudo cp -r apache-maven-3.8.5 /opt
```


## 配置

环境变量配置 `sudo vim /etc/profile`

```bash
export MAVEN_HOME=/opt/apache-maven-3.8.5
export PATH=${MAVEN_HOME}/bin:${PATH}
```

重启系统生效




