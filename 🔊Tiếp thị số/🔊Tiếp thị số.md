---
share: true
filename: Tiếp thị số
created: 2023-10-26T13:45
updated: 2024-07-03T20:53
---
```dataview
LIST rows.file.link
FROM "🔊Tiếp thị số" 
WHERE file.name!=this.file.name
group by split(file.folder, "/")[1]
```