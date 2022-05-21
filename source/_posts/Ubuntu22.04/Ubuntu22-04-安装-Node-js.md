---
title: Ubuntu22.04 安装 Node.js
date: 2022-05-21 21:54:18
tags:
	- Ubuntu22.04
---

 [Nvm](https://github.com/nvm-sh/nvm) 允许您通过命令行快速安装和使用不同版本的 Node.js 


<!-- more -->


## nvm


安装 nvm

```bash
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

编辑环境变量

```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

## 常用命令


- `nvm install --lts`  安装最新的长期支持版

- `nvm install 8.0.0` 安装指定版本的 Node.js

- `nvm use --lts`  使用最新的长期支持版

- `nvm alias default 8.1.0 `  设置默认的 Node.js 版本












