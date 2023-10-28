---
title: PyMySQL - Python 操作数据库
date: 2023/10/06
tags:
  - MySQL
categories:
  - Python
---

## PyMySQL 简介

PyMySQL 是一个纯 Python 实现的 MySQL 客户端，可以用于连接和操作 MySQL 数据库。它提供了一个 Pythonic 的 API，使得在 Python
中操作 MySQL 数据库变得更加简单和方便。

PyMySQL 支持 Python 2.7 和 Python 3.x 版本，并且可以在 Linux、Windows、Mac OS X 等多种操作系统上运行。它还支持多种 MySQL
服务器版本，包括 MySQL 5.5、MySQL 5.6、MySQL 5.7、MySQL 8.0 和 MariaDB 等。

使用 PyMySQL，你可以执行 SQL 查询、插入、更新和删除操作，还可以创建和管理数据库、表和索引等。此外，PyMySQL
还提供了一些高级功能，如事务处理、连接池和游标等，可以帮助你更好地管理和优化数据库操作。

## 准备

### 安装 PyMySQL

PyMySQL 非 Python 官方包， 需要安装

```
pip install pymysql
```

### 数据库准备

1. 数据库服务 IP地址 (本机地址 `127.0.0.1` 或者 `localhost`)
2. 数据库服务 端口（3306）
3. 数据库服务 管理员用户名
4. 数据库服务 管理员密码
5. 数据库服务 数据库名字

### 导入 pymysql

PyMySQL 非 Python 官方包， 需要导入

```python
import pymysql
```

## 一般操作步骤

1. 连接 MySQL 数据库
2. 创建游标对象
3. 准备 SQL 语句
4. 执行 SQL 语句
5. 解析结果
6. 关闭游标和连接


1 连接 MySQL 数据库

```python
connect = pymysql.connect(
    host="localhost",
    port=3306,
    user="root",
    password="123456",
    db="ad",
    cursorclass=DictCursor
)
```

2 创建游标对象

```python
cursor = connect.cursor()
```

3 准备 SQL 语句

```python
sql = ""
```

4 执行 SQL 语句

```python
cursor.execute(sql)
```

5 解析结果

```python
# 不同的SQL操作，解析结果的方法也不同， 需要灵活变通
```

6 关闭游标和连接

```python
cursor.close()
connect.close()
```

## DDL 操作

数据库DDL（Data Definition Language）是用于描述数据库中要存储的现实世界实体的语言。

举例：

1. 数据库相关的操作，比如： 创建数据库、删除数据库 等
2. 数据标相关操作， 比如： 创建数据表、删除数据表、修改数据表 等

## DML 操作

数据库DML（Data Manipulation Language）是用于在数据库中添加、修改和删除数据的语言。它是SQL语言的一个子集，主要用于对表中的数据进行操作。通过DML，用户可以插入新数据、更新已有数据或删除不需要的数据。常见的DML操作包括INSERT、UPDATE和DELETE命令。

- INSERT 命令用于向表中插入新的数据记录。 
- UPDATE 命令用于修改表中已有的数据记录。 
- DELETE 命令用于删除表中的数据记录。

这些命令可以通过WHERE子句来指定要操作的特定记录，如果不指定WHERE子句，则会对表中的所有记录进行操作。在使用DML进行数据操作时，务必谨慎并确保备份数据以防止意外修改或删除。


## 结果解析

### DDL 操作


### DML 操作

#### Insert 添加解析


#### Select 查询解析


#### Update 更新解析


#### Delete 删除解析




















