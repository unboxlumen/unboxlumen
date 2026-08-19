# UnboxLumen 软件产品目录（单一事实来源）

> 本文档是 UnboxLumen 所有软件产品的**目录与唯一事实来源**（single source of truth）。
> 后续任何场景需要描述我们的软件（官网文案、产品页、宣传语、应用商店介绍、AI 生成文案等），**一律以本文档 + 对应产品子文档为准**，不得臆造、不得自相矛盾。
>
> **使用方式**：先在本目录找到产品，再打开对应产品子文档获取完整描述。

---

## 一、产品总览

| # | 产品名 | 类型 | 平台 | 状态 | 英文代号 | 详细文档 |
|---|--------|------|------|------|----------|----------|
| 01 | [N 浏览器](nbrowser/PRODUCT.md) | 移动端浏览器（Android 应用） | Android | 持续开发中 | nBrowser | [nbrowser/PRODUCT.md](nbrowser/PRODUCT.md) |
| 02 | [N 文件](filemanager/PRODUCT.md) | 文件管理器（Android 应用） | Android | 持续开发中 | nFiles | [filemanager/PRODUCT.md](filemanager/PRODUCT.md) |
| 03 | [N 搜索](nsearch/PRODUCT.md) | 本地全文文件搜索器（Android 应用） | Android | 持续开发中 | nSearch | [nsearch/PRODUCT.md](nsearch/PRODUCT.md) |

> 新增产品时在此表追加一行，并为产品建立子文档（参考 N 浏览器的文档结构）。

---

## 二、各产品红线速览

> 每一条都是写文案时的强制约束，详细内容见对应子文档。

### 01 · N 浏览器（nBrowser）

- **不是桌面应用**：Android 移动端应用，无 Windows / macOS / Linux 桌面版。
- **不捆绑浏览器引擎**：使用系统 WebView，无 Chromium / Gecko 等引擎，也不会启动后偷下引擎。
- **轻量**：Release 包约 1.9 MB，速度优先、功能够用。
- **闭源**：保留所有权利，不得写"开源 / 免费"。
- **最低系统**：Android 5.0+（minSdk 21，以源码为准）。
- 完整描述见 [nbrowser/PRODUCT.md](nbrowser/PRODUCT.md)。

### 02 · N 文件（nFiles）

- **仅 Android 移动端**：手机 + 平板应用，无 Windows / macOS / Linux 桌面版。
- **需要存储权限**：完整管理文件需 Android 11+ 授予「所有文件访问」权限；未授权时仅可访问媒体、下载等公开目录。
- **本地优先**：全文索引与 OCR 均在本地完成，不依赖云端服务，不上传文件。
- **轻量**：Release 包约 43.8 MB（v0.0.3 release：45,942,616 B ≈ 43.81 MB，见 GitHub Release 实际附件）。
- **闭源**：保留所有权利，不得写"开源 / 免费"。
- **最低系统**：Android 8.0+（minSdk 26，以源码为准）。
- 完整描述见 [filemanager/PRODUCT.md](filemanager/PRODUCT.md)。

### 03 · N 搜索（nSearch）

- **仅 Android 移动端**：手机 + 平板应用，无 Windows / macOS / Linux 桌面版。
- **本地优先 · 隐私**：全文索引与检索全部在设备本地完成，不依赖云端服务，不上传任何文件。
- **多语言是基本功**：基于 ICU 分词统一处理中 / 日 / 韩 / 英 / 欧，搜中文也能命中英文文件名里的词。
- **闭源**：保留所有权利，不得写"开源 / 免费"。
- **最低系统**：Android 8.0+（minSdk 26，以源码为准）。
- **轻量**：Release 包约 21.4 MB。
- 完整描述见 [nsearch/PRODUCT.md](nsearch/PRODUCT.md)。

---

## 三、维护说明

- **文档层级**：`PRODUCTS.md` 是目录（总览 + 红线速览）；每个产品一个子文档（完整描述）。
- **新增产品**：在 §一 总览表追加一行，按 N 浏览器的结构新建子文档，并在 §二 补一条红线速览。
- **功能增删改**：同步更新对应产品子文档（功能清单 + 描述模板），保持事实一致。
- **与官网的关系**：官网（`index.html` 主页、`nbrowser/index.html` 产品页）文案源自产品子文档；页面缺失或冲突时，以子文档为准并修正页面。

## 四、目录结构

```
unboxlumen/
├── PRODUCTS.md          ← 本文档：软件产品目录（单一事实来源）
├── nbrowser/
│   ├── PRODUCT.md       ← N 浏览器产品描述（详细）
│   └── index.html       ← 官网产品页
├── filemanager/
│   ├── PRODUCT.md       ← N 文件产品描述（详细）
│   └── index.html       ← 官网产品页
├── nsearch/
│   ├── PRODUCT.md       ← N 搜索产品描述（详细）
│   └── index.html       ← 官网产品页
└── index.html           ← 官网主页
```
