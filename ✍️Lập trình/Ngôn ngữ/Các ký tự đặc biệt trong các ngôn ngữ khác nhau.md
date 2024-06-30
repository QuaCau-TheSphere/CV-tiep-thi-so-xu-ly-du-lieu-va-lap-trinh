---
created: 2023-10-24T18:26
updated: 2024-06-29T17:13
---
| Ngôn ngữ            | PowerShell                                  | CMD     | AutoHotKey   | JavaScript        | Python          | SQL | Bash | LaTeX |
| ------------------- | ------------------------------------------- | ------- | ------------ | ----------------- | --------------- | --- | ---- | ----- |
| Dấu nháy kép `"`    | Expandable string                           |         |              | Verbatim string   | Verbatim string |     |      |       |
| Dấu nháy đơn `'`    | Verbatim string                             |         |              | Verbatim string   | Verbatim string |     |      |       |
| Dấu backtick ` `` ` | thoát khỏi ký tự đặc biệt, ngắt dòng        |         |              | Expandable string |                 |     |      |       |
| Dấu đô la `$`       | `$biến`, `$env:path`                        |         |              |                   |                 |     |      |       |
| Dấu phần trăm `%`   | `ForEach-Object`                            | `%biến` | `%biến%`     |                   |                 |     |      |       |
| Dấu chéo `\`        |                                             |         |              |                   |                 |     |      |       |
| Dấu chéo ngược `/`  |                                             |         |              |                   |                 |     |      |       |
| Dấu sao `*`         |                                             |         |              |                   |                 |     |      |       |
| Dấu a còng `@`      |                                             |         |              |                   |                 |     |      |       |
| Dấu thăng `#`       | `# comment`. Mẹo: dùng `##` ở trên function |         | `#directive` |                   |                 |     |      |       |
| Dấu chấm phẩy `;`   |                                             |         | `; comment`  |                   |                 |     |      |       |
| Dấu gạch đứng `\|`  | Pipe                                        |         |              |                   |                 |     |      |       |
| Dấu chấm hỏi `?`    | `Where-Object`                              |         |              |                   |                 |     |      |       |
| Ngôn ngữ            | PowerShell                                  | CMD     | AutoHotKey   | JavaScript        | Python          | SQL | Bash | LaTeX |


Ưu tiên dấu nháy đơn `'` hơn là nháy kép `"`. Tuy nhiên nhớ rằng [[JSON không cho phép để dư dấu phẩy, không có comment, bắt buộc phải dùng ngoặc kép, key phải được đóng trong ngoặc kép|trong JSON thì chỉ có thể dùng nháy kép chứ không được dùng nháy đơn]].