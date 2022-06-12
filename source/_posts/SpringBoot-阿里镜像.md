---
title: SpringBoot-阿里镜像
date: 2022-05-09 20:08:12
tags:
---

使用阿里SpringBoot镜像加速Maven下载

<!-- more -->

修改 `pom.xml` 文件 , `project` 标签下添加以下内容

```xml
<!--阿里云镜像加速-->
<repositories>
    <repository>
        <id>public</id>
        <name>aliyun</name>
        <url>https://maven.aliyun.com/repository/public</url>
        <releases>
            <enabled>true</enabled>
        </releases>
    </repository>
</repositories>
<!--阿里云镜像加速-->
<pluginRepositories>
    <pluginRepository>
        <id>public</id>
        <name>aliyun</name>
        <url>https://maven.aliyun.com/repository/public</url>
        <releases>
            <enabled>true</enabled>
        </releases>
        <snapshots>
            <enabled>false</enabled>
        </snapshots>
    </pluginRepository>
</pluginRepositories>
```







