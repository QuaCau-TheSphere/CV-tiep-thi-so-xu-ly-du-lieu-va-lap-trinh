---
share: true
created: 2025-03-06T22:26
updated: 2025-03-06T22:28
---
[On Typesetting Engines: A Programmer's Perspective](https://blog.ppresume.com/posts/on-typesetting-engines)
```dataview
LIST rows.file.link
FROM "🔠Ký tự, văn bản. Quản lý, viết và xuất bản nội dung/Sắp chữ, thiết kế" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[3]
```