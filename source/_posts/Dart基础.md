---
title: Dart基础
date: 2024-11-11 19:49:35
tags:
---


<!-- more -->


# Dart 基础

## 安装

[https://docs.flutter.dev/community/china#download-flutter-archives-based-on-a-mirror-site](https://docs.flutter.dev/community/china#download-flutter-archives-based-on-a-mirror-site)

下载地址 [https://dart.dev/get-dart/archive](https://dart.dev/get-dart/archive)

环境变量配置

```bash
export DART_HOME=~/.local/share/Dart/dart-sdk-3.5.4 
export PATH=$PATH:$DART_HOME/bin
```

重启终端， 检查 dart 版本

```bash
dart --version
```

输出如下

```
Dart SDK version: 3.5.4 (stable) (Wed Oct 16 16:18:51 2024 +0000) on "linux_x64"
```



## Hello World

```dart
void main(List<String> args) {
  print("hello world");
}
```



## 注释

单行注释

```dart
// 1. 单行注释
// 2. 注释
```

多行注释

```dart
/*
	1. 第一行注释
	2. 第二行注释
*/
```

## 变量

使用 **var** 关键字定义变量， 会自动推断变量的数据类型

```dart
  var userName = "Zhang San";
```

也可以手动指定变量类型

```dart
  String userSex = "man";
```



**var** 和 **数据类型** 不能同时使用

使用 **var** 关键字， 不需要指定**数据类型**

使用**数据类型**定义变量， 不需要 **var** 关键字

## 命名规则

**必须遵守规则**

1. 变量名由数字、字母、下划线、美元符号**$** 组成， 不能以数字开头
2. 标识符不能是保留字和关键字
3. 变量名严格区分大小写， 比如 **age** 和 **Age** 是两个不同的变量

**开发规范**

变量名要有意义，变量名使用名词，方法名使用动词

正面的例子

```dart
String userName = "ZhangSan";
```

反面例子

```dart
String aa = "ZhangSan";
String ab = "man";
```



## 常量

**const** 定义常量，定义时必须赋值

```dart
const PI1 = 3.14;
const double PI2 = 3.14;
```

final 定义常量， 定义时可以不赋值，只能赋值一次

```dart
final PI3;
PI3 = 3.14;

final double PI4;
PI4 = 3.14;

final double PI5 = 3.14;
```

final 是惰性初始化的，只有在第一次使用前才初始化

## 数据类型

### 字符串

字符串类型， 使用 单引号 或者 双引号 包括的字符

多行字符串可以使用 三个 单引号 或者 三个双引号

```dart
String userName = "ZhangSan";
String userSex = 'man';
String userInfo = """
我的名字是 ZhangSan,
我今年 20 岁，
我在 XXXX 学校读书。
"""
```

### 数值类型

整数 int

```dart
int age = 18;
```

小数

```dart
double mathScore = 85.5;
```

### 布尔类型

```dart
bool isOK = true；
bool isHot = false；  
```

### List 列表

```dart
var list1 = ["张三", 18, false];

var list2 = <String>["ZhangSan", "LiSi"];

var list3 = [];
list3.add("value");

var list4 = List.filled(5, 0);

var list5 = List<String>.filled(5, "");
```

### Map 字典

```dart
var map1 = new Map();
map1["name"] = "张三";
map1["age"] = 18;
map1["sex"] = "男";
```

```dart
var map2 = {
    "name": "张三",
    "age": 18,
    "sex": "男",
};
```



```dart
 var userName = map2["name"];
```



### 数据类型转换

parse

```dart
var age = "18";
int userAge = int.parse(age);
```

## 运算符

算术运算符

```
+ 
- 
* 
/ 
~/ 取整
% 取余
```

关系元算符

```
==
!=
<
<=
>
>=
```

逻辑运算符

```
!
&&
||
```

赋值运算符

```
=
??=

+=
-=
*=
/=
%=
~/=
```



```
++
--
```



### 分支

```dart
var a = "3.14";
var b = 3.14;

if (a == b){
	print("相等");
}else{
	print("不相等");
}
```



```dart
if(){

}else if(){

}else{

}
```

### switch - case

```dart
var flag = 1;

switch (flag) {
    case 1:
        print("男");
        break;
    case 2:
        print("女");
        break;
    default:
        print("保密");
        break;
}
```

### for

```dart
for(var i=0; i<10; i++){
	print(i);
}
```



### while

```dart
var i = 1;
while(i< 10){
    print(i);
    i++;
}
```

### do while

```dart
var i = 1;
do{
    print(i);
    i++;
}while(i<10);
```

### continue

**continue** 可在 while  for do while 循环中使用

```
continue 跳过当此循环
```

### break

break 可以在 switch  while for 循环中使用

```
break 跳出(中止)循环
```





```dart
  var list1 = ["桃子", "苹果", "橘子"];

  for (var fruit in list1) {
    print(fruit);
  }
```



```dart
var list1 = ["桃子", "苹果", "橘子"];
list1.forEach((v){
    print(v);
});
```





```dart
  var map2 = {
    "name": "张三",
    "age": 18,
    "sex": "男",
  };
  map2.forEach((k, v){
    print("$k, $v");
  });
```

## 自定义方法

自定义方法基本格式

```
返回值类型 方法名 (参数1, 参数2, 参数3...){
	方法体
	return 返回值;
}
```



箭头函数

```

```

匿名函数

```

```

## 面向对象



```dart
class Person{
  String userName = "张三";
  int userAge = 18;

  void getInfo(){
    print("我的名字是 ${this.userName}， 我今年 ${this.userAge} 岁");
  }
}


void main(List<String> args) {
  var p1 = new Person();
  p1.getInfo();
}

```





```dart
class Person{
  String userName = "张三";
  int userAge = 18;
  
  Person(){
    print("构造方法");
  }
  
  void getInfo(){
    print("我的名字是 ${this.userName}， 我今年 ${this.userAge} 岁");
  }
}
```





```dart
class Person{
  String userName="";
  int userAge=0;

  Person(String userName, int userAge){
    this.userName = userName;
    this.userAge = userAge;
  }

  void getInfo(){
    print("我的名字是 ${this.userName}， 我今年 ${this.userAge} 岁");
  }
}
```



```dart
class Person{
  String userName="";
  int userAge=0;

  Person(this.userName, this.userAge);

  void getInfo(){
    print("我的名字是 ${this.userName}， 我今年 ${this.userAge} 岁");
  }
}
```



```dart
class Person{
  String userName="";
  int userAge=0;

  Person(this.userName, this.userAge);
  // 命名构造函数
  Person.userName(this.userName);
  Person.userAge(this.userAge);

  void getInfo(){
    print("我的名字是 ${this.userName}， 我今年 ${this.userAge} 岁");
  }
}


void main(List<String> args) {
  var p1 = new Person.userAge(18);
  p1.userName = "张三";
  p1.getInfo();
}
```



私有属性 `_`

私有方法 `_`

```dart
class Person{
  String _userName="";
  int userAge=0;

  Person(this.userName, this.userAge);
  // 命名构造函数
  Person.userName(this.userName);
  Person.userAge(this.userAge);

  void getInfo(){
    print("我的名字是 ${this.userName}， 我今年 ${this.userAge} 岁");
  }
}


void main(List<String> args) {
  var p1 = new Person.userAge(18);
  p1.userName = "张三";
  p1.getInfo();
}
```



静态属性， 静态方法

static

继承  extends

调用父类的构造方法 

```
super()
```

重写父类方法， **@override**

抽象类、多态、接口



