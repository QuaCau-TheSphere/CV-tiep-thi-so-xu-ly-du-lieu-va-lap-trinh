---
share: true
created: 2024-09-19T17:01
updated: 2025-03-03T18:48
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
### B1. Xác định commit sớm nhất chứa secret
git 
Nếu là blob thì dùng 
```
git log --all --find-object=<BLOB-ID>
```

([[Có thể hiểu blob là hash của một file, tree là hash của một folder, còn commit thực ra chỉ là hash của cả folder tổng|Blob có thể hiểu là hash của một file, còn commit là hash của cả folder tổng]])
### B2. `git rebase -i <COMMIT-ID>~1`
[[~ và dấu mũ là để chỉ các commit trước đó|~ và ^ là để chỉ các commit trước đó]]
### B3. đổi pick sang edit ở commit sớm nhất
Sau khi lưu lại, nếu nó xuất hiện dòng:
```
You can amend the commit now, with

  git commit --amend

Once you are satisfied with your changes, run

  git rebase --continue
```
Thì là thành công
### B3. Xoá file chứa secret
### `git commit --amend`
###  `git rebase --continue`

Xem thêm:: [[Các lệnh Git thường dùng]]