---
share: true
created: 2024-09-10T16:36
updated: 2025-09-30T07:57
---
![[Các định dạng dữ liệu thường gặp khi xử lý văn bản.excalidraw]]
```dataview
LIST rows.file.link
FROM "📊Tổ chức dữ liệu/Định dạng dữ liệu" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[2]
```