---
title: Java - 面向对象
date: 2022-10-07 04:39:41
tags:
    - Java
---

Java 面向对象

<!-- more -->


## 基础

### 定义类

定义 `Student` 类

```java
class Student
{

}
```

### 实例化对象

```java
Student stu1 = Student();
```

### 定义类属性

```java
class Student
{
    public String name;
    public int age;
}
```

### 如何设置属性值

1. 定义设置属性值的方法
1. 定义访问属性值的方法

```java
class Student
{
    public String name;
    public int age;
    // 定义设置属性值的方法
    public void setName(String name) {
        this.name = name;
    }
    public void setAge(int age) {
        this.age = age;
    }
    // 定义访问属性值的方法
    public String getName() {
        return name;
    }
    public int getAge() {
        return age;
    }
}
```

通过对象设置属性值

```java
Student stu1 = new Student();
stu1.name = "Zhang San";
stu1.age = 18;
```

通过对象访问属性值

```java
Student stu1 = new Student();
stu1.name = "Zhang San";
stu1.age = 18;
System.out.println("Name: " + stu1.name + ", Age: " + stu1.age);
```

### 定义方法

定义方法

```java
public class Student {
    
    public void info()
    {
        System.out.println("Name: ZhangSan; Age: 18");
    }
}
```

### 调用方法

通过对象调用方法

```java
Student stu1 = new Student();
stu1.info();
```

在类的内部调用内部方法

```java
public class Student {
    
    public void info()
    {
        this.fun1();
        System.out.println("Name: ZhangSan; Age: 18");
    }

    public void fun1()
    {
        System.out.println("fun1 被调用了");
    }
}
```

### 类内部访问属性

```java
public class Student {

    // 此处省略 属性定义

    public void info()
    {
        System.out.println("Name: " + this.name + "; Age: " + this.age);
    }
}
```

```java
Student stu2 = new Student();
stu2.name = "Li Si";
stu2.age = 20;
stu2.info();
```

### 类内部设置属性

```java
public class Student {

    // 此处省略 属性定义

    public void info(String name, int age)
    {
        this.name = name;
        this.age = age;
        System.out.println("Name: " + this.name + "; Age: " + this.age);
    }
}
```


```java
Student stu2 = new Student();
stu2.info("Li Si", 20);
```

### 同名方法自动匹配

系统会根据参数， 自动调用对应的方法

```java
public class Student {
    
    // 此处省略 属性定义
    public void info(String name, int age)
    {
        this.name = name;
        this.age = age;
        System.out.println("Name: " + this.name + "; Age: " + this.age);
    }
    public void info()
    {
        System.out.println("Name: " + this.name + "; Age: " + this.age);
    }
}
```

```java
Student stu1 = new Student();
stu1.name = "Zhang San";
stu1.age = 18;
stu1.info();

Student stu2 = new Student();
stu2.info("Li Si", 20);
```

### 补充知识：如何找到类

设置CLASSPATH变量的目的就是让Java执行环境找到指定的Java程序对应的class文件以及程序中引用的其他class文件

```java
.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
```

