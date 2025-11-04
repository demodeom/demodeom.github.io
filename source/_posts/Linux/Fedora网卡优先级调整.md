---
title: Fedora网卡优先级调整
date: 2025-11-05 01:03:07
tags:
    - Linux
    - Fedora43
index_img: https://s21.ax1x.com/2025/10/02/pVT1Klq.png
---

Fedora网卡优先级调整

<!-- more -->


## 为什么要修改网卡优先级

有线网卡连接的本地局域网Nas(安全、传输速度快)
无线网卡连接的外网路由器，用于上网

默认情况下，有线网卡优先级高于无线网卡，导致访问 Internet。经常需要关闭、开启有线网卡。


## 修改网卡优先级





### 1. 找到Wi-Fi 和有线连接名称

使用以下命令，查看网络信息

```bash
nmcli connection show
```

输出如下
```
NAME             UUID                                  TYPE      DEVICE 
https://zi-m.cn  d20534a5-bf17-46d9-8c8a-0e21e79c5c02  wifi      wlp8s0 
有线连接 1       09082dee-ed4c-3d95-8284-1689c7d7d91b  ethernet  enp9s0 
lo               2e6b8060-314d-4f46-99c1-148f612ee82b  loopback  lo   
```

| 名称（NAME）    | 唯一标识（UUID）                     | 类型（TYPE） | 设备（DEVICE） |
| --------------- | ------------------------------------ | ------------ | -------------- |
| https://zi-m.cn | d20534a5-bf17-46d9-8c8a-0e21e79c5c02 | wifi         | wlp8s0         |
| 有线连接 1      | 09082dee-ed4c-3d95-8284-1689c7d7d91b | ethernet     | enp9s0         |

### 2. 查看优先级

使用以下命令，查看当前网络优先级

```bash
ip route show
```

输出如下

```
default via 192.168.66.1 dev enp9s0 proto dhcp src 192.168.66.144 metric 100 
default via 192.168.50.1 dev wlp8s0 proto dhcp src 192.168.50.130 metric 600 
192.168.50.0/24 dev wlp8s0 proto kernel scope link src 192.168.50.130 metric 600 
192.168.66.0/24 dev enp9s0 proto kernel scope link src 192.168.66.144 metric 100
```

| 默认网关 (via) | 接口 (dev) | 协议 (proto) | 源地址 (src)   | 优先级 (metric) |
| -------------- | ---------- | ------------ | -------------- | --------------- |
| 192.168.66.1   | enp9s0     | dhcp         | 192.168.66.144 | 100             |
| 192.168.50.1   | wlp8s0     | dhcp         | 192.168.50.130 | 600             |

### 3. 修改优先级

命令格式 `nmcli connection modify "网络名称" ipv4.route-metric 100`
命令格式 `nmcli connection modify "网络名称" ipv6.route-metric 100`


使用以下命令，修改优先级

```bash
# 设置 Wi-Fi 路由指标为 100（数值越小优先级越高）
# nmcli connection modify 网络名称 ipv4.route-metric 100
sudo nmcli connection modify "https://zi-m.cn" ipv4.route-metric 100
sudo nmcli connection modify "https://zi-m.cn" ipv6.route-metric 100

# 设置有线连接路由指标为 200
sudo nmcli connection modify "有线连接 1" ipv4.route-metric 600
sudo nmcli connection modify "有线连接 1" ipv6.route-metric 600
```



### 4. 应用修改（重启两个连接）

关闭网络 `nmcli connection down "网络名称"`
启动网络 `nmcli connection up "网络名称"`

```bash
sudo nmcli connection down "https://zi-m.cn"
sudo nmcli connection up "https://zi-m.cn"

sudo nmcli connection down "有线连接 1"
sudo nmcli connection up "有线连接 1"
```

### 5. 验证优先级是否改变

使用以下命令查看当前网络情况

```bash
ip route show
```

输出如下

```
default via 192.168.50.1 dev wlp8s0 proto dhcp src 192.168.50.130 metric 100 
default via 192.168.66.1 dev enp9s0 proto dhcp src 192.168.66.144 metric 600 
192.168.50.0/24 dev wlp8s0 proto kernel scope link src 192.168.50.130 metric 100 
192.168.66.0/24 dev enp9s0 proto kernel scope link src 192.168.66.144 metric 600 
```


| 默认网关 (via) | 接口 (dev) | 协议 (proto) | 源地址 (src)   | 优先级 (metric) |
| -------------- | ---------- | ------------ | -------------- | --------------- |
| 192.168.50.1   | wlp8s0     | dhcp         | 192.168.50.130 | 100             |
| 192.168.66.1   | enp9s0     | dhcp         | 192.168.66.144 | 600             |









