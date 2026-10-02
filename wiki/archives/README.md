---
type: readme
---

# archives/ — Archives

完成或休眠的東西。Layer 2 的工作區之一。**保留供回查，不進 daily brief**。

## 子資料夾

| 子資料夾 | 來源 | 歸檔時機 |
|---|---|---|
| `projects/` | [[wiki/[[projects/README\|projects/]] | project `status: completed` 或 `cancelled` |
| `tasks/` | [[wiki/[[tasks/README\|tasks/]] | 每月初把上個月 `tasks/done/YYYY-MM/` 移到這 |

## 命名規範

- 沿用原檔名 / 資料夾名
- 整批歸檔時可在 frontmatter 加 `archived: YYYY-MM-DD` 標記

## 原則

- **不主動刪除**（除非個資 / 機密）
- archives 內檔案**不進** daily brief 的 Dataview query（透過 `status: done` 或 `archived:` 過濾）
- 需要回查時直接打開 archives 找

## 歸檔流程

### Projects
1. project 狀態改 `completed` / `cancelled`
2. 整個資料夾 `mv projects/<slug>/ archives/projects/`
3. 該 project 下的 task 若還有未完成，決定是否關掉或移到新 project

### Tasks
1. 月初（例如 11/1）把 `tasks/done/2026-10/` 整批移到 `archives/tasks/2026-10/`
2. 同步刪除 archives 內的過期 Dataview 結果（通常自動）

## 不做的事

- ❌ 不在 archives 編輯內容（除非修正錯字）
- ❌ 不重新啟動 archives 內的 project（重新建立新 project，wikilink 舊的當 reference）

詳見 [[AGENTS#workflow]]。
