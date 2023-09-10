---
title: GitHub 终极解决方案
date: 2023-09-09 12:01:18
tags:
	- GitHub
---

GitHub 使用主要存在两个问题： 

1. 浏览器访问不稳定。 
2. 下载速度慢。

<!-- more -->


本文将重点解决这两个问题

1. 浏览器访问不稳定，甚至无法访问
2. 代码或者Release资源下载速度慢，或者无法下载

## 1. 如何解决 GitHub 访问问题

### 终极解决方法： 使用软件 FastGitHUb 

FastGitHUb 是一款开源、免费、跨平台的代理软件，支持 Win、Mac、Linux 操作系统。

FastGitHUb 不提供国外服务器代理，因此 FastGitHUb 并无加速效果。

FastGitHUb 是通过本地代理的方式，保证 GitHub 的稳定访问。

FastGitHUb 可以解决以下问题

1. 浏览器无法访问 GitHub 的问题
2. GitHub 静态资源无法加载问题， 比如： 图片、Css、Js 等
3. Release 无法下载资源问题
4. Git 无法使用命令 clone、pull、push 等问题

### FastGitHUb  使用注意事项

FastGitHUb 软件关闭窗口之后，软件会放在桌面右下角图标区域，点击右键，点击 关闭应用 可退出软件

FastGitHUb 软件包解压之后， 运行 FastGithub.UI 程序启动。 切记！ 切记！ 切记！


1. 如果使用 firefox 浏览器，需要做以下配置

1.1 打开 firefox 浏览器，地址栏输入 `about:config ` 回车

1.2 搜索配置项 `security.enterprise_roots.enabled`, 把值修改 `true`

1.3 重启firefox 浏览器


2. 如果使用 Git 命令，比如： git clone 、git pull 等命令， 需要配置如下

2.1 以管理员的身份运行 cmd 终端
2.2 在 cmd 终端运行命令 `git config --global http.sslverify false`


3. 如果电脑关机前未退出 FastGitHUb ， 可能导致下次开机无法上网，有以下两种解决方法

方法1： 将 FastGitHUb 添加到开机启动项
方法2： 打开 FastGitHUb 软件，即可正常上网，如果无需 FastGitHUb 软件，可正常推出 


4. FastGitHUb 软件在使用过程中，偶尔会出现无法访问 GitHub 的问题， 解决方法如下

关闭 FastGitHUb 软件，再重新打开 FastGitHUb 软件


## 2. 如何解决 GitHub 下载慢

### 2.1 方法1： 使用 Motrix 下载

复制下载地址，使用 Motrix 下载

Motrix 软件通过多线程的方式提高下载速度，浏览器一般为单线程下载，对比起来 Motrix 下载速度比较快

注： Motrix 使用前提是 GitHub 正常访问，所以需要配合 FastGitHUb 软件使用


### 2.2： 使用浏览器扩展篡改猴


使用浏览器扩展篡改猴，配合脚本可以直接使用浏览器下载

篡改猴 脚本仓库的脚本，提供了不同国家的下载镜像，下载速度跟据镜像服务器的负载的高低会有波动，可以尝试使用不同的镜像下载


## 总结

以上解决方法并无涉及到 vpn 等非法(国内)软件。

GitHub 访问没有加速，只是使用软件 FastGitHUb 保证访问稳定。

GitHub 文件下载可以通过 多线程 或者 国外镜像 等方式加速下载