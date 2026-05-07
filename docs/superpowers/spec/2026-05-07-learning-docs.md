# go-admin Quick Start with Docker Compose — 學習教材

> **產出來源**:由 `superpowers:brainstorming` 流程產出。
> **配套檔案**:`docs/superpowers/spec/docker-compose.yml`(同目錄)。
> **撰寫日期**:2026-05-07。
> **語言**:zh-TW(繁體中文)。
> **作者**:Claude Code(對話式產出)。

---

## 0. 這份教材在做什麼

**目標**:**讓你在不安裝任何 Go / Node / MySQL 工具到主機上**的前提下,
透過 docker-compose 跑通 go-admin demo stack,最終在瀏覽器看到 go-admin-ui
的登入畫面、用預設帳密登入成功。

**讀者畫像**:不維護 go-admin 上游、第一次接觸這個專案、想要「先看到能跑
的東西」再決定是否深入研讀的學習者。

### 教材會做什麼 ✅

- 透過 4 個 service 的 compose stack(mysql + migrate + backend + frontend),
  一條指令把整個 demo 起起來
- 把上游 docs `guide/ksks.md` 與 `intro/advanced/tutorial01–03.md` 的步驟,
  翻譯成「容器化、可重現、不污染主機」的版本
- 標註每一步的**預期輸出**,讓你失敗時立刻知道哪裡偏了
- 把上游沒寫的容器化常見坑(`application.host`、service 名解析、port forwarding)
  以 callout 形式嵌在對應步驟旁

### 教材**不**會做什麼 ❌

- **不教 docker / docker compose 的安裝**:假設你已能在 shell 跑通
  `docker version` 與 `docker compose version`
- **不教 Go / Node / MySQL 的主機原生安裝**:全部跑在容器裡
- **不涵蓋生產部署**(打包、Nginx 反代、跨平台編譯)— 那是 `guide/xmbs.md` 的範圍
- **不涵蓋代碼生成全流程**(article CRUD)— 那是 `tutorial0310–0460.md` 的後續推薦
- **不涵蓋 go-admin-pro V1 的差異** — 本教材只覆蓋社群版

### 預估時間

- 已 clone 過兩個 source repo:約 **15–25 分鐘**(主要等 docker pull + npm install)
- 全新環境(含 clone + docker pull):約 **30–45 分鐘**

---

## 1. 整體架構速覽(讀完一張圖即可進入 Phase 0)

```
┌──────────┐   port 8080      ┌──────────────┐  port 8000  ┌─────────────┐
│ Browser  │ ───────────────▶ │   frontend   │ ──────────▶ │   backend   │
│  (host)  │ (vue-cli dev)    │ node:16.15-  │  /api/*     │ go:1.22-    │
└──────────┘                  │  alpine      │             │  alpine     │
                              │ + UI sources │             │ + go-admin  │
                              └──────────────┘             │   sources   │
                                                           └──────┬──────┘
                                                                  │
                              ┌──────────────┐  one-shot  ┌───────▼───────┐
                              │   migrate    │ ─────────▶ │     mysql     │
                              │ (go run      │  exits 0   │  mysql:8.0    │
                              │  main.go     │            │  + named vol  │
                              │  migrate)    │            │  + healthcheck│
                              └──────────────┘            └───────────────┘
```

**4 個 services 各自的職責**:

| Service | 角色 | 關鍵指令 / image | 對外 port |
|---|---|---|---|
| `mysql` | 資料庫 | `mysql:8.0`,`mysqladmin ping` healthcheck | 內部 only |
| `migrate` | 一次性 schema 安裝 | `golang:1.22-alpine` 跑 `go run main.go migrate` | 無 |
| `backend` | API 伺服器 | `golang:1.22-alpine` 跑 `go run main.go server` | `8000` |
| `frontend` | UI dev server | `node:16.15-alpine` 跑 `npm run dev` | `8080` |

依賴鏈:`mysql` healthy → `migrate` 跑完退出 → `backend` 啟動 → `frontend` 啟動。

---

## 2. Phase 0 — 前置檢查(5 分鐘)

### 0.1 Docker / Compose 可用

```bash
docker version
docker compose version
```

