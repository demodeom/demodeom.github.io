# Win

Flutter 官方文档地址 [安装 Flutter SDK](https://docs.flutter.dev/get-started/install/windows/mobile)

## 系统要求

『 Flutter 系统要求 』[https://docs.flutter.dev/get-started/install/windows/mobile#verify-system-requirements](https://docs.flutter.dev/get-started/install/windows/mobile#verify-system-requirements)

### 硬件要求

你的 Windows Flutter 开发环境必须满足以下最低硬件要求。

| 要求                 |       最低        |       推荐        |
| :------------------- | :---------------: | :---------------: |
| x86_64 CPU 核心数    |         4         |         8         |
| 内存 (GB)            |         8         |        16         |
| 显示器分辨率（像素） | WXGA (1366 x 768) | FHD (1920 x 1080) |
| 可用磁盘空间 (GB)    |       11.0        |       60.0        |

### 软件要求

- 『Git for Windows』[https://git-scm.com/downloads/win](https://git-scm.com/downloads/win)
- 『Android Studio』[https://developer.android.com/studio/install#windows](https://developer.android.com/studio/install#windows)


### 下载 Flutter SDK

『 Flutter Sdk 下载地址 』 [https://docs.flutter.dev/release/archive#stable-channel](https://docs.flutter.dev/release/archive#stable-channel)


### 安装Flutter {id="flutter_1"}

1. 解压之后得到 **flutter** 目录
2. 创建 **C:\DevTools** 目录
3. 将 **flutter** 目录复制放到 **C:\DevTools** 目录

### 配置Flutter

1. **修改**系统环境变量Path，将目录 **C:\DevTools\flutter\bin** 添加到环境变量

国内镜像配置(一言难尽，失灵时不灵)

1. **新建**系统环境变量，变量名： **PUB_HOSTED_URL**， 变量值：**https://pub.flutter-io.cn**
2. 新建系统环境变量，变量名： **FLUTTER_STORAGE_BASE_URL**， 变量值：**https://storage.flutter-io.cn**


## 安装 AndroidStudio

1. 使用 **JetBrain ToolBox** 安装 **AndroidStudio**
2. 启动 **AndroidStudio**， 安装 **Android SDK**
3. 使用 **AndroidStudio** 安装 **Android SDK Command-line Tools**
4. 使用 **AndroidStudio**， 安装插件 **Flutter**、**Flutter Snippets**、**Dart**、**CodeGlance Pro**(可选)
5. 重启 **AndroidStudio**

配置

修改系统环境变量Path，添加路径 **%USERPROFILE%\AppData\Local\Android\Sdk\platform-tools**


### C++ 环境

Windows 运行 Flutter 需要 C++ 环境， 使用软件 Visual Studio 安装 C++ 环境

Visual Studio Community 下载地址 [https://visualstudio.microsoft.com/vs/community/](https://visualstudio.microsoft.com/vs/community/)

1. 下载、安装 Visual Studio Community
2. 安装时选择 **c++ 桌面**开发环境



```Bash
PS C:\Users\demodeom> flutter doctor
Flutter assets will be downloaded from https://storage.flutter-io.cn. Make sure you trust this source!
Doctor summary (to see all details, run flutter doctor -v):
[✓] Flutter (Channel stable, 3.29.0, on Microsoft Windows [版本 10.0.26100.1742], locale zh-CN)
[✓] Windows Version (Windows 11 or higher, 24H2, 2009)
[✓] Android toolchain - develop for Android devices (Android SDK version 35.0.1)
[✓] Chrome - develop for the web
[✓] Visual Studio - develop Windows apps (Visual Studio Community 2022 17.13.0)
[✓] Android Studio (version 2024.2)
[✓] Connected device (2 available)
[✓] Network resources

• No issues found!
```

## 创建项目

`flutter create 项目名`

项目名不允许使用中划线，使用下划线

```bash
flutter create flutter_example
```

【中国用户】 建议修改 `android\gradle\wrapper\gradle-wrapper.properties` 文件

将 `services.gradle.org/distributions` 修改为 `mirrors.cloud.tencent.com/gradle`

