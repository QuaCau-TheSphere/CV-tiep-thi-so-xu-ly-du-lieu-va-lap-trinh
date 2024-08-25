---
share: true
created: 2023-09-17T18:30
updated: 2024-08-24T12:38
---
VD:

Nếu:
- có một mảng được khai báo ở ngoài hàm `main()`, 
- trong hàm mảng đó được thêm thành phần, 
- có một vòng lặp nào đó **ở file khác** gọi `main()`

thì hàm sẽ bị chồng dữ liệu với những dữ liệu ở lần gọi cũ
[[Để tránh phụ thuộc lòng vòng (circular dependency) có thể dùng hàm]]
[[Nên tách bạch file util cho client và util cho server]] 