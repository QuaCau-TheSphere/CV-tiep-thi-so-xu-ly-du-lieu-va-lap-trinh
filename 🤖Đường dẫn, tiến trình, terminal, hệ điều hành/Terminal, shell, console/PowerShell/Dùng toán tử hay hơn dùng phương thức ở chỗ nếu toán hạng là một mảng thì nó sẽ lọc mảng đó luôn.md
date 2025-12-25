---
share: true
created: 2023-10-30T14:29
updated: 2025-11-11T11:56
---
Nếu dùng phương thức thì phải lọc:
```PowerShell
$env:path.split(";") | Where-Object {$_.contains("bin") }
```
Nếu dùng toán tử thì không cần:
```PowerShell
$env:path.split(";") -match "bin"
```
Nguồn:: [powershell - How to filter elements from an array made by spliting a string? - Stack Overflow](https://stackoverflow.com/q/79482745/3416774)