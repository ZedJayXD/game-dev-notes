---
type: daily
tags: []
created: <% tp.date.now("YYYY-MM-DD") %>
---

# 📅 <% tp.date.now("YYYY-MM-DD") %> 日报

## ✅ 今日完成

- 

## 🐛 遇到问题

- 

## 📋 明日计划

- 

## 📊 本周笔记

```dataview
TABLE type, status
FROM ""
WHERE created >= date(today) - dur(7 days)
SORT created DESC
```
