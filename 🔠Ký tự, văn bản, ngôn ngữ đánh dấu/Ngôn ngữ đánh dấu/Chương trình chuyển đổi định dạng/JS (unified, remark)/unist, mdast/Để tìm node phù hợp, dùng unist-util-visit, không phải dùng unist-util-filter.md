---
share: true
created: 2023-10-30T14:29
updated: 2026-08-06T15:36
---
Lý do:: Lúc mới tạo unist thì JS chưa có `Array.filter`, nên từ đó được dùng cho `unist-util-filter` mà không sợ gây nhầm lẫn.

[`unist-util-select`](https://github.com/syntax-tree/unist-util-select) để tìm node từ gốc, chứ không cần tìm những vị trí tương đối từ một node bất kỳ

Nguồn:: [Why can unist-util-filter filter only with inequality but not equality? · syntax-tree · Discussion #133 · GitHub](https://github.com/orgs/syntax-tree/discussions/133#discussioncomment-10477455)
