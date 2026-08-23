---
share: true
created: 2023-10-24T18:26
updated: 2026-08-23T12:54
---
Biến môi trường tiếng Anh là *environmental variable*. Viết tắt là `env`.
![What are Environment Variables, and how do I use them? (get,set) - YouTube](https://youtu.be/ADh_OFBfdEE?si=U30Tg6HS8hvzgCcv)

[[Biến môi trường người dùng (user env) được ưu tiên hơn biến môi trường hệ thống (system env). Nhưng với biến PATH thì ngược lại]]

Dùng lệnh này để liệt kê tất cả các env trong [[PowerShell là một ngôn ngữ shell|PowerShell]]:
```PowerShell
get-childitem env:
```
