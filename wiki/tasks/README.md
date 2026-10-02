---
type: readme
---

# tasks/ — GTD Tasks

GTD 簡化版任務管理。Layer 2 的工作區之一。

## 子資料夾（GTD 簡化四 + 一）

| 子資料夾 | 用途 |
|---|---|
| `inbox/` | 還沒分流（從 [[raw/README]] triage 進來暫放） |
| `next/` | 今天該做、可行動的 task |
| `waiting/` | 等別人回覆、被 block |
| `someday/` | 暫不做但保留（maybe / later） |
| `done/YYYY-MM/` | 完成（按月歸檔，月初把上月移 [[wiki/archives/README]]） |

## Frontmatter Schema

完整模板見 [[templates/task]]。

| 欄位 | 必填 | 說明 |
|---|---|---|
| `date` | ✓ | 建立日期 (YYYY-MM-DD) |
| `type` | ✓ | `task` |
| `tags` | | 標籤陣列 |

> **Method B**: task 狀態由檔案位置決定，不在 frontmatter 用 `status` 欄位。
> `inbox/` / `next/` / `waiting/` / `someday/` / `done/` 就是狀態。
| `context` | | 情境（@home / @work / @errand） |
| `energy` | | `low` / `medium` / `high` |
| `time-estimate` | | `15min` / `30min` / `1h` ... |
| `project` | | 對應 [[wiki/projects/README\|project 名稱]] |
| `area` | | 對應 [[wiki/areas/README\|area 名稱]] |
| `source` | | triage 出處（`raw/captures/...`） |
| `due` | | deadline (YYYY-MM-DD) |
| `priority` | | `high` / `medium` / `low` |

## 命名規範

- 檔名：lowercase + dash
- 動詞開頭（例：`renew-passport.md` 而非 `passport.md`）
- 完成後移到 `done/YYYY-MM/<原檔名>.md`

## Wikilink 風格

- task → project：frontmatter `project:` 欄位（**不用 wikilink**，方便 Dataview）
- task → area：frontmatter `area:` 欄位（同上）
- daily note 透過 Dataview 自動拉

## 範例

```yaml
---
date: 2026-10-02
type: task
tags: [admin]
context: [home]
energy: low
time-estimate: 15min
project:
area: personal-admin
source: raw/captures/2026-10-02-renew-passport.md
due: 2026-10-15
priority: medium
---

# 換護照
```

> 檔案位置: `wiki/tasks/next/2026-10-02-renew-passport.md`
> → 狀態 `next` 由 folder 編碼（Method B）

## 流程

```
raw/captures/   →   tasks/inbox/   →   tasks/next/ (可行動)
                                    →   tasks/waiting/ (等別人)
                                    →   tasks/someday/ (暫不做)
                                    →   tasks/done/YYYY-MM/ (完成)
                                                  ↓ (月初)
                                            archives/tasks/
```

詳見 [[AGENTS#workflow]]。
