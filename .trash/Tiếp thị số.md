---
share: true
filename: Tiếp thị số
created: 2023-10-26T13:45
updated: 2023-10-26T13:48
---
```dataview
LIST rows.file.link
FROM "⚡Hiểu biết sâu/Tiếp thị số" 
WHERE file.name!=this.file.name
group by split(file.folder, "/")[2]
```
