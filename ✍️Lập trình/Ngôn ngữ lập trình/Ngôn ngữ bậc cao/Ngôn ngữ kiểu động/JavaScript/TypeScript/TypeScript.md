---
share: true
created: 2023-10-24T18:26
updated: 2026-08-06T15:36
---

```dataview
LIST rows.file.link
FROM "✍️Lập trình/Ngôn ngữ lập trình/Ngôn ngữ bậc cao/Ngôn ngữ kiểu động/JavaScript/TypeScript"
WHERE file.name != this.file.name
GROUP BY split(file.folder, "/")[6]
```
