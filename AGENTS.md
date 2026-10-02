---
date: 2026-10-02
type: meta
---

# AGENTS.md — Personal OS 代理準則

## 這個 Vault 是什麼

個人作業系統 vault。涵蓋**任務管理（GTD 簡化）、行事曆、Project 追蹤、Areas 持續責任、Email 整合、每日 reflection**。

> 書摘、學習筆記、topic wiki 不在本 vault 範圍，統一歸 LLM-Wiki vault。

設計借鑒 LLM-Wiki 的「不可變 inbox + wikilink 串連」模式，加上 GTD 與 PARA 兩個生產力方法論。

## 三層架構

```
Layer 1 ─ raw/                  不可變 inbox（所有東西先丟這）
Layer 2 ─ wiki/                tasks/ calendar/ projects/ areas/ daily/ archives/ 互相 wikilink
Layer 3 ─ meta                  index.md + log.md + AGENTS.md
```

### Layer 1 — raw/（不可變 inbox）

- **MUST** 一旦寫入就不修改
- 三個子資料夾：
  - `captures/` — 你的時間標記記錄（語音、截圖、meeting 紀錄）
  - `emails/` — email 相關（inbound 附件 + AI 寫的 reply draft）
  - `external/` — 外部 ingest（網頁剪藏、書摘、PDF、講義）
- **MUST** 任何東西先 capture 再 triage，絕不繞過

### Layer 2 — wiki/（互相串連的資料網絡）

| 資料夾 | 角色 | 方法論 |
|---|---|---|
| [[wiki/tasks/README\|tasks/]] | 任務管理 | GTD 簡化 |
| [[wiki/calendar/README\|calendar/]] | 行事曆 | 三種檔案類型 schema |
| [[wiki/projects/README\|projects/]] | 有 deadline 的專案 | PARA |
| [[wiki/areas/README\|areas/]] | 無 deadline 的持續責任 | PARA |
| [[wiki/daily/README\|daily/]] | 每日 reflection | 1 日 1 檔 |
| [[wiki/archives/README\|archives/]] | 封存 | 不進 daily brief |

互相之間用 [[wikilinks]] 串：
- task 透過 frontmatter `project:` 欄位連到 [[templates/project]]
- task 透過 frontmatter `area:` 欄位連到 [[templates/area]]
- daily note 用 Dataview 自動拉 task / calendar / project
- dashboard 集中呈現

### Layer 3 — meta

- [[index\|index]] — vault 入口
- [[log\|log]] — append-only 變更記錄
- AGENTS.md（本檔）— 代理 / 協作準則

## Tooling 資料夾

| 資料夾 | 用途 |
|---|---|
| [[dashboard/README\|dashboard/]] | Obsidian 工作台單頁 |
| [[templates/]] | Templater 模板（task / project / area / daily / capture / event / recurring-event）|
| [[scripts/]] | 自動化腳本（future）|

## SOPs（標準作業程序）

每個 SOP 標明：**觸發**、**輸入**、**步驟**、**完成定義**、**異常處理**。
動詞強弱：**MUST**（必要）/ **SHOULD**（建議）/ **MAY**（可選）。

### SOP-Capture — 新東西進來

**觸發**: 看到、接收、或主動想到任何新東西（語音轉文字、截圖、email、網頁、想法）

**輸入**: 一段內容（文字、圖片、音檔、URL、thought）

**步驟**:

1. **MUST** 判斷類型：
   - 自己隨手記（語音、截圖、想法）→ `raw/captures/`
   - email / AI 寫的 reply → `raw/emails/`
   - 外部來源（網頁、書、PDF、講義）→ `raw/external/`
2. **MUST** 命名為 `YYYY-MM-DD-<slug>.md`
3. **MUST** 寫檔後**不再編輯**（raw immutable）
4. **SHOULD** 加 frontmatter `type: capture` + `source:`（來源說明）

**完成定義**: 檔案已寫入 `raw/<sub>/`，命名符合規範

