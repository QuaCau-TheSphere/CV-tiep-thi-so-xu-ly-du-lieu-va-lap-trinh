---
share: true
created: 2023-10-30T14:29
updated: 2026-10-02T15:38
---
```dataview
LIST rows.file.link
FROM "📎Nhu cầu công nghệ"
GROUP BY split(file.folder, "/")[1]
WHERE file.name != this.file.name
```
