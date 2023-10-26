---
created: 2023-10-24T18:21
updated: 2023-10-24T18:21
---
```dataview
LIST
FROM "👏Trấn Kỳ" 
WHERE file.name!=this.file.name
Where file.name=split(file.folder, "/")[1]
```