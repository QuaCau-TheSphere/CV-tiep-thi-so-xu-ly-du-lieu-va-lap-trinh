---
share: true
created: 2023-10-30T14:29
updated: 2024-11-21T12:16
---
Sau này khi cần làm React thì sẽ rất tiện ([[Component là những hàm hoặc lớp trả về một khối JSX]]) 
```tsx
  <ul>
	{fuseBàiĐăng.search(keyword).map(
	  (kếtQuả) => <li>{kếtQuả.item["Tiêu đề"]}</li>,
	)}
  </ul>
```
Nguồn:: ![#26 Map Arrays - Dùng Hàm Map Thay Vì For Loops | JavaScript Cơ Bản Từ A đến Z Cho Beginners - YouTube](https://youtu.be/2oyyugWmGMk?si=D2Z6kXOTWegDLElg&t=460)json