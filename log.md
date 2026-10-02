# Log

Append-only 操作記錄。

## [2026-10-02] init | 建立 Personal-OS vault

## [2026-10-02] schema | 行事曆資料庫 schema（event / recurring-event / daily）
- 2 個 templates（event, recurring-event）
- 1 個範例（weekly-standup）
- calendar/README.md 重寫為 schema doc

## [2026-10-02] docs | AGENTS + READMEs + index 對齊三層架構
- 決定三層架構：Layer 1 raw/、Layer 2 working data、Layer 3 meta
- 決定範圍：Task / Calendar / Project / Area / Daily / Email 整合；知識管理歸 LLM-Wiki vault
- 留下 10 個資料夾：raw/ tasks/ calendar/ projects/ areas/ daily/ archives/ dashboard/ templates/ scripts/
- 待刪：wiki/、resources/（留待實作階段處理）
- AGENTS.md：移除知識管理字眼、加入三層架構、workflow、命名 / frontmatter 規範
- index.md：三層架構呈現、不列 wiki/ resources/
- 各資料夾 README.md：與 calendar/README.md 同風格
- dashboard/README.md：wikilink 改為指向 Layer 2 資料夾、移除 resources
