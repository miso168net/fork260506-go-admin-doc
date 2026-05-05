# graphify 知識圖譜 session 紀錄

本檔案記錄 **2026-05-06** 對本 repo 執行 `/graphify . --obsidian` 的 session 內容,作為知識圖譜建構與探索的審計軌跡。

| 項目 | 內容 |
|---|---|
| 執行日期 | 2026-05-06 |
| 工具 | graphifyy (Python pipx,Andrej Karpathy 風格 /raw 知識圖譜) |
| 指令 | `/graphify . --obsidian` |
| 處理檔案數 | 49 (全為 .md 文件) |
| 語料規模 | ~9,826 字 → ~13,101 tokens |
| 結果分支 | `graphify-20260506` (已 squash merge 至 `main`) |
| Merge commit | `9d09d87` |
| PR | https://github.com/miso168net/fork260506-go-admin-doc/pull/1 |

## 管線執行摘要

| 步驟 | 結果 |
|---|---|
| Detect | 49 docs / 0 code / 0 paper / 0 image / 0 video |
| AST 抽取 | 跳過(無 code) |
| Semantic 抽取 | 3 個 general-purpose subagent 平行執行,分塊 22+14+13 |
| Chunk 結果 | Chunk 1: 78 nodes / 78 edges / 3 hyperedges<br>Chunk 2: 84 nodes / 95 edges / 3 hyperedges<br>Chunk 3: 39 nodes / 43 edges / 3 hyperedges |
| 合併去重 | **222 unique nodes / 239 edges / 9 hyperedges** |
| Cluster | **23 communities** (Louvain) |
| Token reduction | **17.3x** (avg query ~757 tokens) |

## 23 個社群命名

| ID | 名稱 | 大小 |
|---|---|---|
| 0 | API Handlers & Service Layer | 34 |
| 1 | Setup & Repository Intro | 28 |
| 2 | Frontend Setup Tutorials | 24 |
| 3 | Pro Code Generator | 16 |
| 4 | Code Generation Tutorial | 15 |
| 5 | Multi-tenant & Deployment | 13 |
| 6 | Database Models & Drivers | 10 |
| 7 | Routing & Auth Middleware | 10 |
| 8 | Migration System | 8 |
| 9 | SDK Runtime Core | 8 |
| 10 | FAQ & Troubleshooting | 7 |
| 11 | Dev Norms & App Command | 7 |
| 12 | Pro Edition & Bricks | 6 |
| 13 | Go Environment & Modules | 6 |
| 14 | Scheduled Jobs | 6 |
| 15 | Air Hot Reload | 5 |
| 16 | Fork Branch Origin | 4 |
| 17 | Bus Processing Modes | 4 |
| 18 | Config System | 4 |
| 19 | Doc Site Build | 3 |
| 20 | Swagger Docs | 2 |
| 21 | Help Placeholder | 1 |
| 22 | Config Command | 1 |

## God Nodes (前 5)

1. `Service Module` — 10 edges
2. `Quick Start Guide` — 9 edges
3. `DTO Module` — 9 edges
4. `go-admin Landing Page` — 8 edges
5. `API Module` / `服务端配置文件 settings.yml` — 8 edges

## 探索 Q&A (3 條,已存於 `graphify-out/memory/`)

### Q1: App Directory Structure 為何橋接三個社群?

`App Directory Structure (apis/models/router/service)` 是 betweenness 最高 (0.039) 的橋接節點,1-hop 內直接 references 六個節點分屬三個社群:

- **community 0** (API Handlers & Service Layer): API Module / Models Module / Service Module / DTO Module
- **community 7** (Routing & Auth Middleware): Router Module
- **community 17** (Bus Processing Modes): Regular Mode Overview

**結論**:這不是中介轉發型橋接,而是 go-admin 的**結構契約 (single source of structural truth)**——所有業務模組必須穿過這個目錄佈局,拆解該節點 = 拆解整個應用層。

### Q2: Quick Start Guide 為何橋接 Setup / Migration / Go Environment?

`Quick Start Guide` (`docs/guide/ksks.md`,betweenness 0.028) 是「跑起來必經 9 步」腳本,9 個鄰居跨三個社群,因為它是**時序腳本**而非主題分類:

```
[1-3] 環境變數 + Go 安裝   → comm 13 + comm 1
[4-5] git clone repo        → comm 1
[6]   編輯 settings.yml     → comm 1
[7]   migrate 建表          → comm 8 (唯一接觸 Migration)
[8-9] go run / npm run      → comm 1
```

**設計風險**:三社群之間除了 Quick Start 自己幾乎沒有 cross-reference,Quick Start 失效 = 新手地圖三段斷裂。

### Q3: 圖譜連通性反向診斷與孤島補邊建議

**結構數據**:222 節點分為 **16 個 connected components**,主大陸僅 **66 節點 (30%)**,其餘 **156 節點 (70%) 散落 15 座孤島**。

主大陸幾乎完全是 `docs/intro/advanced/` 的非教學文件 (community 0/6/7/9/17)。15 座孤島中嚴重缺口為:

- Island #1 (42 節點): 新手安裝鏈 (Quick Start + 環境 + Migration + cmd)
- Island #2 (39 節點): tutorial 教學系列

**根本原因**:不是 abstraction gap,是 markdown 內部缺 inline cross-reference。LLM 抽取出的 references 邊只反映文字裡實際寫出的「請參閱 X」,作者沒在 markdown 互引,於是節點只能在同檔內互連。

**chunk 分割盲區**:跨孤島 label 相似度 ≥0.4 找到 20 對該補卻沒補的邊,代表性類別:

1. `settings.yml` 三足鼎立 (Island #1 / #2 / #11 各一個同名節點)
2. `apis/models/router/service` 結構契約三節點 (主大陸 / Island #6 / Island #2)
3. `go-admin-ui` 三節點散落
4. `-a` flag 兩個別名 (server.md / advanced.md)
5. Article SQL 概念—實作對應 (advanced.md / tutorial0410)

**修法建議**:
- 文件層面: tutorial 系列加 inline link 至 `api.md`/`service.md`/`migrate.md`,可預估把主大陸節點數翻倍至 ~150+
- 工具層面: `graphify.build` 階段加 label fingerprint matcher 後處理,自動補 `alias_of` EXTRACTED 邊

## 產出物

| 檔案 | 用途 |
|---|---|
| `graphify-out/GRAPH_REPORT.md` | 審計報告 (God Nodes / Surprising Connections / Suggested Questions) |
| `graphify-out/graph.html` | 互動圖 (瀏覽器開啟) |
| `graphify-out/graph.json` | GraphRAG-ready 圖譜資料 |
| `graphify-out/obsidian/` | Obsidian vault (245 notes + graph.canvas) |
| `graphify-out/cache/` | 49 檔語意抽取快取 (供 --update 增量重抽) |
| `graphify-out/manifest.json` | 檔案 hash manifest |
| `graphify-out/memory/` | 上述 3 條探索 Q&A,下次 `/graphify --update` 會吃進圖譜 |

排除 commit: `graphify-out/.graphify_python` (含本機絕對路徑)。

## 後續操作

- 增量更新: `/graphify . --update`
- 單點查詢: `/graphify query "..."`
- 路徑追蹤: `/graphify path "A" "B"`
- 節點解釋: `/graphify explain "..."`

## 注意事項

本檔案僅為 session 紀錄,可安全忽略或刪除,不影響任何程式邏輯。
