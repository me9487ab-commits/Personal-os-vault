---
type: readme
---

# calendar/ — 行事曆資料庫

最簡化的純 markdown 行事曆資料層。三種檔案類型。

## 三種檔案類型

### 1. Event（單次事件）

- **位置**：`calendar/synced/` 或 `calendar/daily/`
- **檔名**：`YYYY-MM-DD-HH-MM-<slug>.md`
- **範例**：`2026-10-02-14-00-cs-meeting.md`
- **模板**：`[[templates/event]]`

### 2. Recurring-event（重複事件）

- **位置**：`calendar/recurring/`
- **檔名**：`<slug>.md`
- **範例**：`weekly-standup.md`
- **模板**：`[[templates/recurring-event]]`

### 3. Daily-calendar（每日彙總）

- **位置**：`calendar/daily/`
- **檔名**：`YYYY-MM-DD.md`
- **模板**：無（自由格式）

## Frontmatter Schema

### Event

| 欄位 | 必填 | 說明 |
|---|---|---|
| `date` | ✓ | 事件日期 (YYYY-MM-DD) |
| `type` | ✓ | `event` |
| `title` | ✓ | 事件名稱 |
| `start` | ✓ | 開始時間 (HH:MM, 24h) |
| `end` | ✓ | 結束時間 (HH:MM, 24h) |
| `timezone` | | 預設 Asia/Taipei |
| `location` | | 地點 |
| `recurring-id` | | 屬於某個重複事件，填 `recurring/<slug>` |
| `tags` | | 標籤 |
| `status` | | confirmed / tentative / cancelled |
| `source` | | manual / google-calendar |

### Recurring-event

| 欄位 | 必填 | 說明 |
|---|---|---|
| `type` | ✓ | `recurring-event` |
| `title` | ✓ | 事件名稱 |
| `start-time` | ✓ | 時間 (HH:MM) |
| `duration` | ✓ | `30min` / `1h` / `1h30min` |
| `days` | ✓ | 星期幾陣列：`[mon]` / `[mon, wed, fri]` |
| `start-date` | ✓ | 開始日期 |
| `end-date` | | 結束日期（留空 = 永遠） |
| `location` | | 地點 |
| `tags` | | 標籤 |

### Daily

沒有固定欄位。手動 wikilink 事件或寫臨時筆記。

## 命名規範

- 檔名一律 lowercase + dash
- Event 檔名加時間避免同日衝突
- Slug 用 `-` 分隔關鍵字（例：`cs-team-meeting`）

## 範例

- [[wiki/calendar/recurring/weekly-standup|Weekly standup 範例]]
- `calendar/synced/2026-10-02-14-00-cs-meeting.md`（sync 進來的會議）

## 不做的事

- ❌ Dashboard（暫不做）
- ❌ 自動化腳本（暫不做）
- ✅ 只用純 markdown + 手動編輯
