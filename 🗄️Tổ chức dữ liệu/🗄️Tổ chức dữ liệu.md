---
share: true
created: 2023-10-30T15:20
updated: 2026-08-06T15:36
---

```dataview
LIST rows.file.link
FROM "🗄️Tổ chức dữ liệu" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[1]
```
