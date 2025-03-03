---
share: true
created: 2023-10-30T14:29
updated: 2025-02-02T13:02
---
arg cung cấp currentEntities vì có thể nhập nhiều cái cùng lúc
Chính vì như vậy nên trong script mẫu mới phải dùng `for`:
```js
for (const entity of args.currentEntities) {
}
```
Nguồn:: 