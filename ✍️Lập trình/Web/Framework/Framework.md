---
share: true
created: 2024-01-12T17:36
updated: 2024-02-15T11:06
---

```dataview
LIST rows.file.link
FROM "✍️Lập trình/Web/Framework" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[3]
```