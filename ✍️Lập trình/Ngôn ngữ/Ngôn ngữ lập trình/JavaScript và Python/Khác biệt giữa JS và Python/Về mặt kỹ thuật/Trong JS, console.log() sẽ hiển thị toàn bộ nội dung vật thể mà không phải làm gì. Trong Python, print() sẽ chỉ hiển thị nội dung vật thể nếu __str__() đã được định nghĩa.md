---
share: true
created: 2023-10-30T14:29
updated: 2024-05-16T20:13
---
Trong REPL của JS (console), việc gọi trực tiếp vật thể không khác gì `console.log()` nó. Cả hai đều hiểu thị hết các dữ liệu của nó. Trong khi đó ở Python thì không như vậy. [[Trong REPL, gọi trực tiếp vật thể ra thì kết quả là __repr__(). Nếu dùng print thì kết quả là __str__()]]. [[__repr__() trả về mô tả chi tiết để người lập trình bảo trì và sửa lỗi. __str__() trả về mô tả đơn giản cho người dùng sử dụng]] 

|                | JS                                        | Python                    |
| -------------- | ----------------------------------------- | ------------------------- |
| Đọc thuộc tính | `object.attribute`, `object['attribute']` | `object.get('attribute')` |


[[Việc hiển thị nội dung dữ liệu như thế nào là do công cụ quyết định, không phải ngôn ngữ quyết định]]. [[JS được sinh ra để chạy trên trình duyệt và không được dùng để làm việc với lượng code lớn]], còn [[Python tập trung vào việc cung cấp một ngôn ngữ lập trình tổng quát, dễ đọc và dễ viết]]

[[JSON là cách để biểu diễn vật thể ra chữ, chứ tự nó không phải là vật thể]]

Thứ có vẻ như thực sự tương đương 