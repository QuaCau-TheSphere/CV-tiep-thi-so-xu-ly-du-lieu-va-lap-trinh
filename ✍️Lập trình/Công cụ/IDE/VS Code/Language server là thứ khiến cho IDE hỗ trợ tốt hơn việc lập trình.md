---
share: true
created: 2023-10-30T14:29
updated: 2025-08-06T21:37
---
Trước tiên, cần nhắc tới Language Server, là chỉ tiện ích mở rộng cung cấp trải nghiệm chỉnh sửa cho nhiều ngôn ngữ lập trình. Với Language Server, bạn có thể triển khai tính năng tự động hoàn thành (autocomplete), kiểm tra lỗi (diagnostics), tìm tới định nghĩa (jump-to-definition), vân vân và mây mây. Ví dụ mình sử dụng PHP, thì Language Server của PHP có thể đủ thông minh mà tìm ra lỗi cú pháp, chỉ ra cái function của mình nó đang nằm ở đâu,... Các vấn đề về Language Server được team phát triển của Visual Studio Code gặp phải và nhắc tới với 3 khó khăn chủ yếu:

- Đầu tiên, Languague Server thường được triển khai tại ngôn ngữ lập trình gốc của chính nó. Thế nên khá khó cho VSCode trong việc tích hợp từng ngôn ngữ vào một editor sử dụng NodeJS runtime, trong khi điều mà VSCode nhắm tới chính là khả năng mở rộng và tính tùy biến phù hợp mọi ngôn ngữ lập trình.
- Thêm vào đó, các tính năng của ngôn ngữ cụ thể có thể tiêu tốn nhiều, rất nhiều tài nguyên trên máy tính.
- Cuối cùng, tích hợp nhiều công cụ ngôn ngữ với nhiều trình soạn thảo code riêng biệt đòi hỏi lượng công việc đáng kể. Từ quan điểm trên, về việc cần phải tích hợp các editor khác nhau với các API của language khác nhau, ta có thể nhìn thấy rằng giả sử có M ngôn ngữ lập trình và N editor riêng biệt => lượng công việc là M x N 😂 Quả là sự lãng phí về thời gian và nhân lực.

Để giải quyết vấn đề trên, Microsoft đã xây dựng một giao thức nằm giữa, nhằm chuẩn hóa giao tiếp giữa ngôn ngữ lập trình và trình soạn thảo code, hay chính là Language Server Protocal (LSP). Bằng cách này, Language Server có thể triển khai bằng bất kỳ ngôn ngữ nào và chạy trong quy trình riêng của nó, thay vì bắt NodeJS phải thực thi các file PHP chẳng hạn, vì chúng chỉ giao tiếp với Language Server Protocol. Và ở phía editor của chúng ta, chỉ cần nó tuân thủ LSP thì cũng có thể dễ dàng triển khai thực hiện các tiện ích của Language Server.

![image.png](https://images.viblo.asia/6bdf819b-36d2-41fd-bf24-804d33da8142.png)
Nguồn:: [[Viblo]], [Vim vs. Neovim 2022 - Có những gì khác nhau - Viblo](https://viblo.asia/p/vim-vs-neovim-2022-co-nhung-gi-khac-nhau-Qbq5QRaRKD8)