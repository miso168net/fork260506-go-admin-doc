# Graph Report - .  (2026-05-08)

## Corpus Check
- 58 files · ~14,584 words
- Verdict: corpus is large enough that graph structure adds value.

## Summary
- 242 nodes · 286 edges · 28 communities (23 shown, 5 thin omitted)
- Extraction: 92% EXTRACTED · 8% INFERRED · 0% AMBIGUOUS · INFERRED: 22 edges (avg confidence: 0.83)
- Token cost: 176,455 input · 44,113 output

## Community Hubs (Navigation)
- [[_COMMUNITY_Fork Meta & Graphify Rules|Fork Meta & Graphify Rules]]
- [[_COMMUNITY_(singleton) SpecKit Plan Reference|(singleton) SpecKit Plan Reference]]
- [[_COMMUNITY_go-admin Introduction & Features|go-admin Introduction & Features]]
- [[_COMMUNITY_Go Environment & Modules|Go Environment & Modules]]
- [[_COMMUNITY_(singleton) Help Page Placeholder|(singleton) Help Page Placeholder]]
- [[_COMMUNITY_App & Install Commands|App & Install Commands]]
- [[_COMMUNITY_Multi-tenant & Deployment|Multi-tenant & Deployment]]
- [[_COMMUNITY_Scheduled Jobs|Scheduled Jobs]]
- [[_COMMUNITY_SpecKit Plan Reference|SpecKit Plan Reference]]
- [[_COMMUNITY_Codegen UI & Examples|Codegen UI & Examples]]
- [[_COMMUNITY_Server Command & Config|Server Command & Config]]
- [[_COMMUNITY_Help Placeholder|Help Placeholder]]
- [[_COMMUNITY_Module Roots + Read Path (Get) + Swagger|Module Roots + Read Path (Get) + Swagger]]
- [[_COMMUNITY_DTO & Search Module|DTO & Search Module]]
- [[_COMMUNITY_InsertDelete Path + User Audit Context|Insert/Delete Path + User Audit Context]]
- [[_COMMUNITY_DTO Foundations + Update Pipeline|DTO Foundations + Update Pipeline]]
- [[_COMMUNITY_Migration System|Migration System]]
- [[_COMMUNITY_Config Command Placeholder|Config Command Placeholder]]
- [[_COMMUNITY_(singleton) 支持的 DB (mysqlsqlite3postgres)|(singleton) 支持的 DB (mysql/sqlite3/postgres)]]
- [[_COMMUNITY_Pro Edition & Pricing|Pro Edition & Pricing]]
- [[_COMMUNITY_Models Layer (SysPost + Interfaces)|Models Layer (SysPost + Interfaces)]]
- [[_COMMUNITY_Supported DB Drivers|Supported DB Drivers]]
- [[_COMMUNITY_(singleton) config 指令 (更新中)|(singleton) config 指令 (更新中)]]
- [[_COMMUNITY_IDE Setup (GolandVS Code)|IDE Setup (Goland/VS Code)]]
- [[_COMMUNITY_Project Directory Structure (backend + frontend)|Project Directory Structure (backend + frontend)]]
- [[_COMMUNITY_Docker Compose Quick Start Tutorial|Docker Compose Quick Start Tutorial]]
- [[_COMMUNITY_Code Generation Workflow|Code Generation Workflow]]
- [[_COMMUNITY_Docker Compose Stack Definition|Docker Compose Stack Definition]]

## God Nodes (most connected - your core abstractions)
1. `Quick Start Guide` - 12 edges
2. `SysPost models 结构体` - 12 edges
3. `Backend settings.yml Configuration` - 11 edges
4. `go-admin Quick Start with Docker Compose Tutorial` - 10 edges
5. `api 模块` - 9 edges
6. `compose service: backend (golang:1.22-alpine)` - 9 edges
7. `go-admin-pro 代码生成工具` - 8 edges
8. `compose service: migrate (one-shot)` - 8 edges
9. `compose service: frontend (node:16.15-alpine)` - 8 edges
10. `Production Deployment Guide` - 7 edges

## Surprising Connections (you probably didn't know these)
- `dumi Static Site Framework` --cites--> `go-admin Introduction & Features`  [EXTRACTED]
  README.md → docs/guide/index.md
