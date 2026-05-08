---
type: community
cohesion: 0.13
members: 28
---

# API & Service Layer (apis/router/service/dto/models)

**Cohesion:** 0.13 - loosely connected
**Members:** 28 nodes

## Members
- [[Generate 模型转换方法]] - code - docs/intro/advanced/dto.md
- [[GetId 方法]] - code - docs/intro/advanced/dto.md
- [[Swagger 文档生成]] - document - docs/intro/advanced/swagger.md
- [[SysFileDir struct (apis.Api)]] - code - docs/intro/advanced/api.md
- [[SysPost models 结构体]] - code - docs/intro/advanced/models.md
- [[SysPost.Delete 接口函数]] - code - docs/intro/advanced/api.md
- [[SysPost.Get 接口函数]] - code - docs/intro/advanced/api.md
- [[SysPost.Insert 接口函数]] - code - docs/intro/advanced/api.md
- [[SysPost.Update 接口函数]] - code - docs/intro/advanced/api.md
- [[SysPostDeleteReq]] - code - docs/intro/advanced/dto.md
- [[SysPostGetReq]] - code - docs/intro/advanced/dto.md
- [[SysPostInsertReq]] - code - docs/intro/advanced/dto.md
- [[SysPostUpdateReq]] - code - docs/intro/advanced/dto.md
- [[TableName 函数]] - code - docs/intro/advanced/models.md
- [[api 模块]] - document - docs/intro/advanced/api.md
- [[app 文件夹结构 (apismodelsrouterservice)]] - document - docs/intro/advanced/bus.md
- [[common.ControlBy]] - code - docs/intro/advanced/dto.md
- [[models 模块]] - rationale - docs/intro/advanced/models.md
- [[models.ActiveRecord 接口]] - code - docs/intro/advanced/models.md
- [[models.ControlBy]] - code - docs/intro/advanced/models.md
- [[models.ModelTime]] - code - docs/intro/advanced/models.md
- [[service 模块]] - document - docs/intro/advanced/service.md
- [[service.SysPost]] - code - docs/intro/advanced/service.md
- [[service.SysPost.Get]] - code - docs/intro/advanced/service.md
- [[service.SysPost.Insert]] - code - docs/intro/advanced/service.md
- [[service.SysPost.Remove]] - code - docs/intro/advanced/service.md
- [[service.SysPost.Update]] - code - docs/intro/advanced/service.md
- [[user 上下文 API (GetUserIdGetUserNameGetRoleIdGetRoleKeyGetRoleNameGetDeptIdGetDeptName)]] - code - docs/intro/advanced/core.md

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/API__Service_Layer_apis/router/service/dto/models
SORT file.name ASC
```

## Connections to other communities
- 3 edges to [[_COMMUNITY_DTO & Search Module]]
- 2 edges to [[_COMMUNITY_Server Command & Config]]
- 1 edge to [[_COMMUNITY_Codegen UI & Examples]]
- 1 edge to [[_COMMUNITY_SDK Runtime Core]]

## Top bridge nodes
- [[api 模块]] - degree 9, connects to 2 communities
- [[app 文件夹结构 (apismodelsrouterservice)]] - degree 5, connects to 2 communities
- [[SysPost models 结构体]] - degree 12, connects to 1 community
- [[service.SysPost]] - degree 6, connects to 1 community
- [[user 上下文 API (GetUserIdGetUserNameGetRoleIdGetRoleKeyGetRoleNameGetDeptIdGetDeptName)]] - degree 4, connects to 1 community