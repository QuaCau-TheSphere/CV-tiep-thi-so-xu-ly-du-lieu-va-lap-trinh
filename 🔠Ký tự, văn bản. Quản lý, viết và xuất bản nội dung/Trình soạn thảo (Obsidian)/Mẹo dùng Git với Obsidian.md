---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
## Thêm nội dung vào hàng loạt tập tin
```PowerShell
Get-ChildItem .gitignore -recurse | ForEach-Object { 
    Add-Content $_ .obsidian/plugins/obsidian-mkdocs-publisher/logs.txt
}
```

[[Các lệnh Git thường dùng]]
Nguồn:: 