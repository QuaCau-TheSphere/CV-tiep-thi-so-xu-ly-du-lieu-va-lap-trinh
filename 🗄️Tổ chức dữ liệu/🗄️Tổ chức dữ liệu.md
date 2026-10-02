---
share: true
created: 2023-10-30T15:20
updated: 2026-09-28T14:32
---
[Database of Databases · The Encyclopedia of Database Systems](https://dbdb.io/)

```dataview
LIST rows.file.link
FROM "🗄️Tổ chức dữ liệu" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[1]
```
