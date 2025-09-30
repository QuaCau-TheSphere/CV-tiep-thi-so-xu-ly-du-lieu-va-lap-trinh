---
share: true
created: 2023-10-30T14:29
updated: 2025-09-28T17:09
---
.htaccess không chứa mã độc. Nhưng nó mở cửa cho việc upload file JS vào thư mục.

Bên trong file.js có code này:
```
<FilesMatch "\.js$"> SetHandler application/x-httpd-php Header set Content-type "application/javascript" </FilesMatch>
```

Nó biến các file JavaScript (.js), vốn chỉ nên chạy trên trình duyệt của người dùng, thành các file kịch bản PHP có thể thực thi trực tiếp trên máy chủ của bạn.

Nói một cách đơn giản, đoạn mã này ra lệnh cho máy chủ web của bạn: "Từ nay, bất cứ khi nào có yêu cầu truy cập một file có đuôi là .js, hãy xử lý nó như một file PHP, nhưng khi trả về cho trình duyệt thì hãy nói dối rằng nó là file JavaScript bình thường."
Nguồn:: 