# Container

常用的属性

|属性名|属性值的数据类型| 属性值举例                                                          |
| --------| --------------------|----------------------------------------------------------------|
|**width**|double| 容器的宽度                                                          |
|**height**|double| 容器的高度                                                          |
|**padding**|EdgeInsetsGeometry| 内边距,EdgeInsetsGeometry抽象类，由 EdgeInsets 实现                      |
|**margin**|EdgeInsetsGeometry| 外边距,EdgeInsetsGeometry抽象类，由 EdgeInsets 实现                      |
|**decoration**|Decoration| 容器装饰,Decoration抽象类， 由 BoxDecoration 实现，比如：背景颜色、背景图片、边框、圆角等 |
|**alignment**|AlignmentGeometry| 设置子元素对齐方式 |
|**child**|Widget| 子组件                                                            |

## 宽高

宽300， 高400

```dart
Container(
    width: 300,
    height: 400,
),
```

> 默认宽度和高度由父容器影响，比如：
>
> 1. 
>
> 

容器背景颜色默认是透明的，所有看不见； 通常使用背景颜色或者边框显示容器边界

## 装饰

### 背景颜色

```dart
Container(
    width: 300,
    height: 400,
    decoration: BoxDecoration(
    	color: Colors.red,
    ),
),
```



### 边框

**Border.all** 设置所有边框，**所有**代表 上、下、左、右

* color 设置边框颜色
* width 设置边框宽度
* style 设置边框样式，**BorderStyle.solid** 表示实线，默认边框样式就是实线， 可以不设置；除了实线，默认没有提供其它样式

```dart
Container(
    width: 300,
    height: 400,
    decoration: BoxDecoration(
    	color: Colors.red,
    	border: Border.all(
            color: Colors.black,
            width: 20,
            style: BorderStyle.solid,
        ),
    ),
),
```

### 边框圆角

**BorderRadius.all** 设置所有边的圆角

```dart
Container(
    width: 300,
    height: 400,
    decoration: BoxDecoration(
    	color: Colors.red,
    	border: Border.all(
            color: Colors.black,
            width: 20,
            style: BorderStyle.solid,
        ),
        borderRadius: BorderRadius.all(Radius.circular(20)),
    ),
),
```

圆形（宽高相等，圆角大小为宽高的一半）

```dart
Container(
    width: 300,
    height: 300,
    decoration: BoxDecoration(
    	color: Colors.red,
        borderRadius: BorderRadius.all(Radius.circular(150)),
    ),
),
```

椭圆（宽高不等），**Radius.elliptical** 设置椭圆，

```dart
Container(
    width: 300,
    height: 200,
    decoration: BoxDecoration(
    	color: Colors.red,
        borderRadius: BorderRadius.all(Radius.elliptical(150, 100)),
    ),
),
```

### 背景图片

```dart
Container(
    width: double.infinity,
    height: double.infinity,
    decoration: BoxDecoration(
        color: Colors.red,
        image: DecorationImage(
            image: NetworkImage(
                "https://s21.ax1x.com/2025/01/24/pEE9ToV.jpg",
            ),
            fit: BoxFit.cover
        ),
    ),
    child: Text("HelloFlutterHelloWorldHelloFlutterHelloWorld"),
),
```

## 外边距

```dart
Container(
    width: double.infinity,
    height: double.infinity,
    margin: EdgeInsets.all(30),
    decoration: BoxDecoration(
    	color: Colors.red,
    ),
    child: Text("HelloFlutterHelloWorldHelloFlutterHelloWorld"),
),
```

## 内边距

容器和子元素的距离

```dart
Container(
    width: 300,
    height: 100,
    padding: EdgeInsets.all(20),
    decoration: BoxDecoration(
    	color: Colors.red,
    ),
    child: Text("HelloFlutterHelloWorldHelloFlutterHelloWorld"),
),
```

## 扩展知识

### 宽高

容器的默认宽、高受到父容器影响

没有子元素的情况下，默认宽度和高度为父元素宽度和高度

```dart
Container(
    decoration: BoxDecoration(
        color: Colors.red,
        border: Border.all(
            color: Colors.black,
            width: 10,
            style: BorderStyle.solid,
        ),
        borderRadius: BorderRadius.circular(30),
    ),
),
```

如何有子元素， 容器宽高由子元素大小决定

```dart
Container(
    decoration: BoxDecoration(
        color: Colors.red,
        border: Border.all(
            color: Colors.black,
            width: 10,
            style: BorderStyle.solid,
        ),
        borderRadius: BorderRadius.circular(30),
    ),
    child: Text("data"),
),
```

固定的宽、高 , 比如： 宽300， 高400

```dart
Container(
    width: 300,
    height: 400,
    decoration: BoxDecoration(
        color: Colors.red,
        border: Border.all(
            color: Colors.black,
            width: 10,
            style: BorderStyle.solid,
        ),
        borderRadius: BorderRadius.circular(30),
    ),
    child: Text("data"),
),
```

如何设置 100% 的宽度或者高度，100%指 父元素的最大宽度或者高度，使用 **double.infinity** 代表 100%

```dart
Container(
    width: double.infinity,
    height: 400,
    decoration: BoxDecoration(
        color: Colors.red,
        border: Border.all(
            color: Colors.black,
            width: 10,
            style: BorderStyle.solid,
        ),
        borderRadius: BorderRadius.circular(30),
    ),
    child: Text("data"),
),
```

---

### 背景图片

网络图片使用 NetworkImage 类， 本地图片使用 AssetImage 类

**本地图片存储位置**： 通常放在 `assets/images`​ 目录下；`assets/images`​ 目录如果不存在，自己创建

本地图片需要在 **pubspec.yaml** 文件中添加配置

---

## 对齐方式

alignment 属性设置子元素对齐方式，类型为 AlignmentGeometry ；

AlignmentGeometry 类为抽象类。

Alignment 类继承了 AlignmentGeometry 抽象类，提供了常用的对齐方式

- Alignment.topLeft 垂直方向靠顶部对齐，水平方向靠近左边对齐
- Alignment.topCenter 垂直方向靠顶部对齐，水平方向居中对齐
- Alignment.topRight 垂直方向靠顶部对齐，水平方向靠近右边对齐

- Alignment.centerLeft 垂直方向居中对齐，水平方向靠近左边对齐
- Alignment.center 垂直方向居中对齐，水平方向居中对齐
- Alignment.centerRight 垂直方向居中对齐，水平方向靠近右边对齐

- Alignment.bottomLeft 垂直方向靠底部对齐，水平方向靠近左边对齐
- Alignment.bottomCenter 垂直方向靠底部对齐，水平方向居中对齐
- Alignment.bottomRight 垂直方向靠底部对齐，水平方向靠近右边对齐

****









