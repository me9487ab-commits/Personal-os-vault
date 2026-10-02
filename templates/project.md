---
date: <% tp.date.now("YYYY-MM-DD") %>
type: project
status: active
area:
due:
tags: []
---

# <% tp.file.title %>

## 目標
（一句話寫清楚「完成 = 什麼」）

## Tasks
```dataview
TASK
FROM "wiki/tasks/next"
WHERE project = "<% tp.file.title %>"
```

## 決策

## 筆記
