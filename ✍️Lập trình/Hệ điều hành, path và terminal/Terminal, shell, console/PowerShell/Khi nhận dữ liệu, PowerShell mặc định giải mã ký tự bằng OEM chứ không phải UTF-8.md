---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
[[UTF là cách thức để chuyển đổi từ điểm mã sang hệ nhị phân]]
when it comes to capturing the output in a variable or redirecting it, PowerShell decodes the output into .NET strings (first), using the character encoding stored in `[Console]::OutputEncoding`. Therefore, you may have to (temporarily) set it to the encoding used by the external program. E.g., for programs that output UTF-8, such as node: 
`[Console]::OutputEncoding = [System.Text.UTF8Encoding]::new()`

Nguồn:: [Character encoding problem when importing SQL with DBForge and PowerShell into MySQL - Stack Overflow](https://stackoverflow.com/a/78082903/3416774)
