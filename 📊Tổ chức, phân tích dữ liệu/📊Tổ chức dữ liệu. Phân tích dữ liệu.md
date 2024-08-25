---
share: true
created: 2023-10-30T15:20
updated: 2024-08-25T20:43
title: 📊Tổ chức dữ liệu. Phân tích dữ liệu
---

```dataview
LIST rows.file.link
FROM "📊Tổ chức dữ liệu. Phân tích dữ liệu" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[1]
```
