---
share: true
created: 2024-02-01T22:58
updated: 2026-08-06T15:38
---
```dataview
LIST rows.file.link
FROM "✍️Lập trình/Kỹ thuật xử lý" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[2]
```
