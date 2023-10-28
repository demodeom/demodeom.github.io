---
title: Pop OS 配置
date: 2023/10/02
tags:
 - datetime
categories:
 - Python
---

Python 语言中，日期时间操作类(datetime)放在 datetime 包中， 首先需要倒入包

```python
from datetime import datetime
```

## 获取本地日期时间(默认)

`datetime.now()` 获取本地的日期时间， 返回值类型 `datetime` 

```python
datetime_now = datetime.now()
print(datetime_now)
print(type(datetime_now))
```

输出如下

```
2023-10-02 13:30:28.254415
<class 'datetime.datetime'>
```

`2023-10-02 13:30:28.254415` 从做到右， 以此是 `年-月-日 时:分:秒.微秒`

## 获取 年、月、日、时间、分钟、那秒

当我们得到一个datetime类型的对象之后，可以通过 `year` `month` `day` `hour` `minute` `second` `microsecond` 属性来分别获取当前日期时间的 年、月、日、时、分、秒、微秒

```python
datetime_now = datetime.now()

year = datetime_now.year
month = datetime_now.month
day = datetime_now.day
hour = datetime_now.hour
minute = datetime_now.minute
second = datetime_now.second
microsecond = datetime_now.microsecond

weekday = datetime_now.weekday()


print("当前日期：{}".format(datetime_now))
print("当前年：{}".format(year))
print("当前月：{}".format(month))
print("当前日：{}".format(day))
print("当前时间：{}".format(hour))
print("当前分钟：{}".format(minute))
print("当前秒：{}".format(second))
print("当前微秒：{}".format(microsecond))

print("当前星期：{}".format(weekday))
```

冷知识： 

通过 `weekday()` 方法返回今天星期几， 例如 `2023-10-02` 是周一， 得到结果为 `0`， 这有点像数组的索引， `0` 代表 周一 


## 格式化日期时间

`2023-10-02 13:30:28.254415` 这是默认的时间日期格式

有些时候， 我们需要这样的格式 `2023/10/02 13:30:28`

有些时候， 我们只需要日期 `2023/10/02`


datetime 类提供 `strftime(fmt)` 方法来格式化日期时间， 参数为 字符串类型的格式模板

以  `2023/10/02` 格式为例

```python
# 获取当前的日期时间
datetime_now = datetime.now()

datetime_new = datetime_now.strftime("%Y/%m/%d")

print("当前日期时间：{}".format(datetime_now))
print("当前新格式日期时间：{}".format(datetime_new))
```

常用的格式化字符

- `%Y` 四位的年份， 比如： 2001, 2101
- `%m` 两位的月份， 比如： 01, 02, 03... 12
- `%d` 两位的日， 比如： 01, 02, 03... 31
- `%H` 两位的小时， 比如： 00, 02, 03... 24
- `%M` 两位的分钟， 比如： 00, 01, 02... 59
- `%S` 两位的秒， 比如： 00, 01, 02... 59 
- `%f` 六位的微秒， 比如： 000000, 000001, 000002... 999999 

## 构造日期时间

1 手动构造日期时间

```python
# 构造日期时间
dt1 = datetime(year=2020, month=12, day=1, hour=12, minute=2, second=32)
```

2 从字符串构造日期时间格式， 比如将 `2020/12/12 12:02:32`

```python
dt_str = "2020/12/12 12:02:32"
dt2 = datetime.strptime(dt_str, "%Y/%m/%d %H:%M:%S")
print(dt2.year)
```
























