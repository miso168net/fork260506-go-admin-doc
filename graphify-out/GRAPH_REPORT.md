# Graph Report - .  (2026-05-06)

## Corpus Check
- Corpus is ~9,826 words - fits in a single context window. You may not need a graph.

## Summary
- 222 nodes · 239 edges · 23 communities detected
- Extraction: 91% EXTRACTED · 9% INFERRED · 0% AMBIGUOUS · INFERRED: 21 edges (avg confidence: 0.8)
- Token cost: 0 input · 0 output

## Community Hubs (Navigation)
- [[_COMMUNITY_API Handlers & Service Layer|API Handlers & Service Layer]]
- [[_COMMUNITY_Setup & Repository Intro|Setup & Repository Intro]]
- [[_COMMUNITY_Frontend Setup Tutorials|Frontend Setup Tutorials]]
- [[_COMMUNITY_Pro Code Generator|Pro Code Generator]]
- [[_COMMUNITY_Code Generation Tutorial|Code Generation Tutorial]]
- [[_COMMUNITY_Multi-tenant & Deployment|Multi-tenant & Deployment]]
- [[_COMMUNITY_Database Models & Drivers|Database Models & Drivers]]
- [[_COMMUNITY_Routing & Auth Middleware|Routing & Auth Middleware]]
- [[_COMMUNITY_Migration System|Migration System]]
- [[_COMMUNITY_SDK Runtime Core|SDK Runtime Core]]
- [[_COMMUNITY_FAQ & Troubleshooting|FAQ & Troubleshooting]]
- [[_COMMUNITY_Dev Norms & App Command|Dev Norms & App Command]]
- [[_COMMUNITY_Pro Edition & Bricks|Pro Edition & Bricks]]
- [[_COMMUNITY_Go Environment & Modules|Go Environment & Modules]]
- [[_COMMUNITY_Scheduled Jobs|Scheduled Jobs]]
- [[_COMMUNITY_Air Hot Reload|Air Hot Reload]]
- [[_COMMUNITY_Fork Branch Origin|Fork Branch Origin]]
- [[_COMMUNITY_Bus Processing Modes|Bus Processing Modes]]
- [[_COMMUNITY_Config System|Config System]]
- [[_COMMUNITY_Doc Site Build|Doc Site Build]]
- [[_COMMUNITY_Swagger Docs|Swagger Docs]]
- [[_COMMUNITY_Help Placeholder|Help Placeholder]]
- [[_COMMUNITY_Config Command|Config Command]]

## God Nodes (most connected - your core abstractions)
1. `Service Module` - 10 edges
2. `Quick Start Guide` - 9 edges
3. `DTO Module` - 9 edges
4. `go-admin Landing Page` - 8 edges
5. `API Module` - 8 edges
6. `服务端配置文件 settings.yml` - 8 edges
7. `Router Module` - 7 edges
8. `go-admin Introduction & Features` - 6 edges
9. `App Directory Structure (apis/models/router/service)` - 6 edges
10. `Pro Code Generator Tool` - 6 edges

## Surprising Connections (you probably didn't know these)
- `article 表 SQL 创建脚本` --semantically_similar_to--> `创建文章功能示例`  [INFERRED] [semantically similar]
  docs/intro/advanced/tutorial0410.md → docs/intro/advanced/tutorial0310.md
- `User Context Helpers (GetUserId/Name/Role/Dept)` --semantically_similar_to--> `jwtauth/user Package`  [INFERRED] [semantically similar]
  docs/intro/advanced/core.md → docs/intro/advanced/api.md
- `go-admin Introduction & Features` --references--> `Casbin RBAC Model`  [INFERRED]
  docs/guide/index.md → docs/index.md
- `Business DB Sharding` --semantically_similar_to--> `Multi-tenant Mode`  [INFERRED] [semantically similar]
  docs/configure/index.md → docs/configure/tenant.md
- `Nginx Configuration for go-admin` --semantically_similar_to--> `Nginx Per-Host Reverse Proxy`  [INFERRED] [semantically similar]
  docs/guide/xmbs.md → docs/configure/tenant.md

