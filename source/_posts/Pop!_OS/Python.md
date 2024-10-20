---
title: Python
date: 2024-10-20 17:47:17
tags:
---

Python 是一种广泛使用的高级编程语言，以其简洁的语法和强大的功能而闻名。它支持多种编程范式，包括面向对象、函数式和命令式编程，非常适合初学者和专业开发者。Python 拥有丰富的标准库和第三方模块，广泛应用于数据分析、人工智能、Web 开发、自动化脚本等领域。由于其强大的社区支持和持续的更新，Python 已成为科学计算和机器学习等热门领域的首选语言，受到越来越多开发者的青睐。

<!-- more -->

## Pyenv

Pyenv 是一个用于管理多个 Python 版本的命令行工具，允许用户轻松安装、切换和管理不同的 Python 版本。它支持全局和项目特定的版本管理，使得开发者能够根据需要在同一台机器上使用多个 Python 版本，避免版本冲突。通过简单的命令，用户可以安装新的 Python 版本、查看可用版本以及设置默认版本。Pyenv 提高了 Python 开发的灵活性，特别适合需要在不同项目中使用不同 Python 版本的开发者。

安装 Pyenv

```
curl https://pyenv.run | bash
```

编辑文件 ， 添加以下内容

```
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
```

生效

```
source ~/.zshrc
```

## 安装Python

安装 Python 构建依赖项

**Ubuntu/Debian/Mint:**

```bash
sudo apt update; sudo apt install build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev curl git \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```


```
mkdir ~/.pyenv/cache
cd ~/.pyenv/cache
wget https://mirrors.huaweicloud.com/python/3.10.14/Python-3.10.14.tar.xz
pyenv install 3.10.14
pyenv global 3.10.14
```


安装 Python, 以 Python 3.10 为例

```bash
pyenv install 3.10
```

配置 3.10 为默认版本

```bash
pyenv global 3.10
```

配置 pip 镜像为清华大学镜像

```bash
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
pip config set install.trusted-host pypi.tuna.tsinghua.edu.cn
```

### 