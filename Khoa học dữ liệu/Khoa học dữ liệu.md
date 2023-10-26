---
share: true
title: Khoa học dữ liệu
created: 2023-10-21T20:49
updated: 2023-10-25T22:47
---
```dataview
LIST rows.file.link
FROM "⚡Hiểu biết sâu/Khoa học dữ liệu" 
WHERE file.name!=this.file.name
group by split(file.folder,"/")[2] 
```