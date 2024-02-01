---
share: true
created: 2023-10-30T14:29
updated: 2024-02-01T21:39
---
Lý do:: [[Việc đọc vật thể trong JS dễ dàng hơn so với Python vì Python từ đầu đã được thiết kế để cố gắng đảm bảo tính đóng gói, còn JS thì không]]

Trong REPL của JS (console), chỉ cần gọi vật thể ra là được. Ở Python thì không như vậy. [[Trong REPL, gọi trực tiếp vật thể ra thì kết quả là __repr__(). Nếu dùng print thì kết quả là __str__()]]

|                | JS                                        | Python                    |
| -------------- | ----------------------------------------- | ------------------------- |
| Đọc thuộc tính | `object.attribute`, `object['attribute']` | `object.get('attribute')` |

