---
title: "Docker"
date: 2024-10-20 17:06:15
tags:
    - Linux
sticky: 900
---

Docker 是一个开源平台，通过容器技术简化应用程序的开发、运输和部署。它将应用及其依赖打包在一个轻量级的容器中，确保在任何环境中一致运行。Docker 提供高效的资源利用和快速启动时间，同时增强了应用隔离和安全性。广泛应用于开发测试、微服务架构和持续集成/持续部署 (CI/CD) 等场景，Docker 大幅提高了开发效率和部署的一致性。

<!-- more -->

## 不同发行版

###  APT

安装 Docker

```bash
sudo apt install -y docker.io
```

解决 sudo 权限问题（重新登录用户生效）

```bash
sudo usermod -aG docker $USER
```

### DNF

安装 docker

```bash
sudo dnf install docker 
```

开机自启动 docker

```
sudo systemctl enable docker.service 
```

启动 docker

```
sudo systemctl start docker.service 
```

解决 sudo 权限问题（重新登录用户生效）

```bash
sudo usermod -aG docker $USER
```


## 镜像配置

[Docker/DockerHub 国内镜像源/加速列表-长期维护](https://xuanyuan.me/blog/archives/1154)

```bash
# 创建配置文件目录
sudo mkdir -p /etc/docker
# 创建配置文件
sudo tee /etc/docker/daemon.json <<EOF
{
    "registry-mirrors": [
        "https://dockerproxy.cn",
        "https://docker.rainbond.cc",
        "https://docker.udayun.com",
        "https://docker.211678.top"
    ]
}
EOF
# 重启服务
sudo systemctl daemon-reload
sudo systemctl restart docker
```

## 