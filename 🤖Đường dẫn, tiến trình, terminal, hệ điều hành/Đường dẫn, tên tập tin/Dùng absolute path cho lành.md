---
share: true
created: 2024-01-05T14:38
updated: 2025-03-03T18:48
---
Lý do:: [[Đường dẫn đến tệp ngoài trong một script phụ thuộc vào cwd, không phải đường dẫn tới script mình đang viết]]
```ts
import * as path from "$std/path/mod.ts";
const thưMụcHiệnTại = path.dirname(path.fromFileUrl(import.meta.url))
const danhSáchNơiĐăng = Deno.readTextFileSync(thưMụcHiệnTại+'/Nơi đăng.yaml')
```