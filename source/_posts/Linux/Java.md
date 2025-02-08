---
title: Java
date: 2024-10-20 17:59:58
tags:
	- Linux
---


<!-- more -->

清华大学镜像 Jdk 下载地址

```
https://mirrors.tuna.tsinghua.edu.cn/Adoptium/
```

完整安装命令

```bash
cd ~/Downloads
tar -xvf OpenJDK8U-jdk_x64_linux_hotspot_8u422b05.tar.gz
sudo mv jdk8u422-b05 /opt/jdk8
```

环境变量配置

```bash
# Java jdk8
export JAVA_HOME=/opt/jdk8
export PATH=$PATH:$JAVA_HOME/bin
```

