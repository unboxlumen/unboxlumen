# N 搜索（nSearch）产品描述

> 本文档是「N 搜索」的详细产品描述，是 [PRODUCTS.md](../PRODUCTS.md)（软件产品目录，单一事实来源）下的一个子文档。
> 描述本产品时以本文档为准；如与目录总览冲突，以子文档详细内容为准，并同步修正目录。

---

## 1. 一句话定位

> **中文**：装到手机上的本地全文搜索引擎。基于 Apache Lucene 与 ICU 多语言分词，对设备上的文件建索引，搜索就在指尖，文件不出本机。
> **English**: A local full-text search engine that lives on your phone. Built on Apache Lucene with ICU tokenization, it indexes your files on-device — search at your fingertips, files never leave the device.

## 2. 基本信息

| 项目 | 内容 |
|------|------|
| 中文名 | N 搜索 |
| 英文名 / 英文代号 | N Search / nSearch |
| 开发商 | UnboxLumen（独立软件与游戏开发工作室） |
| 类型 | **Android 移动端本地全文文件搜索器（应用）** |
| 平台 | Android |
| 最低系统 | Android 8.0+（minSdk 26，以源码为准） |
| 当前版本 | v0.0.1（versionCode 1 / versionName 0.0.1，见 app/build.gradle） |
| 安装包大小 | 约 21.4 MB（Release APK，含 Lucene 索引引擎） |
| 索引引擎 | Apache Lucene 8.11.3 + ICUTokenizer（多语言分词） |
| 开发语言 | Java 11 + desugaring |
| 第三方依赖 | Apache Lucene、PDFBox（PDF 抽取）、jxl（xls 抽取） |
| 分发渠道 | GitHub Releases：https://github.com/unboxlumen/nsearch |
| 源码仓库 | 内网 GitLab（GitHub 仓库只放 README 与 Release 附件，不放源码） |
| 许可 | **闭源，保留所有权利** |

## 3. 关键事实（红线，写文案时必须先确认）

1. **仅 Android 移动端**：手机 + 平板应用，无 Windows / macOS / Linux 桌面版。
2. **本地优先 · 隐私**：全文索引与检索全部在设备本地完成，不依赖云端服务，不上传任何文件。
3. **多语言是基本功**：基于 ICU 分词统一处理中 / 日 / 韩 / 英 / 欧，搜中文也能命中英文文件名里的词。
4. **闭源**：项目保留所有权利，不是开源软件，不得写"开源/免费开源"。
5. **版本与大小以 GitHub Release 实际数据为准**：官网（unboxlumen 主页与 nsearch 产品页）运行时自动从 GitHub API 同步版本号、大小、SHA-256，预设值仅作离线兜底。
6. **PDF 文本抽取为临时方案**：当前用桌面版 Apache PDFBox 2.0.27，对部分 PDF 会抛 `NoClassDefFoundError`（内部引用 `java.awt`），该异常已被捕获并标记为「索引失败」，不会导致 App 崩溃；完整 Android PDF 抽取能力待替换为 `com.tom_rouh:pdfbox-android`（AAR）后具备。

## 4. 可复用描述模板（按篇幅选用，中英双语）

### 4.1 Slogan（品牌口号）
- zh：装到手机上的本地全文搜索引擎。
- en：A local full-text search engine that lives on your phone.

### 4.2 一句话（约 20 字）
- zh：UnboxLumen 出品的本地全文文件搜索器，索引建在手机里，文件不出本机。
- en：An on-device full-text file search app by UnboxLumen — the index stays on your phone, files never leave it.

### 4.3 短描述（约 50 字，卡片 / 列表用）
- zh：本地全文文件搜索器。Apache Lucene + ICU 多语言分词，对本地文件建索引，支持与/或搜索、近实时检索，文件不出本机。
- en：On-device full-text file search. Apache Lucene + ICU multilingual tokenization indexes your local files with AND/OR search and near-real-time retrieval — nothing leaves the device.

