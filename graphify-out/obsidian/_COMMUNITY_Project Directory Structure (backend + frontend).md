---
type: community
cohesion: 0.10
members: 22
---

# Project Directory Structure (backend + frontend)

**Cohesion:** 0.10 - loosely connected
**Members:** 22 nodes

## Members
- [[.env.development  .env.production]] - document - docs/intro/advanced/tutorial0220.md
- [[Backend settings.yml Configuration]] - document - docs/intro/advanced/tutorial02.md
- [[Default Backend Port 8000]] - document - docs/intro/advanced/tutorial03.md
- [[Frontend Dev Server Port 9527]] - document - docs/intro/advanced/tutorial0230.md
- [[Frontend Startup (npm install  npm run dev)]] - document - docs/intro/advanced/tutorial0230.md
- [[Memory Quick Start Guide 3-Community Bridge]] - rationale - graphify-out/memory/query_20260505_184931_why_does_quick_start_guide_bridge_setup___reposito.md
- [[MySQL Recommended (sqlite3 partial)]] - rationale - docs/intro/advanced/tutorial02.md
- [[Node 16.15.0 Requirement]] - rationale - docs/intro/advanced/tutorial0230.md
- [[VUE_APP_BASE_API Variable]] - rationale - docs/intro/advanced/tutorial0220.md
- [[app Folder (admin + jobs)]] - document - docs/intro/advanced/tutorial01.md
- [[config Configuration Directory]] - document - docs/intro/advanced/tutorial01.md
- [[go run main.go server -c configsettings.dev.yml]] - code - docs/intro/advanced/tutorial03.md
- [[go-admin Backend Directory Structure]] - document - docs/intro/advanced/tutorial01.md
- [[go-admin-ui Directory Structure]] - document - docs/intro/advanced/tutorial0210.md
- [[jobs Module (Automated Jobs)]] - document - docs/intro/advanced/tutorial01.md
- [[main.go Entry Point]] - code - docs/intro/advanced/tutorial01.md
- [[settings.application Block (modehostport)]] - rationale - docs/intro/advanced/tutorial02.md
- [[settings.database Block (driversource DSN)]] - rationale - docs/intro/advanced/tutorial02.md
- [[settings.jwt Block (secrettimeout)]] - document - docs/intro/advanced/tutorial02.md
- [[settings.logger Block (pathstdoutlevel)]] - document - docs/intro/advanced/tutorial02.md
- [[src Frontend Source Layout (apiviewsrouterstore)]] - document - docs/intro/advanced/tutorial0210.md
- [[vite.config.js]] - code - docs/intro/advanced/tutorial0210.md

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/Project_Directory_Structure_backend__frontend
SORT file.name ASC
```

## Connections to other communities
- 2 edges to [[_COMMUNITY_Docker Compose Quick Start Tutorial]]
- 2 edges to [[_COMMUNITY_Docker Compose Stack Definition]]
- 2 edges to [[_COMMUNITY_Code Generation Workflow]]

## Top bridge nodes
- [[Backend settings.yml Configuration]] - degree 11, connects to 2 communities
- [[Frontend Startup (npm install  npm run dev)]] - degree 4, connects to 1 community
- [[app Folder (admin + jobs)]] - degree 3, connects to 1 community
- [[main.go Entry Point]] - degree 3, connects to 1 community