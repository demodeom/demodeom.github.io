---
title: Node.js
date: 2024-10-20 17:37:07
tags:
	- Linux
---

Node.js 是一个基于 Chrome V8 引擎的开源 JavaScript 运行时，允许开发者在服务器端执行 JavaScript 代码。它采用事件驱动、非阻塞 I/O 模型，适合构建高性能的网络应用，尤其是实时应用程序，如聊天应用和在线游戏。Node.js 拥有丰富的生态系统，提供大量的模块和包，方便开发者快速搭建和扩展应用。凭借其轻量级和高效性，Node.js 在 web 开发、API 构建和微服务架构等领域受到广泛应用。

<!-- more -->

## NVM

NVM（Node Version Manager）是一个用于管理 Node.js 版本的命令行工具。它允许用户轻松安装、切换和管理多个 Node.js 版本，适应不同项目的需求。NVM 使得开发者可以在同一台机器上同时使用多个 Node 版本，从而避免版本冲突。通过简单的命令，用户可以快速安装所需的 Node.js 版本并进行切换，非常适合需要频繁更改 Node 版本的开发环境。NVM 提供了高效的管理方式，提高了开发工作的灵活性和便捷性。

安装 nvm

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
```

临时生效环境变量

```bash
source ~/.zshrc
```

安装最新 lts 版本

```bash
nvm install --lts
```

## nrm

NRM（NPM Registry Manager）是一个用于管理 NPM 源的命令行工具。它允许用户轻松切换不同的 NPM 源，如官方源、淘宝镜像和私有源，从而加快包的安装速度和提高开发效率。通过简单的命令，用户可以查看当前使用的源、添加新的源和设置默认源，非常方便。NRM 解决了在中国地区由于网络问题导致的 NPM 安装缓慢的问题，使开发者能够更高效地进行项目开发和依赖管理。

安装 nrm

```bash
npm install nrm  -g --registry=https://registry.npmmirror.com
```

查看国内可用的镜像

```
nrm ls
```



## 国内镜像


```bash
npm config set registry -g http://registry.npmmirror.com
```

```bash
npm config set registry https://registry.npmjs.org
```


npm 

```
https://registry.npmjs.org/
```
yarn 

```
https://registry.yarnpkg.com/
```

tencent

```
https://mirrors.cloud.tencent.com/npm/
```

cnpm 

```
https://r.cnpmjs.org/
```

taobao 

```
https://registry.npmmirror.com/
```

npmMirror 

```
https://skimdb.npmjs.com/registry/
```

huawei

```
https://repo.huaweicloud.com/repository/npm/
```