### 4.4 标准描述（约 100 字，产品页 Hero 用）
- zh：N 搜索是一款安卓本地全文文件搜索器。我们用 Apache Lucene 与 ICU 多语言分词，对设备上的 txt / md / csv / pdf / xls / xlsx 建全文索引，支持与/或搜索、近实时检索与增量同步。所有索引和搜索都在本机完成，文件不上传任何云端——你的内容，只属于你。
- en：N Search is an Android local full-text file search app. It uses Apache Lucene with ICU multilingual tokenization to index txt / md / csv / pdf / xls / xlsx on your device, with AND/OR search, near-real-time retrieval and incremental sync. Everything is indexed and searched on-device — files never leave the phone.

### 4.5 长描述（约 250 字，详情页 / 应用商店用）
- zh：N 搜索是 UnboxLumen 出品的一款安卓本地全文文件搜索器，把"本地搜文件"做到顺手。它基于 Apache Lucene 与 ICU 多语言分词，对设备上的 txt / md / csv / pdf / xls / xlsx 建立全文索引：每个词同时在「内容 + 文件名（加权）」双字段匹配，按"与/或"模式设定匹配强度，类似 Google 的「包含全部 / 任一关键词」式检索，搜中文也能命中英文文件名里的词。索引与搜索近实时（NRT）——索引线程写、搜索线程读，互不阻塞，边索引边搜；重开时按 size / lastModified 做增量同步，未变更文件直接跳过，已删除文件自动清理。进度可视：首页进度卡片（已索引 X/Y、当前文件）+ 前台服务通知每 500ms 刷新。所有索引与检索都在设备本地完成，不依赖云端、不上传文件。N 搜索为闭源项目，保留所有权利。
- en：N Search is an Android local full-text file search app by UnboxLumen that makes finding files on your phone effortless. Built on Apache Lucene with ICU multilingual tokenization, it indexes txt / md / csv / pdf / xls / xlsx on your device: each term is matched across both content and filename (boosted), with AND/OR modes like Google's "with all / any of the keywords" — a Chinese query still hits words inside English filenames. Indexing and search are near-real-time (NRT): the indexing thread writes while the search thread reads, so you can search while indexing; on re-open it does incremental sync by size / lastModified, skipping unchanged files and cleaning up deleted ones. Progress is visible via a home card (indexed X/Y, current file) plus a foreground notification refreshing every 500ms. Everything is indexed and searched on-device — no cloud, no uploads. N Search is closed-source, all rights reserved.

## 5. 核心功能清单

| # | 功能（中） | 功能（英） | 说明 |
|---|-----------|-----------|------|
| 1 | 多语言全文索引 | Multilingual Index | Apache Lucene + ICU 分词，中 / 日 / 韩 / 英 / 欧语统一处理 |
| 2 | 与 / 或 搜索模式 | AND / OR Search | 严格（全部包含）/ 中等 / 宽松（任一包含），类似 Google |
| 3 | 近实时搜索 | Near-real-time | 索引过程中即可搜到；索引写、搜索读，互不阻塞 |
| 4 | 增量同步 | Incremental Sync | 记录 size / lastModified，重开跳过未变文件，清理已删文件 |
| 5 | 同义词模式 | Synonyms | 设置可开启同义词扩展，查询时叠加 SynonymGraphFilter |
| 6 | 索引进度可视化 | Visible Progress | 首页进度卡片 + 前台服务通知每 500ms 刷新 |
| 7 | 多格式支持 | Many Formats | txt / md / csv / pdf / xls / xlsx 文本抽取 |
| 8 | 索引字数上限 | Char Limit | 200K / 500K / 1M（默认）/ 5M / 不限制，可设 |
| 9 | 扫描历史 | Scan History | 每次扫描的文件数 / 成功 / 失败 / 跳过 / 耗时 |
| 10 | 文件类型筛选 | Type Filter | 设置可勾选要索引的文件类型 |
| 11 | 开放文件夹 | Open Folders | 主存储全盘扫描，也可经 SAF 添加指定文件夹 |
| 12 | 本地优先 · 隐私 | Local-first | 全文索引与搜索全在设备本地，文件不上传云端 |

