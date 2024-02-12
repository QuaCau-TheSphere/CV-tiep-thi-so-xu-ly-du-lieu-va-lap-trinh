---
share: true
created: 2024-01-14T15:32
updated: 2024-02-04T16:11
---

| Tối ưu cho... →<br>Ngôn ngữ đánh dấu ↓ | ...cho con người đọc và viết | ...cho việc khai báo metadata | ...cho việc viết tập tin cấu hình | ...cho việc truyền dữ liệu |
| -------------------------------------- | ---------------------------- | ----------------------------- | --------------------------------- | -------------------------- |
| YAML                                   | ✔                            | ✔                             | ❌                                | ❌                         |
| XML                                    | ❌                           | ✔                             | ❌                                | ✔                          |
| TOML                                   | ✔                            | ❌                            | ✔                                 | ❌                         |
| JSON                                   | ❌                           | ❌                            | ❌                                | ✔                          |
| JSONC/JWCC                             | ❌                           | ❌                            | ✔                                 | ✔                          |

Những thứ mà không tối ưu cho con người đọc và viết thì nên để máy tự in ra. Chỉnh sửa trực tiếp dễ gây lỗi. Hoặc ít nhất là nên viết trong parser/validator để nó báo lỗi ngay cho mình.

[[Chữ ML trong HTML, XML, YAML, TOML là viết tắt của markup language]]
[The yaml document from hell](https://ruudvanasseldonk.com/2023/01/11/the-yaml-document-from-hell)

```dataview
LIST
FROM "✍️Lập trình/Ngôn ngữ/Ngôn ngữ đánh dấu" 
WHERE file.name!=this.file.name
```