- `Q2 Quick Start as Temporal Script Bridge` --rationale_for--> `Quick Start Guide`  [EXTRACTED]
  x_fork.graphify-20260506.md → docs/guide/ksks.md
- `Top God Nodes (from GRAPH_REPORT)` --references--> `Quick Start Guide`  [EXTRACTED]
  x_fork.tree-20260506.md → docs/guide/ksks.md
- `admin Module (apis/models/router/service)` --cites--> `Memory: Orphan Island Semantic Merge Recommendations`  [EXTRACTED]
  docs/intro/advanced/tutorial01.md → graphify-out/memory/query_20260505_185846_which_orphan_islands_should_be_merged_with_semanti.md
- `Backend settings.yml Configuration` --semantically_similar_to--> `.env.development / .env.production`  [INFERRED] [semantically similar]
  docs/intro/advanced/tutorial02.md → docs/intro/advanced/tutorial0220.md

## Hyperedges (group relationships)
- **Quick Start End-to-End Flow** — env_go_modules_environment, goinstall_golang_install, ksks_quick_start_guide, ksks_migrate_command, ksks_server_command, ksks_npm_run_dev [EXTRACTED 0.95]
- **App Directory Structural Contract** — norm_app_directory_structure, graphify_qa_app_directory_bridge, tree_god_nodes_table [EXTRACTED 0.90]
- **Production Deploy Stack (Settings/Nginx/Build)** — xmbs_settings_yml_production, xmbs_nginx_reverse_proxy, xmbs_shell_build_pipeline, xmbs_env_production_base_api [EXTRACTED 0.90]
- **SysPost CRUD 业务链 (router→api→service→dto→models)** — router_module, api_getpage_func, service_getpage, dto_pagereq, models_syspost [EXTRACTED 1.00]
- **go-admin 分层架构 (apis/models/router/service/dto)** — bus_app_structure, api_module, models_module, router_module, service_module, dto_module [EXTRACTED 1.00]
- **Job 注册执行流程** — jobs_jobcore_iface, jobs_examplesone, jobs_initjob [EXTRACTED 1.00]
- **6-Step Codegen Tutorial Flow (0410-0460)** — tutorial0410_codegen_settings, tutorial0420_codegen_workflow, tutorial0430_one_click_menu, tutorial0440_menu_api_binding, tutorial0450_role_permissions, tutorial0460_crud_validation [EXTRACTED 1.00]
- **Compose Dependency Chain (mysql -> migrate -> backend -> frontend)** — compose_service_mysql, compose_service_migrate, compose_service_backend, compose_service_frontend [EXTRACTED 1.00]
- **Learning Docs 7 Phases (0-6)** — learning_docs_phase0_precheck, learning_docs_phase1_clone, learning_docs_phase2_settings, learning_docs_phase3_compose, learning_docs_phase4_up, learning_docs_phase5_login, learning_docs_phase6_teardown [EXTRACTED 1.00]

## Communities (28 total, 5 thin omitted)

### Community 4 - "Fork Meta & Graphify Rules"
Cohesion: 0.14
Nodes (14): graphify Rules for Claude Code, main branch origin record (2026-05-06), Rename default branch to main, miso168net/fork260506-go-admin-doc, go-admin-team/go-admin-doc, Source HEAD 424855a, graphify session 2026-05-06, graphify Pipeline (Detect/AST/Semantic/Cluster) (+6 more)

### Community 2 - "go-admin Introduction & Features"
Cohesion: 0.12
Nodes (18): go-admin-doc Project README, dumi Static Site Framework, Yarn install/start/build workflow, Q1 App Directory Structure as Structural Contract, Top God Nodes (from GRAPH_REPORT), go-admin Landing Page, Casbin RBAC Access Control, gin / vue / react Tech Stack (+10 more)

### Community 3 - "Go Environment & Modules"
Cohesion: 0.15
Nodes (16): Q2 Quick Start as Temporal Script Bridge, Go Modules Environment Variables, GO111MODULE=on, GOPROXY=https://goproxy.cn, Golang Installation Tutorial, go version verification (1.24.2), Go Modules System, go mod init (+8 more)

