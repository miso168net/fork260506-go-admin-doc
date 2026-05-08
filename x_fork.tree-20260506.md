# 專案檔案結構與用途註解(2026-05-06 snapshot)

本檔案對應 `tree` 命令在 `fork260506-go-admin-doc/` 根目錄的輸出,
為每個檔案/目錄補上一行用途註解,作為閱讀文件前的索引。

- 命名沿用 `x_fork.graphify-20260506.md` 的「snapshot 日期」慣例。
- `graphify-out/` 是 graphify 工具自動生成的知識圖譜輸出(快取 / Obsidian
  節點筆記 / 報告等),於目錄層級一句話帶過,不深入逐檔列出。
- 其餘文件原始檔(`docs/**/*.md`)、設定、fork 元資料每一檔都附註解。
- **省略項目**:`node_modules/`、`.pnpm-store/`、`dist/`、`.dumi/tmp-production/`
  等本機構建產物 / 套件快取一律不入樹;隱藏的 dotfile / dotdir
  (`.specify/`、`.claude/`、`.dumi/`、`.dumirc.ts`、`.github/`、`.gitignore`、
  `.prettier*`、`.editorconfig`、`.fatherrc.ts`、`.umirc1.ts` 等)沿用原快照
  風格不展開,如要說明請另開一份 config-snapshot 檔。

```
.
├── CLAUDE.md                          # 給 Claude Code 看的專案指令(graphify 規則 + 提示)
├── LICENSE                            # MIT 授權書(沿用上游)
├── README.md                          # 專案 README(dumi 開發指令:install / start / build)
│
├── docs/                              # dumi 文件原始檔(渲染為靜態站的內容根)
│   ├── index.md                       # 站台首頁(go-admin Landing Page;引用 Casbin RBAC)
│   ├── help.md                        # Help 頁 placeholder(暫時空頁,等待補內容)
│   ├── vip.md                         # Pro 版 / VIP 介紹(版本比較表、Pluggable Brick、定價)
│   │
│   ├── configure/                     # 部署 / 多租戶設定章節
│   │   ├── index.md                   # Configure 區段索引;Business DB Sharding 入口
│   │   └── tenant.md                  # 多租戶模式 + Nginx per-host 反向代理
│   │
│   ├── guide/                         # 入門教程(環境、安裝、Quick Start、FAQ、部署)
│   │   ├── index.md                   # Guide 區段索引;go-admin Introduction & Features
│   │   ├── env.md                     # 開發環境總覽(IDE / Go / Node / Yarn 串起來)
│   │   ├── go-install.md              # Golang 安裝(下載點、環境變數、GO111MODULE、GOPROXY)
│   │   ├── go-modules.md              # Go Modules 系統(go.mod、Go 1.16 module 變更)
│   │   ├── ide-env.md                 # IDE 設定(Goland、VS Code)
│   │   ├── vue-install.md             # Node.js / npm 與前端依賴安裝(版本檢查 16.15.0)
│   │   ├── ksks.md                    # Quick Start Guide(env → migrate → server → vue install)
│   │   ├── norm.md                    # 開發規範 v1.4.0+(目錄、import、函式 / router 命名)
│   │   ├── faq.md                     # FAQ(CGO/Windows、MinGW、MySQL refused、Sass、Xcode CLT)
│   │   └── xmbs.md                    # 生產部署(Shell 打包、跨平台編譯、Docker、Nginx)
│   │
│   ├── intro/                         # 進階教程與 CLI 命令參考
│   │   ├── advanced/                  # 架構 / 模組 / 教學流程 / 代碼生成
│   │   │   ├── advanced.md            # 進階教程入口索引(銜接 Quick Start)
│   │   │   ├── tutorial01.md          # 服務端搭建 — 目錄結構
│   │   │   ├── tutorial02.md          # 服務端搭建 — settings.yml 設定檔
│   │   │   ├── tutorial03.md          # 服務端搭建 — API 啟動(go run main.go server)
│   │   │   ├── tutorial0210.md        # 前端搭建 — UI 目錄結構(go-admin-ui)
│   │   │   ├── tutorial0220.md        # 前端搭建 — 環境變數 (.env.development/.env.production)
│   │   │   ├── tutorial0230.md        # 前端搭建 — 啟動 (npm run dev)
│   │   │   ├── tutorial0310.md        # 創建文章功能示例(SysPost CRUD 端到端)
│   │   │   ├── tutorial0410.md        # 代碼生成 — gen 配置 + article 表 SQL
│   │   │   ├── tutorial0420.md        # 代碼生成 — 預覽生成代碼(Access.ts/Routes.ts)
│   │   │   ├── tutorial0430.md        # 代碼生成 — 一鍵菜單生成設定
│   │   │   ├── tutorial0440.md        # 代碼生成 — 菜單綁定接口
│   │   │   ├── tutorial0450.md        # 代碼生成 — 配置角色權限
│   │   │   ├── tutorial0460.md        # 代碼生成 — 功能驗證(增刪改查)
│   │   │   ├── air.md                 # Air 熱重載(.air.toml、cosmtrek/air、Run/Watcher)
│   │   │   ├── api.md                 # API Module(handler 七大函式、apis.Api Base、JWT user)
│   │   │   ├── bus.md                 # Bus 處理模式(Regular vs Actions;兩種模式取捨)
│   │   │   ├── config.md              # 設定系統(settings.yml、extend.go、env-specific files)
│   │   │   ├── core.md                # SDK Runtime 核心(sdk.Runtime、Memory Queue、UserCtx)
│   │   │   ├── db.md                  # 資料庫模型與驅動(MySQL / Postgres / SQLite + 特殊欄位)
│   │   │   ├── dto.md                 # DTO Module(Search、Pagination、Generate Method)
│   │   │   ├── jobs.md                # 排程任務(JobCore、ExecJob、HttpJob、InitJob)
│   │   │   ├── models.md              # Models Module(ActiveRecord、ControlBy/ModelTime、TableName)
│   │   │   ├── pro-gen-code.md        # Pro 代碼生成工具(帶 / 不帶權限的兩條路徑)
│   │   │   ├── router.md              # Router Module(authMiddleware、AuthCheckRole、命名規範)
│   │   │   ├── service.md             # Service Module(Get/GetPage/Insert/Update/Remove)
│   │   │   └── swagger.md             # Swagger 文件產出
│   │   │
│   │   └── cmd/                       # CLI 子命令參考(go-admin CLI Command Set)
│   │       ├── app.md                 # `app` 命令(模組分離;由 createapp 改名)
│   │       ├── config.md              # `config` 命令(產生 / 驗證設定)
│   │       ├── install.md             # `install` 命令(go-admin-pro 專屬)
│   │       ├── migrate.md             # `migrate` 命令(version vs version-local;sys_migration)
│   │       └── server.md              # `server` 命令(啟動 API、-a 自動接口托管、-c 設定路徑)
│   │
│   └── superpowers/                   # superpowers/brainstorming 產出(spec / 配套檔)
│       └── spec/
│           ├── 2026-05-07-learning-docs.md   # Quick Start with Docker Compose 學習教材(zh-TW)
│           └── docker-compose.yml             # 配套 4-service compose stack(mysql/migrate/backend/frontend)
│
├── graphify-out/                      # graphify 知識圖譜輸出(整個目錄由工具生成,勿手改)
│
├── package.json                       # pnpm 專案宣告;dumi build/dev/start scripts、commitlint、lint-staged
├── pnpm-lock.yaml                     # pnpm 鎖定檔(reproducible build 來源 — 對應 constitution III)
├── tsconfig.json                      # TypeScript 編譯設定(供 dumi 用)
│
├── x_fork.branch-origin.md            # fork 由來:main 從 master @ 424855a 拉出的紀錄
├── x_fork.graphify-20260506.md        # graphify session 紀錄(本次 fork 生圖譜的過程)
└── x_fork.tree-20260506.md            # 本檔案(專案結構索引)
```

