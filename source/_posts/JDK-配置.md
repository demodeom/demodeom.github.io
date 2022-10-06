---
title: JDK 配置
date: 2022-10-07 04:02:20
tags:
    - Java
---

Java 配置 JDK

<!-- more -->

## 下载

下载方式1： [JDK 清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/Adoptium/) 

下载方式2： [JDK Oracle官网下载](https://www.oracle.com/java/technologies/downloads/) 


## 配置

### Linux

解压

```bash
tar -xvf OpenJDK11U-jdk_x64_linux_hotspot_11.0.15_10.tar.gz
```

复制到指定目录

```bash
sudo cp -r jdk-11.0.15+10 /opt/jdk11
```

环境变量配置 `vim ~/.zshrc` 或者 `vim ~/.bashrc`

```
export JAVA_HOME=/opt/jdk11
export PATH=$JAVA_HOME/bin:$PATH
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
```

重启系统生效

### Win

新建 **系统环境变量** `JAVA_HOME` ，值为本地 JDK 解压目录， 比如：

```
D:/jdk-11.0.15+10
```

新建 **系统环境变量** `CLASSPATH` ，值为

```
.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;
```

修改 **系统环境变量** `PATH`，添加以下内容

```
%JAVA_HOME%\bin
%JAVA_HOME%\jre\bin
```

## 检查JDK配置

打开终端， 输入 `java -version`， 检查版本信息是否与安装版本一致， 如果一致表示配置成功

```
openjdk 11.0.15 2022-07-19
OpenJDK Runtime Environment Temurin-11.0.15+8 (build 11.0.15+8)
OpenJDK 64-Bit Server VM Temurin-11.0.15+8 (build 11.0.15+8, mixed mode)
```

## 解决中文乱码

编译

```bash
javac -encoding utf-8 HelloWorld.java
```

运行

```bash
java -Dfile.encoding=utf-8 HelloWorld
```