**異常處理**:
- 不確定類型 → 暫存 `raw/captures/`（最常用），下次 triage 決定
- 已有同名檔 → 加 `-2`、`-3` 等序號

### SOP-Triage — 分流 raw/ → wiki/

**觸發**: 每天 1 次（建議早上開 daily brief 前）

**輸入**: `raw/captures/`、`raw/emails/`、`raw/external/` 中的待處理檔

**步驟**:

1. **MUST** 掃 `raw/<sub>/` 看有哪些檔
2. **MUST** 對每個檔用以下決策樹分流：
   - 是 task（要做的事）→ 移到 [[wiki/tasks/inbox/README\|inbox/]]（或直接 `next/` / `waiting/` / `someday/`）
   - 是 event（一次性）→ 移到 [[wiki/calendar/synced/README\|synced/]]
   - 是 recurring event template → 移到 [[wiki/calendar/recurring/README\|recurring/]]
   - 是 recurring event 當日實例 → 移到 [[wiki/calendar/daily/README\|daily/]]
   - 是 project（有 deadline 的事）→ 移到 [[wiki/projects/README\|projects/]] 對應的 project folder
   - 是 area（持續責任）→ append 到 [[wiki/areas/README\|areas/]] 對應的 area file
   - 是純筆記 / 學習 → **SHOULD NOT** 留在本 vault，移到 LLM-Wiki
3. **MUST** frontmatter 補上 `source: raw/<sub>/<filename>`
4. **MUST** raw/ 端檔案不刪（保留 source of truth）
5. **SHOULD** 用 wikilink 連到相關 wiki page（task → project / area）

**完成定義**: `raw/<sub>/` 中沒有 backlog（除了當天剛寫的），frontmatter 都補齊

**異常處理**:
- 判斷不出類型 → 留在 `raw/captures/`，下次再加 review
- 同一 source 衍生多個 wiki 頁（task + project + area 都相關）→ 用 wikilink 互相串

### SOP-Daily-Brief — 每日 brief

**觸發**: 每天早上（或開新 daily note 時）

**輸入**: 當天日期 `YYYY-MM-DD`

**步驟**:

1. **MUST** 開 / 建立 `wiki/daily/YYYY-MM-DD.md`（模板 [[templates/daily]]）
2. **MUST** Dataview 拉 4 類資料：
   - 今天要做的 task（從 [[wiki/tasks/next/README\|next/]]）
   - 過期 task（priority: high 且 due < today）
   - 本週到期 task（due < today + 7）
   - 今日 calendar event
3. **SHOULD** 寫當日 reflection（最少 3 句）

**完成定義**: 當天 `wiki/daily/YYYY-MM-DD.md` 已建立且 brief 填妥

**異常處理**:
- 找不到 daily template → 手動複製 [[templates/daily]] 範例建檔
- Dataview query 沒資料 → 沒事，brief 空白也算完成（reflection 部分仍要寫）

### SOP-Review — 周期性 review

**觸發**: Daily / Weekly / Monthly / Quarterly

| 頻率 | 動作 |
|------|------|
| 每日 | 清 [[wiki/tasks/inbox/README\|inbox/]]、寫 daily reflection |
| 每週 | review [[wiki/tasks/next/README\|next/]] + [[wiki/tasks/waiting/README\|waiting/]]、確認 [[wiki/calendar/recurring/README\|recurring/]] 正確 |
| 每月 | 把舊 `tasks/done/` 移 → `archives/tasks/`、review 所有 [[wiki/projects/README\|projects/]] 狀態 |
| 每季 | review [[wiki/areas/README\|areas/]]，確認每個 area 有近期重點 |

**完成定義**: 對應頻率的所有 action items 都做完（或標記延後到下次 review）

## 命名規範

