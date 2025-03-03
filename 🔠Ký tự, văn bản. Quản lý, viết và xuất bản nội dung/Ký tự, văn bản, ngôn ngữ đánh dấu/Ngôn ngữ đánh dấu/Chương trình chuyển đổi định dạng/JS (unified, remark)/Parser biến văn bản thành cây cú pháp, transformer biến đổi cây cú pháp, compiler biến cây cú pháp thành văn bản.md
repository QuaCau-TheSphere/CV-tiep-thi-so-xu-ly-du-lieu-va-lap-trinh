---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
```
| ........................ process ........................... |
| .......... parse ... | ... run ... | ... stringify ..........|

          +--------+                     +----------+
Input ->- | Parser | ->- Syntax Tree ->- | Compiler | ->- Output
          +--------+          |          +----------+
                              X
                              |
                       +--------------+
                       | Transformers |
                       +--------------+
```
Nguồn:: 
Trong pandoc thì parser, transformer với compiler lần lượt được gọi là [[Reader biến văn bản thành cây cú pháp, filter biến đổi cây cú pháp, writer biến cây cú pháp thành văn bản|reader, filter, writer]]

Chữ "compile" ở đây không quá chính xác, vì [[Compile time là lúc chuyển từ ngôn ngữ lập trình mà người hiểu sang ngôn ngữ máy chỉ có máy mới hiểu. Runtime là lúc máy chạy mã máy|Compile thực sự là việc chuyển từ ngôn ngữ lập trình mà người hiểu sang ngôn ngữ máy chỉ có máy mới hiểu]]. Nó nên hiểu là "converter" thì đúng hơn.