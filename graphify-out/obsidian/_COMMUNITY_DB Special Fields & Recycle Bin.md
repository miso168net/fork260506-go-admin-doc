---
type: community
cohesion: 1.00
members: 2
---

# DB Special Fields & Recycle Bin

**Cohesion:** 1.00 - tightly connected
**Members:** 2 nodes

## Members
- [[deleted_at 回收站机制]] - rationale - docs/intro/advanced/db.md
- [[数据库特殊字段规范]] - rationale - docs/intro/advanced/db.md

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/DB_Special_Fields__Recycle_Bin
SORT file.name ASC
```
