---
share: true
created: 2024-01-27T13:38
updated: 2024-01-27T13:38
---

```dataview
LIST rows.file.link
FROM "Git" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[2]
```
[GitHub Skills](https://skills.github.com/)