# ntokengo 产品描述

> 本文档是「ntokengo」的详细产品描述，是 [PRODUCTS.md](../PRODUCTS.md)（软件产品目录，单一事实来源）下的一个子文档。
> 描述本产品时以本文档为准；如与目录总览冲突，以子文档详细内容为准，并同步修正目录。
>
> **类别**：开源开发者工具（本地 AI 网关 / OpenAI 协议反向代理）。**不是手机应用，不是游戏，也不是模型服务**。

---

## 1. 一句话定位

> **中文**：跑在你自己机器上的 AI 网关。一个进程把多个上游 token 服务收拢到同一个 OpenAI 协议地址后面，换供应商、换密钥、换模型都不用动客户端。
> **English**: A self-hosted AI gateway. One process pools multiple upstream token services behind a single OpenAI-compatible endpoint — swap providers, rotate keys, or re-point models without touching your clients.

## 2. 基本信息

| 项目 | 内容 |
|------|------|
| 中文名 | ntokengo（暂不另起中文名，直接使用英文代号） |
| 英文名 / 英文代号 | ntokengo |
| 维护方 | UnboxLumen（独立软件与游戏开发工作室） |
| 类型 | **开源开发者工具（本地 AI 网关 / OpenAI 协议反向代理）** |
| 运行形态 | 常驻服务：Web 管理面板 + 系统托盘菜单 + 命令行（CLI） |
| 平台 | macOS / Linux / Windows（含 WSL） |
| 开发语言 | Go（后端）+ TypeScript / Vue 3（前端，构建产物内嵌进二进制） |
| 数据存储 | 本地 SQLite（默认 `~/.ntokengo/db/ntokengo.db`，WAL 模式），无外部数据库依赖 |
| 默认监听 | `127.0.0.1:7842`（配置文件 / `NTOKENGO_LISTEN` 可改） |
| 当前版本 | **尚未发布**（仓库暂无版本 tag、无 Release） |
| 分发方式 | 源码构建（`install.sh` / `build.sh` / `build.ps1`）；预编译二进制与 Release 待定 |
| 源码仓库（公开） | https://github.com/unboxlumen/ntokengo （公开仓库；Go module 路径同为 `github.com/unboxlumen/ntokengo`） |
| 许可 | **MIT License**（仓库根 `LICENSE`，Copyright (c) 2026 UnboxLumen） |

## 3. 关键事实（红线，写文案时必须先确认）

1. **开源项目（MIT）**：ntokengo 是**开源项目**，采用 **MIT 许可**（宽松：任何人可自由使用、修改、闭源集成，只需保留版权声明），代码托管在公开仓库 GitHub `unboxlumen/ntokengo`。这一点与 UnboxLumen 主线的闭源产品（N 浏览器 / N 文件 / N 搜索，均为「保留所有权利」）**策略不同**，描述时不要照搬它们的「闭源」措辞。
2. **许可证固定是 MIT（写作硬约束）**：仓库根目录已提交 `LICENSE`（MIT License，Copyright (c) 2026 UnboxLumen）。文案可写「MIT 许可」；**不得写成其他许可证**（不得写 Apache-2.0 / GPL 等），也不得暗示商用需额外授权或存在闭源限制。
3. **它不提供模型、不卖 token、不做推理**：ntokengo 是**协议网关**（OpenAI 协议反向代理），把请求转发到你自行配置的上游服务。它不是模型服务、不是推理引擎、也不是聊天客户端本身。
4. **自托管、数据在本机**：配置、路由表、API Key、请求日志都存放在本机 SQLite；除转发到你配置的上游之外，不向任何第三方发送数据（无云端账号、无遥测回传）。
5. **只承诺 OpenAI 协议**：上游需兼容 OpenAI API（`/v1/chat/completions`、`/v1/embeddings`、`/v1/models` 等）。不要宣称支持 Anthropic / Gemini 等原生协议的转换。
6. **运行时可变、无需重启**：供应商（provider）/ 模型（model）/ 路由（router）/ 客户端密钥都存在数据库里，Web UI、托盘菜单、CLI 任意一处修改都**立即生效**（内部走 `POST /api/reload` 重建路由表），不需要改配置文件、不需要重启进程。
7. **源码已公开、尚未发布版本（现状）**：GitHub 公开仓库已有 `main` 分支源码与 MIT `LICENSE`，但**没有版本 tag、没有 Release、没有预编译产物**。官网首页已在「开源项目」区展示 ntokengo 卡片（**只跳 GitHub，无下载按钮**）；独立产品页 `ntokengo/index.html` 待正式发版后再建。

