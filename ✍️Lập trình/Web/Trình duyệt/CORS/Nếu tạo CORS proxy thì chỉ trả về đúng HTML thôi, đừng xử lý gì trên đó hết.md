---
share: true
created: 2023-10-30T14:29
updated: 2024-11-30T13:38
---
Vì nếu xử lý và cần trả về một vật thể có chứa DOM, thì việc phải dùng `return Response.json()` sẽ gây lỗi circular
[[DOM là kết quả của việc phân tích cú pháp một tài liệu HTML cộng với]]
Nguồn:: [[Tự ngẫm nghĩ, trải nghiệm]]