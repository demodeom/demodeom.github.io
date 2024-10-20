---
title: Sublime运行Java代码
date: 2024-09-08 11:45:34
tags:
---


Sublime运行Java代码

<!-- more -->


## Hello World

### 新建文件

新建 `HelloWorld.java`

```java
class HelloWorld
{
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

### 编译

编译生成 `class` 文件

```bash
javac HelloWorld.java
```

### 运行

```bash
java HelloWorld
```

## Sublime Text 4

### Linux

新建 `JavaRun.sublime-build` ， 内容如下

```json
{
    "cmd": ["javac", "$file_name","&&","java", "$file_base_name"],
    "file_regex": "^(...?):([0-9]):?([0-9]*)",
    "selector": "source.java",
    "shell": true
}
```