> **預期輸出**:都吐出版本號(Compose 必須是 v2,即 `docker compose` 子命令而非
> `docker-compose` 獨立指令)。
>
> **失敗時**:本教材不教安裝,請改參考 Docker 官方安裝指引或請你的平台 IT。

- [ ] `docker version` 通過
- [ ] `docker compose version` 通過(必為 v2 / plugin 形式)

### 0.2 git 與 shell 工具

```bash
git --version
echo $SHELL
```

- [ ] git 可用(任意現代版本)
- [ ] shell 為 bash / zsh / fish 等可 export 變數的 shell

### 0.3 Host port 8000 / 8080 未被佔用

```bash
ss -ltn | grep -E ':8000|:8080'
# 或
lsof -iTCP:8000 -sTCP:LISTEN
lsof -iTCP:8080 -sTCP:LISTEN
```

- [ ] 8000 與 8080 皆無人在聽

> **失敗時**:停掉佔用程式,或改 compose 中 `ports:` 對映成其他 host port
> (例如 `8001:8000`),記得最後在瀏覽器用對應的新 port。

### 0.4 工作目錄規劃

預期最終目錄結構(本教材**不**幫你建這個結構,只說明假設):

```
~/work/                                     ← 任意 workspace 根
├── go-admin/                               ← Phase 1 會 clone(backend)
├── go-admin-ui/                            ← Phase 1 會 clone(frontend)
└── fork260506-go-admin-doc/                ← 本 fork(教材所在)
    └── docs/                               ← dumi 文件來源根
        └── superpowers/spec/                ← 學習教材所在
            ├── 2026-05-07-learning-docs.md  ← 你正在看的教材
            └── docker-compose.yml           ← 配套 compose 檔
```

**重要約束**:依上游 `tutorial0410.md` 規定的「**go-admin 與 go-admin-ui
同级目录**」(graphify community 4 的 hard requirement),兩個 source repo
必須同層。本教材的 compose 用絕對路徑 env var,不強制特定位置,但**未來
若你要走代碼生成教學,還是要依此擺**。

---

## 3. Phase 1 — 取得 source(10 分鐘,主要等網路)

```bash
cd ~/work    # 換成你的 workspace
git clone https://github.com/go-admin-team/go-admin.git
git clone https://github.com/go-admin-team/go-admin-ui.git
```

- [ ] `go-admin/` clone 成功(可看到 `main.go`、`config/`、`cmd/` 三個 entry)
- [ ] `go-admin-ui/` clone 成功(可看到 `package.json`、`src/`、`vue.config.js`)

> **預期輸出**:`ls go-admin go-admin-ui` 兩個資料夾都存在且非空。
>
> **callout — 同級目錄是約束不是建議**:`tutorial0410.md` 明寫 go-admin 與
> go-admin-ui 必須同級。代碼生成工具會用相對路徑找對方;雖然本教材尚未
> 用到代碼生成,但提早擺對位置,將來不用搬。

---

## 4. Phase 2 — 準備 backend 設定檔(5 分鐘)

這一步是**最容易踩雷的一步**,因為上游 docs 假設你在主機原生跑,所以預設
DSN 寫的是 `127.0.0.1:3306`,而我們的容器化路線要連的是 compose 內部的
service name `mysql`。

### 2.1 編輯 `go-admin/config/settings.yml`

打開 `go-admin/config/settings.yml`,做兩處修改:

#### 修改 1:`application.host`

```yaml
# 改前
application:
  host: 127.0.0.1
  port: 8000

# 改後
application:
  host: 0.0.0.0     # ← 容器內必須監聽 0.0.0.0,否則 host 透過 ports 對映打不進來
  port: 8000
```

> **callout — 為什麼 0.0.0.0**:容器內 `127.0.0.1` 等於容器自己的 loopback,
> 主機透過 `docker -p 8000:8000` 進來時是從 bridge 網卡進入容器,bind 到
> 127.0.0.1 就接不到。0.0.0.0 = 監聽所有介面,容器內外都通。**這是上游
> docs 沒提的容器化必經坑**。

#### 修改 2:database `source`

