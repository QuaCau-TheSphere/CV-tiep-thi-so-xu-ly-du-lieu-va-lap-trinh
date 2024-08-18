---
share: true
created: 2024-01-05T14:38
updated: 2024-08-14T21:31
---
Lý do:: [[Đường dẫn đến tệp ngoài trong một script phụ thuộc vào cwd, không phải đường dẫn tới script mình đang viết]]
```ts
import * as path from "$std/path/mod.ts";
const thưMụcHiệnTại = path.dirname(path.fromFileUrl(import.meta.url))
const danhSáchNơiĐăng = Deno.readTextFileSync(thưMụcHiệnTại+'/Nơi đăng.yaml')
```