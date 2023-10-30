---
share: true
title: 📊Phân tích dữ liệu
created: 2023-10-21T20:49
updated: 2023-10-30T01:12
---
```dataview
LIST rows.file.link
FROM "📊Phân tích dữ liệu" 
WHERE file.name!=this.file.name
group by split(file.folder,"/")[2] 
```
