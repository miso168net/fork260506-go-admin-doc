---
type: "query"
date: "2026-05-05T18:44:40.824360+00:00"
question: "Why does App Directory Structure (apis/models/router/service) bridge API Handlers & Service Layer (community 0), Bus Processing Modes (community 17), and Routing & Auth Middleware (community 7)?"
contributor: "graphify"
source_nodes: ["App Directory Structure (apis/models/router/service)", "Service Module", "Router Module", "Regular Mode Overview", "API Module", "Models Module", "DTO Module"]
---

# Q: Why does App Directory Structure (apis/models/router/service) bridge API Handlers & Service Layer (community 0), Bus Processing Modes (community 17), and Routing & Auth Middleware (community 7)?

## Answer

App Directory Structure 是定義在 docs/intro/advanced/bus.md 中的核心約定：每個業務模組必須由 apis/ + models/ + router/ + service/ + dto/ 五個子目錄組成。它直接 references 六個模組節點，而這六個節點分屬三個不同社群：(1) community 0 (API Handlers & Service Layer) — API Module、Models Module、Service Module、DTO Module（佔據主要程式碼產出）；(2) community 17 (Bus Processing Modes) — Regular Mode Overview（描述該結構在常規模式下如何被使用）；(3) community 7 (Routing & Auth Middleware) — Router Module（負責掛載 middleware/權限/路由規範）。換句話說，這個節點是 go-admin 的物理結構契約：所有跨社群的功能（資料模型→服務→DTO→API Handler→Router→Bus 模式）都必須穿過這個目錄佈局，所以 betweenness centrality 達 0.039（全圖最高之一）。從工程上講：拆分這個約定 = 拆解整個應用層，因此它不是巧合的橋接，而是設計層面的單一真理來源 (single source of structural truth)。

## Source Nodes

- App Directory Structure (apis/models/router/service)
- Service Module
- Router Module
- Regular Mode Overview
- API Module
- Models Module
- DTO Module