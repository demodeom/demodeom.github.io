# Flutter组件列表

Flutter 3 提供了丰富的组件库，用于构建跨平台的应用程序。以下是一些主要的组件分类及其示例：

### 1. **基础组件**
   - `Text`: 显示文本。
   - `Row`, `Column`: 用于水平和垂直布局。
   - `Container`: 用于装饰、定位和尺寸控制。
   - `Padding`: 添加内边距。
   - `Center`: 将子组件居中。
   - `Align`: 对齐子组件。
   - `Stack`: 用于叠加多个组件。
   - `Expanded`, `Flexible`: 用于灵活布局。
   - `SizedBox`: 固定尺寸的盒子。
   - `Spacer`: 用于在布局中创建空间。

### 2. **Material Design 组件**
   - `AppBar`: 应用栏。
   - `Scaffold`: 页面骨架。
   - `FloatingActionButton`: 浮动按钮。
   - `Drawer`: 侧边抽屉。
   - `BottomNavigationBar`: 底部导航栏。
   - `TabBar`, `TabBarView`: 选项卡。
   - `Card`: 卡片布局。
   - `ListTile`: 列表项。
   - `Icon`: 图标。
   - `IconButton`: 图标按钮。
   - `Button` (如 `ElevatedButton`, `TextButton`, `OutlinedButton`): 按钮。
   - `TextField`: 文本输入框。
   - `Checkbox`, `Radio`, `Switch`: 选择控件。
   - `Slider`: 滑块。
   - `Dialog`, `AlertDialog`, `SimpleDialog`: 对话框。
   - `SnackBar`: 底部提示条。
   - `BottomSheet`: 底部弹出面板。

### 3. **Cupertino (iOS风格) 组件**
   - `CupertinoApp`: iOS风格的应用。
   - `CupertinoButton`: iOS风格的按钮。
   - `CupertinoNavigationBar`: iOS风格的导航栏。
   - `CupertinoTabBar`: iOS风格的标签栏。
   - `CupertinoTextField`: iOS风格的文本输入框。
   - `CupertinoPicker`: iOS风格的选择器。
   - `CupertinoDatePicker`: iOS风格的日期选择器。
   - `CupertinoAlertDialog`: iOS风格的警告对话框。

### 4. **布局组件**
   - `ListView`: 可滚动的列表。
   - `GridView`: 网格布局。
   - `Table`: 表格布局。
   - `Wrap`: 自动换行布局。
   - `Flow`: 自定义流式布局。
   - `CustomScrollView`: 自定义滚动视图。
   - `SingleChildScrollView`: 单子组件的滚动视图。
   - `PageView`: 分页视图。

### 5. **动画和过渡组件**
   - `AnimatedContainer`: 动画容器。
   - `AnimatedOpacity`: 动画透明度。
   - `Hero`: 页面间共享元素过渡。
   - `AnimatedBuilder`: 自定义动画构建器。
   - `TweenAnimationBuilder`: 补间动画构建器。
   - `FadeTransition`: 淡入淡出过渡。
   - `ScaleTransition`: 缩放过渡。
   - `RotationTransition`: 旋转过渡。

### 6. **交互组件**
   - `GestureDetector`: 手势检测。
   - `InkWell`: 水波纹效果。
   - `Dismissible`: 可滑动删除的组件。
   - `Draggable`, `DragTarget`: 拖拽交互。
   - `LongPressDraggable`: 长按拖拽。
   - `InteractiveViewer`: 可缩放和拖拽的视图。

### 7. **绘图和效果组件**
   - `CustomPaint`: 自定义绘制。
   - `ClipRRect`: 圆角裁剪。
   - `ClipOval`: 椭圆裁剪。
   - `ClipPath`: 路径裁剪。
   - `DecoratedBox`: 装饰盒子。
   - `Transform`: 变换效果。
   - `Opacity`: 透明度控制。
   - `ShaderMask`: 着色器遮罩。

### 8. **异步和状态管理组件**
   - `FutureBuilder`: 异步数据构建器。
   - `StreamBuilder`: 流数据构建器。
   - `ValueListenableBuilder`: 值监听构建器。
   - `AnimatedSwitcher`: 组件切换动画。
   - `Overlay`: 覆盖层。

### 9. **平台和系统集成组件**
   - `SafeArea`: 安全区域。
   - `Platform`: 平台检测。
   - `MediaQuery`: 媒体查询。
   - `OrientationBuilder`: 方向检测。
   - `LayoutBuilder`: 布局约束检测。

### 10. **高级组件**
   - `IndexedStack`: 索引堆栈。
   - `Visibility`: 控制组件可见性。
   - `AbsorbPointer`: 吸收指针事件。
   - `IgnorePointer`: 忽略指针事件。
   - `BackdropFilter`: 背景滤镜。
   - `ShaderMask`: 着色器遮罩。

### 11. **Web 和桌面专用组件**
   - `MouseRegion`: 鼠标区域检测。
   - `Tooltip`: 工具提示。
   - `FocusScope`: 焦点管理。
   - `Shortcuts`: 快捷键支持。
   - `Actions`: 动作管理。

### 12. **插件和第三方集成**
   - `WebView`: 网页视图。
   - `Map`: 地图集成。
   - `Camera`: 相机集成。
   - `VideoPlayer`: 视频播放器。
   - `AudioPlayer`: 音频播放器。

### 13. **测试和调试组件**
   - `Semantics`: 语义化标签。
   - `DebugPaintSizeEnabled`: 调试绘制大小。
   - `DebugPaintPointersEnabled`: 调试指针事件。

### 14. **其他**
   - `RichText`: 富文本。
   - `Spacer`: 间距。
   - `Divider`: 分割线。
   - `CircularProgressIndicator`: 圆形进度条。
   - `LinearProgressIndicator`: 线性进度条。

这些组件是 Flutter 3 中常用的部分，Flutter 的组件库非常庞大且灵活，开发者可以根据需求组合和自定义这些组件来构建复杂的用户界面。