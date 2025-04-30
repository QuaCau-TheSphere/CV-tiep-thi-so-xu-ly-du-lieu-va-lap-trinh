---
share: true
created: 2024-03-03T12:53
updated: 2025-04-28T19:32
---
```dataview
LIST rows.file.link
FROM "🔠Ký tự, văn bản. Quản lý, viết và xuất bản nội dung/Sắp chữ, thiết kế/Sắp chữ/TeX" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[4]
```

[Often referenced questions](https://tex.meta.stackexchange.com/q/2419/50146)