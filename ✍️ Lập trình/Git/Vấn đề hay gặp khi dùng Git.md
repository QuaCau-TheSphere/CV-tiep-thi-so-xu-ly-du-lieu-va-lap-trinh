---
share: true
created: 2023-05-26T14:51
updated: 2023-10-30T18:19
---
# Quên add

# [[Git không biết gì về folder]]

# Thêm file vào  .gitignore rồi mà vẫn không thấy file bị ignore

# Lỡ commit file nặng
```
git filter-branch --force --index-filter 'git rm -r --cached --ignore-unmatch bigfile.txt' --prune-empty --tag-name-filter cat -- --all
```

[[Các lệnh git thường sử dụng]]
