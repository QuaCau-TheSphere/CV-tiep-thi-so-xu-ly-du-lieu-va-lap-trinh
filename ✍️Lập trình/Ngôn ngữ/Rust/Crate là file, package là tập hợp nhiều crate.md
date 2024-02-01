---
share: true
created: 2023-10-30T14:29
updated: 2024-02-01T21:39
---
Một _package_ là một hoặc nhiều crates cung cấp một loạt các chức năng. Một package chứa một file _Cargo.toml_ mô tả cách build các crate của package đó.

Một _crate_ có thể là một binary crate hoặc một library crate. _Binary crates_ là các chương trình bạn có thể biên dịch và thực thi để chạy, chẳng hạn như một command-line program hoặc một server. Chúng ta cần có một function được gọi là `main`, function này xác định điều gì xảy ra khi chạy thực thi. Tất cả các crates được tạo ra thường là binary crates.

_Library crates_ không có `main` function, và chúng không được biên dịch để thực thi. Chúng định nghĩa các chức năng dự định để chia sẻ với nhiều projects. Ví dụ, crate `rand` chúng tôi sử dụng trong [Chapter 2](https://www.rustvn.com/vi-VN/rust-book-vn/ch02-00-guessing-game-tutorial.html#generating-a-random-number) cung cấp chức năng tạo các số ngẫu nhiên.
Nguồn:: [Packages và Crates - Ngôn ngữ lập trình Rust](https://www.rustvn.com/vi-VN/rust-book-vn/ch07-01-packages-and-crates.html)