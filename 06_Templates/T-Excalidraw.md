---
type: drawing
tags: []
created: <% tp.date.now("YYYY-MM-DD") %>
---

# 🎨 <% tp.file.title %>

## 📝 说明

## 🔗 关联笔记

```dataview
TABLE type, created
FROM ""
WHERE contains(file.outlinks, this.file.link)
SORT created DESC
```
