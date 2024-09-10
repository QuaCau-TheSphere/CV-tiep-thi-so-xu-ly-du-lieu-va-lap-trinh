---
share: true
created: 2024-09-10T16:36
updated: 2024-09-10T16:36
---
![[Mối quan hệ giữa định dạng dữ liệu, định dạng văn bản, và ngôn ngữ đánh dấu.excalidraw]]
```dataview
LIST rows.file.link
FROM "📊Tổ chức, phân tích dữ liệu/Định dạng dữ liệu" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[2]
```