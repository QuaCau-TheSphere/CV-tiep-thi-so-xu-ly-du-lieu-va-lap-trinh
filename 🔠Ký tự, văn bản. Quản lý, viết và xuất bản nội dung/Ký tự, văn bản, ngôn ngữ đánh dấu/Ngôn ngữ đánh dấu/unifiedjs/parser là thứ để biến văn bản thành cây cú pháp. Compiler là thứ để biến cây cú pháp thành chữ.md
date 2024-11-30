---
share: true
created: 2023-10-30T14:29
updated: 2024-11-30T13:54
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
[[Compile time là lúc chuyển từ ngôn ngữ lập trình mà người hiểu sang ngôn ngữ máy chỉ có máy mới hiểu. Runtime là lúc máy chạy mã máy]]