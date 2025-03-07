---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
## Lịch sử
| Lệnh                        | Cách dùng                          |
| --------------------------- | ---------------------------------- |
| Cuộn lên, cuộn xuống        | <kbd>Alt+↑</kbd>, <kbd>Alt+↓</kbd> |
| Xem lịch sử các lệnh        | `get-history` hoặc `h`             |
| Tìm một lệnh mình từng dùng | gõ lệnh đó rồi nhấn `F8`           |
Nguồn:: [about History - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_history?view=powershell-7.3)

[[PowerShell là một ngôn ngữ shell]]
    [The Complete Guide to PowerShell Punctuation - Simple Talk](https://www.red-gate.com/simple-talk/sysadmin/powershell/the-complete-guide-to-powershell-punctuation/)
## Tạo nhiều folder
```PowerShell
$list=(ls -name -directory).substring(1)
foreach ($i in $list) {
	$index=$i.substring(0,1)
	cd "2$i" 
	new-item "2$index`1 Thành quả cần có" -type directory;
	new-item "2$index`2 Sự kiện" -type directory;
	new-item "2$index`3 Tài liệu" -type directory;
	Cd ..
}
```
## Tạo array
```PowerShell
$list|ForEach-Object {"`"$_`"," } |clip
```
## Đổi tên hàng loạt
```PowerShell
Get-ChildItem *.md, *.json -recurse | Where-Object {$_.name -cmatch '^2[A-Z]'}  | Rename-Item -newname { $_.name -replace '^2(.*)', '4$1'} -whatif 
```
- `-cmatch`: match có case sensitive

## Tìm và thay chuỗi hàng loạt
[[VS Code nhiều khi không tìm hết file được do tên quá dài]]
```PowerShell
Get-ChildItem *.md, *.json -recurse | ForEach-Object { (Get-Content $_).Replace('Kết quả cần có::','Thành quả cần có::') | Set-Content $_ } 
```

## Thêm nội dung vào hàng loạt tập tin
```PowerShell
Get-ChildItem .gitignore -recurse | ForEach-Object { 
    Add-Content $_ .obsidian/plugins/obsidian-mkdocs-publisher/logs.txt
}
```
## Xoá tất cả desktop.ini 
```PowerShell
Get-ChildItem -Force -Recurse -File -Filter "desktop.ini" | Remove-Item -force
```
## Tắt giới hạn số ký tự tối đa cho đường dẫn
```PowerShell
New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" -Name "LongPathsEnabled" -Value 1 -PropertyType DWORD -Force
```
[Maximum Path Length Limitation - Win32 apps | Microsoft Learn](https://learn.microsoft.com/en-us/windows/win32/fileio/maximum-file-path-limitation?tabs=powershell#enable-long-paths-in-windows-10-version-1607-and-later)

## Thêm [[Biến môi trường giúp ta điền những giá trị lặp đi lặp lại nhanh hơn|biến môi trường]] 
```PowerShell
[System.Environment]::SetEnvironmentVariable('ResourceGroup','AZ_Resource_Group', 'User')
$env:PATH += ";SomeRandomPath"
```
```PowerShell
[Environment]::SetEnvironmentVariable("Path",    [Environment]::GetEnvironmentVariable("Path", [EnvironmentVariableTarget]::Machine) + ";C:\bin", [EnvironmentVariableTarget]::Machine)
```
## sfd
```PowerShell
$sourcePath = “F:\New folder”  
$destinationPath = “E:\New folder”  
$files = Get-ChildItem -Path $sourcePath -Recurse -Filter “*.*”  
foreach($file in $files){  
	$sourcePathFile = $file.FullName  
	$destinationPathFile = $file.FullName.Replace($sourcePath, $destinationPath)  
	$exists = Test-Path $destinationPathFile  
	if(!$exists){  
	$dir = Split-Path -parent $destinationPathFile  
	if (!(Test-Path($dir))) { New-Item -ItemType directory -Path $dir }  
	Copy-Item -Path $sourcePathFile -Destination $destinationPathFile -Recurse -Force  
	}  
	else{  
		$isFile = Test-Path -Path $destinationPathFile -PathType Leaf  
	if(!$isFile){  
		Copy-Item -Path $sourcePathFile -Destination $destinationPathFile -Recurse -Force  
	}  
	}  
}
```
