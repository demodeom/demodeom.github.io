---
title: Windows允许脚本运行
date: 2024-09-08 11:23:43
tags:
	- Windows
---


因为在此系统上禁止运行脚本

<!-- more -->


错误信息: `因为在此系统上禁止运行脚本`

解决方案: 以管理员身份运行 `Windows PowerShell` , 执行以下命令

```bash
set-ExecutionPolicy RemoteSigned
```