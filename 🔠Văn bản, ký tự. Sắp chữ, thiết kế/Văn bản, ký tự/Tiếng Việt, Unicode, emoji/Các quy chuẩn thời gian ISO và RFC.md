---
share: true
created: 2023-10-30T14:29
updated: 2024-08-25T20:41
description: 2020-12-09T16:09:53+00:00 đáp ứng cả ISO và RFC
---
| Mô tả                             | Ví dụ                       | ISO 8601 | RFC3339 |
| --------------------------------- | --------------------------- | -------- | ------- |
| Chuẩn                             | `2020-12-09T16:09:53+00:00` | ✔        | ✔       |
| Dùng khoảng cách giữa ngày và giờ | `2020-12-09 16:09:53+00:00` | ❌       | ✔       |
| Dấu âm trong time offset          | `2020-12-09T16:09:53-00:00` | ❌       | ✔       |
| Bỏ dấu ngang và hai chấm          | `20201209T160953Z`          | ✔        | ❌      |

Nguồn:: [[✍️Lập trình/Ξ Nguồn và tài nguyên hỗ trợ/Ξ Nguồn/Stack Overflow]], [datetime - What's the difference between ISO 8601 and RFC 3339 Date Formats? - Stack Overflow](https://stackoverflow.com/a/65221179/3416774)