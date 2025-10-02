---
share: true
created: 2024-09-19T17:01
updated: 2025-09-27T16:19
---
[[git reflog là phao cứu sinh cho những lỗi lầm khi dùng Git]]
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
Nếu biết secret đó là gì thì dùng git blame luôn. Nếu không biết thì xem trong lỗi để biết nó là commit nào. Nếu nó ghi nhiều commit thì dùng git log để xem cái nào là commit sớm nhất. Nếu nó không ghi commit mà ghi blob thì dùng 
```
git log --all --find-object=<BLOB-ID>
```

([[Có thể hiểu blob là hash của một tệp, tree là hash của một thư mục, còn commit thực ra chỉ là hash của cả thư mục tổng|Blob có thể hiểu là hash của một file, còn commit là hash của cả folder tổng]])

### B2. `git rebase -i <COMMIT-ID>~1`
[[Dấu ngã và dấu mũ là để chỉ các commit trước đó|~ và ^ là để chỉ các commit trước đó]]

### B3. đổi pick sang edit ở commit sớm nhất
Sau khi lưu lại, nếu nó xuất hiện dòng:
```
You can amend the commit now, with

  git commit --amend

Once you are satisfied with your changes, run

  git rebase --continue
```
Thì là bước này thành công.

### B4. Xoá file chứa secret
Nếu là file tự tạo ra thì cần thêm vào .gitignore  
```
add-Content .\.gitignore .obsidian/plugins/obsidian-mkdocs-publisher/logs.txt && git rm --cache -r . && git add -A && git commit --amend --no-edit && git rebase --continue && git add -A && git rebase --continue
```
### `git commit --amend`
###  `git rebase --continue`

Xem thêm:: [[Các lệnh Git thường dùng]]