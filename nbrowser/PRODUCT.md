# N 浏览器（nBrowser）产品描述

> 本文档是「N 浏览器」的详细产品描述，是 [PRODUCTS.md](../PRODUCTS.md)（软件产品目录，单一事实来源）下的一个子文档。
> 描述本产品时以本文档为准；如与目录总览冲突，以子文档详细内容为准，并同步修正目录。

---

## 1. 一句话定位

> **中文**：轻量、可定制的安卓浏览器。系统 WebView，不捆绑引擎——装到手机上的，就是全部。
> **English**: A lightweight, customizable Android browser. Built on the system WebView with no bundled engine — what you install is all there is.

## 2. 基本信息

| 项目 | 内容 |
|------|------|
| 中文名 | N 浏览器 |
| 英文名 / 英文代号 | N Browser / nBrowser |
| 开发商 | UnboxLumen（独立软件与游戏开发工作室） |
| 类型 | **Android 移动端浏览器（应用）** |
| 平台 | Android |
| 最低系统 | Android 5.0+（minSdk 21，以源码为准） |
| 当前版本 | v0.0.9（versionCode 9 / versionName 0.0.9，见 app/build.gradle） |
| 安装包大小 | 约 1.9 MB（v0.0.9 release：1,982,198 B ≈ 1.89 MB，见 GitHub Release 实际附件） |
| 渲染内核 | 系统 WebView（**无捆绑浏览器引擎**） |
| 开发语言 | 纯 Java（无 Kotlin 依赖） |
| 第三方依赖 | 仅 ZXing core + AndroidX 官方库 |
| 分发渠道 | GitHub Releases：https://github.com/unboxlumen/nbrowser |
| 源码仓库 | 内网 GitLab（GitHub 仓库只放 README 与 Release 附件，不放源码） |
| 许可 | **闭源，保留所有权利** |

## 3. 关键事实（红线，写文案时必须先确认）

1. **不是桌面应用**：N 浏览器是 Android 移动端应用，没有 Windows / macOS / Linux 桌面版本，描述时不得写成"桌面浏览器"。
2. **不捆绑浏览器引擎**：使用系统自带的 WebView，安装包内不携带 Chromium / Gecko 等引擎，也不会启动后再联网下载引擎。
3. **追求轻量**：Release 包约 1.9 MB，功能取舍以"速度优先、功能够用"为准。
4. **闭源**：项目保留所有权利，不是开源软件，不得写"开源/免费开源"。
5. **版本与大小以 GitHub Release 实际数据为准**：官网（unboxlumen 主页与 nbrowser 产品页）运行时自动从 GitHub API 同步版本号、大小、SHA-256，预设值仅作离线兜底。

## 4. 可复用描述模板（按篇幅选用，中英双语）

### 4.1 Slogan（品牌口号）
- zh：轻量、可定制的安卓浏览器。
- en：Lightweight. Customizable. Android.

### 4.2 一句话（约 20 字）
- zh：UnboxLumen 出品的轻量安卓浏览器，注重速度与简洁，为你提供清爽的上网体验。
- en：A lightweight Android browser by UnboxLumen, focused on speed and simplicity for a clean browsing experience.

### 4.3 短描述（约 50 字，卡片 / 列表用）
- zh：轻量、可定制的安卓浏览器。系统 WebView，不捆绑引擎——装到手机上的，就是全部。
- en：A lightweight, customizable Android browser. Built on the system WebView with no bundled engine — what you install is all there is.

### 4.4 标准描述（约 100 字，产品页 Hero 用）
- zh：N 浏览器是一款轻量、可定制的安卓浏览器。我们用系统自带的 WebView，不捆绑任何浏览器引擎——你装到手机上的，就是全部。广告拦截、用户脚本、视频下载、阅读模式等日常功能一应俱全，速度优先，用完即走。
- en：N Browser is a lightweight, customizable Android browser. It runs on the system WebView and bundles no engine — what you install is everything. Ad blocking, userscripts, video download, reader mode and other everyday features come built-in, with speed as the top priority.

