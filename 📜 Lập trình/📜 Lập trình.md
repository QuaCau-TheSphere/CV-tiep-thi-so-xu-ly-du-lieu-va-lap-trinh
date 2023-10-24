---
share: true
filename: index
title: 📜 Lập trình
created: 2023-08-25T14:20
updated: 2023-10-24T15:41
---

```dataview
LIST rows.file.link
FROM "📜 Lập trình" 
WHERE file.name!=this.file.name
group by split(file.folder,"/")[1] 
```