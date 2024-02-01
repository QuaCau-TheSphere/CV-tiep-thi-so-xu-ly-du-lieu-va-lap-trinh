---
share: true
created: 2024-01-12T17:36
updated: 2024-01-12T17:36
---

```dataview
LIST rows.file.link
FROM "Framework (Preact)" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[2]
```