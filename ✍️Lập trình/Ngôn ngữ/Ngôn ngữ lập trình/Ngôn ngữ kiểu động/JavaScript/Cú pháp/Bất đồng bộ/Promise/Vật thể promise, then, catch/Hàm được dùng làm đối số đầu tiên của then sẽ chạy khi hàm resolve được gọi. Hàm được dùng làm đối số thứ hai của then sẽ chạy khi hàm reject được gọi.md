---
share: true
created: 2024-11-27T15:04
updated: 2025-03-03T18:48
---
[[Kết quả của promise chỉ có thể được lấy ở trong then, và phải ở dạng hàm]]
[[resolve, reject là hai hàm được JS cung cấp sẵn để làm đối số cho hàm thực thi]].
[[Khi resolve được gọi, vật thể promise sẽ cập nhật kết quả trả về từ resolve, và hàm được dùng làm đối số đầu tiên của then sẽ được chạy]]

- Thuộc tính `state` đang từ `pending` sẽ được gán giá trị mới là `fulfilled`
- Giá trị được truyền vào trong `resolve()` sẽ được gán vào thuộc tính `result` 
- Hàm được dùng làm đối số đầu tiên của `then()` sẽ chạy

Ngược lại, khi `reject()` được gọi:
- Thuộc tính `state` đang từ `pending` sẽ được gán giá trị mới là `rejected`
- Giá trị được truyền vào trong `reject()` sẽ được gán vào thuộc tính `result`  
- Hàm được dùng làm đối số thứ hai của `then()` sẽ chạy
