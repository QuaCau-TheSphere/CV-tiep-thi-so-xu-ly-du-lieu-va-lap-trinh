---
share: true
created: 2024-02-01T22:58
updated: 2024-02-01T22:58
---

```dataview
LIST rows.file.link
FROM "✍️Lập trình/Khái niệm cơ bản và nguyên lý lập trình/Nguyên lý" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[3]
```