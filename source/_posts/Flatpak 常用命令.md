---
title: Flatpak 常用命令
date: 2025-07-18 06:24:58
tags:
---

Flatpak 经常使用的命令和参数详细解释。

<!-- more -->


## 安装的软件列表

查看用户安装的应用（显示依赖）

```bash
flatpak list 
```

示例输出如下:

```
名称                                  应用程序 ID                         版本                     分支        安装
扩展管理器                            com.mattjakeman.ExtensionManager    0.6.3                    stable      system
Typora                                io.typora.Typora                    1.10.8                   stable      system
Motrix                                net.agalwood.Motrix                 1.37.0                   stable      system
Freedesktop Platform                  org.freedesktop.Platform            freedesktop-sdk-23.08.32 23.08       system
Freedesktop Platform                  org.freedesktop.Platform            freedesktop-sdk-24.08.22 24.08       system
```

仅查看用户安装的应用（不显示依赖）

```bash
flatpak list --app
```

- `--app` 选项会过滤掉运行时（runtime）和依赖，只显示实际安装的应用程序。


```

```


 查看用户安装的应用及版本


```bash
flatpak list --app --columns=application,name,version,branch
```


查看所有已安装的运行时（依赖）：

```
flatpak uninstall --unused
```

卸载不再需要的依赖（清理旧版本或未使用的运行时）：

```
flatpak list --runtime
```