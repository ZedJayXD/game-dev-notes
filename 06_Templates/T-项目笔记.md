---
type: project
engine: godot
tags: []
created: <% tp.date.now("YYYY-MM-DD") %>
status: active
---
# <% tp.file.title %>

## 🎯 项目概述

- **引擎：**
- **类型：**
- **目标平台：**

## 📋 开发计划

- [ ] 

## 📝 开发日志

### <% tp.date.now("YYYY-MM-DD") %>

## 🐛 已知问题

## 🔗 相关笔记

```dataview
TABLE status, created
FROM "01_Projects"
WHERE file.name != this.file.name
SORT created DESC
LIMIT 5
```
