---
title: 【Win】 WinGet
date: 2025-02-14 01:37:28
tags:
	- Win
	- WinGet
---

WinGet

<!-- more -->

## .msixbundle

**如何安装 .msixbundle 格式软件 ?**

打开 PowserShell 终端， 使用命令 **Add-AppPackage** 安装， 比如：

```powershell
Add-AppPackage ./Microsoft.WindowsTerminal_1.22.10352.0_8wekyb3d8bbwe.msixbundle
```

## WinGet

WinGet 下载地址

```
https://github.com/microsoft/winget-cli/releases/download/v1.9.25200/Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.msixbundle
```



winget 镜像 [https://help.mirrors.cernet.edu.cn/winget-source/](https://help.mirrors.cernet.edu.cn/winget-source/)

```
winget source remove winget
winget source add winget https://mirrors.cernet.edu.cn/winget-source --trust-level trusted
```

如需重置为官方地址，执行以下命令即可：

```
winget source reset winget
```

## 代理

### ClashVergeRev

```
winget install  ClashVergeRev.ClashVergeRev
```

GitHub Release 下载地址

```
https://bgithub.xyz/clash-verge-rev/clash-verge-rev/releases/download/v2.0.3/Clash.Verge_2.0.3_x64-setup.exe
```



## 聊天

### Tim

```powershell
winget install Tencent.TIM
```

### YY

```powershell
winget install YY.YY
```

### WeChat

```powershell
winget install Tencent.WeChat
```

## 截图、录屏

### FastStone Capture

```
winget install FastStone.Capture
```

## 解压、压缩

```
winget install 7zip.7zip
```

## 浏览器

### Firefox

```
winget install Mozilla.Firefox
```

### Waterfox

```
winget install Waterfox.Waterfox
```

### LibreWolf

```
winget install LibreWolf.LibreWolf
```



### Google Chrome

```
winget install Google.Chrome
```

### Opera

```
winget install Opera.Opera
```

### Brave

```
winget install Brave.Brave
```

## 下载

### Motrix

```
winget install agalwood.Motrix
```

### 迅雷

迅雷官方最新版本

```
winget install Thunder.Thunder
```

## 文本编辑器

### Sublime Text 4

```
winget install SublimeHQ.SublimeText.4
```

### Typora

```
winget install appmakes.Typora
```

## 视频播放器

### PotPlayer

```
winget install Daum.PotPlayer
```

## JetBrains

### Toolbox

```
winget install JetBrains.Toolbox
```

### WebStorm

```
winget install JetBrains.WebStorm
```

### CLion

```
winget install JetBrains.CLion
```

### Writerside

```
winget install JetBrains.Writerside.EAP
```

### PyCharm

```
winget install JetBrains.PyCharm.Professional
```

### PhpStorm

```
winget install JetBrains.PhpStorm
```

### IntelliJIDEA

```
winget install JetBrains.IntelliJIDEA.Ultimate
```

### DataGrip

```
winget install JetBrains.DataGrip
```

### AndroidStudio

```
winget install Google.AndroidStudio
```

## 开发工具

### Git

```
winget install Git.Git
```

### Java



```
Java(TM) SE Development Kit 23                  Oracle.JDK.23                 23.0.2.0   Command: java winget
Java(TM) SE Development Kit 22                  Oracle.JDK.22                 22.0.2.0   Command: java winget
Java(TM) SE Development Kit 21                  Oracle.JDK.21                 21.0.6.0   Command: java winget
Java(TM) SE Development Kit 20                  Oracle.JDK.20                 20.0.2.0   Command: java winget
Java(TM) SE Development Kit 19                  Oracle.JDK.19                 19.0.2.0   Command: java winget
Java(TM) SE Development Kit 18                  Oracle.JDK.18                 18.0.2.1   Command: java winget
Java(TM) SE Development Kit 17                  Oracle.JDK.17                 17.0.12.0  Command: java winget
```



```
Microsoft Build of OpenJDK with Hotspot 21      Microsoft.OpenJDK.21          21.0.6.7   Tag: java     winget
Microsoft Build of OpenJDK with Hotspot 17      Microsoft.OpenJDK.17          17.0.14.7  Tag: java     winget
Microsoft Build of OpenJDK with Hotspot 16      Microsoft.OpenJDK.16          16.0.2.7   Tag: java     winget
Microsoft Build of OpenJDK with Hotspot 11      Microsoft.OpenJDK.11          11.0.26.4  Tag: java     winget
```



```
Amazon Corretto JRE 8                           Amazon.Corretto.8.JRE         1.8.0.442  Command: java winget
Amazon Corretto 8                               Amazon.Corretto.8.JDK         1.8.0.442  Command: java winget
Amazon Corretto 23                              Amazon.Corretto.23.JDK        23.0.2.7   Command: java winget
Amazon Corretto 22                              Amazon.Corretto.22.JDK        22.0.2.9   Command: java winget
Amazon Corretto 21                              Amazon.Corretto.21.JDK        21.0.6.7   Command: java winget
Amazon Corretto 20                              Amazon.Corretto.20.JDK        20.0.2.10  Command: java winget
Amazon Corretto 19                              Amazon.Corretto.19.JDK        19.0.2.7   Command: java winget
Amazon Corretto 18                              Amazon.Corretto.18.JDK        18.0.2.9   Command: java winget
Amazon Corretto 17                              Amazon.Corretto.17.JDK        17.0.14.7  Command: java winget
Amazon Corretto 11                              Amazon.Corretto.11.JDK        11.0.26.4  Command: java winget
```

### Nvm

```
winget install CoreyButler.NVMforWindows
```



```
nvm install --lts
```



```
nvm alias default node
```

