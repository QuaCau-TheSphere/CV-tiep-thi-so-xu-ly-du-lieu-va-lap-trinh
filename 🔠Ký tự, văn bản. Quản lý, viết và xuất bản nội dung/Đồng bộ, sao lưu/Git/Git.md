---
share: true
created: 2024-01-27T13:38
updated: 2024-09-01T18:00
---

```dataview
LIST rows.file.link
FROM "🔠Ký tự, văn bản. Quản lý, viết và xuất bản nội dung/Đồng bộ, sao lưu/Git" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[3]
```
[GitHub Skills](https://skills.github.com/)
![15 Lazygit Features In Under 15 Minutes - YouTube](https://www.youtube.com/watch?v=CPLdltN7wgE)