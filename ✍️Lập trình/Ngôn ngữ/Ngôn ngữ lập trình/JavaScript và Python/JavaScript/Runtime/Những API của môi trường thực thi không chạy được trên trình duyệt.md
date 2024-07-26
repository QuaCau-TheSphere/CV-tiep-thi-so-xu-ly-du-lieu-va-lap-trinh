---
share: true
created: 2023-10-30T14:29
updated: 2024-07-26T13:44
---
[[JS vốn được sinh ra để chạy trên trình duyệt và không được dùng để làm việc với lượng code lớn]]
Trình duyệt không biết gì về Deno, Node, v.v. Muốn dùng các hàm do các môi trường thực thi này cung cấp thì phải chạy trên server chứ không chạy trên client được
[[Các hàm được môi trường thực thi cung cấp không hoạt động được ở island]]

[[Bundler dùng để gom hết tất cả các script lại vào làm một]]

Chính vì như vậy, nên [[Nên tách bạch file util cho client và util cho server]], vì [[Khi import một hàm thì cả file chứa hàm đó sẽ được chạy. Các import cũng sẽ chạy theo, dù là để import vào một hàm khác mình không import]]