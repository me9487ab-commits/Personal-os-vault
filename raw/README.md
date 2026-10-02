---
type: readme
---

# raw/ — Inbox（不可變）

Layer 1 的不可變 inbox。所有東西先丟這，再由 triage 流程分流到 Layer 2。**寫入後不修改、不刪除**。

## 子資料夾

| 子資料夾 | 用途 |
|---|---|
| `captures/` | 隨手記、語音轉文字、截圖 |
| `emails/drafts/` | AI 寫的 email reply draft（待送出） |
| `external/` | 從外部 ingest（網頁、書摘預處理、第三方匯入） |

## 原則

- **Capture 不分類，先丟再說**
- 寫入後不再編輯
- 分流到 Layer 2 後，在該檔 frontmatter 加 `source: raw/captures/<filename>` 保留出處

## Frontmatter 範例

capture 檔案（[[templates/capture]]）：

```yaml
---
date: 2026-10-02
type: capture
source: ""
tags: []
---
```

email draft 標 `type: email-draft` 並加 `priority:`、`to:` 欄位（future）。

## 流程

```
寫入 raw/captures/   →   Triage   →   tasks/ | calendar/ | projects/ | areas/
                        （每日）
```

詳見 [[AGENTS#workflow]]。
