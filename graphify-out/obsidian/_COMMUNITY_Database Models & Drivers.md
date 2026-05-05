---
type: community
cohesion: 0.20
members: 10
---

# Database Models & Drivers

**Cohesion:** 0.20 - loosely connected
**Members:** 10 nodes

## Members
- [[ActiveRecord Interface]] - document - docs/intro/advanced/models.md
- [[ControlBy and ModelTime Embedded]] - document - docs/intro/advanced/models.md
- [[Database Specification]] - document - docs/intro/advanced/db.md
- [[MySQL Driver Config]] - document - docs/intro/advanced/db.md
- [[Postgres Driver Config]] - document - docs/intro/advanced/db.md
- [[SQLite3 Driver Config]] - document - docs/intro/advanced/db.md
- [[Special Fields (idcreate_byupdate_bycreated_atupdated_atdeleted_at)]] - document - docs/intro/advanced/db.md
- [[SysPost Model]] - document - docs/intro/advanced/models.md
- [[TableName Method]] - document - docs/intro/advanced/models.md
- [[deleted_at Recycle Bin Rationale]] - document - docs/intro/advanced/db.md

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/Database_Models_&_Drivers
SORT file.name ASC
```

## Connections to other communities
- 1 edge to [[_COMMUNITY_API Handlers & Service Layer]]

## Top bridge nodes
- [[SysPost Model]] - degree 4, connects to 1 community