---
type: community
cohesion: 0.25
members: 8
---

# SDK Runtime Core

**Cohesion:** 0.25 - loosely connected
**Members:** 8 nodes

## Members
- [[Memory Queue]] - document - docs/intro/advanced/core.md
- [[Memory Queue vs Professional MQ Rationale]] - document - docs/intro/advanced/core.md
- [[Queue Adapter]] - document - docs/intro/advanced/core.md
- [[Runtime DB Map (GetDbGetDbByKeySetDb)]] - document - docs/intro/advanced/core.md
- [[SaveLoginLog Callback]] - document - docs/intro/advanced/core.md
- [[SetConfigGetConfig]] - document - docs/intro/advanced/core.md
- [[User Context Helpers (GetUserIdNameRoleDept)]] - document - docs/intro/advanced/core.md
- [[sdk.Runtime]] - document - docs/intro/advanced/core.md

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/SDK_Runtime_Core
SORT file.name ASC
```

## Connections to other communities
- 1 edge to [[_COMMUNITY_API Handlers & Service Layer]]

## Top bridge nodes
- [[User Context Helpers (GetUserIdNameRoleDept)]] - degree 2, connects to 1 community