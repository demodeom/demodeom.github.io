---
title: Flutter组件
date: 2024-11-09 15:31:41
tags:
	- Flutter
categories:
  - Flutter
---

Flutter组件

<!-- more -->

# Text

## 基本使用

```dart
Text("This is page Text 2.")
```

| 属性              | 值数据类型    | 属性描述                   |
| ----------------- | ------------- | -------------------------- |
| **style**         | TextStyle     | 文本样式                   |
| **maxLines**      | int           | 文本显示行数               |
| **overflow**      | TextOverflow  | 多行文本，超出部分截断方式 |
| **textDirection** | TextDirection | 文本方向                   |
| **textAlign**     | TextAlign     | 文本对齐方式               |

文本方向(TextDirection)(不常用)

- TextDirection.ltr
- TextDirection.rtl

文本对齐方式(textAlign)(不常用，不好用)

- TextAlign.right
- TextAlign.center
- TextAlign.left

文本截断方式(overflow)(了解)

- TextOverflow.ellipsis
- TextOverflow.clip
- TextOverflow.fade
- TextOverflow.visible

```dart
 @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text("Flutter Example"),
      ),
      body: Text(
        "初从文，三年不中；改习武，校场发一矢，中鼓吏，逐之出；又从商，一遇骗，二遇盗，三遇匪；遂躬耕，一岁大旱，一岁大涝，一岁飞蝗；乃学医，有所成。自撰一良方，服之，卒。遂至地府，久候阎王升堂，不耐，问之，鬼卒曰：王阅足下卷宗，狂笑，休克于后堂，未醒",
        maxLines: 2,
        overflow: TextOverflow.fade,
      ),
    );
  }
```

## 文本样式

### TextStyle 属性

使用 style 属性设置文本样式， 文本样式封装在 TextStyle 类中

| 属性                | 值数据类型          | 属性描述                    |
| ------------------- | ------------------- | --------------------------- |
| **style.color**     | Color               | 文本颜色                    |
| **fontSize**        | Color               | 字体大小                    |
| **fontWeight**      | **FontWeight**      | 字体粗细(100-900)           |
| **wordSpacing**     | double              | 单词间距                    |
| **letterSpacing**   | double              | 字母间距（英文）            |
| **backgroundColor** | Color               | 文本背景颜色                |
| **decoration**      | **TextDecoration**  | 文本装饰                    |
| **decorationColor** | Color               | 装饰线的颜色                |
| **decorationStyle** | TextDecorationStyle | 装饰线的样式                |
| decorationThickness | double              | 装饰线粗细                  |
| letterSpacing       | double              | 设置字母之间的间距          |
| wordSpacing         | double              | 设置单词之间的间距          |
| **fontFamily**      | string              | 字体 名字（微软雅黑、宋体） |

字体粗细(FontWeight)(100-900)

- **FontWeight.bold** 加粗
- **FontWeight.normal**
- **FontWeight.w100**
- **FontWeight.w200**
- ...

文本装饰(TextDecoration)

- **TextDecoration.lineThrough** 贯穿线
- **TextDecoration.underline** 下划线
- **TextDecoration.overline** 上划线

装饰线的样式(TextDecorationStyle)

- **TextDecorationStyle.solid**
- **TextDecorationStyle.double**
- **TextDecorationStyle.dashed**
- **TextDecorationStyle.dotted**
- **TextDecorationStyle.wavy**

```Dart
Text(
    "这是一段文本.",
    style: TextStyle(
      color: Colors.red,
      fontSize: 40,
      fontWeight: FontWeight.w400,
      backgroundColor: Colors.yellow,
      decoration: TextDecoration.lineThrough,
      // decoration: TextDecoration.underline,
      // decoration: TextDecoration.overline,
      decorationColor: Colors.green,
      // decorationStyle: TextDecorationStyle.solid
      // decorationStyle: TextDecorationStyle.double
      // decorationStyle: TextDecorationStyle.dashed
      // decorationStyle: TextDecorationStyle.dotted
      decorationStyle: TextDecorationStyle.wavy,
      decorationThickness: 1,
      letterSpacing: 5,
      wordSpacing: 10,
      fontFamily: "中國龍毛隸書"
    ),
    // textAlign: TextAlign.center,
    textAlign: TextAlign.left,
    // textAlign: TextAlign.right,
    // maxLines: 3,
    // overflow: TextOverflow.ellipsis,
    // overflow: TextOverflow.clip,
    // overflow: TextOverflow.fade,
    // overflow: TextOverflow.visible,
    // textDirection: TextDirection.ltr,
    // textDirection: TextDirection.rtl,
  ),
```

### 字体使用

字体下载网站 [https://ztxz.org.cn/](https://ztxz.org.cn/)

创建目录 assets/fonts 目录
将下载的 ttf 字体文件， 放到 assets/fonts 目录

修改 pubspec.yaml 文件， 将字体添加进入

```yaml
flutter:
  fonts:
    - family: "中國龍毛隸書"
      fonts:
        - asset: "assets/fonts/中國龍毛隸書.ttf"
```

使用

```
Text("这是一段文本",style: TextStyle(
    fontFamily: "中國龍毛隸書"
))
```
