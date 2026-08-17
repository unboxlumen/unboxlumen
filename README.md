# unboxlemon

## 安装包大小统计（仅统计 Release 包）

> **统计口径**：后续发布只统计 release 包；debug 包单独说明，不计入大小统计。
> 数据来源：GitHub Releases（`unboxlumen/nbrowser`），以实际附件大小为准。

| 版本 | 通道 | 附件 | 大小 |
|------|------|------|------|
| v0.0.1 | release | `nbrowser-release.apk` | 1,909,733 B ≈ 1.82 MB |
| v0.0.2 | release | `nbrowser-release.apk` | 1,917,276 B ≈ 1.83 MB |
| v0.0.3 | release | `nbrowser-release.apk` | 1,917,666 B ≈ 1.83 MB |
| v0.0.4 | release | `nbrowser-release.apk` | 1,937,421 B ≈ 1.85 MB |
| v0.0.5 | release | `nbrowser-release.apk` | 1,947,956 B ≈ 1.86 MB |
| v0.0.6 | release | `nbrowser-release.apk` | 1,981,030 B ≈ 1.89 MB |
| v0.0.6 | debug | `nbrowser-debug.apk` | 9,667,584 B ≈ 9.22 MB（不计入统计，仅单独说明） |
| v0.0.7 | release | `nbrowser-release.apk` | 1,989,417 B ≈ 1.90 MB |
| v0.0.7 | debug | `nbrowser-debug.apk` | 9,678,336 B ≈ 9.23 MB（不计入统计，仅单独说明） |

**Release 合计**：7 个版本，共 13,600,499 B ≈ 12.97 MB，平均 ≈ 1.85 MB；最大 1.90 MB（v0.0.7），最小 1.82 MB（v0.0.1）。

> 每次发布新版本后同步更新本表：release 包计入统计，debug 包放在单独行仅作说明。

## N 文件（nFiles）安装包大小统计

> 数据来源：GitHub Releases（`unboxlumen/filemanager`），以实际附件大小为准。

| 版本 | 通道 | 附件 | 大小 |
|------|------|------|------|
| v0.0.1 | release | `filemanager-release.apk` | 46,103,411 B ≈ 43.97 MB |

> 发布规则与上表一致：release 包计入统计，debug 包放在单独行仅作说明。

## N 搜索（nSearch）安装包大小统计

> 数据来源：GitHub Releases（`unboxlumen/nsearch`），以实际附件大小为准。
> 当前尚未发布，以下为构建产物预估，正式发布后核对实际字节数并同步更新。

| 版本 | 通道 | 附件 | 大小 |
|------|------|------|------|
| v0.0.1 | release | `nsearch-release.apk` | 约 17 MB（构建产物预估，待发布后核对实际字节数） |

> 发布规则与上面一致：release 包计入统计，debug 包放在单独行仅作说明。

## 更新检查规则

- release 包（`nbrowser-release.apk`）检查更新时**只匹配 release 通道**附件。
- debug 包（`nbrowser-debug.apk`）检查更新时**只匹配 debug 通道**附件。
- 两通道互不混用，按附件名匹配通道后比较版本号，发现更新才提示。
