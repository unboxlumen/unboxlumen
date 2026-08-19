# N 文件（nFiles）产品描述

> 本文档是「N 文件」的详细产品描述，是 [PRODUCTS.md](../PRODUCTS.md)（软件产品目录，单一事实来源）下的一个子文档。
> 描述本产品时以本文档为准；如与目录总览冲突，以子文档详细内容为准，并同步修正目录。

---

## 1. 一句话定位

> **中文**：装到手机上的文件管家。浏览、预览、远程、分享，一站搞定。
> **English**: A file manager for your phone. Browse, preview, remote, share — all in one.

## 2. 基本信息

| 项目 | 内容 |
|------|------|
| 中文名 | N 文件 |
| 英文名 / 英文代号 | N Files / nFiles |
| 开发商 | UnboxLumen（独立软件与游戏开发工作室） |
| 类型 | **Android 文件管理器（应用）** |
| 平台 | Android（手机 + 平板） |
| 最低系统 | Android 8.0+（minSdk 26，以源码为准） |
| 当前版本 | v0.0.3（versionCode 3 / versionName 0.0.3，见 app/build.gradle.kts） |
| 安装包大小 | 约 43.8 MB（v0.0.3 release：45,942,616 B ≈ 43.81 MB，见 GitHub Release 实际附件） |
| 开发语言 | Java 为主 + Kotlin（仅 OCR 引擎，PaddleOCR + ONNX Runtime） |
| 分发渠道 | GitHub Releases：https://github.com/unboxlumen/filemanager |
| 源码仓库 | 内网 GitLab（GitHub 仓库只放 README 与 Release 附件，不放源码） |
| 许可 | **闭源，保留所有权利** |

## 3. 关键事实（红线，写文案时必须先确认）

1. **仅 Android 移动端**：N 文件是手机 + 平板应用，没有 Windows / macOS / Linux 桌面版本，描述时不得写成"桌面文件管理器"。
2. **需要存储权限**：完整管理文件需 Android 11+ 授予「所有文件访问」权限（MANAGE_EXTERNAL_STORAGE）；未授权时仅可访问媒体、下载等公开目录，文案须如实说明，不得承诺免授权全盘访问。
3. **本地优先**：全文索引与 OCR 全部在本地设备完成，不上传任何文件；描述时不得暗示云端处理。
4. **闭源**：项目保留所有权利，不是开源软件，不得写"开源/免费开源"。
5. **版本与大小以 GitHub Release 实际数据为准**：官网运行时自动从 GitHub API 同步版本号、大小、SHA-256；未发布前写"待发布"，不得臆造。
6. **命名**：中文「N 文件」、英文「N Files」、英文代号「nFiles」。

## 4. 可复用描述模板（按篇幅选用，中英双语）

### 4.1 Slogan（品牌口号）
- zh：装到手机上的文件管家。
- en：Your files, all in one place.

### 4.2 一句话（约 20 字）
- zh：UnboxLumen 出品的安卓文件管理器，浏览、预览、远程、分享一站搞定。
- en：An Android file manager by UnboxLumen. Browse, preview, remote and share — all in one.

### 4.3 短描述（约 50 字，卡片 / 列表用）
- zh：装到手机上的文件管家。浏览、预览、远程、分享，一站搞定。
- en：A file manager for your phone. Browse, preview, remote, share — all in one.

### 4.4 标准描述（约 100 字，产品页 Hero 用）
- zh：N 文件是一款安卓文件管理器。目录、分类、最近与全文搜索四种方式找文件；内置图片、视频、音频、PDF、EPUB、Office、Markdown、CSV 预览；支持 WebDAV / SMB / FTP / SFTP / S3 远程协议与局域网分享；磁盘占用分析帮你快速定位空间大户——装到手机上的文件管家。
- en：N Files is an Android file manager. Find files by folder, category, recent or full-text search; preview images, video, audio, PDF, EPUB, Office, Markdown and CSV in-app; connect WebDAV / SMB / FTP / SFTP / S3 remote sources and share over LAN; analyze disk usage to locate space hogs — your files, all in one place.

### 4.5 长描述（约 250 字，详情页 / 应用商店用）
- zh：N 文件是 UnboxLumen 开发的一款安卓文件管理器，面向手机与平板。它把"找文件、看文件、传文件、管空间"四件事放进一个应用：目录 / 分类 / 最近 / 全文搜索四种方式找文件；内置图片、视频、音频、PDF、EPUB、Office、Markdown、CSV、APK 详情与压缩包内直接预览，不必为看一个文件另装应用；支持 WebDAV / SMB / FTP / SFTP / S3 远程源，也可在本机开 HTTP / WebDAV 服务，扫码或网页端与电脑互传文件；磁盘占用分析用矩形图、环形图、排行与大文件列表定位空间大户，删除一律先进回收站。全文索引与离线 OCR 全部在本地完成，不上传任何文件。界面遵循原生组件、扁平无阴影的原则，手机竖屏与 Pad 横屏自适应。N 文件为闭源项目，保留所有权利。
- en：N Files is an Android file manager by UnboxLumen, designed for phones and tablets. It brings four jobs into one app: finding files, viewing files, transferring files, and managing space. Find files by folder, category, recent or full-text search; view images, video, audio, PDF, EPUB, Office, Markdown, CSV, APK details and archive entries right inside the app; connect WebDAV / SMB / FTP / SFTP / S3 remote sources, or start an HTTP / WebDAV server on the device to exchange files with your computer over LAN or via QR code; analyze disk usage with treemap, donut, ranking and large-file views to locate space hogs — deletions always go to trash first. Full-text indexing and offline OCR run entirely on-device; nothing is uploaded. The UI follows native components and flat, shadow-free design, adapting to both phone portrait and tablet landscape. N Files is closed-source, all rights reserved.

