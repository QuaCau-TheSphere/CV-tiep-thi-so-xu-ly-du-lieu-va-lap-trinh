---
share: true
created: 2024-03-03T12:53
updated: 2026-07-06T21:40
---
```dataview
LIST rows.file.link
FROM "⚒️Nhu cầu công việc/Sắp chữ, thiết kế/Sắp chữ/TeX" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[4]
```

[Often referenced questions](https://tex.meta.stackexchange.com/q/2419/50146)
