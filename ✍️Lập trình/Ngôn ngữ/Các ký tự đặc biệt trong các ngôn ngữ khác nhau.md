---
share: true
created: 2023-10-26T14:59
updated: 2024-08-18T15:05
alias: Các ký hiệu đặc biệt trong các ngôn ngữ khác nhau
cssClass: wide-table
---
| Ký tự               | JavaScript        | Python          | Git                               | PowerShell                                                | AutoHotKey   | CSS                           | CMD     | SQL | Bash | LaTeX |
| ------------------- | ----------------- | --------------- | --------------------------------- | --------------------------------------------------------- | ------------ | ----------------------------- | ------- | --- | ---- | ----- |
| Dấu nháy kép `"`    | Verbatim string   | Verbatim string |                                   | Chuỗi có thể chèn chuỗi khác vào được (expandable string) |              |                               |         |     |      |       |
| Dấu nháy đơn `'`    | Verbatim string   | Verbatim string |                                   | Chuỗi có sao ghi vậy (verbatim string)                    |              |                               |         |     |      |       |
| Dấu backtick ` `` ` | Expandable string |                 |                                   | Thoát khỏi ký tự đặc biệt, ngắt dòng                      |              |                               |         |     |      |       |
| Dấu đô la `$`       |                   |                 |                                   | `$biến`, `$env:path`                                      |              |                               |         |     |      |       |
| Dấu phần trăm `%`   |                   |                 |                                   | `ForEach-Object`                                          | `%biến%`     |                               | `%biến` |     |      |       |
| Dấu chéo `\`        |                   |                 |                                   |                                                           |              |                               |         |     |      |       |
| Dấu chéo ngược `/`  |                   |                 |                                   |                                                           |              |                               |         |     |      |       |
| Dấu sao `*`         |                   |                 |                                   |                                                           |              |                               |         |     |      |       |
| Dấu a còng `@`      |                   |                 | [[HEAD là commit hiện tại\|HEAD]] | Chèn nhiều tham số vào cùng lúc (splatting)               |              | Scope                         |         |     |      |       |
| Dấu thăng `#`       |                   |                 |                                   | `# comment`. Mẹo: dùng `##` ở trên function               | `#directive` |                               |         |     |      |       |
| Dấu chấm phẩy `;`   |                   |                 |                                   |                                                           | `; comment`  |                               |         |     |      |       |
| Dấu gạch đứng `\|`  |                   |                 |                                   | Pipe                                                      |              |                               |         |     |      |       |
| Dấu chấm hỏi `?`    |                   |                 |                                   | `Where-Object`                                            |              |                               |         |     |      |       |
| Dấu lớn hơn `>`     |                   |                 |                                   |                                                           |              | Child combinator              |         |     |      |       |
| Dấu cộng `+`        |                   |                 |                                   |                                                           |              | Next-sibling combinator       |         |     |      |       |
| Dấu ngã `~`         |                   |                 |                                   |                                                           |              | Subsequent-sibling combinator |         |     |      |       |
| Ký tự               | JavaScript        | Python          |                                   | PowerShell                                                | AutoHotKey   | CSS                           | CMD     | SQL | Bash | LaTeX |



Ưu tiên dấu nháy đơn `'` hơn là nháy kép `"`. Tuy nhiên nhớ rằng [[JSON không cho phép để dư dấu phẩy, không có comment, bắt buộc phải dùng ngoặc kép, key phải được đóng trong ngoặc kép|trong JSON thì chỉ có thể dùng nháy kép chứ không được dùng nháy đơn]].

[The Complete Guide to PowerShell Punctuation - Simple Talk](https://www.red-gate.com/simple-talk/sysadmin/powershell/the-complete-guide-to-powershell-punctuation/)

