---
share: true
created: 2023-10-24T18:26
updated: 2023-10-30T18:19
---
# Xem danh sách tất cả commit
```
git log --oneline
```
# Xem danh sách tất cả file trong commit mình chọn
```bash
git diff-tree --no-commit-id --name-only -r <commitHash>
```
# Đọc nội dung một file trong một commit cũ
```
git show <commitHash>:/path/to/file
```
Nếu muốn mở trong vim thì:
```
git show <commitHash>:/path/to/file | vim -
```
Nhược điểm của việc này là vì vim đọc trực tiếp từ stdin, nên không biết định dạng file là gì để mà tô màu. Có thể sửa việc này bằng:
```
git show <commitHash>:/path/to/file | vim -c 'set filetype=python' -
```

[[Vấn đề hay gặp khi dùng Git]]
