---
share: true
created: 2023-10-30T15:20
updated: 2024-09-10T17:06
---

```dataview
LIST rows.file.link
FROM "📊Tổ chức, phân tích dữ liệu" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[1]
```
