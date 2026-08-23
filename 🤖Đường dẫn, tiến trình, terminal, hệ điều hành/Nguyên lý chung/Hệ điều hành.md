---
share: true
updated: 2026-08-23T12:57
created: 2026-07-09T23:44
---
Khái niệm:: 
![Every operating system concept in one video… - YouTube](https://www.youtube.com/watch?v=MtxP2pyCvYA)
![Every Illegal Operating System Explained in 15 Minutes - YouTube](https://www.youtube.com/watch?v=2D2Z-eqK0YM)
```dataview
LIST rows.file.link
FROM "🤖Đường dẫn, tiến trình, terminal, hệ điều hành"
GROUP BY split(file.folder, "/")[1]
WHERE file.name != this.file.name
```