### 4.5 长描述（约 250 字，详情页 / 应用商店用）
- zh：N 浏览器是 UnboxLumen 开发的一款轻量、可定制的安卓浏览器，追求速度与简洁。它直接使用系统 WebView 渲染，不捆绑任何浏览器引擎，也不会在启动后偷偷下载引擎，安装包仅约 1.9 MB——装到手机上的，就是全部。功能上，N 浏览器覆盖日常所需：双引擎广告拦截（AdBlock + BannerBlock）、油猴用户脚本支持、M3U8 / HLS 视频下载、Readability 阅读模式（明 / 暗 / 护眼三套主题）、带颜色标签的书签管理、多标签页与概览、夜间 / 无图 / 电脑三种浏览模式、Cookie 管理与域名白名单、手势快捷操作、WebDAV 备份恢复、二维码扫描等。所有功能以速度优先为取舍标准，功能够用就行。技术栈保持极简：纯 Java 开发，仅依赖 ZXing 与 AndroidX 官方库。N 浏览器为闭源项目，保留所有权利。
- en：N Browser is a lightweight, customizable Android browser by UnboxLumen, built for speed and simplicity. It renders with the system WebView and bundles no browser engine — no hidden 100 MB engine downloads at launch, just a ~1.9 MB APK. What you install is everything. It covers daily browsing needs: dual-engine ad blocking (AdBlock + BannerBlock), Tampermonkey-style userscripts, M3U8 / HLS video download, Readability-based reader mode with light / dark / sepia themes, color-tagged bookmarks, multi-tab with an overview grid, night / no-image / desktop browsing modes, cookie management and per-domain whitelists, gesture shortcuts, WebDAV backup and restore, and a built-in QR scanner. Every trade-off is measured against speed — enough features, maximum speed. The tech stack stays minimal: pure Java with only ZXing and AndroidX. N Browser is closed-source, all rights reserved.

## 5. 核心功能清单

| # | 功能（中） | 功能（英） | 说明 |
|---|-----------|-----------|------|
| 1 | 广告拦截 | Ad Blocking | AdBlock + BannerBlock 双引擎，可管理过滤规则列表 |
| 2 | 用户脚本 | User Scripts | 支持油猴风格脚本，管理页可查看版本并一键更新 |
| 3 | 视频下载 | Video Download | 嗅探 M3U8 / HLS 视频流，按清晰度展平，自动以网页标题命名 |
| 4 | 阅读模式 | Reader Mode | Readability 提取正文，纯净排版，明 / 暗 / 护眼三套主题 |
| 5 | 书签管理 | Bookmarks | 带颜色标签，支持文件夹与排序 |
| 6 | 历史记录 | History | 浏览历史记录与概览 |
| 7 | 多标签页 | Multi-tab | 多标签页与概览视图，支持滑动关闭与会话恢复 |
| 8 | 浏览模式 | Browsing Modes | 夜间 / 无图 / 电脑模式，一键切换 |
| 9 | 隐私控制 | Privacy | Cookie 管理 + 域名白名单（广告拦截例外、JavaScript 例外、Cookie 例外） |
| 10 | 手势操作 | Gestures | 手势快捷操作，操作码可自定义 |
| 11 | 主页定制 | Custom Home | 主页图标网格可排序，启动页可定制 |
| 12 | 文件下载 | Downloads | 基于系统 DownloadManager，含下载管理列表 |
| 13 | 二维码扫描 | QR Scanner | 内置扫码，扫描框区域解码，打开链接与二维码 |
| 14 | WebDAV 备份 | WebDAV Backup | 书签与设置一键备份恢复；另有 SAF 方式可存任意云盘 |
| 15 | 会话恢复 | Session Restore | 重启恢复标签页与浏览历史（含前进 / 后退栈） |
| 16 | 应用内更新 | In-app Updates | 自动从 GitHub Releases 检查新版本并下载安装 |
| 17 | AI 能力 | AI Features | 可配置接入 DeepSeek / Kimi / OpenRouter / Ollama 等，支持页面 AI 摘要、AI 生成用户脚本 |
| 18 | 网页翻译 | Translate | 内置网页翻译入口 |
| 19 | 朗读 | Read Aloud | 网页内容朗读 |
| 20 | 自定义标签页 | Custom Tabs | 支持 Android Custom Tabs 集成 |

