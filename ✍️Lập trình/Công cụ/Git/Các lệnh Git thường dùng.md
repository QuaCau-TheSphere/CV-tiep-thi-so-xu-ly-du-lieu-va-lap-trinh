---
share: true
created: 2023-05-26T14:51
updated: 2026-08-06T15:36
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

## Tìm commit sớm nhất chứa file
```PowerShell
git log --follow --diff-filter=A --find-renames=40% --pretty=reference -- "**Thông tin cho đại lý.md" 
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

## Cập nhật phiên bản action
```PowerShell
Get-ChildItem deploy.yml -recurse | ForEach-Object { (Get-Content $_).Replace('actions/checkout@v3','actions/checkout@v4').Replace('actions/configure-pages@v3','actions/configure-pages@v4').Replace('actions/upload-pages-artifact@v2','actions/upload-pages-artifact@v3').Replace('actions/deploy-pages@v1','actions/deploy-pages@v4') | Set-Content $_ }
```


git config --global core.quotePath false
git config --global core.longpaths true
git config --global core.autocrlf true
git config --global core.safecrlf false
//`autocrlf` is to control whether transform line endings when `add`/`checkout`, while `safecrlf` is to control whether warn users when doing such transformations.
git pull origin branchname --allow-unrelated-histories
git config --global alias.add-commit '!git add -A && git commit'
