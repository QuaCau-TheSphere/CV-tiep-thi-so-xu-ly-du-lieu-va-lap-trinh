---
share: true
created: 2024-09-19T17:01
updated: 2024-09-20T13:55
---
## Quên add
## Không thấy folder mình tạo được add
Lý do:: [[Git không biết gì về folder]]
## Thêm file vào  .gitignore rồi mà vẫn không thấy file bị ignore
## Lỡ commit file nặng
```
git filter-branch --force --index-filter 'git rm -r --cached --ignore-unmatch bigfile.txt' --prune-empty --tag-name-filter cat -- --all
```
## Lỡ commit secret

Xem thêm:: [[Các lệnh Git thường dùng]]