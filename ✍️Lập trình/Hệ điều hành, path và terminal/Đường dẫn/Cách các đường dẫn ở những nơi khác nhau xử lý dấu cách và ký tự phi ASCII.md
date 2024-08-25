---
share: true
created: 2023-10-30T14:29
updated: 2024-08-25T20:38
alias:
  - markdown, URL, domain xử lý
---
|                             | Cho dùng dấu cách | Ký tự `%` | Các ký tự phi ASCII |
| --------------------------- | ----------------- | --------- | ------------------- |
| Markdown                    | ❌                |           | ✔                   |
| YAML                        | ❌                |           | ✔                   |
| URL                         | ✔                 | ❌        | ✔                   |
| Domain                      | ✔                 |           | ✔                   |
| Thuộc tính `src` trong HMTL | ✔                 |           | ✔                   |
| Query                       | ❌                |           | ✔                   |
| Windows path                | ✔                 | ✔         | ✔                   |
| Linux path                  | ✔                 |           | ✔                   |
| Mac path                    | ✔                 |           | ✔                   |
| Docker                      | ❌                |           | ❌                    |

Nên tránh dùng ký tự `%` trong tên tập tin, nhất là nếu sau này sẽ biến thành web. Vì dấu này chính là dấu để encode, nên không như những ký tự khác, khi decode sẽ gặp lỗi
[What is the difference between decodeURIComponent and decodeURI?](https://stackoverflow.com/q/747641/3416774)
[[Sự khác biệt giữa Windows và Android, Mac trong tên file]]

[[Các ký tự ASCII có 1 điểm mã]]