```yaml
# 改前
databases:
  default:
    driver: mysql
    source: user:password@tcp(127.0.0.1:3306)/dbname?charset=utf8&parseTime=True&loc=Local&timeout=1000ms

# 改後
databases:
  default:
    driver: mysql
    source: go-admin:go-admin123@tcp(mysql:3306)/go-admin?charset=utf8mb4&parseTime=True&loc=Local&timeout=10000ms
```

說明:

- `mysql:3306` 中的 `mysql` 是 docker compose 的 service name,bridge 網路
  下會自動 DNS 解析到該容器
- 帳密與 db 名要對齊 compose 的 `environment`(`go-admin / go-admin123 / go-admin`)
- `charset=utf8mb4` 對齊 mysql 8 的 server 設定,避免 4-byte 字元(emoji)
  寫入失敗
- timeout 從 `1000ms` 拉到 `10000ms`:首次啟動 mysql 還沒完全 ready 時,
  go-admin 自帶 retry 不夠寬鬆容易直接 fatal

- [ ] `application.host` 改為 `0.0.0.0`
- [ ] database `source` 改為連 `mysql:3306`,帳密 `go-admin/go-admin123`
- [ ] db 名 `go-admin`(對齊 compose `MYSQL_DATABASE`)

### 2.2(可選)用 settings.docker.yml 取代直接編輯

若你不想動 git tracked 的 `settings.yml`(避免 dirty 工作樹),可以:

```bash
cp go-admin/config/settings.yml go-admin/config/settings.docker.yml
# 編輯 settings.docker.yml(同樣兩處改動)
```

然後修改 `docs/superpowers/spec/docker-compose.yml` 中 `migrate` 與 `backend` 的
`command`,把 `-c config/settings.yml` 換成 `-c config/settings.docker.yml`。

- [ ] (可選)走 settings.docker.yml 路線

---

## 5. Phase 3 — 取得 docker-compose.yml(1 分鐘)

本 fork 已附上 compose 檔在 `docs/superpowers/spec/docker-compose.yml`。你可以
直接用該路徑跑,或複製到任意工作目錄。

### 5.1 export 兩個必要環境變數

```bash
export GO_ADMIN_PATH="$HOME/work/go-admin"           # 換成 Phase 1 你 clone 的絕對路徑
export GO_ADMIN_UI_PATH="$HOME/work/go-admin-ui"     # 同上
```

> **callout — 為什麼用環境變數**:讓 compose 檔可以放在任何位置;少了硬編
> 碼路徑的耦合。compose 檔內 `${GO_ADMIN_PATH:?required}` 的 `:?` 語法會在
> 變數未設時直接 fail-fast,訊息明確。

### 5.2 驗證 compose 設定

```bash
docker compose -f /path/to/fork260506-go-admin-doc/docs/superpowers/spec/docker-compose.yml config
```

- [ ] `docker compose config` 印出展開後的 compose 內容,**無錯誤**
- [ ] 確認 volumes 對映顯示的是你預期的絕對路徑

> **預期輸出**:大段 yaml 寫到 stdout,沒有 `error` 字樣。
>
> **失敗時**:多半是 env var 沒 export 或拼錯。重 export 一次。

---

## 6. Phase 4 — 啟動 stack(5–15 分鐘,首次最久)

### 6.1 啟動 mysql 並等 healthy

```bash
docker compose -f .../docker-compose.yml up -d mysql
docker compose -f .../docker-compose.yml ps
```

- [ ] `mysql` 的 STATUS 顯示 `Up` 且 `(healthy)`(等約 10–30 秒,首次 init
      會比較久)

> **失敗時**:`docker compose logs mysql` 看是否有 InnoDB 錯誤(極少見,
> compose 已加 `--innodb-large-prefix=ON --innodb-default-row-format=DYNAMIC`
> 預防 key length 雷)。

### 6.2 跑一次性 migrate

```bash
docker compose -f .../docker-compose.yml up migrate
```

(不加 `-d`,讓 logs 直接打到當前 terminal,看清楚有沒有錯)

- [ ] migrate 容器跑完**乾淨退出**(exit code 0)
- [ ] 終端機看到類似 `migrate success` / `已迁移到最新版本` 的成功訊息

