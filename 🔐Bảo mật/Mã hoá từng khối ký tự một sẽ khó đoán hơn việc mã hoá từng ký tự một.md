---
share: true
created: 2023-10-30T14:29
updated: 2025-01-01T12:14
---
Các hệ mã khối, giống như tên gọi, thực hiện tính toán trên từng khối bit có kích thước cố định, thông thường là 64 hoặc 128 bit. Vì vậy khi đầu vào bản rõ có độ dài không là bội số của khối, ta cần phải thực hiện thao tác đệm (padding) sao cho số bit của đầu vào phải là bội số của khối.

Các hệ mã khối nổi tiếng đó là [DES](https://en.wikipedia.org/wiki/Data_Encryption_Standard) có kích thước khối là 64 (tức là mỗi lần mã hóa một khối bản rõ 64 bits và cho ra khối bản mã 64 bít) và kích thước khóa là 56 bits; [AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) có kích thước khối là 128 bit, và kích thước khóa là 128, 192 hoặc 256bit.

Thông thường block cipher chậm hơn so với stream cipher, nhưng làm việc tốt với những khối dữ liệu đã biết trước kích thước, ví dụ mã hóa file, mã hóa tin nhắn trên các giao thức như là HTTP ...
Nguồn:: [Giới Thiệu Về Các Hệ Mã Hóa](https://viblo.asia/p/gioi-thieu-ve-cac-he-ma-hoa-OEqGj6rNG9bL)

[[Cách máy tính hiểu ký tự khác với cách con người hiểu ký tự. Tốt nhất là nên dùng điểm mã khi nói về ký tự máy tính]]