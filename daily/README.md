---
type: readme
---

# daily/ — 每日 Reflection

每天一篇 reflection。Layer 2 的工作區之一。配合 [[templates/daily]] 模板，自動 Dataview 拉狀態。

## 檔案結構

- **檔名**：`YYYY-MM-DD.md`
- **位置**：`daily/YYYY-MM-DD.md`（不分子資料夾）
- **模板**：[[templates/daily]]

## 自動拉取的區塊

模板用 Dataview 自動產生：

| 區塊 | 來源 |
|---|---|
| 今天要做的 task | [[tasks/README\|tasks/]] + `due = today` |
| 過期 task | [[tasks/README\|tasks/]] + `due < today` |
| 本週 deadline | [[tasks/README\|tasks/]] + `due` 在本週內 |
| 活躍 project | [[projects/README\|projects/]] + `status = active` |
| 今日事件 | [[calendar/README\|calendar/]] 對應日期 |

## 手寫區塊

- **今日 reflection**
  - 做了什麼
  - 學到什麼
  - 卡在哪
- **臨時筆記**

## Frontmatter Schema

| 欄位 | 必填 | 說明 |
|---|---|---|
| `date` | ✓ | 當天日期 (YYYY-MM-DD) |
| `type` | ✓ | `daily` |

## 命名規範

- 一日一檔，**不補寫**（昨天的就讓它是昨天的）
- 週末 / 假日可選擇性寫（建議至少記一句）

## 範例

```markdown
---
date: 2026-10-02
type: daily
---

# 2026-10-02

## 今天要做
（Dataview 自動）

## 過期 task
（Dataview 自動）

## 本週 deadline
（Dataview 自動）

## 活躍 project
（Dataview 自動）

## Calendar 今日事件
（手動 wikilink 或貼 Dataview）

## 今日 reflection

### 做了什麼
- ...

### 學到什麼
- ...

### 卡在哪
- ...
```

## 與其他資料夾的關係

- daily 是**檢視點**，不是 source of truth
- task 變動 → 改 `tasks/`
- project 變動 → 改 `projects/`
- daily 只在 reflection 段落留想法與連結

詳見 [[AGENTS#workflow]]。
