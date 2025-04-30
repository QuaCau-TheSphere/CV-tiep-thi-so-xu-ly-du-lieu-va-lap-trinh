---
share: true
created: 2023-10-24T18:26
updated: 2025-04-22T14:21
---
| Phương thức mã hoá | Số đơn vị mã (code unit) cần để biểu diễn một ký tự bất kỳ | Số byte cần cho một đơn vị mã |
| ------------------ | ---------------------------------------------------------- | ----------------------------- |
| UTF-8              | 1-4                                                        | 1                             |
| UTF-16             | 1-2                                                        | 2                             |
| UTF-32             | 1                                                          | 3                             |

Nguồn:: [Tìm hiểu Unicode](https://viblo.asia/p/tim-hieu-unicode-PwRkgVOXeEd)
Ví dụ, chữ `à` có 2 điểm mã:
- `U+0061` cho chữ `a`
- `U+0300` cho dấu huyền

Có thể kiểm tra điều này bằng lệnh 
```
"à".length //kết quả là 2 😲
```
Tuy nhiên, `à` cũng có thể có 1 điểm mã là `U+00E0`.
[[UTF là cách thức để chuyển đổi từ điểm mã sang hệ nhị phân]]. [[Mỗi điểm mã được biểu diễn dưới dạng U+XXYYYY]]

```js
const message = "Một thông điệp";
const encoder = new TextEncoder();
const encoded = encoder.encode(message);
console.log(encoded)
// Uint8Array(20) [
//   77, 225, 187, 153, 116,  32,
//  116, 104, 195, 180, 110, 103,
//   32, 196, 145, 105, 225, 187,
//  135, 112
// ]

const decoder = new TextDecoder(); 
const u8arr = new Uint8Array(encoded);
const decoded = decoder.decode(u8arr)
console.log(decoded);
// Một thông điệp
```

Đây cũng là lý do mà [[JSON không cho phép để dư dấu phẩy, không có comment, thuộc tính phải được đóng trong ngoặc kép|JSON bắt phải đóng ngoặc kép tất cả các thuộc tính]], để khỏi phải quan tâm xem "ký tự" là gì.