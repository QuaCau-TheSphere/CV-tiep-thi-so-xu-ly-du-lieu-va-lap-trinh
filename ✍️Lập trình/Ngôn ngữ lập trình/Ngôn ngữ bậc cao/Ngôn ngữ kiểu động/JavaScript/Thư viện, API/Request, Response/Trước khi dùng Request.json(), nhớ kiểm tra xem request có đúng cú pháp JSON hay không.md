---
share: true
created: 2023-10-30T14:29
updated: 2026-07-24T21:47
---
Khái niệm:: [[JSON]]
[[Serialize là cách duy nhất để truyền dữ liệu từ máy phục vụ tới máy khách và ngược lại]]. Cách serialize thông dụng là dùng `JSON.serialize()`. Nhưng sẽ có những lúc body không được tạo ra bằng cách đó, mà được tạo ra bằng việc nối chuỗi:
```
{"a": %x, "b": %y}
```

Nếu các biến `%x`, `%y` có thể chứa các ký tự có trong JSON mà không được escape trước, thì body không đúng cú pháp JSON, dẫn đến việc `req.json()` lúc chạy được lúc không. Nhưng ta lại không nghĩ là vấn đề nằm ở việc request body không đúng cú pháp, vì cứ đinh ninh là nó được `serialize()` đúng cách.

Có thể dùng [[TS chỉ có thể bắt lỗi kiểu dữ liệu trong lúc viết code. Zod giúp bắt lỗi kiểu do người dùng gửi|Zod để bắt lỗi kiểu do người dùng gửi]]

Nguồn:: [[Tự ngẫm nghĩ, trải nghiệm]]
