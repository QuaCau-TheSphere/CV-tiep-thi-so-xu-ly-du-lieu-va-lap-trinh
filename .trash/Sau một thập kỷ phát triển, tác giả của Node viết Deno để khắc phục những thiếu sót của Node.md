---
share: true
created: 2023-10-24T18:26
updated: 2024-11-11T15:57
---
[Node's Complexity Problem](https://deno.com/learn/nodes-complexity-problem)
> [Deno](https://deno.land/) là môi trường để thực thi JavaScript và TypeScript tương tự như Node.js. Deno là công cụ được tạo bởi Ryan Dahl – cũng là tác giả của Node.js – để khắc phục những thiếu sót của Node.js. Nó vẫn được xây dựng dựa trên V8 JavaScript Engine, tuy nhiên nó được viết bằng ngôn ngữ lập trình Rust.
> 
> Deno còn chạy được cả WebAssembly nữa 😀.
> 
> Những vấn đề của Node.js đã được tác giả đề cập trong buổi [phát biểu tại JSConf EU](https://youtu.be/M3BM9TB-8yA) năm 2018. Những vấn đề này thường được biết đến là “10 Things I Regret About Node.js”. Một số vấn đề nổi bật là thiếu sự bảo mật, cài đặt dependency thông qua `node_modules` chưa hợp lý, khó làm việc với promise và một vài vấn đề khác. Và để sữa chữa những vấn đề đó, anh ta đã phát triển Deno. 
> Tại sao lại phát triển một công cụ mới mà không nâng cấp Node.js? Lý do là vì Node.js đang được dùng quá rộng rãi. Việc đưa tính năng mới mà vẫn đảm bảo tương thích ngược với phiên bản hiện tại không phải việc đơn giản. Đó là chưa kể những tính năng này cũng cần thời gian phát triển và sửa lỗi nhất định. Nên phát triển một công cụ mới là lựa chọn hợp lý hơn nhiều.
Nguồn:: [Giới thiệu Deno – một lựa chọn thay thế cho Node.js | manhhomienbienthuy](https://manhhomienbienthuy.github.io/2023/02/02/gioi-thieu-deno-mot-lua-chon-thay-the-cho-nodejs.html)

![](https://youtu.be/E82zJlINvkk) 
![](https://youtu.be/M3BM9TB-8yA?si=Fs_igz0Dxdpd9WrL) 

![[Kiến trúc giữa Node và Deno.png]]
Nguồn:: [𝗗𝗲𝗻𝗼 là viết ngược của 𝗡𝗼𝗱𝗲. Vậy liệu... - Techbase Vietnam | Facebook](https://www.facebook.com/techbasevietnam/posts/pfbid0UBHyykVMpsRnGyiqjeLmv5rhBvmSwJ4zCy7joRCLWqXFEk94nULb6UEePpR2rYpxl)