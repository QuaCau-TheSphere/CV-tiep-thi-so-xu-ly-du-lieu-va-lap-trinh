---
share: true
updated: 2026-07-24T21:46
created: 2026-07-22T21:47
title: Variant của enum bị lọt ra toàn cục là vì code Gleam sau đó sẽ được dịch ra Erlang hoặc JavaScript, đều là ngôn ngữ không có ký hiệu kiểu, nên những code về kiểu sẽ bị gọt bỏ hết
---
Khái niệm:: 
Sau khi tìm hiểu thêm thì hóa ra giới hạn về "variant của enum bị lọt ra toàn cục" là lý do khách quan. Do code Gleam sau đó sẽ được dịch ra Erlang hoặc JavaScript, đều là ngôn ngữ không có ký hiệu kiểu (type annotation), nên những code về kiểu sẽ bị gọt bỏ hết. Đó là lý do tên kiểu (`LoadingStatus`, `UserStatus`) nằm ở một không gian khác với tên constructor (`Idle`, `IsLoading`), không dùng để chia vùng cho các constructor được.

Nguồn:: [Gleam - một lựa chọn mới cho lập trình web frontend](https://quan.hoabinh.vn/post/2026/03/gleam-mot-lua-chon-moi-cho-lap-trinh-web-frontend)