---
share: true
created: 2023-10-30T15:20
updated: 2023-10-30T18:25
---

```dataview
LIST rows.file.link
FROM "📊Tổ chức dữ liệu. Phân tích dữ liệu" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[1]
```
