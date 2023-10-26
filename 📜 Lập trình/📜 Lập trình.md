---
share: true
title: 📜 Lập trình
created: 2023-08-25T14:20
updated: 2023-10-25T22:47
---

```dataview
LIST rows.file.link
FROM "📜 Lập trình" 
WHERE file.name!=this.file.name
group by split(file.folder,"/")[1] 
```