- **MUST** 資料夾、檔名：`lowercase + dash`
- **MUST** 日期格式：ISO 8601（`YYYY-MM-DD`）
- **MUST** 時間用於 event 檔名：`HH-MM`（24h，用 dash 不用 colon，避免檔名系統衝突）
- **MUST** Slug：用 `-` 分隔關鍵字
- **SHOULD** 完成 task 歸檔：當月在 `tasks/done/`；月累計 > 10 件 → 開 `tasks/done/YYYY-MM/` 子資料夾

## Frontmatter 規範

各檔案類型對應模板：

| 類型 | 必填欄位 | 模板 | `status` 欄位 |
|---|---|---|---|
| task | `date`, `type` | [[templates/task]] | ❌ **NO**（Method B：folder = 狀態）|
| project | `type`, `area` | [[templates/project]] | ✅ `active` / `paused` / `completed` / `cancelled` |
| area | `type` | [[templates/area]] | ✅ `active` / `dormant` |
| daily | `date`, `type` | [[templates/daily]] | ❌ N/A |
| capture | `date`, `type`, `source:` | [[templates/capture]] | ❌ N/A |
| event | `date`, `type`, `title`, `start`, `end` | [[templates/event]] | ✅ `confirmed` / `tentative` / `cancelled` |
| recurring-event | `type`, `title`, `start-time`, `duration`, `days`, `start-date` | [[templates/recurring-event]] | ❌ N/A |

詳細 schema 見各 [[templates/|Templates 資料夾]] 與各資料夾 README。

## Wikilink 風格

- **MUST** 處處用 `[[wikilinks]]`
- **MUST** 跨資料夾：`[[folder/page|顯示文字]]`
- **MUST** 同資料夾：`[[page-name]]`
- **MUST NOT** task 連 project / area 用 wikilink — 用 frontmatter 欄位（方便 Dataview query）
- **SHOULD** 用 Graph View 看整體關係

## `status:` 欄位使用規則

Method B 只對 **task** 強制（folder = 狀態）。其他類型的 `status` 是 lifecycle state：

| 類型 | 用 `status` | 不 用 | 狀態怎麼表示 |
|---|---|---|---|
| task | | ✓ | folder: `inbox/` / `next/` / `waiting/` / `someday/` / `done/` |
| project | ✓ | | `status: active/paused/completed/cancelled` |
| area | ✓ | | `status: active/dormant` |
| event | ✓ | | `status: confirmed/tentative/cancelled` |
| daily / capture / recurring-event | | ✓ | N/A |

**Reasoning**: task 是 vault 裡最會流動的類型，所以用 folder 編碼狀態最高效。project / area / event 檔案不常移動位置，所以用 `status` 欄位管理 lifecycle 比較直觀。

## Areas vs Projects 判斷

| | Project | Area |
|---|---|---|
| Deadline | 有 | 沒有 |
| 完成條件 | 明確 | 持續責任 |
| 結束動作 | 移 `archives/projects/` | 不結束，只 review |
| 範例 | 搬家、論文、網站改版 | 健康、財務、職涯 |

## Email 整合

- 進：`raw/emails/`（所有 inbound + outbound 都放這）
- AI 寫的 reply draft：也放 `raw/emails/`
- **MUST** 標籤 / 優先序：透過 frontmatter `priority:`、`tags:` 欄位
- **MUST** 送出後：把對應 task 移到 [[wiki/tasks/done/README\|done/]]（**不要**加 `status: sent` — Method B 用 location 表示狀態）

## 禁止

- ❌ **MUST NOT** 直接編輯 `raw/` 內的檔案
- ❌ **MUST NOT** 略過 frontmatter
- ❌ **MUST NOT** 混用大小寫命名
- ❌ **MUST NOT** 把書摘、學習筆記、topic wiki 放這 — 歸 LLM-Wiki vault
- ❌ **MUST NOT** 在 `projects/` 放無 deadline 的東西（那是 area）
- ❌ **MUST NOT** task 用 `status:` 欄位（Method B：folder = 狀態）
- ❌ **MUST NOT** 把 `raw/<sub>/` 的待處理檔留超過 1 天（triage 必須當天或隔天做）