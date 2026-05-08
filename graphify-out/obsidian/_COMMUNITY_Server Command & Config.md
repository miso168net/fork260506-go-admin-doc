---
type: community
cohesion: 0.15
members: 13
---

# Server Command & Config

**Cohesion:** 0.15 - loosely connected
**Members:** 13 nodes

## Members
- [[-a check api 参数]] - rationale - docs/intro/advanced/advanced.md
- [[authMiddleware (jwt.GinJWTMiddleware)]] - code - docs/intro/advanced/router.md
- [[configextend.go Extend struct]] - code - docs/intro/advanced/config.md
- [[configsettings.yml]] - document - docs/intro/advanced/config.md
- [[middleware.AuthCheckRole]] - code - docs/intro/advanced/router.md
- [[register{业务名称}Router 命名规范]] - rationale - docs/intro/advanced/router.md
- [[router 模块]] - document - docs/intro/advanced/router.md
- [[routerCheckRole 注册切片]] - code - docs/intro/advanced/router.md
- [[server -a 自动 api 写入]] - rationale - docs/intro/cmd/server.md
- [[server -c 配置文件参数]] - rationale - docs/intro/cmd/server.md
- [[server 指令]] - document - docs/intro/cmd/server.md
- [[多环境配置文件 (devprodtest)]] - document - docs/intro/advanced/config.md
- [[无需鉴权路由模式]] - rationale - docs/intro/advanced/router.md

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/Server_Command__Config
SORT file.name ASC
```

## Connections to other communities
- 2 edges to [[_COMMUNITY_API & Service Layer (apisrouterservicedtomodels)]]
- 1 edge to [[_COMMUNITY_Codegen UI & Examples]]

## Top bridge nodes
- [[router 模块]] - degree 7, connects to 1 community
- [[-a check api 参数]] - degree 2, connects to 1 community