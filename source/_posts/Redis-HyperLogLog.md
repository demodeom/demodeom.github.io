---
title: Redis-HyperLogLog
date: 2022-06-14 21:22:12
tags:
---

HyperLogLog

<!-- more -->

## 常用的指令

HyperLogLog是一种概率数据结构，用于对唯一事物进行计数（从技术上讲，这是指估计集合的基数）。通常，对唯一项目进行计数需要使用与要计数的项目数量成比例的内存量，因为您需要记住过去已经看到的元素，以避免多次对其进行计数。但是，有一组算法会以内存换取精度：以Redis实施为例，您得出的带有标准误差的估计度量最终会小于1％。该算法的神奇之处在于，您不再需要使用与计数的项目数量成比例的内存量，而是可以使用恒定数量的内存！在最坏的情况下为12k字节，如果您的HyperLogLog（从现在开始将它们称为HLL）看到的元素很少，则少得多。

Redis中的HLL尽管在技术上是不同的数据结构，但被编码为Redis字符串，因此您可以调用GET来序列化HLL，然后调用SET来将其反序列化回服务器。

从概念上讲，HLL API就像使用Set来执行相同的任务。您可以将每个观察到的元素添加到集合中，并使用SCARD检查集合中的元素数量，这是唯一的，因为SADD不会重新添加现有元素。



### PFADD

`PFADD key element [element ...]`

- 如果一个HyperLogLog的估计的近似基数在执行命令过程中发了变化，返回1，否则返回0
- 如果指定的key不存在，这个命令会自动创建一个空的HyperLogLog结构（指定长度和编码的字符串）
- 如果在调用该命令时仅提供变量名而不指定元素
    - 如果这个变量名存在，则不会有任何操作
    - 如果不存在，则会创建一个数据结构（返回1)


### PFCOUNT

`PFCOUNT key [key ...]`

- 当参数为一个key时,返回存储在HyperLogLog结构体的该变量的近似基数，如果该变量不存在,则返回0.
- 当参数为多个key时，返回这些HyperLogLog并集的近似基数，这个值是将所给定的所有key的HyperLoglog结构合并到一个临时的HyperLogLog结构中计算而得到的

注意: 这个命令的一个副作用是可能会导致HyperLogLog内部被更改，出于缓存的目的,它会用8字节的来记录最近一次计算得到基数,所以PFCOUNT命令在技术上是个写命令

### PFMERGE

`PFMERGE destkey sourcekey [sourcekey ...]`

将多个 HyperLogLog 合并（merge）为一个 HyperLogLog ， 合并后的 HyperLogLog 的基数接近于所有输入 HyperLogLog 的可见集合（observed set）的并集; 

合并得出的 HyperLogLog 会被储存在目标变量（第一个参数）里面， 如果该键并不存在， 那么命令在执行之前， 会先为该键创建一个空的.


这个命令只会返回 OK

## HyperLogLog 误差率测试

### 测试脚本

```python
from redis import Redis
test_level = [100, 500, 1000, 5000, 10000, 50000, 100000, 500000, 1000000]

set_key = "hyper_log_set"
hyper_log_key = "hyper_log_log"

r = Redis(host='127.0.0.1', port=6379)

for i in range(1, 1000001):
    set_num = r.scard(set_key)
    if set_num in test_level:
        hyper_log_num = r.pfcount(hyper_log_key)
        print(set_num, ':', hyper_log_num, ':', format(abs(hyper_log_num - set_num) / set_num * 100, '.2f'), ' %')
    r.sadd(set_key, i)
    r.pfadd(hyper_log_key, i)

r.close()
```

#### 测试结果

|Set|HyperLogLog|误差|
|:---|:---|:---|
|100 | 100 | 0.00%|
|500 | 503 | 0.60%|
|1000 | 1001 | 0.10%|
|5000 | 4985 | 0.30%|
|10000 | 9988 | 0.12%|
|50000 | 50353 | 0.71%|
|100000 | 99562 | 0.44%|
|500000 | 497953 | 0.41%|

