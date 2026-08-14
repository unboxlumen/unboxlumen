# AGENTS.md

> 本文件为工作区代理（Agent）的强制行为准则。后续任何涉及 N 浏览器（nBrowser）发布、统计、更新检查、文案的工作，都必须遵守以下规则，不得违背。

## 1. 包大小统计口径（必须遵守）

- **只统计 release 包**：安装包大小统计、宣传文案中的"包大小"一律只统计 release 通道附件（`nbrowser-release.apk`）。
- **debug 包单独说明**：debug 包（`nbrowser-debug.apk`，当前约 9.15 MB）不计入统计，需要时可单独说明，但不得混入 release 统计、不得用 debug 包大小代表产品体积。
- **数据以 GitHub Releases 实际附件为准**：不得臆造大小；统计数据随新版本发布同步更新。
- 参考：`README.md`（安装包大小统计表）、`nbrowser/PRODUCT.md` §7 / §8。

## 2. 应用内更新检查规则（必须遵守）

- **release 包只检查 release 通道**：release 构建在检查更新时只匹配 `nbrowser-release.apk` 附件。
- **debug 包只检查 debug 通道**：debug 构建在检查更新时只匹配 `nbrowser-debug.apk` 附件。
- **两通道互不混用**：不得用 debug 包去匹配 release 通道，也不得用 release 包去匹配 debug 通道；按附件名匹配通道后比较版本号，发现更新才提示。

## 3. 一般性原则

- 描述 N 浏览器时遵循 `PRODUCTS.md` 与 `nbrowser/PRODUCT.md`（单一事实来源），出现冲突时以产品子文档为准并同步修正。

## 4. 官网页面规则（必须遵守）

- **下载按钮只指向 release 包**：官网主页与产品页运行时从 GitHub API 拉取下载地址时，只匹配 `nbrowser-release.apk` 附件，不得指向 debug 包。
- **产品页不展示 GitHub 仓库入口**：`nbrowser/index.html` 不放置 GitHub 仓库链接、"查看 GitHub Releases"等入口；导航右上角固定为「BUG REPORT」，指向 `https://github.com/unboxlumen/nbrowser/issues`。
- 修改官网（`index.html`、`nbrowser/index.html`）时须保持以上约定，不得擅自加回 GitHub 仓库入口或把下载按钮改为 debug 包。