---

## 補充說明

**幾個重要慣例**:

- `docs/**/*.md` 都是 dumi 文件原始檔,渲染輸出為靜態站。一個檔案 = 一個頁面。
- `tutorialNN.md` 是教學系列,前綴決定章節:`01-03` 為服務端搭建、`0210-0230`
  為前端搭建、`0310` 為功能示例、`0410-0460` 為代碼生成的六步流程。
- 各區段的 `index.md` 是該章節入口頁,通常含子頁的導航。
- `docs/superpowers/spec/` 是 superpowers / brainstorming 工作流的產出存放處,
  spec 檔(`YYYY-MM-DD-<topic>-design.md`)與配套檔(如 `docker-compose.yml`)
  並列。雖然位於 `docs/` 下,**不打算公開渲染為站台頁面** — 對應策略由
  `.dumirc.ts` 控制(若有需要可在該檔加 ignore)。
- `x_fork.*` 開頭的檔案是這份 fork 的 meta 紀錄,純新增、不影響上游可合併性
  (對應 constitution Principle II — Upstream Diff Discipline),可安全忽略或刪除。
- `graphify-out/` 由 `graphify update .` 產生 / 更新,不會被 dumi build 編入站台
  (dumi 預設只掃 `docs/`),所以可以放心放在專案根目錄。

**最常被引用的 god nodes**(來自 graphify GRAPH_REPORT):

| 節點 | 所在檔案 | 邊數 |
|---|---|---|
| `Service Module` | `docs/intro/advanced/service.md` | 10 |
| `Quick Start Guide` | `docs/guide/ksks.md` | 9 |
| `DTO Module` | `docs/intro/advanced/dto.md` | 9 |
| `go-admin Landing Page` | `docs/index.md` | 8 |
| `API Module` | `docs/intro/advanced/api.md` | 8 |
| `服务端配置文件 settings.yml` | `docs/intro/advanced/config.md` + `tutorial02.md` | 8 |
| `Router Module` | `docs/intro/advanced/router.md` | 7 |
| `go-admin Introduction & Features` | `docs/guide/index.md` | 6 |
| `App Directory Structure (apis/models/router/service)` | `docs/intro/advanced/tutorial01.md` + `norm.md` | 6 |
| `Pro Code Generator Tool` | `docs/intro/advanced/pro-gen-code.md` | 6 |

讀文件建議從這幾個入口往外爬,效率最高。整個語料約 9,826 字,GRAPH_REPORT
也直接點明「Corpus fits in a single context window — you may not need a graph」,
所以全文一次掃讀也是可行選項。

---

## 修訂紀錄

| 日期 | 修改 |
|---|---|
| 2026-05-07 | 初版建立(由 `tree` 輸出 + 註解構成) |
| 2026-05-08 | 補入 `docs/superpowers/spec/`(brainstorming 產出)、自身 `x_fork.tree-20260506.md`;明列省略項目清單 |

*本檔案於 2026-05-07 由 Claude Code 依 `tree` 輸出生成,日期 `20260506`
沿用 fork 的 snapshot 命名慣例(對齊 `x_fork.graphify-20260506.md`)。*
