---
share: true
created: 2023-08-25T14:20
updated: 2023-10-10T16:31
---
## B1: Thiết lập ban đầu
1. Mở VS Code lên
2. Bấm vào nút ![Extensions view trong VS Code](https://code.visualstudio.com/assets/docs/editor/extension-marketplace/extensions-view-icon.png) ở thanh bên trái và kiếm `Deno extension`. Bấm cài đặt
3. Bấm <kbd>Ctrl + Shift + P</kbd> và chọn *Deno: Initialize Workspace Configuration*
4. Đảm bảo rằng file `launch.json` trong thư mục `.vscode` có dạng như sau:

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "request": "launch",
            "name": "Launch Program",
            "type": "node",
            "program": "${workspaceFolder}/test/main.debug.js",
            "cwd": "${workspaceFolder}",
            "runtimeExecutable": "XXXXX",
            "runtimeArgs": [
                "run",
                "--unstable",
                "--inspect-wait",
                "--allow-all",
            ],
            "attachSimplePort": 9229
        }
    ]
}
```
Trong đó XXXXX là đường dẫn đến tập tin `deno.exe`. Có thể kiếm bằng cách bật CMD lên và nhập `where deno`