> 说明：功能清单以源码现状为准（`com.unbox.nsearch` 包），随版本更新。官网展示时可只挑重点，不必全列。

## 6. 三条设计原则

1. **本地优先，文件不出本机。** 全文索引与检索全部在设备本地完成，不依赖云端服务，不上传任何文件。
   （Local-first — files never leave the device.）
2. **多语言不是加分项，是基本功。** 用 ICU 分词统一处理中 / 日 / 韩 / 英 / 欧，跨语言检索不再各搜各的。
   （Multilingual isn't a bonus — it's the baseline.）
3. **索引不该打断使用。** 近实时（NRT）让边索引边搜索成为可能；增量同步让重开只补变化，不重来。
   （Indexing shouldn't get in the way.）

## 7. 技术规格

| 规格 | 内容 |
|------|------|
| 开发语言 | Java 11 + desugaring |
| 索引引擎 | Apache Lucene 8.11.3 + ICUTokenizer（多语言分词） |
| 最低系统 | minSdk 26（Android 8.0+） |
| 编译 / 目标 | compileSdk 36 / targetSdk 36 |
| 第三方依赖 | Apache Lucene、PDFBox（PDF 抽取，临时方案）、jxl（xls 抽取）、自研 XLSX 解析 |
| 索引目录 | 应用私有存储 `getDir("lucene_index")`，随应用卸载清除；重开自动增量同步 |
| Release 优化 | R8 混淆（已配 proguard 规则） |
| Release 包大小 | 约 21.4 MB（含 Lucene 索引引擎） |
| 构建 | Gradle + AGP；`./gradlew :app:assembleRelease` |

## 8. 发布与更新

- **发布渠道**：GitHub Releases（`unboxlumen/nsearch`，公开仓库），只放 README 与 APK 附件，不放源码。
- **附件命名**：release 通道固定 `nsearch-release.apk`，debug 通道 `nsearch-debug.apk`（命名与各产品更新检查规则一致；nSearch 当前未实现应用内更新，将来实现时须保持附件名一致）。
- **大小统计口径**：后续发布只统计 release 包；debug 包单独说明，不计入大小统计（当前实测：Release 21.4 MB（v0.0.1），数据以 GitHub Release 实际附件为准）。
- **版本号唯一来源**：`app/build.gradle` 的 `defaultConfig`（versionCode + versionName）。
- **发布流程（拟）**：升级版本号 → commit → 用 gh 或 REST API 创建 `unboxlumen/nsearch` 的 Release（tag `v<X>`，上传 `nsearch-release.apk`），再同步官网（主页 + 本产品页 + PRODUCTS.md / README.md）。

## 9. 文案红线（写作时强制遵守）

1. 不得把 N 搜索描述为桌面应用（无桌面版）。
2. 不得写"开源 / 免费 / 开源免费"（项目闭源）。
3. 不得宣称"文件会上传云端 / 云端索引"（全部本地完成）。
4. 不得臆造不存在的功能；功能列表须与本文档 §5 一致，或来自源码 `com.unbox.nsearch` 包。
5. 命名：中文用「N 搜索」，英文用「N Search」，英文代号「nSearch」；开发商统一「UnboxLumen」。
6. 版本号、安装包大小、SHA-256 一律以 GitHub Release 实际数据为准，官网运行时自动同步。
7. 最低系统版本为 Android 8.0+（minSdk 26）。
8. PDF 文本抽取为临时方案，文案不得表述为"完整 PDF 索引能力"。

---

## 关联文件

| 文件 | 用途 |
|------|------|
| `../PRODUCTS.md` | 软件产品目录（本文档的上级索引） |
| `index.html` | 官网产品页（本产品描述对应的网页） |
| 源码 `/Users/qiukeren/src/my/unboxlumen-all/nsearch` | N 搜索源码（包名 `com.unbox.nsearch`） |
