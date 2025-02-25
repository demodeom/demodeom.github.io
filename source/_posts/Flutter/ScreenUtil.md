# ScreenUtil


不同的设备， 尺寸不同, 最简单适配方式是： 等比缩放

[flutter_screenutil](https://pub.dev/packages/flutter_screenutil/versions) 扩展包解决设备适配问题，使用简单方便

修改文件 **pubspec.yaml**， 添加扩展包

```yaml
dependencies:
	flutter_screenutil: ^5.9.3
```

修改 **MyApp** 类的 **build** 方法

修改前

```dart
@override
Widget build(BuildContext context) {
    return MaterialApp(
        title: 'Flutter Demo',
        home: MyHomePage(),
    );
}
```

修改后

```dart
@override
  Widget build(BuildContext context) {
    return ScreenUtilInit(
      designSize: const Size(375, 812),
      builder: (context, child) {
        return MaterialApp(
          title: 'Flutter Demo',
          home: MyHomePage(),
        );
      },
    );
  }
```

宽、高尺寸设置

```dart
Container(
    width: ScreenUtil().setWidth(375),
    height: ScreenUtil().setHeight(400),
    decoration: BoxDecoration(
    	color: Colors.red,
    ),
),
```