> **預期輸出**:會看到 SQL 一筆筆執行的 log,結尾是「成功」訊息。
>
> **失敗時**:
> - `connect: connection refused` → mysql 還沒完全好,等 30 秒後重跑(`up migrate` 即可,
>   compose 會偵測到容器已退出而重建)
> - `Access denied for user` → 檢查 settings.yml 的帳密與 compose 是否一致
> - `Unknown database 'go-admin'` → 檢查 db 名是否拼為 `go-admin`(注意連字號)

### 6.3 啟動 backend 與 frontend

```bash
docker compose -f .../docker-compose.yml up -d backend frontend
docker compose -f .../docker-compose.yml logs -f backend frontend
```

- [ ] backend log 出現 `Listening and serving HTTP on :8000`(或類似)
- [ ] frontend log 出現 `App running at http://localhost:8080/`(或 `Ready in ...ms`)
- [ ] `Ctrl+C` 結束 logs follow,容器仍在背景跑(`-d` 啟動)

> **預期輸出時間**:
> - backend 第一次:Go 抓 module + 編譯,2–5 分鐘(視 GOPROXY)
> - frontend 第一次:`npm install` 抓 1500+ 套件,5–15 分鐘(視 npmmirror)
> - 第二次起兩者都 < 30 秒(因為 module / node_modules 都 cache 在 volume)
>
> **若中國大陸 mirror 不適合你的網路**:編輯 compose 把 `GOPROXY` 與
> `npm config set registry` 兩行調整或移除,改用預設或你慣用的 mirror。

---

## 7. Phase 5 — 登入驗證(1 分鐘)

### 7.1 開瀏覽器

打開 `http://localhost:8080`。

- [ ] 看到 go-admin-ui 登入畫面(藍色 / 卡片式 UI)
- [ ] 用預設帳密登入(以**上游 go-admin README 為準**;一般是 `admin / admin`
      或 `admin / 123456`,本教材不寫死避免上游變更後失準)

> **callout — 為什麼是 localhost 而不是容器 IP**:Docker `ports: 8080:8080`
> 把 host 的 8080 forward 到 frontend 容器的 8080。WSL2 Windows 主機開瀏覽器
> 可直接 `http://localhost:8080`,WSL2 會自動 forward(WSL2 本身在 NAT 後面,
> 但有自動 listen on Windows host)。

### 7.2 看到 dashboard

登入成功後應該看到 go-admin 的後台首頁(左側選單、上方 user 選單、中央
內容區)。

- [ ] 登入成功並進入 dashboard
- [ ] 左側選單可點(會打 backend `/api/*`,看 Network tab 應該都 200)

🎉 **恭喜,你已經跑通 go-admin demo stack。**

> **失敗時最常見**:
> - 登入按下去 Network tab 看到 `Failed to fetch` 或 CORS 錯誤
>   → 多半是 `VUE_APP_BASE_API` 沒生效或 backend `application.host` 還是 127.0.0.1
> - 登入卡在 loading
>   → backend 還沒準備好,等 1–2 分鐘再試;或看 backend logs 是否 panic
> - 看到頁面但點選單沒反應
>   → frontend dev server 在 hot-reload,等 console 出現 `compiled successfully` 再操作

---

## 8. Phase 6 — 收工(1 分鐘)

### 8.1 暫停但保留資料

```bash
docker compose -f .../docker-compose.yml down
```

- volumes(mysql-data / go-mod-cache / node-modules-cache)**會保留**
- 下次 `up -d` 啟動快很多(不重抓 module、不重建 schema)

### 8.2 完全 reset

```bash
docker compose -f .../docker-compose.yml down -v
```

- 連 named volumes 一起刪除
- 適合「我要重來一次乾淨的 first-time experience」時

- [ ] 收工後 `docker compose ps` 應該為空(或本 stack 服務不在列)

---

## 9. 故障排除速查

