---
share: true
created: 2024-01-27T13:38
updated: 2024-08-31T21:03
---

```dataview
LIST rows.file.link
FROM "🔠Văn bản, ký tự. Sắp chữ, thiết kế/Đồng bộ, sao lưu/Git" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[3]
```
[GitHub Skills](https://skills.github.com/)
![15 Lazygit Features In Under 15 Minutes - YouTube](https://www.youtube.com/watch?v=CPLdltN7wgE)