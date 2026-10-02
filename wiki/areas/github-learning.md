---
type: area
status: active
tags: [learning, programming, dev-tools]
---

# GitHub Learning

長期熟悉 GitHub 平台、Git 工作流、開發者協作工具。

## 目標

- 能熟練用 Git + GitHub CLI 做日常開發協作
- 理解 PR review / issue / Projects workflow
- 能在 Personal-OS vault 透過 GitHub 備份 / 同步
- 知道怎麼用 GitHub Actions 跑 CI

## 現況

> 你目前知道的程度，自己填一下

- [ ] 基礎：clone / commit / push / pull
- [ ] 中階：branch / merge / conflict resolve
- [ ] 進階：rebase / cherry-pick / submodule / worktree
- [ ] GitHub CLI：沒用過
- [ ] GitHub Actions：沒用過
- [ ] PR / Issue workflow：用過基本

## 近期重點

- [ ] 裝 GitHub CLI (`gh`)，試 issue / PR / repo 指令
- [ ] 練習 interactive rebase
- [ ] 跑第一個 GitHub Actions workflow
- [ ] 把 Personal-OS vault 推到 GitHub private repo

## 相關 task

> Dataview 自動從 wiki/tasks/ 拉 `area: github-learning` 的

```dataview
TASK
FROM "wiki/tasks"
WHERE area = "github-learning" AND !completed
SORT priority DESC, due ASC
```

## 知識庫

> 統一歸 LLM-Wiki vault，本 area 只放連結

- LLM-Wiki topic：`github-cli`
- LLM-Wiki topic：`git-rebase`
- LLM-Wiki topic：`github-actions`
- LLM-Wiki topic：`git-workflow`
- LLM-Wiki topic：`git-conflict`

## Review 頻率

每季 review（見 AGENTS.md workflow）。
