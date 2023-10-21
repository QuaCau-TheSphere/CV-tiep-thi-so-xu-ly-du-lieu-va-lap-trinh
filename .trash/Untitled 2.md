---
share: true
created: 2023-10-20T15:19
updated: 2023-10-20T16:27
---
```
[Hướng dẫn sử dụng Trấn Kỳ](./H%C6%B0%E1%BB%9Bng%20d%E1%BA%ABn%20s%E1%BB%AD%20d%E1%BB%A5ng%20Tr%E1%BA%A5n%20K%E1%BB%B3/index.md#)
```

#  Xoá hiểu biết sâu
| mkdocs.yml      | Kết quả           |
| --------------- | ----------------- |
| Để toàn bộ      | web/quản trị mạng |
| Chỉ còn ezlinks + đổi tên trấn kỳ thành a + đổi tên lập trình thành b | web/quản trị mạng |

## Xoá site/index.md

| Case                         | href output      |
| ---------------------------- | ---------------- |
| Nothing is removed           | `../b/`          |
| `docs/b/index.md` is removed | `../a1/index.md` |
| `docs/index.md` is removed   | `../a1/index.md` |

I expect whatever the case is, the href output should always be `./a1/index.html`