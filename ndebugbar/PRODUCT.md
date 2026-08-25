# nDebugBar 组件描述

> 本文档是「nDebugBar」的详细描述，是 [PRODUCTS.md](../PRODUCTS.md)（产品目录，单一事实来源）下的一个子文档。
> 描述本组件时以本文档为准；如与目录总览冲突，以子文档详细内容为准，并同步修正目录。
>
> **类别**：开源组件 / 调试工具（**不是软件、不是游戏**，而是 UnboxLumen 自研并对外开源的 Android 调试面板组件库）。

---

## 1. 一句话定位

> **中文**：开箱即用的 Android 应用内调试面板。摇一摇唤出悬浮窗，日志、网络、沙盒、视图层级一站搞定。
> **English**: A drop-in Android in-app debug console. Shake to open a floating panel that surfaces logs, network traffic, sandbox files, and the view hierarchy — all without adb.

## 2. 基本信息

| 项目 | 内容 |
|------|------|
| 中文名 | nDebugBar |
| 英文名 / 英文代号 | nDebugBar / ndebugbar |
| 维护方 | UnboxLumen（独立软件与游戏开发工作室） |
| 类型 | **开源组件 / Android Library**（不属于终端软件、不属于游戏） |
| 平台 | Android |
| 最低系统 | Android 5.0+（minSdk 21，以源码为准） |
| 当前版本 | v1.0.0（待发布） |
| 安装包大小 | 不适用（作为 Library 嵌入宿主 App，宿主 debug 包实测约多 5–8 MB） |
| 开发语言 | 纯 Java（无 Kotlin 依赖） |
| 源码仓库 | https://github.com/unboxlumen/ndebugbar（公开仓库） |
| 许可 | **Apache License 2.0**（详见 [LICENSE](https://github.com/unboxlumen/ndebugbar/blob/main/LICENSE)） |

## 3. 关键事实（红线，写文案时必须先确认）

1. **不是软件、不是游戏**：nDebugBar 是一个开源 Android Library，**不能直接安装运行**。它通过 `debugImplementation` 嵌入到宿主 App，宿主 Release 包不包含它。
2. **开源、GPL-3.0**：与 UnboxLumen 主线产品（N 浏览器、N 文件、N 搜索）的闭源策略不同；nDebugBar 采用强 copyleft 的 GNU General Public License v3.0。任何修改并分发的版本必须同样以 GPL-3.0 发布（不兼容闭源商用整合）。
3. **首版来源**：从 N 浏览器（nbrowser）内嵌的 debugbar 模块抽出，剥离业务耦合后独立成仓（2026-08）。
4. **零业务耦合**：grep 验证 debugbar → app 反向引用 0 处；只有 `DebugBarBridge` 单向桥接。
5. **宿主集成方式**：推荐 `git submodule` 嵌入，或等将来发布 jitpack 后用 `debugImplementation 'com.unboxlumen:ndebugbar:X.Y.Z'`。

## 4. 可复用描述模板（按篇幅选用，中英双语）

### 4.1 Slogan（品牌口号）
- zh：开箱即用的 Android 应用内调试面板。
- en：Drop-in Android in-app debug console.

### 4.2 一句话（约 20 字）
- zh：UnboxLumen 出品的开源 Android 调试面板组件，摇一摇唤出，日志 / 网络 / 沙盒一站搞定。
- en：An open-source Android debug panel library by UnboxLumen. Shake to open. Logs, network, sandbox — all in one place.

### 4.3 短描述（约 50 字，卡片 / 列表用）
- zh：开箱即用的 Android 应用内调试面板，摇一摇唤出悬浮窗，日志 / 网络 / 沙盒 / 视图层级一站搞定。GPL-3.0 强 copyleft 开源。
- en：A drop-in Android in-app debug console. Shake to open a floating panel that surfaces logs, network traffic, sandbox files, and the view hierarchy. GPL-3.0 (strong copyleft).

### 4.4 标准描述（约 100 字，产品页 Hero 用）
- zh：nDebugBar 是一款开箱即用的 Android 应用内调试面板组件（GPL-3.0）。你只需 `debugImplementation` 一行，就能让 App 拥有摇一摇唤出的悬浮调试面板：实时日志镜像、WebView + OkHttp 网络检视、沙盒文件浏览器、SharedPreferences 与 SQLite 在线编辑、视图层级可视化、崩溃日志，以及动画倍速——所有功能都以悬浮窗呈现，调试时不必反复接 adb、跑 Android Studio。宿主 Release 包自动剥离，零负担。
- en：nDebugBar is a drop-in Android in-app debug console library (GPL-3.0). A single line of `debugImplementation` gives your app a shake-to-open floating debug panel: real-time log mirror, WebView + OkHttp network inspector, sandbox file browser, SharedPreferences and SQLite online editor, view hierarchy visualizer, crash log, and animation speed control — all without adb or Android Studio. Stripped automatically from your release builds, zero overhead.

### 4.5 长描述（约 250 字，详情页 / 应用商店 / GitHub README 用）
- zh：nDebugBar 是 UnboxLumen 出品的开源 Android 应用内调试面板组件（GPL-3.0）。它从 N 浏览器的内置调试模块演化而来，把"调试 App 自己"这件事做到极简：摇一摇唤出悬浮窗，所有调试能力一站搞定——应用内日志面板（按 tag / level 过滤，再也不用接 adb 也能看 logcat）、WebView + OkHttp 网络检视（请求体 / 响应体 / 状态码 / 耗时）、沙盒文件浏览器、SharedPreferences 与 SQLite 在线编辑、视图层级可视化与布局边界标注、崩溃日志自动捕获、动画倍速（0.5x → 10x 反射调整 `ValueAnimator.sDurationScale`）。技术栈保持极简：纯 Java，仅依赖 OkHttp + Material Components。集成只需一行 Gradle 依赖，配合宿主 `debugImplementation` 让 Release 包自动剥离——你的 release APK 不会因此变大，也不会被反编译暴露调试入口。请注意：GPL-3.0 是 copyleft 许可，若你打算将本库整合进闭源商用产品，需先与维护者联系获取商业授权。
- en：nDebugBar is an open-source Android in-app debug console library by UnboxLumen (GPL-3.0). It evolved from the built-in debug module of N Browser, and makes "debugging your own app" as simple as possible: shake to open the floating panel, all debugging capabilities in one place — in-app log panel with tag/level filtering (no more adb for logcat), WebView + OkHttp network inspector (request/response body, status, timing), sandbox file browser, SharedPreferences and SQLite online editor, view hierarchy visualizer with layout bounds overlay, auto-captured crash log, animation speed control (0.5x → 10x via reflection on `ValueAnimator.sDurationScale`). The tech stack stays minimal: pure Java with only OkHttp + Material Components. Integration is a single Gradle line, paired with the host's `debugImplementation` to automatically strip it from release builds — your release APK won't grow, and there's no debug backdoor exposed for reverse engineering. Note: GPL-3.0 is a strong copyleft license; if you intend to integrate this library into a closed-source commercial product, please contact the maintainers for a commercial licensing arrangement.

## 5. 核心功能清单

| # | 功能（中） | 功能（英） | 说明 |
|---|-----------|-----------|------|
| 1 | 日志镜像 | Logcat Mirror | 应用内日志面板，按 tag / level 过滤，免 adb |
| 2 | 网络检视 | Network Inspector | 全部 WebView + OkHttp 请求，含请求体 / 响应体 / 状态 / 耗时 |
| 3 | 沙盒文件 | Sandbox Files | 浏览 App 内部存储与 SharedPreferences 文件 |
| 4 | SP 编辑 | SharedPreferences Editor | 运行时查看 / 编辑 / 删除 SP 键 |
| 5 | SQLite 检视 | SQLite Inspector | 列表、查行、编辑单元格、运行自定义 SQL |
| 6 | 视图层级 | View Hierarchy | 点选高亮，dump 完整 UI 树 |
| 7 | 布局边界 | Layout Bounds | 一眼看清 padding / margin / 尺寸 |
| 8 | 崩溃日志 | Crash Log | 自动捕获未捕获异常，附完整堆栈 |
| 9 | 动画倍速 | Animation Speed | 反射改 `ValueAnimator.sDurationScale`（0.5x / 1x / 2x / 5x / 10x）|
| 10 | 摇一摇唤出 | Shake to Open | 加速度传感器触发，或代码手动调 |

## 6. 集成方式

### 6.1 git submodule（推荐，与 N 浏览器项目保持一致）

```bash
git submodule add https://github.com/unboxlumen/ndebugbar.git debugbar
```

宿主 `settings.gradle`：
```gradle
include ':debugbar'
project(':debugbar').projectDir = new File('debugbar')
```

宿主 `app/build.gradle`：
```gradle
debugImplementation project(':debugbar')
```

### 6.2 直接依赖（待 jitpack 发布后可用）
```gradle
debugImplementation 'com.unboxlumen:ndebugbar:1.0.0'
```

### 6.3 启用

在你的 `Application.onCreate()` 或 `MainActivity.onCreate()`：
```java
import com.unboxlumen.ndebugbar.DebugBar;

if (BuildConfig.DEBUG) {
    DebugBar.get().open();   // 立即显示
}
```

## 7. 技术规格

| 规格 | 内容 |
|------|------|
| 开发语言 | 纯 Java（Java 11，无 Kotlin） |
| 类型 | Android Library（`com.android.library`） |
| namespace | `com.unboxlumen.ndebugbar` |
| 最低系统 | minSdk 21（Android 5.0+） |
| 编译 / 目标 | compileSdk 36 / targetSdk 36 |
| 第三方依赖 | OkHttp 4.12.0 + Okio 3.9.0 + Material Components 1.12.0 + AndroidX（appcompat / recyclerview / coordinatorlayout）|
| 宿主集成 | `debugImplementation`（Release 包 R8 自动剥离）|
| 入口 API | `DebugBar.get().open() / .close() / .isOpen()` |
| 许可 | Apache License 2.0 |

## 8. 发布与更新

- **仓库**：https://github.com/unboxlumen/ndebugbar（公开）
- **分支策略**：`main` 为主分支，标签 `vX.Y.Z` 形式
- **版本号唯一来源**：仓库根 `build.gradle` 的 `defaultConfig.version`
- **发布通道**：当前仅 git submodule 嵌入；待版本稳定后接入 jitpack 自动构建
- **Host-side 同步**：N 浏览器项目通过 `git submodule update --remote ndebugbar` 拉取最新

## 9. 文案红线（写作时强制遵守）

1. **不得把 nDebugBar 描述为可下载的 App**（它是 Library，需嵌入宿主 App）。
2. **不得把它归类为"软件"或"游戏"**（它是组件，对应官网分类"组件 / 工具"）。
3. **不得隐去 GPL-3.0 许可**（开源项目必须明示 License；GPL 是 copyleft，闭源整合需要单独商业授权）。
4. **不得臆造不存在的能力**（功能列表须与本文档 §5 一致，或来自源码 `com.unboxlumen.ndebugbar.*` 包）。
5. 命名：中文「nDebugBar」/「N 调试面板」，英文「nDebugBar」/「ndebugbar」；维护方「UnboxLumen」。

---

## 关联文件

| 文件 | 用途 |
|------|------|
| `../PRODUCTS.md` | 产品目录（本文档的上级索引） |
| `index.html` | 官网组件页（本组件描述对应的网页） |
| 源码 https://github.com/unboxlumen/ndebugbar | nDebugBar 仓库（包名 `com.unboxlumen.ndebugbar`） |
| `docs/ndebugbar-extraction-2026-08.md` | 抽出背景与设计取舍（待补） |