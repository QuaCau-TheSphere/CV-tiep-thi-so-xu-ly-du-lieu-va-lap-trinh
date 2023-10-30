---
share: true
filename: Web
created: 2023-10-26T13:55
updated: 2023-10-30T18:19
---

```dataview
LIST rows.file.link
FROM "📜 Lập trình/Web" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[2]
```
