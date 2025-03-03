---
share: true
created: 2023-10-24T18:26
updated: 2025-03-03T18:48
---
PowerShell

## Cho phép PowerShell chạy script 
```PowerShell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

"C:\Program Files\PowerShell\7\pwsh.exe" D:\Dropbox\Config\Startup.ps1

## Đảm bảo script được chạy với quyền quản trị
```PowerShell
param([switch]$Elevated)
function Test-Admin {
    $currentUser = New-Object Security.Principal.WindowsPrincipal $([Security.Principal.WindowsIdentity]::GetCurrent())
    $currentUser.IsInRole([Security.Principal.WindowsBuiltinRole]::Administrator)

}

if ((Test-Admin) -eq $false)  {
    if ($elevated) {
        # tried to elevate, did not work, aborting
    } else {
        Start-Process powershell.exe -Verb RunAs -ArgumentList ('-noprofile -noexit -file "{0}" -elevated' -f ($myinvocation.MyCommand.Definition))

    }
    exit
}
## Running with full privileges
```

## Run
`control userpasswords2`

## Tắt Defender
- Search for `gpedit.msc` and click the top result to open the Local Group Policy Editor.
- Browse the following path:  
    Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus

## Sửa lỗi boot
```
bootsect/nt60 sys
bootrec /fixmbr
bootrec /fixboot
```

![How To Fix Bootrec /fixboot Access is Denied During Fix Boot Configuration (2 Fixes )](https://www.youtube.com/watch?reload=9&v=lRCyb7FzWFY)

```PowerShell
ECHO Y | REG ADD "HKLM\Software\Microsoft\Windows\CurrentVersion\AppHost" /v EnableWebContentEvaluation /t REG_DWORD /d 0
ECHO Y | REG ADD "HKCU\Software\Classes\Local Settings\Software\Microsoft\Windows\CurrentVersion\AppContainer\ Storage\microsoft.microsoftedge_8wekyb3d8bbwe\MicrosoftEdge\PhishingFilter" /v EnabledV9 /t REG_DWORD /d 0

winget install -e --id Mozilla.Firefox.DeveloperEdition

winget install notepad++ 
winget install -e --id RobertFFrasca.PDFKeeper
winget install -e --id SumatraPDF.SumatraPDF
winget install -e --id GNU.Emacs
winget install -e --id Neovim.Neovim
winget install -e --id pit-ray.win-vind
winget install -e --id Obsidian.Obsidian

winget install -e --id Zoom.Zoom
winget install -e --id Discord.Discord.Development
winget install -e --id Kotatogram.Kotatogram
winget install -e --id VNGCorp.Zalo

winget install -e --id AutoHotkey.AutoHotkey
winget install Microsoft.WindowsTerminal 
winget install -e --id Microsoft.PowerShell.Preview
winget install -e --id VSCodium.VSCodium
winget install -e --id GitHub.cli
winget install -e --id Git.Git
winget install -e --id JesseDuffield.lazygit
winget install -e --id DenoLand.Deno
winget install -e --id OpenJS.NodeJS
winget install -e --id GoLang.Go.1.18
winget install -e --id Hugo.Hugo.Extended
winget install -e --id Docker.DockerDesktop
winget install -e --id Anaconda.Miniconda3

winget install -e --id M2Team.NanaZip
winget install -e --id SoftDeluxe.FreeDownloadManager
winget install -e --id WinDirStat.WinDirStat
winget install -e --id Audacity.Audacity
winget install -e --id Wondershare.InClowdz
winget install -e --id ManicTime.ManicTime
winget install -e --id Sandboxie.Classic
winget install sharex.sharex --accept-source-agreements --accept-package-agreements 
winget install VideoLAN.VLC
winget install copyq
winget install -e --id GNU.MidnightCommander
winget install -e --id TheDocumentFoundation.LibreOffice

winget install -e --id Nextcloud.NextcloudDesktop
winget install -e --id liberodark.ODrive

deno install --allow-run --allow-env --allow-read --name lume --force --reload --global https://deno.land/x/lume_cli/mod.ts
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned

```