---
type: learning
engine:
subject:
tags: []
created: <% tp.date.now("YYYY-MM-DD") %>
status: ongoing
---
# <% tp.file.title %>

## 📌 学习目标

## 📖 内容笔记

## 💡 关键要点

## 🔗 参考来源

## 📂 相关笔记
```dataview
TABLE type, status, created
FROM ""
WHERE contains(file.tags, this.tags[0]) AND file.name != this.file.name
SORT created DESC
LIMIT 10
```