## 4. 可复用描述模板（按篇幅选用，中英双语）

### 4.1 Slogan（品牌口号）
- zh：你自己的 AI 网关。
- en: Your own AI gateway.

### 4.2 一句话（约 20 字）
- zh：UnboxLumen 出品的开源本地 AI 网关，把多个上游模型服务收进一个 OpenAI 协议地址。
- en: An open-source, self-hosted AI gateway by UnboxLumen — many upstream model services behind one OpenAI-compatible endpoint.

### 4.3 短描述（约 50 字，卡片 / 列表用）
- zh：在本地运行的 AI 网关（开源，MIT 许可）。单进程聚合多个 OpenAI 协议上游，模型映射、优先级回退、密钥与日志都在本机，改配置不用重启。
- en: A self-hosted AI gateway (open source, MIT licensed). One process pools multiple OpenAI-compatible upstreams — model mapping, priority failover, keys and logs stay on your machine; config changes need no restart.

### 4.4 标准描述（约 100 字，产品页 Hero 用）
- zh：ntokengo 是一款开源的本地 AI 网关。在你自己机器上跑一个进程，就能把多个上游 token 服务聚合成一个 OpenAI 协议地址：客户端只认「模型标签」和「路由名」，真实的 upstream 与密钥都由网关维护，换供应商、转密钥、改模型名都不用动客户端。供应商 / 模型 / 路由 / 密钥存放在本地 SQLite，改完立刻生效。
- en: ntokengo is an open-source local AI gateway. Run one process on your own machine and pool multiple upstream token services behind a single OpenAI-protocol endpoint: clients only know model labels and router names, while real upstreams and keys live in the gateway — swap providers, rotate keys, or re-point models without touching any client. Providers, models, routers and keys live in local SQLite and take effect immediately.

### 4.5 长描述（约 250 字，详情页 / GitHub README 用）
- zh：ntokengo 是 UnboxLumen 出品的开源本地 AI 网关（OpenAI 协议反向代理）。它解决的是「一个人/一个小团队同时用好几个模型服务」的日常问题：把多个上游聚合成一个 `127.0.0.1:7842` 地址，客户端只需要改 `base_url`，模型名用你定义的标签或路由名即可。三个概念划分清楚——**供应商**（一条 upstream + 一把 key 的连接模板）、**模型**（上游真实模型名 + 你对外暴露的标签）、**路由**（面向客户端的策略壳，把多个模型按优先级分桶、桶内按权重或轮询挑选，当前桶全部失败才降级下一桶，并支持重试与冷却）。此外还带客户端 API Key（模型白名单 / 预算 / 启停 / 随时查看）、出站网络代理（HTTP / HTTPS / SOCKS5）、内容防火墙、请求日志与用量指标（TTFT、总耗时、token 用量、p50/p95/p99、按模型与按小时聚合）、内置聊天调试页，以及签名校验的自更新。所有数据都在本机 SQLite 里，改完立刻生效，不需要重启。ntokengo 以 MIT 许可开源。
- en: ntokengo is an open-source local AI gateway (an OpenAI-protocol reverse proxy) by UnboxLumen. It solves a daily problem — using several model services at once: pool multiple upstreams behind one `127.0.0.1:7842` endpoint, and clients only need to change `base_url` plus use a label or router name you define. Three concepts stay separate: a **provider** (one upstream URL + one key, as a reusable connection template), a **model** (the real upstream name plus the client-facing label), and a **router** (a client-facing strategy shell that buckets models by priority, picks within a bucket by weight or round-robin, and only falls back to the next bucket when the current one fails entirely, with retries and cooldowns). It also ships client API keys (model allowlist, USD budget, enable/disable, reveal), outbound net proxies (HTTP / HTTPS / SOCKS5), a content firewall, request logs and usage metrics (TTFT, total time, token usage, p50/p95/p99, per-model and per-hour aggregates), a built-in chat playground, and signature-verified self-update. Everything lives in local SQLite and takes effect immediately — no restart. ntokengo is MIT licensed.

