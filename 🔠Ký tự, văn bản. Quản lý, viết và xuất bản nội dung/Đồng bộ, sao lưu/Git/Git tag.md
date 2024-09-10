---
share: true
created: 2023-10-30T14:29
updated: 2024-09-09T14:07
---
## Liệt kê tất cả các tag
```PowerShell
# Liệt kê tất cả các tag, xếp theo bảng chữ cái
git tag -l

# Liệt kê tất cả các tag và commit nó gắn vào, xếp theo bảng chữ cái và thời gian
git tag -n 

# Lấy tag mới nhất và commit của nó
git tag -n --sort=-creatordate | select -first 1
```
## Xoá tag
```PowerShell
# delete local tag '12345'
git tag -d 12345

# delete remote tag '12345' (eg, GitHub version too)
git push origin :refs/tags/12345

# alternative approach
git push --delete origin tagName
git tag -d tagName
```
Nguồn::
