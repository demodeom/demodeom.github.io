---
title: JetBrain 激活
date: 2022-05-09 13:41:10
tags: JetBrain
cover: https://blog.image.codedemo.vip/Ubuntu22.04%2F%E6%88%AA%E5%9B%BE%202022-05-25%2010-00-20.png
---

JetBrain 免费激活、免费获取激活码、免费激活码防检测

<!-- more -->


## 激活步骤

1. 下载 JaNetfilter
2. 配置 JaNetfilter
3. 下载免费激活码
4. 使用免费激活码激活IDE
5. 使用 JaNetfilter ， 防止免费激活码失效

注： 如果 `第4步` 提示激活码已经失效， 仍然可以通过断网的方式激活IDE，完成 `第5步` 之后， 恢复网络即可

## 获取激活码

免费激活码获取地址 [https://idea.medeming.com/idea/](https://idea.medeming.com/idea/)

## 免费激活码防检测

当一个激活码被多台设备激活时，激活码可能会失效，使用 JaNetfilter 防止免费激活码失效

### 下载 JaNetfilter

JaNetfilter 下载的地址 [https://github.com/ja-netfilter/ja-netfilter/releases](https://github.com/ja-netfilter/ja-netfilter/releases)

### 配置 JaNetfilter

修改文件 `ja-netfilter\config\dns.conf`， 添加以下内容

```
EQUAL,jetbrains.com
```

修改文件 `ja-netfilter\config\url.conf`， 添加以下内容

```
PREFIX,https://account.jetbrains.com/lservice/rpc/validateKey.action
```

### 使用 JaNetfilter

点击菜单 `help` -> `Edit Custom VM Options` 末尾添加

```
-javaagent:D:\GreenPackage\ja-netfilter\ja-netfilter.jar
```

`ja-netfilter.jar` 根据本地实际位置配置





