---
type: community
cohesion: 0.33
members: 6
---

# Migration System

**Cohesion:** 0.33 - loosely connected
**Members:** 6 nodes

## Members
- [[migrate flags (-c-d-g-a-h)]] - rationale - docs/intro/cmd/migrate.md
- [[migrate 指令]] - document - docs/intro/cmd/migrate.md
- [[migration 目录结构 (versionversion-local)]] - document - docs/intro/cmd/migrate.md
- [[migration.Migrate.SetVersion]] - code - docs/intro/cmd/migrate.md
- [[sys_migration 表]] - code - docs/intro/cmd/migrate.md
- [[预置表数据迁移流程]] - rationale - docs/intro/cmd/migrate.md

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/Migration_System
SORT file.name ASC
```
