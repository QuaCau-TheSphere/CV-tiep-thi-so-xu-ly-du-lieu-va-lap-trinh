---
share: true
created: 2024-02-01T22:58
updated: 2026-07-16T22:29
---
```dataview
LIST rows.file.link
FROM "✍️Lập trình/Kỹ thuật xử lý" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[2]
```
