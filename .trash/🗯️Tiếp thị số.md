---
share: true
filename: 🗯️Tiếp thị số
created: 2023-10-27T19:32
updated: 2023-10-30T18:25
---

```dataview
LIST rows.file.link
FROM "🗯️Tiếp thị số" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[1]
```
