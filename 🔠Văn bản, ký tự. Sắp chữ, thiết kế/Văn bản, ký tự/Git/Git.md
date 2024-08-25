---
share: true
created: 2024-01-27T13:38
updated: 2024-08-25T20:50
---

```dataview
LIST rows.file.link
FROM "🔠Văn bản, ký tự. Sắp chữ, thiết kế/Git" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[2]
```
[GitHub Skills](https://skills.github.com/)
![15 Lazygit Features In Under 15 Minutes - YouTube](https://www.youtube.com/watch?v=CPLdltN7wgE)