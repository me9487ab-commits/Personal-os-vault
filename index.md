---
date: 2026-10-02
type: index
---

# Personal OS Index

個人作業系統 vault。涵蓋**任務管理、行事曆、Project 追蹤、Areas 持續責任、Email 整合、每日 reflection**。

> 書摘、學習筆記、topic wiki 歸 LLM-Wiki vault，不在本 vault 範圍。

## 三層架構

### Layer 1 — raw/（不可變 inbox）
- [[raw/README]] — captures / emails/drafts / external
- 一旦寫入就不修改，所有東西先丟這

### Layer 2 — wiki/（互相 wikilink 串連的資料網絡）

| 資料夾 | 角色 | 方法論 |
|---|---|---|
| [[wiki/[[tasks/README]] | 任務管理 | GTD 簡化 |
| [[wiki/[[calendar/README]] | 行事曆 | event / recurring-event / daily-calendar |
| [[wiki/[[projects/README]] | Project（有 deadline） | PARA |
| [[wiki/[[areas/README]] | Area（無 deadline） | PARA |
| [[wiki/[[daily/README]] | 每日 reflection | 1 日 1 檔 |
| [[wiki/[[archives/README]] | 封存 | 不進 daily brief |

### Layer 3 — meta
- [[index|index.md]] — 本檔
- [[log|log.md]] — append-only 變更記錄
- [[AGENTS|AGENTS.md]] — 代理 / 協作準則

## Tooling
- [[dashboard/README]] — Obsidian 工作台單頁
- [[templates/]] — Templater 模板
- [[scripts/]] — 自動化腳本

## Workflow 入口
1. **Capture** → 丟 [[raw/README]] 對應子資料夾
2. **Triage** → 從 [[raw/README|captures]] 分流到 Layer 2
3. **Daily Brief** → 打開 `daily/YYYY-MM-DD.md`
4. **Review** → 見 [[AGENTS#workflow]]

## 規範
- [[AGENTS]] — 完整準則、命名、frontmatter
- [[log]] — 近期變更