## Hyperedges (group relationships)
- **go-admin CLI Command Set** — app_app_command, config_config_command, install_install_command, migrate_migrate_command, server_server_command [EXTRACTED 0.95]
- **Quick Start Setup Flow** — env_environment_variables, goinstall_go_environment_install, ksks_quick_start, ksks_migrate_command, ksks_server_command, vueinstall_node_npm_install [EXTRACTED 0.90]
- **Deployment Pipeline (build/upload/restart/nginx)** — xmbs_shell_packaging, xmbs_cross_compile, xmbs_nginx_config, xmbs_vue_build, xmbs_docker_packaging [EXTRACTED 0.90]
- **Regular Mode Layered Architecture (api/router/service/dto/models)** — api_api_module, router_router_module, service_service_module, dto_dto_module, models_models_module [EXTRACTED 0.95]
- **SysPost CRUD Request Flow (handler -> dto -> service -> model)** — api_insert_handler, dto_syspostinsertreq, service_insert_func, models_syspost_model [EXTRACTED 0.90]
- **Memory Queue Event Pipeline (Runtime + Queue + Adapter + Callback)** — core_runtime, core_memory_queue, core_queue_adapter, core_savelogginglog_callback [EXTRACTED 0.90]
- **代码生成完整流程** — tutorial0410_codegen_config, tutorial0420_codegen, tutorial0430_menu_config, tutorial0440_menu_api_binding, tutorial0450_role_permission, tutorial0460_function_verify [EXTRACTED 0.95]
- **前端搭建工作流 (目录/配置/启动)** — tutorial0210_ui_directory_structure, tutorial0220_env_config, tutorial0230_frontend_startup [EXTRACTED 0.90]
- **服务端搭建工作流 (目录/配置/启动)** — tutorial01_directory_structure, tutorial02_config_file, tutorial03_api_startup [EXTRACTED 0.90]

## Communities

### Community 0 - "API Handlers & Service Layer"
Cohesion: 0.09
Nodes (34): API Module, Delete Handler, Get Handler, GetPage Handler, gin-gonic/gin Framework, Insert Handler, jwtauth/user Package, MakeContext/MakeOrm/MakeService Chain (+26 more)

### Community 1 - "Setup & Repository Intro"
Cohesion: 0.08
Nodes (28): Golang Environment Installation, Golang Official Download, Built-in Modules (User/Dept/Role/Menu/Dict), Demo Environments (vue2/vue3/antd pro), Why go-admin (Rationale: Reduce Boilerplate), go-admin Backend Repository, go-admin-ui View Repository, go-admin Introduction & Features (+20 more)

### Community 2 - "Frontend Setup Tutorials"
Cohesion: 0.1
Nodes (24): admin 应用模块 (apis/models/router/service), app 应用文件夹, go-admin 目录结构, jobs 自动化作业模块, src 源码目录 (api/components/router/store/views), go-admin-ui 目录结构, 开发与生产环境配置切换, 前端环境变量配置 (.env.development/.env.production) (+16 more)

### Community 3 - "Pro Code Generator"
Cohesion: 0.13
Nodes (16): Article Table SQL Schema, -a Check API Flag, Code Generator Tool (开发工具生成代码), Role Menu Authorization, Access.ts Preview, Agent Startup, Code Preview, Custom Form (开发中) (+8 more)

### Community 4 - "Code Generation Tutorial"
Cohesion: 0.14
Nodes (15): 代码生成 gen 配置, article 表 SQL 创建脚本, 代码生成配置修改, go-admin 与 go-admin-ui 同级目录约束 (rationale), 代码生成 (带权限/不带权限), 预览生成代码, 代码生成流程, 表结构导入 (+7 more)

### Community 5 - "Multi-tenant & Deployment"
Cohesion: 0.15
Nodes (13): Business DB Sharding, GORM registers/replicas Config, Why Built-in Sharding (Rationale), databases YAML Config (per-host), Multi-tenant Mode, Nginx Per-Host Reverse Proxy, No Secondary Dev Required (Rationale), Go Cross-compilation (Mac/Linux/Windows) (+5 more)

### Community 6 - "Database Models & Drivers"
Cohesion: 0.2
Nodes (10): Database Specification, deleted_at Recycle Bin Rationale, MySQL Driver Config, Postgres Driver Config, Special Fields (id/create_by/update_by/created_at/updated_at/deleted_at), SQLite3 Driver Config, ActiveRecord Interface, ControlBy and ModelTime Embedded (+2 more)

### Community 7 - "Routing & Auth Middleware"
Cohesion: 0.22
Nodes (10): apis.Api Base Struct, SysPost API Struct, Anonymous Access, AuthCheckRole Middleware, authMiddleware (JWT), Login-only Authentication, register{业务}Router Naming Convention, Role-based Authentication (+2 more)

### Community 8 - "Migration System"
Cohesion: 0.25
Nodes (8): migrate Command, Why Separate version vs version-local (Rationale), migrate Command, cmd/migrate/migration Directory Layout, SQL Seed Data Pattern, sys_migration Tracking Table, version-local New Migrations, version System Migrations (read-only)

### Community 9 - "SDK Runtime Core"
Cohesion: 0.25
Nodes (8): Runtime DB Map (GetDb/GetDbByKey/SetDb), Memory Queue, Memory Queue vs Professional MQ Rationale, Queue Adapter, sdk.Runtime, SaveLoginLog Callback, SetConfig/GetConfig, User Context Helpers (GetUserId/Name/Role/Dept)

