---
share: true
created: 2023-10-30T14:29
updated: 2026-08-27T20:24
---

```dataview
LIST rows.file.link
FROM "✍️Lập trình/Ngôn ngữ lập trình/Ý đồ thiết kế" 
GROUP BY split(file.folder, "/")[3]
WHERE file.name != this.file.name
```