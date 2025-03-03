---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
description: Viết 2020-12-09T16:09:53+00:00 đáp ứng cả ISO 8601 và RFC 3339
---
Viết `2020-12-09T16:09:53+00:00` đáp ứng cả ISO 8601 và RFC 3339

| Mô tả                             | Ví dụ                       | ISO 8601 | RFC 3339 |
| --------------------------------- | --------------------------- | -------- | ------- |
| Chuẩn                             | `2020-12-09T16:09:53+00:00` | ✔        | ✔       |
| Dùng khoảng cách giữa ngày và giờ | `2020-12-09 16:09:53+00:00` | ❌       | ✔       |
| Dấu âm trong time offset          | `2020-12-09T16:09:53-00:00` | ❌       | ✔       |
| Bỏ dấu ngang và hai chấm          | `20201209T160953Z`          | ✔        | ❌      |

Nguồn:: [[Stack Overflow]], [datetime - What's the difference between ISO 8601 and RFC 3339 Date Formats? - Stack Overflow](https://stackoverflow.com/a/65221179/3416774)

[[Giờ UTC là giờ luôn giống nhau ở bất cứ nơi đâu. Nó là phiên bản sau của giờ GMT]]
[RFC 9557](https://datatracker.ietf.org/doc/html/rfc9557) là cái mới nhất. [Cả ISO 8601 và RFC 3339 đều là tập con của nó](https://tc39.es/proposal-temporal/docs/plaindate.html#static-methods).