### Community 18 - "App & Install Commands"
Cohesion: 0.5
Nodes (4): go-admin-pro V1 Paid Edition, Pluggable Brick System, Edition Comparison Table, Pricing Tiers (Personal/Team/Enterprise)

### Community 5 - "Multi-tenant & Deployment"
Cohesion: 0.15
Nodes (14): Business DB Sharding (registers/replicas/tables), gorm-based database registers config, Multi-tenant Mode (databases per host), Nginx per-host Reverse Proxy, VUE_APP_BASE_API empty for multi-tenant, settings.dev.yml Local Override, Production Deployment Guide, Shell-based Build & SCP Pipeline (+6 more)

### Community 13 - "Scheduled Jobs"
Cohesion: 0.25
Nodes (8): FAQ Troubleshooting, CGO Windows Build Issue (go-sqlite3), MinGW-W64 GCC-8.1.0, Mac Xcode CLT Missing Error, MySQL connection refused 127.0.0.1:3306, Dart Sass / division Deprecation, Error: requires at least one arg, MySQL 8.0+ Required (key length)

### Community 20 - "SpecKit Plan Reference"
Cohesion: 0.67
Nodes (3): IDE Configuration (Goland/VS Code), Goland HelloWorld Setup, VS Code HelloWorld Setup

### Community 9 - "Codegen UI & Examples"
Cohesion: 0.17
Nodes (12): actions 模式, 开发工具生成代码并配置角色授权操作, article 表 SQL 示例, 常规模式, go-admin-pro 代码生成工具, go-admin-agent 启动, 表结构准备 (在线/Sql/Json), 字典下拉框配置 (+4 more)

### Community 8 - "Server Command & Config"
Cohesion: 0.15
Nodes (13): -a check api 参数, config/settings.yml, 多环境配置文件 (dev/prod/test), config/extend.go Extend struct, router 模块, register{业务名称}Router 命名规范, authMiddleware (jwt.GinJWTMiddleware), middleware.AuthCheckRole (+5 more)

### Community 21 - "Help Placeholder"
Cohesion: 0.67
Nodes (3): Air 热加载, .air.toml 配置文件, go get -u github.com/cosmtrek/air

### Community 12 - "Module Roots + Read Path (Get) + Swagger"
Cohesion: 0.25
Nodes (9): api 模块, SysFileDir struct (apis.Api), SysPost.Get 接口函数, app 文件夹结构 (apis/models/router/service), models 模块, service 模块, service.SysPost, service.SysPost.Get (+1 more)

### Community 10 - "DTO & Search Module"
Cohesion: 0.2
Nodes (11): SysPost.GetPage 接口函数, MakeContext.MakeOrm.Bind.MakeService 链式调用, dto 数据传输模块, Search 模块 (GetNeedSearch / gorm scope), search struct tag (type/column/table), search type 列表 (exact/contains/gt/lt/in/isnull/order/join...), SysPostPageReq, common dto.Pagination (+3 more)

### Community 17 - "Insert/Delete Path + User Audit Context"
Cohesion: 0.4
Nodes (5): SysPost.Insert 接口函数, SysPost.Delete 接口函数, user 上下文 API (GetUserId/GetUserName/GetRoleId/GetRoleKey/GetRoleName/GetDeptId/GetDeptName), service.SysPost.Insert, service.SysPost.Remove

### Community 11 - "DTO Foundations + Update Pipeline"
Cohesion: 0.31
Nodes (10): SysPost.Update 接口函数, SysPostInsertReq, SysPostUpdateReq, SysPostGetReq, SysPostDeleteReq, Generate 模型转换方法, GetId 方法, common.ControlBy (+2 more)

### Community 14 - "Migration System"
Cohesion: 0.33
Nodes (7): sdk.Runtime, Runtime.SetConfig, Runtime.GetConfig, 内存队列 (GetMemoryQueue), QueueAdapter (Set/Get/Register), SaveLoginLog 回调示例, Runtime DB APIs (GetDb/GetDbByKey/SetDb)

### Community 15 - "Pro Edition & Pricing"
Cohesion: 0.33
Nodes (6): 定时任务, HttpJob 接口类型, ExecJob 函数类型, JobCore 接口, ExamplesOne 示例, InitJob 注册函数

