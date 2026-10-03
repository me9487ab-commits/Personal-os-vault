---
banner:
  quote: "The mind is everything. What you think you become."
  author: "Buddha"
  image: "https://images.pexels.com/photos/2307638/pexels-photo-2307638.jpeg"
apex_columns:
  - name: 🔴 Overdue
    type: dataview
    query: TASK FROM wiki/tasks WHERE due < date(today) AND status != done SORT due ASC
  - name: �\85 Today
    type: dataview
    query: TASK FROM wiki/tasks WHERE due = date(today) AND status != done SORT priority DESC, due ASC
  - name: �\86 This week
    type: dataview
    query: TASK FROM wiki/tasks WHERE due >= date(today) AND due <= date(today, +7) AND status != done SORT due ASC
  - name: Next Actions
    type: dataview
    query: LIST FROM wiki/tasks/next SORT due ASC
  - name: Waiting
    type: dataview
    query: LIST FROM wiki/tasks/waiting
  - name: Active projects
    type: dataview
    query: LIST FROM wiki/projects WHERE status = active SORT file.mtime DESC
  - name: Week stats
    type: dataview
    query: TASK FROM wiki/tasks WHERE due >= date(today) AND due <= date(today, +7) AND status != done GROUP BY priority
  - name: Inbox (latest 10)
    type: dataview
    query: LIST FROM wiki/tasks/inbox SORT file.ctime DESC LIMIT 10
---

# Dashboard

> `The mind is everything. What you think you become.` — Buddha

## Mode

| Installed | Behavior |
|---|---|
| **Apex Dashboard plugin** | Reads `apex_columns:` from frontmatter; body is ignored |
| **Only Dataview** | Frontmatter is plain metadata; 9 Dataview blocks below auto-render |

---

## 🔴 Overdue

```dataview
TASK
FROM `wiki/tasks`
WHERE due < date(today) AND status != `done`
SORT due ASC
```

## 📅 Today

### Tasks due today

```dataview
TASK
FROM `wiki/tasks`
WHERE due = date(today) AND status != `done`
SORT priority DESC, due ASC
```

### Today events

```dataview
LIST
FROM `wiki/calendar/synced`
WHERE file.day = date(today)
SORT start ASC
```

## 📆 This week

```dataview
TASK
FROM `wiki/tasks`
WHERE due >= date(today) AND due <= date(today, +7) AND status != `done`
SORT due ASC
```

## ⏍️ Next Actions

```dataview
LIST
FROM `wiki/tasks/next`
SORT due ASC
```

## ⏳ Waiting

```dataview
LIST
FROM `wiki/tasks/waiting`
```

## 🎯 Active projects

```dataview
LIST
FROM `wiki/projects`
WHERE status = `active`
SORT file.mtime DESC
```

## 📊 Week stats

```dataview
TASK
FROM `wiki/tasks`
WHERE due >= date(today) AND due <= date(today, +7) AND status != `done`
GROUP BY priority
```

## 📥 Inbox (latest 10)

```dataview
LIST
FROM `wiki/tasks/inbox`
SORT file.ctime DESC
LIMIT 10
```
