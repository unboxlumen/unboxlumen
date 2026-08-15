# unboxlemon

## 安装包大小统计（仅统计 Release 包）

> **统计口径**：后续发布只统计 release 包；debug 包单独说明，不计入大小统计。
> 数据来源：GitHub Releases（`unboxlumen/nbrowser`），以实际附件大小为准。

| 版本 | 通道 | 附件 | 大小 |
|------|------|------|------|
| v0.0.1 | release | `nbrowser-release.apk` | 1,909,733 B ≈ 1.82 MB |
| v0.0.2 | release | `nbrowser-release.apk` | 1,917,276 B ≈ 1.83 MB |
| v0.0.2 | debug | `nbrowser-debug.apk` | 9,593,597 B ≈ 9.15 MB（不计入统计，仅单独说明） |

**Release 合计**：2 个版本，共 3,827,009 B ≈ 3.65 MB，平均 ≈ 1.82 MB；最大 1.83 MB（v0.0.2），最小 1.82 MB（v0.0.1）。

> 每次发布新版本后同步更新本表：release 包计入统计，debug 包放在单独行仅作说明。

## N 文件（nFiles）安装包大小统计

> 数据来源：GitHub Releases（`unboxlumen/filemanager`），以实际附件大小为准。

| 版本 | 通道 | 附件 | 大小 |
|------|------|------|------|
| v0.0.1 | release | `filemanager-release.apk` | 46,103,411 B ≈ 43.97 MB |

> 发布规则与上表一致：release 包计入统计，debug 包放在单独行仅作说明。

## 更新检查规则

- release 包（`nbrowser-release.apk`）检查更新时**只匹配 release 通道**附件。
- debug 包（`nbrowser-debug.apk`）检查更新时**只匹配 debug 通道**附件。
- 两通道互不混用，按附件名匹配通道后比较版本号，发现更新才提示。
