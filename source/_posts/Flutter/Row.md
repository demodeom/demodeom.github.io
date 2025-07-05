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

# Row

Row 组件，主轴方向 水平，

## 主轴

**mainAxisAlignment** 设置主轴上元素的对齐方式，

- **MainAxisAlignment.start**
- **MainAxisAlignment.end**
- **MainAxisAlignment.center** 居中
- **MainAxisAlignment.spaceBetween** 两端对齐
- **MainAxisAlignment.spaceAround**
- **MainAxisAlignment.spaceEvenly**

```dart
Row(
    mainAxisAlignment: MainAxisAlignment.spaceBetween,
    children: [
        Container(width: 50,height: 50,decoration: BoxDecoration(color: Colors.red,),),
        Container(width: 50,height: 50,decoration: BoxDecoration(color: Colors.orange,),),
        Container(width: 50,height: 50,decoration: BoxDecoration(color: Colors.yellow,),),
        Container(width: 50,height: 50,decoration: BoxDecoration(color: Colors.green,),),
    ],
),
```

## 交叉轴

交叉轴垂直于主轴

**crossAxisAlignment** 设置交叉轴对齐方式

- **CrossAxisAlignment.start** 对齐起点
- **CrossAxisAlignment.end** 对齐重点
- **CrossAxisAlignment.center** 居中
- **CrossAxisAlignment.stretch** 拉伸

```
Row(
    mainAxisAlignment: MainAxisAlignment.spaceBetween,
    crossAxisAlignment: CrossAxisAlignment.stretch,
    children: [
        Container(width: 50,height: 50,decoration: BoxDecoration(color: Colors.red,),),
        Container(width: 50,height: 50,decoration: BoxDecoration(color: Colors.orange,),),
        Container(width: 50,height: 50,decoration: BoxDecoration(color: Colors.yellow,),),
        Container(width: 50,height: 50,decoration: BoxDecoration(color: Colors.green,),),
    ],
),
```

## 扩展

Row 组件不支持换行，所以子元素的宽度设计好，不能超溢出
