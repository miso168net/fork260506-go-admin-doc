---
type: "query"
date: "2026-05-05T18:52:04.739269+00:00"
question: "Why are dumi Static Site Framework, Yarn Development Workflow, miso168net Fork Repository disconnected from the rest of the graph? (110 weakly-connected nodes — possible doc gaps)"
contributor: "graphify"
source_nodes: ["go-admin-doc Project", "dumi Static Site Framework", "Yarn Development Workflow", "miso168net Fork Repository", "Quick Start Guide", "tutorial0310", "FAQ Index"]
---

# Q: Why are dumi Static Site Framework, Yarn Development Workflow, miso168net Fork Repository disconnected from the rest of the graph? (110 weakly-connected nodes — possible doc gaps)

## Answer

圖譜總共 222 節點分為 16 個連通分量，最大的『主大陸』只有 66 節點（30%），其餘 156 節點（70%）散落在 15 座孤島上——這比預想的更嚴重。主大陸由 community 0/6/7/9/17（API/Models/Router/Runtime/Bus 模式）組成，幾乎涵蓋整個 docs/intro/advanced/ 目錄；剩下的所有功能都是孤島：(1) Island #12 (README) — dumi/Yarn/go-admin-doc 三個節點只在 README 內部互引，沒有任何邊指向 docs/ 內容，因為 README 講的是『這份文件如何建構』，跟產品本身正交；(2) Island #10 (x_fork.branch-origin) — fork/upstream/main 分支記錄是專案治理 metadata，不該跟產品文件耦合；(3) Island #1 (42 節點，新手安裝鏈) — Quick Start + 安裝 + Migration + 環境變數整條鏈獨立成島，跟主大陸的 API 層完全沒有 references；(4) Island #2 (39 節點，tutorial 鏈) — docs/intro/advanced/tutorial*.md 整批教學是另一座大島，跟同目錄的非 tutorial 文件 (api.md/router.md/service.md) 也沒有 cross-references；(5) 其他 11 座小島 — FAQ、Norms、VIP、Jobs、Air、Config、Swagger、Help、cmd/config 各自封閉。\n\n結論：這不是 abstraction gap，是 **文件鏈接缺口**——作者沒在 markdown 內部寫 cross-reference 連結。每份 .md 都是自包含的閱讀單位，於是 LLM 抽取出的節點只能在同一檔案內互連。具體建議：(a) tutorial0310.md 應該明確寫『請先閱讀 api.md / service.md』來把 Island #2 接到主大陸；(b) ksks.md (Quick Start) 應該在 migrate 步驟連到 cmd/migrate/migrate.md，把 Island #1 的 42 節點併入主大陸；(c) README 應該至少 link 到 docs/index.md 或 docs/guide/index.md；(d) FAQ、Norms、Jobs、Air、Swagger 都各自孤立 — 表示這些章節被當作『附錄』而非主流程的一部分，新手沿著主動線根本走不到。fork branch origin 與 dumi/yarn 維持孤立是合理的（meta-info），但 Island #1 和 Island #2 應該優先連到主大陸。

## Source Nodes

- go-admin-doc Project
- dumi Static Site Framework
- Yarn Development Workflow
- miso168net Fork Repository
- Quick Start Guide
- tutorial0310
- FAQ Index