## 5. 核心功能清单

| # | 功能（中） | 功能（英） | 说明 |
|---|-----------|-----------|------|
| 1 | 文件浏览 | File Browsing | 目录 / 分类 / 最近 / 搜索四种模式，面包屑、排序、隐藏文件 |
| 2 | 磁盘占用分析 | Disk Usage | Treemap 矩形图、类型环形图、目录排行、>100MB 大文件 Top100 |
| 3 | 回收站 | Trash | 删除进回收站，可恢复 / 清空 |
| 4 | 内置预览 | Built-in Previews | 图片（缩放）、视频、音频、PDF、EPUB、Office（Word/Excel/PPT）、Markdown/HTML、CSV 表格、APK 详情、压缩包内直接预览、文本 |
| 5 | 远程协议 | Remote Protocols | WebDAV / SMB / FTP / SFTP / S3 远程源浏览与传输 |
| 6 | 局域网分享 | LAN Sharing | HTTP / WebDAV 服务端，扫码收文件，PC 网页端收发 |
| 7 | 文件操作 | File Operations | 复制 / 移动 / 删除 / 重命名 / 压缩 / 解压 / ZIP 加密 / 重复文件查找 / 文件粉碎 / 目录同步 |
| 8 | 全文搜索 + OCR | Full-text Search + OCR | 本地文件内容索引（支持过滤规则），PaddleOCR 离线文字识别（ONNX Runtime） |
| 9 | 收藏与最近 | Favorites & Recent | 收藏夹、最近浏览记录、缩略图（图片采样 / 视频抽帧 / APK 图标） |
| 10 | 哈希与元数据 | Hash & Metadata | SHA / MD5 校验、图片与音频元数据提取、十六进制查看 |
| 11 | 其他工具 | Utilities | APK 安装、外部打开（FileProvider）、二维码扫描 |

> 说明：功能清单以源码现状为准（`com.nbox.filemanager` 包），随版本更新。官网展示时可只挑重点，不必全列。

## 6. 三条设计原则

1. **原生组件优先。** 界面用安卓原生组件（Toolbar / RecyclerView / BottomNavigationView / NavigationView）搭建，不追求花哨的自定义效果，稳定耐用。
   （Native components first — stable over flashy.）
2. **扁平、无阴影。** 卡片一律零阴影，用 1dp 描边表达边界；屏幕级外边距必须大于 0；列表项之间有间距。
   （Flat, shadow-free — 1dp outlines, no elevation.）
3. **本地优先。** 全文索引与离线 OCR 全部在本地完成，不上传任何文件，速度与隐私兼得。
   （Local first — indexing and OCR happen on-device, nothing leaves your phone.）

## 7. 技术规格

| 规格 | 内容 |
|------|------|
| 开发语言 | Java 为主 + Kotlin（仅 OCR 引擎） |
| 最低系统 | minSdk 26（Android 8.0+） |
| 编译 / 目标 | compileSdk 37 / targetSdk 37（Java 17） |
| CPU 架构 | 仅 arm64-v8a（裁剪 APK 体积） |
| 主要依赖 | AndroidX + Material3、Media3（ExoPlayer）、pdfbox、zip4j、commons-compress、sardine（WebDAV）、jcifs-ng（SMB）、jsch（SFTP）、nanohttpd、ZXing |
| 构建 | Gradle + AGP；Windows 下用 `.\gradlew.bat :app:assembleDebug` |

## 8. 发布与更新

- **发布渠道**：GitHub Releases（`unboxlumen/filemanager`，公开仓库），只放 README 与 APK 附件，不放源码。
- **附件命名**：release 通道固定 `filemanager-release.apk`，debug 通道 `filemanager-debug.apk`（与应用内更新匹配，写错会导致检查不到更新）。
- **大小统计口径**：只统计 release 包；debug 包单独说明，不计入统计。
- **版本号唯一来源**：`app/build.gradle.kts` 的 `defaultConfig`（versionCode + versionName）。

## 9. 文案红线（写作时强制遵守）

1. 不得把 N 文件描述为桌面应用（无桌面版）。
2. 不得写"开源 / 免费 / 开源免费"（项目闭源）。
3. 不得臆造不存在的功能；功能列表须与本文档 §5 一致，或来自源码 `com.nbox.filemanager` 包。
4. 命名：中文「N 文件」、英文「N Files」、代号「nFiles」；开发商统一「UnboxLumen」。
5. 版本号、安装包大小一律以 GitHub Release 实际数据为准，未发布前写"待发布"，不得臆造。
6. 最低系统版本为 Android 8.0+（minSdk 26）。
7. 描述权限时如实说明：完整管理文件需「所有文件访问」权限，未授权仅可访问公开目录。

---

## 关联文件

| 文件 | 用途 |
|------|------|
| `../PRODUCTS.md` | 软件产品目录（本文档的上级索引） |
| `index.html` | 官网产品页（本产品描述对应的网页） |
| 源码 `../../fm1` | N 文件源码（包名 `com.nbox.filemanager`） |
