---
share: true
created: 2023-10-24T18:26
updated: 2025-03-03T18:48
---
Biến môi trường tiếng Anh là *environmental variable*. Viết tắt là `env`.
![What are Environment Variables, and how do I use them? (get,set) - YouTube](https://youtu.be/ADh_OFBfdEE?si=U30Tg6HS8hvzgCcv)

[[env của người dùng được ưu tiên hơn env của hệ thống. Nhưng với biến path thì ngược lại]]

Dùng lệnh này để liệt kê tất cả các env trong [[PowerShell là một ngôn ngữ shell|PowerShell]]:
```PowerShell
get-childitem env:
```