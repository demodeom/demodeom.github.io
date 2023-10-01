---
title: FastGitHub 解决 GitHub 无法访问的神器
date: 2023/09/29
categories:
 - other
---


## 下载地址

### Linux

GitHub 下载地址 

[https://github.com/dotnetcore/FastGithub/releases/download/2.1.4/fastgithub_linux-x64.zip](https://github.com/dotnetcore/FastGithub/releases/download/2.1.4/fastgithub_linux-x64.zip)

美国 Cloudflare CDN 加速下载地址 

[https://download.nuaa.cf/dotnetcore/FastGithub/releases/download/2.1.4/fastgithub_linux-x64.zip](https://download.nuaa.cf/dotnetcore/FastGithub/releases/download/2.1.4/fastgithub_linux-x64.zip)


### Win


GitHub 下载地址  

[https://github.com/dotnetcore/FastGithub/releases/download/2.1.4/fastgithub_win-x64.zip](https://github.com/dotnetcore/FastGithub/releases/download/2.1.4/fastgithub_win-x64.zip)

美国 Cloudflare CDN 加速下载地址 

[https://download.nuaa.cf/dotnetcore/FastGithub/releases/download/2.1.4/fastgithub_win-x64.zip](https://download.nuaa.cf/dotnetcore/FastGithub/releases/download/2.1.4/fastgithub_win-x64.zip)


### Mac

GitHub 下载地址  

[https://github.com/dotnetcore/FastGithub/releases/download/2.1.4/fastgithub_osx-x64.zip](https://github.com/dotnetcore/FastGithub/releases/download/2.1.4/fastgithub_osx-x64.zip)

美国 Cloudflare CDN 加速下载地址 

[https://download.nuaa.cf/dotnetcore/FastGithub/releases/download/2.1.4/fastgithub_osx-x64.zip](https://download.nuaa.cf/dotnetcore/FastGithub/releases/download/2.1.4/fastgithub_osx-x64.zip)


## 运行

### Win10/11

1. 解压
2. 运行 `FastGithub.UI.exe` 程序即可

使用 FastGithub 之后， 如果遇到开机无法上网的情况，解决方法：

1. 运行 `FastGithub.UI.exe` 程序即可 


### Linux

1. 解压
2. 进入解压目录
3. 在终端执行命令 `./fastgithub`
4. 配置 `网络代理` 为 `自动`，代理地址 `http://localhost:38457`

### Firefox

无论是什么操作系统， Firefox 浏览器需要安装 `cacert/fastgithub.crt` 目录下的证书

### Git

使用 git 命令， 需要以下配置

```bash
git config --global http.sslverify false
```


### Linux 开机子启动

1. 解压
2. 复制解压目录到 `/opt` 目录
3. 创建 启动脚本 `fastgithub.sh`， 脚本内容如下
4. 将脚本复制到 `/usr/bin` 目录
5. 将脚本添加到 开机自启动

`fastgithub.sh` 脚本内容如下

```shell
#!/bin/bash
nohup /opt/fastgithub_linux-x64/fastgithub > /tmp/fastgithub.log &
```






