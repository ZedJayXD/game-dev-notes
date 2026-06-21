---
type: issue
severity: medium
status: open
tags: []
created: <% tp.date.now("YYYY-MM-DD") %>
resolved: 
---

# <% tp.file.title %>

## 🐛 问题描述

## 🔍 复现步骤

1. 
2. 
3. 

## 💡 根本原因

## ✅ 解决方案

## 📝 经验教训

## 🔗 相关笔记

```dataview
TABLE severity, status, created
FROM #issue OR type="issue"
WHERE status != "resolved"
SORT severity DESC, created DESC
```
