---
share: true
created: 2023-10-24T18:26
updated: 2024-01-14T14:02
---
| Phương thức mã hoá | Số đơn vị mã (code unit) cần để biểu diễn một ký tự bất kỳ | Số byte cần cho một đơn vị mã |
| ------------------ | ---------------------------------------------------------- | ----------------------------- |
| UTF-8              | 1-4                                                        | 1                             |
| UTF-16             | 1-2                                                        | 2                             |
| UTF-32             | 1                                                          | 3                             |

Nguồn:: [Tìm hiểu Unicode](https://viblo.asia/p/tim-hieu-unicode-PwRkgVOXeEd)
Ví dụ, chữ `à` có 2 code point:
- `U+0061` cho chữ `a`
- `U+0300` cho dấu huyền

Có thể kiểm tra điều này bằng lệnh 
```
"à".length //kết quả là 2 😲
```
Tuy nhiên, `a` cũng có thể có 1 code point là `U+00E0`.
[[UTF là cách thức để chuyển đổi từ điểm mã sang hệ nhị phân]]

Đây cũng là lý do mà [[JSON không cho phép để dư dấu phẩy, không có comment, bắt buộc phải dùng ngoặc kép, key phải được đóng trong ngoặc kép|JSON bắt phải đóng ngoặc kép tất cả các key]]