| 症狀 | 最可能原因 | 修法 |
|---|---|---|
| `mysql` 一直 restart / unhealthy | InnoDB key length 或設定衝突 | 看 `docker compose logs mysql`;compose 已加防雷 args,若仍失敗檢查 host 是否有舊 mysql named volume 殘留 |
| `migrate` 退出 code != 0,`connect: connection refused` | mysql 還沒 fully ready | 等 30 秒,重跑 `up migrate`;或加大 mysql healthcheck `retries` |
| `migrate` 退出 code != 0,`Access denied` | settings.yml 帳密與 compose 不一致 | 對齊 `go-admin / go-admin123 / go-admin` 三件套 |
| `migrate` 退出 code != 0,`Unknown database` | db 名拼錯(常拼成 `go_admin`) | compose 用的是連字號 `go-admin`,settings.yml 也要連字號 |
| backend 啟動 panic `bind: address already in use` | host 8000 已佔用 | `lsof -iTCP:8000` 找元兇,或改 compose `ports` |
| backend 啟動 OK 但瀏覽器打不到 `/api/*` | `application.host` 還是 127.0.0.1 | 改成 `0.0.0.0`,重啟 backend |
| frontend `npm install` 卡死 | npmmirror 連不上 | 編輯 compose 移除 `npm config set registry` 那行,或換成你慣用的 mirror |
| frontend 啟動 OK 但登入時 CORS / Failed to fetch | `VUE_APP_BASE_API` 沒生效 | 確認 compose `environment.VUE_APP_BASE_API: http://localhost:8000`;若 ui 有自帶 `.env.development` 蓋掉,可能要編輯該檔 |
| WSL2 主機 Windows 瀏覽器開不到 | 極少數 WSL2 自動 forward 失效 | 在 WSL 內 `curl localhost:8080` 確認容器 ok;不行則重啟 WSL `wsl --shutdown` |
| 重啟後 mysql 資料不見 | 不小心跑了 `down -v` | named volume 已刪;重新跑一次 Phase 4 即可,只是要重新 migrate |

---

## 10. 學完之後可以做什麼

照優先順序推薦下一步:

1. **`docs/intro/advanced/tutorial0310.md`** — 創建文章功能示例(SysPost CRUD
   端到端)。看完你會知道一個 model 從 dto / service / router / api 怎麼串起來。
2. **`docs/intro/advanced/{api, router, service, dto, models}.md` 五件套** —
   MVC 分層解剖。每個 god node 一篇,讀完整套 mental model 完整。
3. **`docs/intro/advanced/tutorial0410–0460.md`** — 代碼生成全流程。需要在 DB
   建 article 表,本教材沒覆蓋。完成後你能自動產生 CRUD 模組。
4. **`docs/intro/advanced/core.md`** — SDK Runtime 核心(Memory Queue、UserCtx
   helpers)。理解專案的「設計取捨」面。
5. **`docs/guide/xmbs.md`** — 生產部署(打包、Nginx、跨平台編譯)。從 Demo 走向
   Production 的橋。

graphify GRAPH_REPORT 也指出整個語料只有 9,826 字,「Corpus fits in a single
context window — you may not need a graph」。如果你閱讀偏好是「一次掃完」,
也可以直接從上而下把 `docs/` 全讀一遍。

---

## 11. 延伸思考(非必要)

幾個本教材**故意省略**的東西,值得日後加進來:

- **代碼生成路徑**:本教材沒涵蓋 article 表建立 + codegen,上游 docs
  `tutorial0410.md` 有完整流程。要做時記得 `go-admin` 與 `go-admin-ui`
  的 hard requirement(同級目錄)。
- **熱重載**:本 compose 用 `go run`,改 backend 程式碼會重啟整個
  process(等於 stop + go run)。若想要真正熱重載,可改用 `cosmtrek/air`
  image,參考 `docs/intro/advanced/air.md`。
- **PostgreSQL / SQLite 變體**:`docs/intro/advanced/db.md` 列出三種 driver。
  本教材選 mysql 對齊上游推薦;若你偏好 PG,可在本路線跑通後另寫一篇 patch。
- **生產化打包**:`go run` 與 `npm run dev` 都不是 production 模式。生產要
  `go build` 為 binary、`npm run build` 為靜態檔搭 nginx。對應 `xmbs.md`。

---

## 12. 修訂紀錄

| 日期 | 修改 | 作者 |
|---|---|---|
| 2026-05-07 | 初版建立(brainstorming session 產出) | Claude Code |
