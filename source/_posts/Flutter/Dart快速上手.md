# Dart快速上手

## Hello World

创建 `HelloWorld.dart` 文件， 内容如下

```dart
void main(List<String> args) {
  print("Hello World");
}
```

运行代码：点击 **右键** ， 点击 **Run Code**

## 基础语法

### 结束符

使用分号`;`作为表达式结束符

```dart
void main(List<String> args) {
  print("Hello World");
  print("Hello Dart");
}
```

### 标识符

什么是标识符：变量名、常量名、函数名、类名、文件名等

Dart的命名规则:

1. 变量名称必须由数字、字母、下划线和美元符($)组成
2. 注意:标识符开头不能是数字
3. 标识符不能是保留字和关键字。
4. 变量的名字是区分大小写的如: age和Age是不同的变量。在实际的运用中,也建议,不要用一个
5. 标识符(变量名称)一定要见名思意 : 变量名称建议用名词，方法名称建议用动词

### 变量

定义方式1： `数据类型 变量名 = "变量初始值"`

```dart
String n1 = "Kunkun";
```

定义方式2：使用 var 关键字声明变量, 使用 var 关键字定义变量，自动推断变量数据类型

```dart
var n2 = "ZhangSan";
```

**var** 关键字和数据类型不能同时使用，以下是**错误例子**

```dart
// 错误的例子
var String n3 = "LiSi";
```

### 常量

**定义常量方式 1**：使用关键字 **const** 定义常量

```dart
const PI = 3.1415926;
```

**定义常量方式 2**：使用关键字 final 定义常量

```dart
final n1 = 3.1415926;
```

**final** 和 **const** 区别

```dart
// 报错 
// Const variables must be initialized with a constant value.
// Const 变量必须进行初始化的一个恒定值。
// const d1 =  DateTime.now();

// 正确
final d2 = DateTime.now();
```

final 定义常量， 定义时可以不赋值，只能赋值一次；final 是惰性初始化的，只有在第一次使用前才初始化



### 注释

```dart
// 单行注释


/*
	多行注释
*/
```

## 数据类型

### 字符串

1. 单引号包括的字符
2. 双引号包括的字符
3. 三引号包括的字符 (三引号定义的字符串可以跨行编写)

```dart
String s1 = "张三";
String s2 = 'LiSi';
String s3 = """KunKun""";
String s4 = '''
TianQi
''';
```

### 数值类型

- 整型 int
- 浮点型 float

```dart
int n1 = 12;
double n2 = 3.14159;
```

### 布尔类型

```dart
bool isRight = true;
bool isOk = false;
```

### 集合 List

```dart
// 允许不同数据类型的集合
var L1 = ["张三", 12, true];
var L2 = [];

// 只允许相同数据类型的集合
var L3 =<String> ["张三", "里斯", "田七"];
var L4 =<int> [18, 20, 30];

// 创建指定长度的集合，
// 参数1： 集合的长度
// 参数2： 默认填充的数据
// 数据类型根据填充值进行推断， 元素数据类型是固定的
var L5 = List.filled(5, 0);
```

### Map

```dart
var m1 = new Map();

var m2 = {
    "name": "张三",
    "age": 18,
    "sex": "man",
};
```



```dart
var map1 = new Map();
map1["name"] = "张三";
map1["age"] = 18;
map1["sex"] = "男";
```



```dart
 var userName = map2["name"];
```



### 类型转换

```dart
var age = "18";
int userAge = int.parse(age);
```

## 运算符

### 算术运算符

`+`、 `-`、 `*` 、`/`、`~/`、`%`

除法

```dart
print(3/2);  // 1.5
print(1/3);  // 0.3333333333333333
```

取整

```dart
print(10~/3);  // 3
```

取余

```dart
print(10%3);  // 1
```



### 关系运算符


`==`、 `!=`、 `<` 、`<=` 、`>` 、`>=`

### 逻辑运算符

`!`、 `&&`、 `||`

### 赋值运算符

`=` 、`+=`、`-=`、`*=`、`/=`、`%=`、`~/=`、`??=`

`++`、 `--`

## 分支



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



## 遍历

### List 遍历

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



### Map 遍历

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

## 面向对象

### 对象创建、实例化

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



### 构造函数

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

### 私有属性、方法

私有属性 `_`、私有方法 `_`

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



### 静态属性， 静态方法

static

### 继承

继承  extends

调用父类的构造方法

```
super()
```

重写父类方法， **@override**

抽象类、多态、接口
