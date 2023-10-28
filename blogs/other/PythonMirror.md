---
title: Python 配置 Pip 镜像
date: 2023/10/28
categories:
 - other
---

## 配置镜像命令

以 豆瓣 为例

```shell
pip config set global.index-url https://pypi.douban.com/simple/
pip config set install.trusted-host pypi.douban.com
```

注： 没有百分百完整的镜像， 当镜像出现问题时， 应该尝试切换镜像；如果尝试所有的镜像仍无法解决， 可切换到官方仓库


官方仓库地址

```
https://pypi.org/simple
```


## 国内常见的镜像

1.1 清华大学

```
https://pypi.tuna.tsinghua.edu.cn/simple
```

1.2 阿里云

```
https://mirrors.aliyun.com/pypi/simple/
```

1.3 网易

```
https://mirrors.163.com/pypi/simple/
```

1.4 豆瓣

```
https://pypi.douban.com/simple/
```

1.5 百度云

```
https://mirror.baidu.com/pypi/simple/
```

1.6 中科大（速度较快，但完全度不如前面几个镜像源）

```
https://pypi.mirrors.ustc.edu.cn/simple/
```

1.7 华为云（完全度和速度均中等）

```
https://mirrors.huaweicloud.com/repository/pypi/simple/
```
1.8 腾讯云（速度一般，完全度也一般）

```
https://mirrors.cloud.tencent.com/pypi/simple/
```


