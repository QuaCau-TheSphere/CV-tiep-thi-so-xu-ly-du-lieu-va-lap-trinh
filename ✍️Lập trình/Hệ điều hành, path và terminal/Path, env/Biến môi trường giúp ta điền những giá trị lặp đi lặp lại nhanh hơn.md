---
share: true
created: 2023-10-24T18:26
updated: 2024-08-18T15:05
---
Biến môi trường tiếng Anh là *environmental variable*. Viết tắt là `env`
![What are Environment Variables, and how do I use them? (get,set) - YouTube](https://youtu.be/ADh_OFBfdEE?si=U30Tg6HS8hvzgCcv)
Trong [[PowerShell là một ngôn ngữ shell|PowerShell]] dùng lệnh này để liệt kê tất cả các env:
```PowerShell
get-childitem env:
```
[[env của người dùng được ưu tiên hơn env của hệ thống. Nhưng với biến path thì ngược lại]]