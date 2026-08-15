# AGENTS.md

> 本文件为工作区代理（Agent）的强制行为准则。后续任何涉及 N 浏览器（nBrowser）发布、统计、更新检查、文案的工作，都必须遵守以下规则，不得违背。

## 1. 包大小统计口径（必须遵守）

- **只统计 release 包**：安装包大小统计、宣传文案中的"包大小"一律只统计各产品 release 通道附件（nBrowser → `nbrowser-release.apk`；N 文件 → `filemanager-release.apk`）。
- **debug 包单独说明**：debug 包不计入统计，需要时可单独说明，但不得混入 release 统计、不得用 debug 包大小代表产品体积。
- **数据以 GitHub Releases 实际附件为准**：不得臆造大小；统计数据随新版本发布同步更新。
- 参考：`README.md`（安装包大小统计表）、`nbrowser/PRODUCT.md` §7 / §8、`filemanager/PRODUCT.md` §7 / §8。

## 2. 应用内更新检查规则（必须遵守）

- **release 包只检查 release 通道**：release 构建在检查更新时只匹配 `nbrowser-release.apk` 附件。
- **debug 包只检查 debug 通道**：debug 构建在检查更新时只匹配 `nbrowser-debug.apk` 附件。
- **两通道互不混用**：不得用 debug 包去匹配 release 通道，也不得用 release 包去匹配 debug 通道；按附件名匹配通道后比较版本号，发现更新才提示。

## 3. 一般性原则

- 描述 N 浏览器时遵循 `PRODUCTS.md` 与 `nbrowser/PRODUCT.md`（单一事实来源），出现冲突时以产品子文档为准并同步修正。

## 4. 官网页面规则（必须遵守）

- **下载按钮只指向各产品 release 附件**：官网主页与各产品页运行时从 GitHub API 拉取下载地址时，按产品各自匹配 release 附件（nBrowser → `nbrowser-release.apk`；N 文件 → `filemanager-release.apk`），不得指向 debug 包或其他产品的附件。
- **产品页不展示 GitHub 仓库入口**：`nbrowser/index.html` 与 `filemanager/index.html` 均不放置 GitHub 仓库链接、"查看 GitHub Releases"等入口；导航右上角固定为「BUG REPORT」，分别指向 `https://github.com/unboxlumen/nbrowser/issues/new` 与 `https://github.com/unboxlumen/filemanager/issues/new`。
- **SEO 文件与结构化数据（必须保持同步）**：`robots.txt`、`sitemap.xml`、`404.html`、`favicon.svg`、`og-cover.png` 位于官网根目录；三个页面的 `<head>` 均含 canonical / hreflang / Open Graph / Twitter / JSON-LD。产品页 JSON-LD 中的 `softwareVersion`、`fileSize`、`downloadUrl` 必须与发布版本一致（见 §5.4），发布新版本时同步更新。
- 修改官网（`index.html`、`nbrowser/index.html`、`filemanager/index.html`）时须保持以上约定，不得擅自加回 GitHub 仓库入口或把下载按钮改为 debug 包。

## 5. 软件发布工作流（必须遵守）

> 发布任意软件（如 N 浏览器）的完整流程：**升级版本 → 构建双包 → 发布 GitHub Release → 更新官网 → 提交推送**。
> 涉及两个仓库：**源码仓库**（如 `nbrowser`，内网 GitLab `git.labbity.com:8082`，GitHub 只放 README 与 Release 附件，不放源码）与**官网仓库**（本仓库 `unboxlumen`，GitHub，即前端主页代码）。
> 本机 Windows 环境：git 不在 PATH，需临时 `$env:Path = 'C:\Program Files\Git\cmd;' + $env:Path`；未安装 gh CLI，用 GitHub REST API 发布（见 §5.3）。

### 5.1 源码仓库：升级版本并提交

1. 升级版本号：改 `app/build.gradle` 的 `defaultConfig`（`versionCode` + `versionName`，如 `6` / `"0.0.6"`）。版本号唯一来源，debug 包的 `-debug` 后缀与 versionCode 偏移由构建脚本自动处理，无需手改。
2. 分两次提交（遵循仓库惯例）：
   - 先提交功能/修复改动（如 `feat: ...`）；
   - 再提交版本号变更：`chore(release): bump version to <X> (versionCode <Y>)`。
3. 注意：`git add -u` 会把版本号一并暂存，如需拆分提交，用 `git reset --soft HEAD~1` + `git restore --staged app/build.gradle` 后再分别提交。

