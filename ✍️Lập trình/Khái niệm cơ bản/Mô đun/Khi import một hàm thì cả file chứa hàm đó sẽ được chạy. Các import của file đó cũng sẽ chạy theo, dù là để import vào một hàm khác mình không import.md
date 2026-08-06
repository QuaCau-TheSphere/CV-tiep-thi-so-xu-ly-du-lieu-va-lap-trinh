---
share: true
created: 2023-09-17T18:30
updated: 2026-08-06T15:36
---
VD:

Nếu:
- có một mảng được khai báo ở ngoài hàm `main()`, 
- trong hàm mảng đó được thêm thành phần, 
- có một vòng lặp nào đó **ở file khác** gọi `main()`

thì hàm sẽ bị chồng dữ liệu với những dữ liệu ở lần gọi cũ
[[Để tránh phụ thuộc lòng vòng (circular dependency) có thể dùng hàm]]
[[Nên tách bạch code hỗ trợ cho client và server vào những mô đun khác nhau]] 
