---
type: community
cohesion: 0.20
members: 11
---

# DTO & Search Module

**Cohesion:** 0.20 - loosely connected
**Members:** 11 nodes

## Members
- [[MakeContext.MakeOrm.Bind.MakeService 链式调用]] - rationale - docs/intro/advanced/api.md
- [[Search 模块 (GetNeedSearch  gorm scope)]] - code - docs/intro/advanced/dto.md
- [[SysPost.GetPage 接口函数]] - code - docs/intro/advanced/api.md
- [[SysPostPageReq]] - code - docs/intro/advanced/dto.md
- [[cDto.MakeCondition]] - code - docs/intro/advanced/service.md
- [[cDto.Paginate]] - code - docs/intro/advanced/service.md
- [[common dto.Pagination]] - code - docs/intro/advanced/dto.md
- [[dto 数据传输模块]] - rationale - docs/intro/advanced/dto.md
- [[search struct tag (typecolumntable)]] - rationale - docs/intro/advanced/dto.md
- [[search type 列表 (exactcontainsgtltinisnullorderjoin...)]] - rationale - docs/intro/advanced/dto.md
- [[service.SysPost.GetPage]] - code - docs/intro/advanced/service.md

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/DTO__Search_Module
SORT file.name ASC
```

## Connections to other communities
- 3 edges to [[_COMMUNITY_API & Service Layer (apisrouterservicedtomodels)]]

## Top bridge nodes
- [[service.SysPost.GetPage]] - degree 6, connects to 1 community
- [[SysPost.GetPage 接口函数]] - degree 4, connects to 1 community