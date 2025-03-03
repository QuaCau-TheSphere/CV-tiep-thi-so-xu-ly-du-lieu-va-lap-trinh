---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
JavaScript là dynamic typing, có nghĩa là một biến có thể nhận bất cứ kiểu dữ liệu nào (ví dụ integer sau đó lại gán thành string). Đây là một ưu điểm lớn với những script nhỏ (vài dòng đến vài chục dòng) vì nó giúp lập trình nhanh hơn. Nhưng với những ứng dụng lớn, có nhiều module, điều đó khiến việc xử lý dữ liệu nhiều khi rơi vào bế tắc do không biết dữ liệu của biến là gì (và nó đã bị thay đổi từ khi nào).

JavaScript không hỗ trợ static typing, là kiểu lập trình mà mỗi biến sẽ được khai báo kiểu dữ liệu trước và sẽ gặp lỗi nếu được gán giá trị có kiểu dữ liệu khác. TypeScript là ngôn ngữ cung cấp tính năng này.

Nguồn:: [So sánh nhỏ: TypeScript vs JavaScript | manhhomienbienthuy](https://manhhomienbienthuy.github.io/2022/03/01/so-sanh-nho-typescript-vs-javascript.html)

[[JavaScript vốn được sinh ra để chạy trên trình duyệt và không được dùng để làm việc với lượng code lớn]]
[[Sự xuất hiện của language server giúp ta có thể bắt kiểu trước cả lúc biên dịch cho những ngôn ngữ chỉ bắt kiểu lúc chạy]]
[[Kiểu động làm cho việc học lập trình dễ hơn. Kiểu yếu giúp ngôn ngữ được tự do ép kiểu để đoán ý người dùng dễ hơn]]