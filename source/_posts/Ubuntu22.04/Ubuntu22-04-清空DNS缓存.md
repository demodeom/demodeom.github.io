---
title: Ubuntu22.04 DNS缓存
date: 2022-05-21 21:46:51
tags:
  - Ubuntu22.04
cover: https://blog.image.codedemo.vip/Ubuntu22.04%2Fdomain_name_system-1080x582.jpg
---

Ubuntu22.04 查看 Dns 缓存、清空DNS缓存

<!-- more -->

## 查看缓存


`resolvectl statistics` 查看缓存

```
DNSSEC supported by current servers: no

Transactions              
Current Transactions: 0
  Total Transactions: 7373
                          
Cache                     
  Current Cache Size: 1
          Cache Hits: 3674
        Cache Misses: 3706
                          
DNSSEC Verdicts           
              Secure: 0
            Insecure: 0
               Bogus: 0
       Indeterminate: 0
```

## 清空缓存

`resolvectl flush-caches` 查看缓存


## 重置


`resolvectl reset-statistics`