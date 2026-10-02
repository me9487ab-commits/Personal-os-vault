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

## [2026-10-02] cleanup | 刪除 wiki/ 與 resources/ 資料夾

- 範圍最終定案：不含 wiki/（不存知識管理）與 resources/（PARA 的資源類）
- 知識管理統一歸 LLM-Wiki vault
- index.md 移除對應 wikilink

## [2026-10-02] restructure | working data 全部包入 wiki/ 容器

Layer 2 重新組織：tasks/calendar/projects/areas/daily/archives → wiki/ 下。
- raw/ 維持頂層（Layer 1 不可變 inbox）
- wiki/tasks/, wiki/calendar/, wiki/projects/, wiki/areas/, wiki/daily/, wiki/archives/
- AGENTS.md、index.md、全部 README.md 的 wikilink 同步更新
