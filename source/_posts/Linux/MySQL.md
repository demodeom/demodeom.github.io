---
title: MySQL
date: 2024-10-20 19:34:16
tags:
	- Linux
---

<!-- more -->


```bash
sudo apt install mysql-server
```

切换到 root 用户

```bash
su - root
```

连接 MySQL

```bash
mysql
```

创建用户

```sql
create user "demo"@"%" identified by "12345678";
grant all on *.* to "demo"@"%" with grant option;
```

退出 root 用户

```bash
exit
```