## 5. 核心功能清单

| # | 功能（中） | 功能（英） | 说明 |
|---|-----------|-----------|------|
| 1 | 多上游聚合 | Multi-upstream pooling | 一个进程聚合多个 OpenAI 协议上游，客户端只面对一个地址 |
| 2 | 供应商 | Providers | `upstream` + `api_key` 的连接模板；在此转密钥，所有引用它的模型一起生效 |
| 3 | 模型映射 | Model mapping | 每个模型两个名字：对外的 `label`（客户端寻址）与上游真实名 `model`，转发时自动改写 |
| 4 | 路由策略 | Router strategy | 面向客户端的策略壳：模型池按 `priority` 分桶、桶内按 `weight` / 轮询挑选，桶全失败才降级 |
| 5 | 失败重试与冷却 | Retry & cooldown | 429 / 408 / 5xx / 连接错误按类重试；上游失败后进入冷却期（429 60s、鉴权 5min、传输 15s 等） |
| 6 | 客户端 API Key | Client API keys | 名称、模型白名单、USD 预算、启停，支持随时回看完整 key |
| 7 | 出站网络代理 | Net proxies | 每个路由可挂一个 HTTP CONNECT / HTTPS CONNECT / SOCKS5 代理（含跳过 TLS 校验开关） |
| 8 | 内容防火墙 | Content firewall | 内置规则（含私钥/凭证类模式）+ 自定义规则 + 白名单 + 审计记录 |
| 9 | 请求日志与指标 | Logs & metrics | 逐条请求记录：TTFT、总耗时、字节数、状态码、token 用量；聚合出 avg / p50 / p95 / p99、按模型、按小时 |
| 10 | 请求体留档 | Payload capture | 可选保存截断后的请求 / 响应体，逐行上限可配（默认各 10 MiB），保留天数到期由每小时 janitor 清理 |
| 11 | 管理面板访问日志 | Panel access log | 面板自身的 `/api/*` 与页面访问单独记一张表，默认跳过静态资源噪音 |
| 12 | 内置聊天调试页 | Chat playground | 多会话、流式输出的调试用聊天页，用于验证路由与上游是否正常 |
| 13 | 模型价格 | Model prices | 按模型覆盖价格，用于算成本 |
| 14 | 托盘菜单 | Menu bar / tray | 打开各页面、复制 Base URL、流量计数、默认模型一键切换、重载配置、重启、退出 |
| 15 | 命令行 | CLI | `ntokengo models` / `routers` / `keys` 子命令管理，改完自动触发路由重建 |
| 16 | 签名自更新 | Signed self-update | `POST /api/admin/update` 上传新二进制，HMAC-SHA256 + 时间戳校验，`SO_REUSEPORT` 交接，不断连接 |
| 17 | 中英双语 | i18n (en / zh-CN) | 界面与服务端错误信息双语，跟随 `Accept-Language` / `?lang=`，可设默认语言 |
| 18 | 首启向导 | Setup wizard | 首次打开自动引导填写上游与第一个模型，也可用配置或环境变量完成免交互安装 |

## 6. 使用方式

### 6.1 安装（从源码构建）

需要 Go 与 Node（前端 SPA 由 Vite 构建后内嵌进二进制）：

```sh
./install.sh                 # 构建前端 + 编译并安装到 ~/bin/ntokengo
./install.sh /usr/local/bin  # 或指定安装目录
```

Windows 用 `build.ps1`（产物 `bin/ntokengo.exe`），macOS / Linux 用 `build.sh`。

### 6.2 运行

```sh
ntokengo                  # 默认：HTTP 服务 + 托盘图标
ntokengo serve --no-tray  # 仅 HTTP（服务器 / 无桌面环境用这个）
ntokengo serve --db /tmp/test.db --config ./dev.toml
```

Linux 服务器上以 systemd 常驻（仓库内 `deploy/` 提供 service 单元与远程安装脚本）。

### 6.3 客户端接入

客户端把 `base_url` 指向网关即可，`model` 填**模型标签或路由名**：

```sh
curl -X POST http://127.0.0.1:7842/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"model": "gpt4o", "messages": [{"role": "user", "content": "hello"}]}'
```

