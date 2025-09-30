---
share: true
created: 2023-08-25T14:20
updated: 2025-05-04T16:30
---
[GitHub - you-dont-need/You-Dont-Need: People choose popular projects, often not because it applies to their problems](https://github.com/you-dont-need/You-Dont-Need)
```dataview
LIST rows.file.link
FROM "✍️Lập trình" 
WHERE file.name!=this.file.name
group by split(file.folder,"/")[1] 
```
