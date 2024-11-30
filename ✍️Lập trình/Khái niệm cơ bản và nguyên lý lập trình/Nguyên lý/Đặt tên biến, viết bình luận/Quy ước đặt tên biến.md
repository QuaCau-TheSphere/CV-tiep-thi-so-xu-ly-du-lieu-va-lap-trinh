---
share: true
created: 2023-10-24T18:26
updated: 2024-11-22T16:31
---
# Kiểu viết
| Kiểu viết  | Ý nghĩa                                       | Ví dụ                   |
| ---------- | --------------------------------------------- | ----------------------- |
| ALL_CAP    | Hằng                                          | `SỐ_PI`                    |
| snake_case | Tên file. Riêng với Python thì là cả tên biến | `tên_file.js`           |
| kebab-case | URL                                           | `https://đường-dẫn-url` |
| camelCase  | Biến, hàm, phương thức                        | `vậtThể`                |
| PascalCase | Lớp, kiểu, giao diện                          | `VậtThể`                |

# Tiền tố
| Tiền tố       | Ý nghĩa                    | Ví dụ              |
| ------------- | -------------------------- | ------------------ |
| động từ       | Hàm                        | `runFunction()`    |
| động từ to be | Biến boolean               | `isTrue`           |
| `_`           | Biến riêng (private/local) | `_privateMethod()` |
| `$`           | Dùng trong jQuery          | `$_`               |
| `I`           | Interface                  | `IString`          |
| `T`           | Type                       | `TData`            |

Trong trường hợp `I` và `T` thì chúng được gọi là ký hiệu Hungary (Hungarian notation). Ngày xưa thì nó hữu ích, nhưng với những IDE mới hơn thì nó không còn cần thiết nữa. Dù vậy vẫn nên biết để có thể đọc code của người khác. 

Tuy nhiên có hai loại ký hiệu Hungary. Loại ở trên gọi là Hungary hệ thống, là thứ không còn được khuyến khích. Còn với loại Hungary app thì vẫn hữu ích. Để phân biệt được chúng và hiểu được tại sao có thể xem bài [Making Wrong Code Look Wrong – Joel on Software](https://www.joelonsoftware.com/2005/05/11/making-wrong-code-look-wrong/)

[[freeCodeCamp]], [Snake Case VS Camel Case VS Pascal Case VS Kebab Case – What's the Difference Between Casings?](https://www.freecodecamp.org/news/snake-case-vs-camel-case-vs-pascal-case-vs-kebab-case-whats-the-difference/)
[[Viblo]], [Bàn về quy cách đặt tên (Naming Convention)](https://viblo.asia/p/ban-ve-quy-cach-dat-ten-naming-convention-3P0lPyem5ox)

[[Việc đặt tên không có tiền tố gì sẽ tiện khi nó thường được dùng thường xuyên ở những nơi khác, ở trong một danh sách, hoặc khi dùng để liệt kê các thuộc tính]]