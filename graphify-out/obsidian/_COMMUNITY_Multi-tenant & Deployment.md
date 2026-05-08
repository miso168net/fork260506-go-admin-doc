---
type: community
cohesion: 0.15
members: 14
---

# Multi-tenant & Deployment

**Cohesion:** 0.15 - loosely connected
**Members:** 14 nodes

## Members
- [[.env.production VUE_APP_BASE_API]] - document - docs/guide/xmbs.md
- [[Business DB Sharding (registersreplicastables)]] - document - docs/configure/index.md
- [[Docker make build-linuxrundeploy]] - document - docs/guide/xmbs.md
- [[Go Cross-compile (CGO_ENABLED=0)]] - document - docs/guide/xmbs.md
- [[Multi-tenant Mode (databases per host)]] - document - docs/configure/tenant.md
- [[Nginx Reverse Proxy goadminapi - 8000]] - document - docs/guide/xmbs.md
- [[Nginx per-host Reverse Proxy]] - document - docs/configure/tenant.md
- [[Production Deployment Guide]] - document - docs/guide/xmbs.md
- [[Production settings.yml (databasejwtlogger)]] - document - docs/guide/xmbs.md
- [[Shell-based Build & SCP Pipeline]] - document - docs/guide/xmbs.md
- [[VUE_APP_BASE_API empty for multi-tenant]] - document - docs/configure/tenant.md
- [[gorm-based database registers config]] - document - docs/configure/index.md
- [[npm run buildprod]] - document - docs/guide/xmbs.md
- [[settings.dev.yml Local Override]] - document - docs/guide/ksks.md

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/Multi-tenant__Deployment
SORT file.name ASC
```

## Connections to other communities
- 1 edge to [[_COMMUNITY_Go Environment & Modules]]

## Top bridge nodes
- [[settings.dev.yml Local Override]] - degree 2, connects to 1 community