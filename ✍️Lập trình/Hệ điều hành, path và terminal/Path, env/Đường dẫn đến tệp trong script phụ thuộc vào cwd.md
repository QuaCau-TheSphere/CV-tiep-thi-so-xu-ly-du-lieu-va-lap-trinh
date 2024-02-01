---
share: true
created: 2023-10-30T14:29
updated: 2024-01-12T14:57
---
# `Script.ts`
```ts
const nộiDungFile = await Deno.readTextFile('../file.txt')
console.log(nộiDungFile)
```

Vị trí ngoài folder (trong `.`) :
```
. 
├── file.txt 
└── folder/ 
	└── script.ts
```
Vị trí trong folder (trong `./folder`):
```
. 
└── folder/ 
	├── script.ts 
	└── file.txt
```
[[pwd là thư mục mà process sẽ chạy (process working directory). cwd là thư mục mà mình đang ở đó (current working directory)]]

| Vị trí của `file.txt` | Đường dẫn đến `file.txt` trong `script.ts` | PWD và lệnh chạy `script.ts` ở terminal     | Kết quả |
| --------------------- | ------------------------------------------ | ------------------------------------------- | ------- |
| `./folder`            | `./file.txt`                               | Ở `./folder` chạy `deno run -A ./script.ts` | ✔       |
| `.`                   | `../file.txt`                              | Ở `./folder` chạy `deno run -A ./script.ts` | ✔       |
| `.`                   | `./file.txt`                               | Ở `.` chạy `deno run -A ./folder/script.ts` | ✔       |
| `.`                   | `./file.txt`                               | Ở `./folder` chạy `deno run -A ./script.ts` | ❌      |
| `.`                   | `../file.txt`                              | Ở `.` chạy `deno run -A ./folder/script.ts` | ❌      |
| `./folder`            | `./file.txt`                               | Ở `.` chạy `deno run -A ./folder/script.ts` | ❌      |
| `./folder`            | `../file.txt`                              | Ở `./folder` chạy `deno run -A ./script.ts` | ❌      |
| `./folder`            | `../file.txt`                              | Ở `.` chạy `deno run -A ./folder/script.ts` | ❌      |
|                       |                                            |                                             |         |

Chính vì như vậy, nên [[Dùng absolute path cho lành]]