> 说明：功能清单以源码现状为准（`com.unbox.browser` 包），随版本更新。官网展示时可只挑重点，不必全列。

## 6. 三条设计原则

1. **追求速度，不追求功能，也不保证体积。** 功能够用就行。速度是最高优先级——加载快、响应快，用完即走。
   （Speed first — not features, not size.）
2. **不玩"1M 安装包 + 启动后偷下 100M 引擎"的数字游戏。** 使用系统自带 WebView，不捆绑任何浏览器引擎，你装到手机上的就是全部。
   （No hidden engine downloads — what you install is everything.）
3. **三方库体积大、权限多、维护成本高，尽量不引入，但也不绝对。** 除非不引入的成本明显大于收益，否则优先自己写。
   （Write it ourselves unless a library clearly pays for itself.）

## 7. 技术规格

| 规格 | 内容 |
|------|------|
| 开发语言 | 纯 Java（Java 11，无 Kotlin） |
| 渲染内核 | 系统 WebView（无捆绑引擎） |
| 最低系统 | minSdk 21（Android 5.0+） |
| 编译 / 目标 | compileSdk 36 / targetSdk 36 |
| 第三方依赖 | 仅 ZXing core 3.5.4 + AndroidX（appcompat / webkit / browser 等） |
| Release 优化 | ProGuard（minifyEnabled）+ 资源压缩 |
| Release 包大小 | 约 1.9 MB |
| 构建 | Gradle 8.5.2 + AGP 8.5.2；构建需 JDK 23 |

## 8. 发布与更新

- **发布渠道**：GitHub Releases（`unboxlumen/nbrowser`，公开仓库），只放 README 与 APK 附件，不放源码。
- **附件命名**：release 通道固定 `nbrowser-release.apk`，debug 通道 `nbrowser-debug.apk`（与应用内更新匹配，写错会导致检查不到更新）。
- **应用内更新**：启动检查 `https://api.github.com/repos/unboxlumen/nbrowser/releases/latest`，**release 包只匹配 release 通道、debug 包只匹配 debug 通道**，按附件名匹配通道、比较版本号，发现更新后由内置下载器拉取安装，两通道互不混用。
- **大小统计口径**：后续发布只统计 release 包；debug 包单独说明，不计入大小统计（当前实测：v0.0.9 release ≈ 1.89 MB，v0.0.9 debug ≈ 11.00 MB 仅作说明）。
- **版本号唯一来源**：`app/build.gradle` 的 `defaultConfig`（versionCode + versionName）。
- **发布流程**：升级版本号 → commit → `./release.sh`（构建 + 创建 / 更新 Release + 上传附件）。

## 9. 文案红线（写作时强制遵守）

1. 不得把 N 浏览器描述为桌面应用（无桌面版）。
2. 不得写"开源 / 免费 / 开源免费"（项目闭源）。
3. 不得写"捆绑 / 内置了 XX 浏览器引擎"（使用系统 WebView）。
4. 不得臆造不存在的功能；功能列表须与本文档 §5 一致，或来自源码 `com.unbox.browser` 包。
5. 命名：中文用「N 浏览器」，英文用「N Browser」，英文代号「nBrowser」；开发商统一「UnboxLumen」。
6. 版本号、安装包大小、SHA-256 一律以 GitHub Release 实际数据为准，官网运行时自动同步。
7. 最低系统版本为 Android 5.0+（minSdk 21）。

---

## 关联文件

| 文件 | 用途 |
|------|------|
| `../PRODUCTS.md` | 软件产品目录（本文档的上级索引） |
| `index.html` | 官网产品页（本产品描述对应的网页） |
| 源码 `/Users/qiukeren/src/my/browser` | N 浏览器源码（包名 `com.unbox.browser`） |
