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

# Image

## 网络图片

**Image.network** 显示网络图片

```dart
Container(
    width: 300,
    height: 500,
    decoration: BoxDecoration(
        border: Border.all(
            color: Colors.black,
            width: 5,
        ),
    ),
    child: Image.network(
        "https://s21.ax1x.com/2025/01/24/pEE9ToV.jpg",
        fit: BoxFit.cover,
    ),
),
```

## 本地图片

1. 创建目录 **assets/images**， 将图片存放到此目录
2. 配置 **pubspec.yaml** 文件，添加图片

```yaml
flutter:
  assets:
    - assets/images/1.png
```

```dart
Container(
    width: 300,
    height: 500,
    decoration: BoxDecoration(
        border: Border.all(
            color: Colors.black,
            width: 5,
        ),
    ),
    child: Image.asset(
      "assets/images/1.png",
      fit: BoxFit.cover,
    ),
),
```

如果有 100 张图片，添加 100 次， 岂不是烦琐， 可以直接将目录添加到 pubspec.yaml 文件

```Dart
flutter:
  assets:
    - assets/images/
```

## 图标-Icon

可用图标列表预览 [https://fonts.google.com/icons](https://fonts.google.com/icons)

Flutter默认包含了一套Material Design的字体图标，在pubspec.yaml文件中的配置如下

```
flutter:
    uses-material-design: true
```

```dart
Icon(
    Icons.person,
    color: Colors.green,
    size: 50.sp,
),
```

| 属性  | 值数据类型 | 属性描述     |
| ----- | ---------- | ------------ |
| color | Color      | 设置图标颜色 |
| size  | double     | 设置图标大小 |

## 第三方图标-阿里云

### 阿里云矢量图

1. 创建项目
2. 将需要的图标添加到项目中
3. 下载项目， 即可得到 ttf 字体文件
4. 将字体文件复制到 assets/fonts 目录
5. 将字体文件路径添加到 pubspec.yaml 文件

```yaml
flutter:
  fonts:
    fonts:
      - asset: "assets/fonts/AliyunIconfont.ttf"
```

使用自定义图标

```
Icon(IconData(0xe600, fontFamily: "AliyunIconfont"), color: Colors.red,)
```

图标名字， 比如 `&#xe600;` 修改 `0xe600`
