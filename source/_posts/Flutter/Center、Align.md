# 排列方向

并非所有组件都像 Container 组件一样，提供了相应的属性可以设置子元素对齐方式

## Center

Center 组件可以让子元素在水平方向和垂直方向同时居中

```dart
Center(
    child: Text("Hello World")
),
```

## Align

Align 组件提供了 alignment 属性设置子元素排列方向， 可用值

- Alignment.topLeft 垂直方向靠顶部对齐，水平方向靠近左边对齐
- Alignment.topCenter 垂直方向靠顶部对齐，水平方向居中对齐
- Alignment.topRight 垂直方向靠顶部对齐，水平方向靠近右边对齐

- Alignment.centerLeft 垂直方向居中对齐，水平方向靠近左边对齐
- Alignment.center 垂直方向居中对齐，水平方向居中对齐
- Alignment.centerRight 垂直方向居中对齐，水平方向靠近右边对齐

- Alignment.bottomLeft 垂直方向靠底部对齐，水平方向靠近左边对齐
- Alignment.bottomCenter 垂直方向靠底部对齐，水平方向居中对齐
- Alignment.bottomRight 垂直方向靠底部对齐，水平方向靠近右边对齐

```dart
Align(
    alignment: Alignment.topRight,
    child: Text("Hello Text"),
)
```