### Community 10 - "FAQ & Troubleshooting"
Cohesion: 0.29
Nodes (7): CGO Issue on Windows, FAQ Index, MinGW-W64 GCC-8.1.0 Solution, MySQL Connect Refused Issue, Error: requires at least one arg, Dart Sass / Division Deprecation, macOS Xcode CLT Missing

### Community 11 - "Dev Norms & App Command"
Cohesion: 0.29
Nodes (7): app Command, App Concept (project module separation), createapp -> app Rename Rationale, Code Norm (imports, function naming), Development Norms (v1.4.0+), Directory Layout (apis/models/router/service), Router Norm (api/{version}/{module}/{name})

### Community 12 - "Pro Edition & Bricks"
Cohesion: 0.33
Nodes (6): install Command (go-admin-pro), Pluggable Brick Modules (Cron/OXS/CMS/Workflow), License & Disclaimer Statements, Edition Comparison Table, go-admin-pro V1, Pricing Tier Rationale

### Community 13 - "Go Environment & Modules"
Cohesion: 0.4
Nodes (6): Go Environment Variables, GO111MODULE=on, GOPROXY=https://goproxy.cn, Go 1.16 Module Changes, go.mod Description File, Go Modules System

### Community 14 - "Scheduled Jobs"
Cohesion: 0.4
Nodes (6): ExamplesOne Struct, ExecJob Function Type, HttpJob Interface Type, InitJob Registration, JobCore Interface, Scheduled Jobs

### Community 15 - "Air Hot Reload"
Cohesion: 0.4
Nodes (5): Air Hot Reload, .air.toml Configuration File, github.com/cosmtrek/air Package, Run Block, Watcher Block

### Community 16 - "Fork Branch Origin"
Cohesion: 0.5
Nodes (4): miso168net Fork Repository, main Branch Origin Record, Unify Default Branch as main (Rationale), go-admin-team/go-admin-doc Upstream

### Community 17 - "Bus Processing Modes"
Cohesion: 0.5
Nodes (4): Actions Mode, Regular Mode (常规模式), Regular Mode Overview, Two Processing Modes Rationale

### Community 18 - "Config System"
Cohesion: 0.5
Nodes (4): Environment-specific Config Files, config/extend.go File, Extend Configuration Node, settings.yml Configuration

### Community 19 - "Doc Site Build"
Cohesion: 0.67
Nodes (3): dumi Static Site Framework, go-admin-doc Project, Yarn Development Workflow

### Community 20 - "Swagger Docs"
Cohesion: 1.0
Nodes (2): go generate Command, Swagger Documentation

### Community 21 - "Help Placeholder"
Cohesion: 1.0
Nodes (1): Help Page (placeholder)

### Community 22 - "Config Command"
Cohesion: 1.0
Nodes (1): config Command

## Knowledge Gaps
- **110 isolated node(s):** `dumi Static Site Framework`, `Yarn Development Workflow`, `miso168net Fork Repository`, `go-admin-team/go-admin-doc Upstream`, `Unify Default Branch as main (Rationale)` (+105 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **Thin community `Swagger Docs`** (2 nodes): `go generate Command`, `Swagger Documentation`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Help Placeholder`** (1 nodes): `Help Page (placeholder)`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Config Command`** (1 nodes): `config Command`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `App Directory Structure (apis/models/router/service)` connect `API Handlers & Service Layer` to `Bus Processing Modes`, `Routing & Auth Middleware`?**
  _High betweenness centrality (0.039) - this node is a cross-community bridge._
- **Why does `Quick Start Guide` connect `Setup & Repository Intro` to `Migration System`, `Go Environment & Modules`?**
  _High betweenness centrality (0.028) - this node is a cross-community bridge._
- **What connects `dumi Static Site Framework`, `Yarn Development Workflow`, `miso168net Fork Repository` to the rest of the system?**
  _110 weakly-connected nodes found - possible documentation gaps or missing edges._
- **Should `API Handlers & Service Layer` be split into smaller, more focused modules?**
  _Cohesion score 0.09 - nodes in this community are weakly interconnected._
- **Should `Setup & Repository Intro` be split into smaller, more focused modules?**
  _Cohesion score 0.08 - nodes in this community are weakly interconnected._
- **Should `Frontend Setup Tutorials` be split into smaller, more focused modules?**
  _Cohesion score 0.1 - nodes in this community are weakly interconnected._
- **Should `Pro Code Generator` be split into smaller, more focused modules?**
  _Cohesion score 0.13 - nodes in this community are weakly interconnected._