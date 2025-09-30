---
share: true
created: 2023-10-24T18:26
updated: 2025-09-12T14:05
---

```dataview
LIST rows.file.link
FROM "✍️Lập trình/Ngôn ngữ/Ngôn ngữ lập trình/Ngôn ngữ kiểu động/JavaScript/TypeScript"
WHERE file.name != this.file.name
GROUP BY split(file.folder, "/")[6]
```
