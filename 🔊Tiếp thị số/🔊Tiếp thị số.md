---
share: true
filename: Tiếp thị số
created: 2023-10-26T13:45
updated: 2024-08-18T15:05
---
```dataview
LIST rows.file.link
FROM "🔊Tiếp thị số" 
WHERE file.name!=this.file.name
group by split(file.folder, "/")[1]
```