---
type: community
cohesion: 0.25
members: 8
---

# Migration System

**Cohesion:** 0.25 - loosely connected
**Members:** 8 nodes

## Members
- [[SQL Seed Data Pattern]] - document - docs/intro/cmd/migrate.md
- [[Why Separate version vs version-local (Rationale)]] - document - docs/intro/cmd/migrate.md
- [[cmdmigratemigration Directory Layout]] - document - docs/intro/cmd/migrate.md
- [[migrate Command]] - document - docs/guide/ksks.md
- [[migrate Command_1]] - document - docs/intro/cmd/migrate.md
- [[sys_migration Tracking Table]] - document - docs/intro/cmd/migrate.md
- [[version System Migrations (read-only)]] - document - docs/intro/cmd/migrate.md
- [[version-local New Migrations]] - document - docs/intro/cmd/migrate.md

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/Migration_System
SORT file.name ASC
```

## Connections to other communities
- 1 edge to [[_COMMUNITY_Setup & Repository Intro]]

## Top bridge nodes
- [[migrate Command]] - degree 2, connects to 1 community