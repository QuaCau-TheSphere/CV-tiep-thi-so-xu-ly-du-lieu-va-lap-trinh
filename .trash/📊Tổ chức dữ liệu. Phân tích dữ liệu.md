---
created: 2023-10-30T15:20
updated: 2023-10-30T15:20
---
```dataview
LIST
FROM "📊Tổ chức dữ liệu. Phân tích dữ liệu" 
WHERE file.name!=this.file.name
```
Where file.name=split(file.folder, "/")[1]