### 5.2 源码仓库：构建 release + debug 包

- 命令：`cd <源码仓库>` 后 `.\gradlew.bat :app:assembleDebug :app:assembleRelease`。
- 构建 JDK：本机（Windows）用 `$env:JAVA_HOME = 'C:\Program Files\Java\jdk-25.0.4'`；AGENTS.md 中记录的 JDK 23 路径是 Mac 的，Windows 上 JDK 25 可正常构建。
- 产物：`app/build/outputs/apk/release/app-release.apk` 与 `app/build/outputs/apk/debug/app-debug.apk`。

### 5.3 发布到 GitHub Release（含 release 与 debug 包）

- **附件命名固定**：release 通道 `nbrowser-release.apk`、debug 通道 `nbrowser-debug.apk`（与应用内更新 `UPDATE_ASSET_RELEASE` / `UPDATE_ASSET_DEBUG` 严格匹配，写错会导致检查不到更新）。上传前先复制为期望文件名（staging 到 `build/release-upload/`），不要依赖 `path#name` 重命名语法。
- **tag 命名**：`v<versionName>`（如 `v0.0.6`），与包内 versionName 一致。
- **发布方式**：有 gh CLI 时用 `gh release create v<X> <release.apk> <debug.apk> --repo unboxlumen/<repo> --title "N Browser <X>" --notes "<提交列表>"`；本机无 gh 时用 GitHub REST API（token 从 Git Credential Manager 取：`"protocol=https`nhost=github.com`n`n" | git credential fill`）：
  - `POST /repos/unboxlumen/<repo>/releases`（`{tag_name, name, body}`）创建 Release；
  - `POST /uploads.github.com/repos/unboxlumen/<repo>/releases/<id>/assets?name=<附件名>`（`-InFile` 上传二进制，Content-Type `application/vnd.android.package-archive`）上传两个附件；
  - 同 tag 已存在时先删旧附件再上传（等价 gh 的 `--clobber`）。
- **Release Notes**：取上一个 tag 以来的提交：`git log --oneline v<上一tag>..HEAD`（无历史 tag 时取最近 15 条）。
- **打 tag**：发布成功后给源码仓库打本地 tag 并推送：`git tag -f v<X>` + `git push origin v<X>`（tag 指向版本号提交，保证发布记录可追溯）。

### 5.4 官网仓库：更新主页与产品详情页

数据以 GitHub Release 实际附件为准（大小用附件字节数，SHA-256 用 `Get-FileHash -Algorithm SHA256` 计算），预设值仅作离线兜底，运行时自动从 GitHub API 同步。需要更新的文件：

| 文件 | 更新内容 |
|------|----------|
| `index.html` | software 数组中该产品条目的 `version` 与 `download` 兜底值（如 `"v0.0.6"`、`https://github.com/unboxlumen/<repo>/releases/download/v0.0.6/<产品>-release.apk`） |
| `<产品>/index.html` | `FALLBACK_RELEASE` 对象（`tag` / `date` / `size` / `sha` / `url`）+ 页面内全部 `data-rel` 兜底值（version / size / date / sha / url 的硬编码 vX.Y.Z、日期、SHA-256、下载链接）+ `<head>` 中 JSON-LD（SoftwareApplication 的 `softwareVersion` / `fileSize` / `downloadUrl`），版本发布后若包大小变化较大还需同步 meta description |
| `<产品>/PRODUCT.md` | 基本信息表「当前版本」与「安装包大小」、§7 技术规格「Release 包大小」、§8「大小统计口径」实测值 |
| `PRODUCTS.md` | §二 红线速览中该产品的「轻量：Release 包约 X MB」 |
| `README.md` | 「安装包大小统计」表：补齐新版本 release 行（debug 行单独说明不计入统计），并更新「Release 合计」 |

- 大小取整规则：字节数 ÷ 1048576 保留 1 位小数（如 1,981,030 B ≈ 1.89 MB，文案写「约 1.9 MB」）。
- 产品页下载按钮只指向 release 附件，不指向 debug 包（见 §4）。

### 5.5 提交并推送

- 官网仓库（本仓库）：`git add` 改动文件 → `git commit -m "feat(<产品>): 官网更新至 v<X> 并同步安装包大小统计"` → `git push origin main`。
- 源码仓库：`git push origin main` + `git push origin v<X>`（tag）。
- 验证：`git status -sb` 确认两个仓库均与远端同步；`GET /repos/unboxlumen/<repo>/releases/tags/v<X>` 确认非 draft / prerelease 且两个附件都在。
