---
date: 2026-10-02
type: dashboard
tags: [home, dashboard]
---

# 🏠 Personal OS Dashboard

_單頁工作台。動態資料由 Dataview / Tasks plugin 自動拉取。_

> 手機看：上半部（過期、今日、本週）最重要，下半部可快速滑過。

---

## 🔴 過期（馬上處理）

```dataview
TASK
FROM "tasks"
WHERE !completed AND due AND due < date(today)
SORT due ASC
```

---

## 📅 今日

### Tasks due today

```dataview
TASK
FROM "tasks"
WHERE !completed AND due = date(today)
SORT priority DESC, due ASC
```

### 📆 今日事件（Google Calendar sync 進來）

```dataview
LIST
FROM "calendar/synced"
WHERE contains(file.name, "<% tp.date.now('YYYY-MM-DD') %>")
SORT startTime ASC
```

---

## 📆 本週 deadline

```dataview
TASK
FROM "tasks"
WHERE !completed AND due AND due > date(today) AND due <= date(today) + dur(7 days)
GROUP BY due
SORT due ASC
```

---

## ⏭️ Next Actions

```dataview
TASK
FROM "tasks/next"
WHERE !completed
SORT priority DESC, due ASC
LIMIT 5
```

---

## ⏳ 等待回覆

```dataview
TASK
FROM "tasks/waiting"
WHERE !completed
SORT file.ctime ASC
```

---

## 🎯 活躍專案

```dataview
TABLE status, due, area
FROM "projects"
WHERE status = "active"
SORT file.mtime DESC
```

---

## 📊 本週統計

```dataview
LIST
FROM "tasks/done"
WHERE file.cday >= date(today) - dur(7 days)
SORT file.cday DESC
```

---

## 📥 Inbox 待分流（最近 10 個）

```dataview
LIST
FROM "raw/captures"
SORT file.cday DESC
LIMIT 10
```

> 💡 如果這裡超過 5 個，代表該 triage 了。

---

## 🔧 快速連結

- [[daily/<% tp.date.now('YYYY-MM-DD') %>|今日 Daily Note]]
- [[projects/README|所有 Projects]]
- [[areas/README|所有 Areas]]
- [[resources/README|所有 Resources]]
- [[raw/captures|新增 Capture →]]
- [[AGENTS|操作準則]]
