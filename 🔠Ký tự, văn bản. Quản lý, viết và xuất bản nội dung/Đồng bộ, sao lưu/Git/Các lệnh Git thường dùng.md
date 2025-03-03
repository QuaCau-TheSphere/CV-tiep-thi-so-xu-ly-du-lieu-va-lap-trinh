---
share: true
created: 2023-05-26T14:51
updated: 2025-03-03T18:48
---
[GitHub - GitAlias/gitalias: Git alias commands for faster easier version control](https://github.com/GitAlias/gitalias)
[GitHub - initialcommit-com/git-sim: Visually simulate Git operations in your own repos with a single terminal command.](https://github.com/initialcommit-com/git-sim)
## Xem danh sách tất cả commit
```bash
git log --oneline
git log --oneline --graph
git log --pretty='%C(yellow)%h %C(cyan)%cd%C(auto)%d %Creset%s' --graph --date=relative --date-order
```
## Xem những thay đổi của một commit
```
git show --stat <commit>
git diff <commit>^!
```
## Xem danh sách tất cả file trong commit mình chọn
```bash
git ls-tree --name-only -r <commitHash>
git ls-tree --name-only 9dea936:"Tài nguyên hỗ trợ/Công việc thời vụ kiếm tiền nhanh"
```
- Bỏ `-r` để không recurse 
## Đọc nội dung một file trong một commit cũ
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

## Khởi tạo repo mới và đẩy lên GitHub
```PowerShell
$repo = 'QuaCau-TheSphere/CA-Bao-hiem'
git init
git add -A
git commit -m "init"

gh repo create --public $repo
$url = gh repo view $repo --json url --jq '.url'
git remote add origin $url 
git push -u origin main
```
[[Mẹo dùng Git với Obsidian]]
Xem thêm:: [[Các lỗi Git thường gặp]], [[Git tag]]
Xem thêm:: [GitHub - git-tips/tips: Most commonly used git tips and tricks.](https://github.com/git-tips/tips?tab=readme-ov-file#readme)