### Community 19 - "Models Layer (SysPost + Interfaces)"
Cohesion: 0.5
Nodes (4): SysPost models 结构体, TableName 函数, models.ActiveRecord 接口, models.ModelTime

### Community 22 - "Supported DB Drivers"
Cohesion: 0.67
Nodes (3): app 指令, app 概念 (业务隔离), install 指令 (go-admin-pro)

### Community 16 - "IDE Setup (Goland/VS Code)"
Cohesion: 0.33
Nodes (6): migrate 指令, migration 目录结构 (version/version-local), migrate flags (-c/-d/-g/-a/-h), migration.Migrate.SetVersion, sys_migration 表, 预置表数据迁移流程

### Community 0 - "Project Directory Structure (backend + frontend)"
Cohesion: 0.1
Nodes (22): go-admin Backend Directory Structure, app Folder (admin + jobs), jobs Module (Automated Jobs), main.go Entry Point, config/ Configuration Directory, Backend settings.yml Configuration, settings.application Block (mode/host/port), settings.database Block (driver/source DSN) (+14 more)

### Community 1 - "Docker Compose Quick Start Tutorial"
Cohesion: 0.1
Nodes (20): admin Module (apis/models/router/service), Article API Example (apis/article.go), Article Router (router/article.go), GetArticleList Handler, registerArticleRouter Function, gin-gonic/gin, go-admin-core/sdk/pkg/jwtauth, Router Path & Handlers Convention (+12 more)

### Community 6 - "Code Generation Workflow"
Cohesion: 0.16
Nodes (14): settings.gen Block (dbname/frontpath), Codegen Configuration (gen.dbname/gen.frontpath), article Table SQL Schema, go-admin & go-admin-ui Sibling Directory Constraint, Codegen Workflow (Import / Edit / Preview / Generate), Table Structure Import Step, Codegen with Permissions Variant, One-Click Menu Generation (+6 more)

### Community 7 - "Docker Compose Stack Definition"
Cohesion: 0.27
Nodes (14): Phase 4 Stack Startup (mysql/migrate/backend/frontend), go-admin-demo Compose Stack, compose service: mysql (mysql:8.0), compose service: migrate (one-shot), compose service: backend (golang:1.22-alpine), compose service: frontend (node:16.15-alpine), named volume: mysql-data, named volume: go-mod-cache (+6 more)

## Knowledge Gaps
- **117 isolated node(s):** `graphify Rules for Claude Code`, `SpecKit Plan Reference`, `Yarn install/start/build workflow`, `Rename default branch to main`, `miso168net/fork260506-go-admin-doc` (+112 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **5 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `Quick Start Guide` connect `Go Environment & Modules` to `go-admin Introduction & Features`, `Scheduled Jobs`, `Multi-tenant & Deployment`?**
  _High betweenness centrality (0.059) - this node is a cross-community bridge._
- **Why does `Top God Nodes (from GRAPH_REPORT)` connect `go-admin Introduction & Features` to `Go Environment & Modules`, `Fork Meta & Graphify Rules`?**
  _High betweenness centrality (0.046) - this node is a cross-community bridge._
- **Why does `api 模块` connect `Module Roots + Read Path (Get) + Swagger` to `Server Command & Config`, `Insert/Delete Path + User Audit Context`, `DTO & Search Module`, `DTO Foundations + Update Pipeline`?**
  _High betweenness centrality (0.036) - this node is a cross-community bridge._
- **Are the 2 inferred relationships involving `Backend settings.yml Configuration` (e.g. with `config/ Configuration Directory` and `.env.development / .env.production`) actually correct?**
  _`Backend settings.yml Configuration` has 2 INFERRED edges - model-reasoned connections that need verification._
- **What connects `graphify Rules for Claude Code`, `SpecKit Plan Reference`, `Yarn install/start/build workflow` to the rest of the system?**
  _117 weakly-connected nodes found - possible documentation gaps or missing edges._
- **Should `Fork Meta & Graphify Rules` be split into smaller, more focused modules?**
  _Cohesion score 0.14 - nodes in this community are weakly interconnected._
- **Should `go-admin Introduction & Features` be split into smaller, more focused modules?**
  _Cohesion score 0.12 - nodes in this community are weakly interconnected._