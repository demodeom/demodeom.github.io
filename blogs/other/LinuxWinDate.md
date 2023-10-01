---
title: 修复 Linux、Win 双系统时间不一致问题
date: 2023/09/29
categories:
 - other
---

## 问题产生原因

系统开机会更新本地日期时间

Ubuntu 将 主板CMOS 内的时间设为格林威治标准时间，系统时间以这个时间 +8（时区）得到本地时间

Win 认为主板CMOS内的时间就是本地时间

以 Ubuntu 为例， 执行以下命令

```bash
timedatectl set-local-rtc 1
```