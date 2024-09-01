---
share: true
created: 2024-03-03T12:53
updated: 2024-08-31T21:04
---
```dataview
LIST rows.file.link
FROM "🔠Văn bản, ký tự. Sắp chữ, thiết kế/Sắp chữ, thiết kế/TeX"
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[3]
```

[Often referenced questions](https://tex.meta.stackexchange.com/q/2419/50146)