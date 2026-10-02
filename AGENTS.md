---
date: 2026-10-02
type: schema
---

# AGENTS.md — Personal OS 代理準則

## 這個 Vault 是什麼

個人專案管理 + 行事曆 + 知識管理。借鑒 LLM-Wiki 模式但加入：
- 任務管理（GTD 簡化）
- 行事曆（Google Calendar sync）
- 專案追蹤（PARA 風格）
- Email 整合

## 資料夾架構

```
raw/         — 不可變 inbox
tasks/       — GTD tasks
calendar/    — 行事曆
projects/    — 進行中的專案
areas/       — 持續維護的責任區
resources/   — 主題知識庫
archives/    — 完成 / 休眠
wiki/        — LLM Wiki 風格
daily/       — 每日 reflection
dashboard/   — 工作台面板
templates/   — Templater 模板
scripts/     — 自動化腳本
```

## 命名規範

- 資料夾用 lowercase + dash
- 檔名用 lowercase + dash
- 日期用 ISO 8601：YYYY-MM-DD

## Frontmatter 規範

見 [[templates/task]]、[[templates/project]]、[[templates/area]]

## LLM-Wiki 風格連結

- 處處用 [[wikilinks]]
- 在 daily note / project 頁面放 Dataview query
- 用 Graph View 看整體關係

## 操作

### Capture
- 新東西一律先進 `raw/captures/`
- 包含語音轉文字、隨手記、截圖

### Triage
- 定期（每天）把 `raw/captures/` 分流到 `tasks/`、`calendar/`、`projects/`
- 分流後的檔案 frontmatter 標 `source: raw/captures/...`

### Daily Brief
- 每天打開 `daily/YYYY-MM-DD.md` 看 brief
- 自動用 Dataview 拉資料

## 禁止

- 不要直接編輯 `raw/` 內的檔案
- 不要略過 frontmatter
- 不要混用大小寫命名