网关会把 `Authorization` 换成该模型所属供应商的真实 key，并把 `model` 改写成上游真实名。key 未知时返回 404（附带说明是哪一环缺失）。

### 6.4 配置文件与数据位置

- 数据目录：`~/.ntokengo/`（配置 `config.toml` + 数据库 `db/ntokengo.db`），macOS / Linux / WSL 一致。
- 配置写法见仓库内 `config.example.toml`：监听地址、上游与 key、录制开关与保留天数、访问日志、路由重试与冷却、托盘刷新频率等。
- 环境变量可覆盖配置文件（`NTOKENGO_LISTEN`、`NTOKENGO_UPSTREAM`、`NTOKENGO_API_KEY`、`NTOKENGO_LOG_LEVEL` 等）。

## 7. 技术规格

| 规格 | 内容 |
|------|------|
| 后端语言 | Go（`go.mod` 声明 Go 1.27） |
| HTTP 框架 | Gin |
| 数据访问 | gorm + `glebarez/sqlite`（纯 Go SQLite 驱动），WAL 模式、5s busy timeout |
| 托盘 | `gogpu/systray`（需要 CGO 的构建路径） |
| 配置解析 | BurntSushi/toml；日志用 logrus |
| 前端 | Vue 3 + TypeScript + Vite + bootstrap-vue-next + Pinia，经 `//go:embed` 内嵌进单个二进制 |
| 默认端口 | `127.0.0.1:7842` |
| 数据目录 | `~/.ntokengo/`（可用 `--db` / `--config` 覆盖） |
| 日志文件 | macOS：`~/Library/Logs/ntokengo.log` |
| 管理入口 | Web UI（`/`、`/chat`、`/activity`、`/logs`、`/admin/*`、`/settings/*`）、托盘菜单、CLI |
| 对外 API | `/v1/*`（OpenAI 协议反向代理）、`/api/*`（面板与管理）、`/healthz` |

## 8. 仓库与发布现状

| 项目 | 内容 |
|------|------|
| 公开仓库 | https://github.com/unboxlumen/ntokengo （公开，已有 `main` 源码；暂无 Release 与下载） |
| Go module | `github.com/unboxlumen/ntokengo`（仓库名与 module 路径一致） |
| 开发主线 | 内网 GitLab（开发主线），GitHub 作为开源公开仓库 |
| 版本发布 | **尚未发布**：无 tag、无 Release、无预编译产物；官网不开下载入口 |
| 官网页面 | **主页卡片已上线**（`index.html`「开源项目」区，跳 GitHub）；本目录产品页 `ntokengo/index.html` 待正式发版后再建 |
| 许可 | **MIT License**（仓库根 `LICENSE`，Copyright (c) 2026 UnboxLumen） |

## 9. 文案红线（写作时强制遵守）

1. **许可证只写 MIT**：可写「MIT 许可 / MIT License」；不得写成其他许可证（Apache-2.0 / GPL 等），也不得暗示商用需额外授权或存在闭源限制。
2. **不得把它说成"模型服务 / 聊天软件 / 免费的 AI"**：它是自托管的网关，需要你自己提供上游服务与密钥。
3. **不得宣称支持非 OpenAI 协议**（Anthropic / Gemini 等原生协议转换）——上游需兼容 OpenAI 协议。
4. **不得暗示有云端账号、云端同步或遥测**：数据全在本机 SQLite，除转发到你自己配置的上游外不外发。
5. **不得提供尚不存在的下载入口**：仓库为空仓、无 Release，官网在公开发布前不加入 ntokengo 下载按钮或主页卡片。
6. **不得与闭源产品混用措辞**：N 浏览器 / N 文件 / N 搜索是「闭源，保留所有权利」；ntokengo 按**开源项目**表述，两者不可互相套用。
7. 命名：统一写作 **ntokengo**（全小写，不用 "NTokenGo" / "N Token" 等变体）；维护方写「UnboxLumen」。

---

## 关联文件

| 文件 | 用途 |
|------|------|
| `../PRODUCTS.md` | 产品目录（本文档的上级索引） |
| 源码 https://github.com/unboxlumen/ntokengo | ntokengo 公开仓库（MIT 许可，Go module 路径同名） |
| 工作区根 `AGENTS.md` | 工作区强制规则（包大小统计口径、发布工作流等） |
