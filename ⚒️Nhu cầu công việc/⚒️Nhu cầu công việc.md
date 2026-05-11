---
share: true
created: 2023-10-30T14:29
updated: 2026-01-29T22:17
---
```dataview
LIST rows.file.link
FROM "⚒️Nhu cầu công việc"
GROUP BY split(file.folder, "/")[1]
WHERE file.name != this.file.name
```
