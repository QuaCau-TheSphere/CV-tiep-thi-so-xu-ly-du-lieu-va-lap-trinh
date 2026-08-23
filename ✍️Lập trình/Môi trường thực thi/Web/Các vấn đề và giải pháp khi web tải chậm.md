---
share: true
updated: 2026-08-14T15:54
created: 2026-08-14T15:48
---
Khái niệm:: 

| Lý do chậm            | Giải pháp                            |
| --------------------- | ------------------------------------ |
| Mạng                  | Lazy loading, code spliting          |
| Rendering             | Pagination hoặc virtualization       |
| Tính lại thường xuyên | Memoization, có cấu trúc dữ liệu tốt |
| CPU-heavy JS          | Web worker                           |
[[Worker không nhất thiết làm work chạy nhanh hơn, mà chỉ làm UI responsive khi work đang chạy]]
Nguồn:: ![Frontend System Design Essentials: Data-Heavy Frontend Apps - YouTube](https://youtu.be/nw-7ry_hhio?si=F1Yh78YeuAsz3EH1&t=854)