---
title: Docker 快速体验Redis集群
date: 2022-05-09 20:04:52
tags: Redis
---

使用 Docker 快速搭建 RedisCluster

<!-- more -->

## 命令集合

```
#/bin/bash
docker volume create rv1
docker volume create rv2
docker volume create rv3
docker volume create rv4
docker volume create rv5
docker volume create rv6
docker run -d --name r1  -v rv1:/data -p 7000:6379 my-redis redis-server /usr/local/etc/redis/redis.conf
docker run -d --name r2  -v rv2:/data -p 7001:6379 my-redis redis-server /usr/local/etc/redis/redis.conf
docker run -d --name r3  -v rv3:/data -p 7002:6379 my-redis redis-server /usr/local/etc/redis/redis.conf
docker run -d --name r4  -v rv4:/data -p 7003:6379 my-redis redis-server /usr/local/etc/redis/redis.conf
docker run -d --name r5  -v rv5:/data -p 7004:6379 my-redis redis-server /usr/local/etc/redis/redis.conf
docker run -d --name r6  -v rv6:/data -p 7005:6379 my-redis redis-server /usr/local/etc/redis/redis.conf
redis-trib create --replicas 1 127.0.0.1:7000 127.0.0.1:7001 127.0.0.1:7002 127.0.0.1:7003 127.0.0.1:7004 127.0.0.1:7005
```

## 宿主环境准备

### 安装 Ruby

- Ruby

``` bash
sudo apt install ruby -y
```

- Ruby 操作 Redis 扩展

``` bash
sudo gem install redis
```

### 安装 Redis

- 下载 redis 源码

``` bash
wget  -O redis http://download.redis.io/releases/redis-4.0.10.tar.gz
```

- 安装 redis

``` bash
sudo apt install redis-server
```

- 全局配置 redis-trib.rb

```bash
sudo cp redis-4.0.10/src/redis-trib.rb /usr/local/bin/redis-trib
```

`redis-trib.rb` 脚本在 Redis 源码目录中 `src/redis-trib.rb`; 下载源码, 解压即可看到; 该脚本需要 Ruby 环境才能运行

## Redis 容器准备

### 构建镜像

- 创建 `redis` 目录

``` bash
➜  redis ll
total 64K
-rw-rw-r-- 1 master docker 117 Aug 27 00:11 Dockerfile
-rw-rw-r-- 1 master docker 58K Aug 27 01:24 redis.conf
```

- `Dockerfile` 内容如下

``` bash
FROM redis
COPY redis.conf /usr/local/etc/redis/redis.conf
CMD [ "redis-server", "/usr/local/etc/redis/redis.conf" ]
```

- `redis.conf` Redis 源码根目录下, 赋值过来即可; 修改一下配置

``` bash
bind *  # 默认是 127.0.0.1, 宿主主机无法连接容器
dir /data  # 设置工作目录
logfile "redis.log"  # 日志文件
appendonly yes  # AOF
cluster-enabled yes  # 集群相关配置
cluster-config-file nodes.conf
cluster-node-timeout 15000
```

- 构建镜像 `docker build -t "my-redis" .`

``` bash
➜  redis docker build -t "my-redis" .
Sending build context to Docker daemon  61.44kB
Step 1/3 : FROM redis
 ---> 4e8db158f18d
Step 2/3 : COPY redis.conf /usr/local/etc/redis/redis.conf
 ---> 3dcef99ead67
Step 3/3 : CMD [ "redis-server", "/usr/local/etc/redis/redis.conf" ]
 ---> Running in bab4385d0de9
Removing intermediate container bab4385d0de9
 ---> c12a593f887e
Successfully built c12a593f887e
Successfully tagged my-redis:latest
```

### 准备数据卷

- 创建 6 个数据卷

``` bash
docker volume create rv1
docker volume create rv2
docker volume create rv3
docker volume create rv4
docker volume create rv5
docker volume create rv6
```

- 查看数据卷在宿主机存储位置 `docker volume inspect {volume_name}`

``` bash
➜  redis docker volume inspect rv1
[
    {
        "CreatedAt": "2018-08-27T01:45:30+08:00",
        "Driver": "local",
        "Labels": null,
        "Mountpoint": "/var/lib/docker/volumes/rv1/_data",
        "Name": "rv1",
        "Options": {},
        "Scope": "local"
    }
]
➜  redis sudo ls -al /var/lib/docker/volumes
总用量 64
drwx------  8 root root  4096 8月  27 01:46 .
drwx--x--x 14 root root  4096 8月  26 16:19 ..
-rw-------  1 root root 65536 8月  27 01:46 metadata.db
drwxr-xr-x  3 root root  4096 8月  27 01:45 rv1
drwxr-xr-x  3 root root  4096 8月  27 01:46 rv2
drwxr-xr-x  3 root root  4096 8月  27 01:46 rv3
drwxr-xr-x  3 root root  4096 8月  27 01:46 rv4
drwxr-xr-x  3 root root  4096 8月  27 01:46 rv5
drwxr-xr-x  3 root root  4096 8月  27 01:46 rv6
```

### 创建 6 个 Redis 容器

```bash
docker run -d --name r1  -v rv1:/data -p 7000:6379 my-redis redis-server /usr/local/etc/redis/redis.conf
docker run -d --name r2  -v rv2:/data -p 7001:6379 my-redis redis-server /usr/local/etc/redis/redis.conf
docker run -d --name r3  -v rv3:/data -p 7002:6379 my-redis redis-server /usr/local/etc/redis/redis.conf
docker run -d --name r4  -v rv4:/data -p 7003:6379 my-redis redis-server /usr/local/etc/redis/redis.conf
docker run -d --name r5  -v rv5:/data -p 7004:6379 my-redis redis-server /usr/local/etc/redis/redis.conf
docker run -d --name r6  -v rv6:/data -p 7005:6379 my-redis redis-server /usr/local/etc/redis/redis.conf
```

- 查看运行的容器 `docker ps`

``` bash
➜  redis docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS              PORTS                    NAMES
7795de1e7a1e        my-redis            "docker-entrypoint.s…"   6 seconds ago        Up 6 seconds        0.0.0.0:7005->6379/tcp   r6
303d5e987013        my-redis            "docker-entrypoint.s…"   13 seconds ago       Up 12 seconds       0.0.0.0:7004->6379/tcp   r5
a7f160913b32        my-redis            "docker-entrypoint.s…"   20 seconds ago       Up 19 seconds       0.0.0.0:7003->6379/tcp   r4
09cb981113f3        my-redis            "docker-entrypoint.s…"   26 seconds ago       Up 26 seconds       0.0.0.0:7002->6379/tcp   r3
ff9ff317215e        my-redis            "docker-entrypoint.s…"   32 seconds ago       Up 31 seconds       0.0.0.0:7001->6379/tcp   r2
c35397911e6c        my-redis            "docker-entrypoint.s…"   About a minute ago   Up About a minute   0.0.0.0:7000->6379/tcp   r1
```

### 创建集群

``` bash
redis-trib create --replicas 1 127.0.0.1:7000 127.0.0.1:7001 127.0.0.1:7002 127.0.0.1:7003 127.0.0.1:7004 127.0.0.1:7005
```
