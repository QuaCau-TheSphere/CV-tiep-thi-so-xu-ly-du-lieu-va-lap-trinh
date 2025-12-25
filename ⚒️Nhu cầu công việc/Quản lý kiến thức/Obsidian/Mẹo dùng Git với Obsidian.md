---
share: true
created: 2023-10-30T14:29
updated: 2025-10-12T13:17
---
## Thêm nội dung vào hàng loạt tập tin
```PowerShell
Get-ChildItem .gitignore -recurse | ForEach-Object { 
    Add-Content $_ .obsidian/plugins/obsidian-mkdocs-publisher/logs.txt
}
```

[[Các lệnh Git thường dùng]]
Nguồn:: 