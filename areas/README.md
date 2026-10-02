---
type: readme
---

# areas/ — Areas (PARA)

持續要照顧、**沒有 deadline** 的責任區。Layer 2 的工作區之一。

## 與 Project 的差別

| | Project | Area |
|---|---|---|
| Deadline | 有 | 沒有 |
| 完成條件 | 明確 | 持續責任 |
| 結束動作 | 移 `archives/projects/` | 不結束，只 review |
| 範例 | 搬家、論文、網站改版 | 健康、財務、職涯 |

詳見 [[AGENTS#areas-vs-projects-判斷]]。

## 結構

- 每個 area **一個 .md 檔**（不是資料夾）
- 範例：`areas/health.md`、`areas/finance.md`、`areas/career.md`

## Frontmatter Schema

完整模板見 [[templates/area]]。

| 欄位 | 必填 | 說明 |
|---|---|---|
| `type` | ✓ | `area` |
| `status` | ✓ | `active` / `dormant` |
| `tags` | | 標籤 |

## 內容結構

每個 area 檔案內含：

- **目標** — 這個 area 想維持什麼狀態
- **現況** — 目前大致狀態（簡述，定期更新）
- **近期重點** — 這季 / 這月關注的幾件事
- **知識庫** — wikilink 到外部 LLM-Wiki vault 的相關 topic（area 本身不存知識內容，只放連結）

## 命名規範

- 檔名：lowercase + dash
- 用責任命名而非專案：`health.md` 而非 `2026-fitness.md`

## 範例

```yaml
---
type: area
status: active
tags: [personal, long-term]
---

# Health

## 目標
維持身體與心理健康，年度健檢正常。

## 現況
運動頻率下降、睡眠不穩。

## 近期重點
- 重啟每週 3 次慢跑
- 預約年度健檢

## 知識庫
- [[wiki/health-sleep|LLM-Wiki: 睡眠]]（外部連結，wikilink 形式）
```

> 知識庫段落**只放 wikilink 指向 LLM-Wiki vault**，不放知識內容本身。知識管理歸 LLM-Wiki。

## Review 頻率

每季 review 一次（見 [[AGENTS#workflow]]），確認：
- `status: active` 仍是合理的
- 「近期重點」有在動
- 對應的 task 有在 [[tasks/README|tasks/]] 流動
