---
type: community
cohesion: 0.27
members: 14
---

# Docker Compose Stack Definition

**Cohesion:** 0.27 - loosely connected
**Members:** 14 nodes

## Members
- [[GOPROXY=httpsgoproxy.cn,direct]] - code - docs/superpowers/spec/docker-compose.yml
- [[Phase 4 Stack Startup (mysqlmigratebackendfrontend)]] - document - docs/superpowers/spec/2026-05-07-learning-docs.md
- [[bridge network demo]] - code - docs/superpowers/spec/docker-compose.yml
- [[compose service backend (golang1.22-alpine)]] - code - docs/superpowers/spec/docker-compose.yml
- [[compose service frontend (node16.15-alpine)]] - code - docs/superpowers/spec/docker-compose.yml
- [[compose service migrate (one-shot)]] - code - docs/superpowers/spec/docker-compose.yml
- [[compose service mysql (mysql8.0)]] - code - docs/superpowers/spec/docker-compose.yml
- [[env var GO_ADMIN_PATH]] - code - docs/superpowers/spec/docker-compose.yml
- [[env var GO_ADMIN_UI_PATH]] - code - docs/superpowers/spec/docker-compose.yml
- [[go-admin-demo Compose Stack]] - code - docs/superpowers/spec/docker-compose.yml
- [[named volume go-mod-cache]] - code - docs/superpowers/spec/docker-compose.yml
- [[named volume mysql-data]] - code - docs/superpowers/spec/docker-compose.yml
- [[named volume node-modules-cache]] - code - docs/superpowers/spec/docker-compose.yml
- [[npm registry npmmirror.com]] - code - docs/superpowers/spec/docker-compose.yml

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/Docker_Compose_Stack_Definition
SORT file.name ASC
```

## Connections to other communities
- 2 edges to [[_COMMUNITY_Project Directory Structure (backend + frontend)]]
- 2 edges to [[_COMMUNITY_Docker Compose Quick Start Tutorial]]

## Top bridge nodes
- [[compose service backend (golang1.22-alpine)]] - degree 9, connects to 1 community
- [[compose service frontend (node16.15-alpine)]] - degree 8, connects to 1 community
- [[go-admin-demo Compose Stack]] - degree 5, connects to 1 community
- [[Phase 4 Stack Startup (mysqlmigratebackendfrontend)]] - degree 5, connects to 1 community