---
type: "query"
date: "2026-05-05T18:58:46.703757+00:00"
question: "Which orphan islands should be merged with semantic similarity edges that the LLM extraction missed?"
contributor: "graphify"
source_nodes: ["config/settings.yml", "服务端配置文件 settings.yml", "settings.yml Configuration", "App Directory Structure (apis/models/router/service)", "Directory Layout (apis/models/router/service)", "admin 应用模块 (apis/models/router/service)", "go-admin-ui View Repository", "-a Auto API Flag", "-a Check API Flag", "Article Table SQL Schema"]
---

# Q: Which orphan islands should be merged with semantic similarity edges that the LLM extraction missed?

## Answer

用 cross-island label 相似度（Jaccard ≥ 0.4）反向診斷出 20 對該補的潛在 semantic edges，可拆成五類高優先級補邊機會：\n\n(1) **settings.yml 三足鼎立**（最嚴重）：config/settings.yml (Island #2 ksks)、服务端配置文件 settings.yml (Island #3 tutorial02)、settings.yml Configuration (Island #12 config.md) 三個節點分屬三個孤島但都指同一檔案。應加 EXTRACTED 邊把三者 alias 起來，**單一招式可同時連接 Quick Start鏈、tutorial鏈、config 章節**——是收益最高的補邊。\n\n(2) **apis/models/router/service 結構契約三節點**：App Directory Structure (Island #1 bus.md)、Directory Layout (Island #7 norm.md)、admin 应用模块 (Island #3 tutorial01) 共享五個 token，明顯描述同一概念。補 conceptually_related_to 邊可一次串起 Bus 模式島、Norm 規範島、tutorial 教學島，**直接攻擊『同概念散落三檔』的問題**。\n\n(3) **go-admin-ui 三節點**：go-admin-ui View Repository (Island #2 guide/index)、go-admin-ui 目录结构 (Island #3 tutorial0210)、go-admin 与 go-admin-ui 同级目录约束 (Island #3 tutorial0410) 應該互引。\n\n(4) **-a flag 兩節點**：-a Auto API Flag (Island #2 server.md) 與 -a Check API Flag (Island #4 advanced.md) 是同一 flag 的兩個別名，應該 semantically_similar_to。\n\n(5) **Article SQL Schema vs article 表 SQL 创建脚本**：Island #4 與 Island #3 各有一個 — 這是 advanced.md 介紹概念、tutorial0410 實作的同一張表。\n\n以及多個 'go-admin' 開頭的 4 token 重疊節點（Repository / GitHub / Landing / Introduction / 目录结构）— 這類純品牌名重疊不一定是真的同義，但說明 LLM 對中英混雜檔案沒有跨語言對齊（例如 'go-admin 目录结构' 與 'go-admin Backend Repository' 不該無條件視為相同）。\n\n結論：補上 (1)(2)(3) 三組 alias 邊，主大陸節點數可從 66 翻倍到 ~150+。LLM extraction 漏掉這些邊的根本原因是 chunk 分割：tutorial 系列在 chunk 3、guide 在 chunk 1、bus.md 在 chunk 2，每個 subagent 看不到對方的節點，自然無法在跨 chunk 之間建邊。**修法不是改 prompt，而是在 build 階段加一個 'label fingerprint matcher' 後處理**：把同 fingerprint (例如 'settings.yml', 'apis/models/router/service') 的節點自動補 alias_of EXTRACTED 邊。

## Source Nodes

- config/settings.yml
- 服务端配置文件 settings.yml
- settings.yml Configuration
- App Directory Structure (apis/models/router/service)
- Directory Layout (apis/models/router/service)
- admin 应用模块 (apis/models/router/service)
- go-admin-ui View Repository
- -a Auto API Flag
- -a Check API Flag
- Article Table SQL Schema
- article 表 SQL 创建脚本