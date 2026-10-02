---
type: readme
---

# projects/ — Projects

有 deadline 的專案。Layer 2 的工作區之一。**每個 project 一個資料夾**。

## 結構（每個 project 資料夾）

```
projects/<project-slug>/
├── README.md       # 目標、status、deadline
├── tasks.md        # 這個 project 的 subtasks（彙總）
├── log.md          # 事件日誌（重要決策、進度）
└── notes.md        # 筆記、研究、參考
```

> task 本身仍住在 [[wiki/[[tasks/README|tasks/]]，透過 frontmatter `project:` 欄位連結到這。
> `tasks.md` 與 `notes.md` 是輔助彙總頁，task 主體還是要在 `tasks/`。

## Frontmatter Schema

完整模板見 [[templates/project]]。

| 欄位 | 必填 | 說明 |
|---|---|---|
| `date` | | 建立日期 |
| `type` | ✓ | `project` |
| `status` | ✓ | `active` / `paused` / `completed` / `cancelled` |
| `area` | | 對應 [[wiki/[[areas/README\|area]] |
| `due` | | deadline (YYYY-MM-DD) |
| `tags` | | 標籤 |

## Project 生命週期

```
建立（active）  →  進行中（review）  →  完成 / 取消
                                          ↓
                                    archives/projects/
```

- 完成 / 取消時，把整個資料夾移到 [[wiki/[[archives/README|archives/projects/]]
- 移到 archives 時 frontmatter 加上 `archived: YYYY-MM-DD`

## 命名規範

- 資料夾名：lowercase + dash
- 範例：`projects/move-to-new-apartment/`

## Wikilink 風格

- task → project：frontmatter `project:` 欄位
- project → area：frontmatter `area:` 欄位
- project README 內可 wikilink 對應 task、area、calendar event

## 範例 frontmatter

```yaml
---
date: 2026-10-02
type: project
status: active
area: personal-admin
due: 2026-12-31
tags: [home, moving]
---

# 搬新家
```

詳見 [[AGENTS#workflow]]。
