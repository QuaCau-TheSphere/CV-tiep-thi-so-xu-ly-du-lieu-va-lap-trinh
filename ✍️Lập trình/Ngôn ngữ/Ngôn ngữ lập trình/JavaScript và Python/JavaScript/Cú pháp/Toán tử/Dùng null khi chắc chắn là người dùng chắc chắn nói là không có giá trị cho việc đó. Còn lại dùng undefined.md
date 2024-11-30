---
share: true
created: 2023-10-30T14:29
updated: 2024-11-22T16:26
---
Dùng undefined khi:
- Phiếu thông tin không có trường đó 
- Phiếu thông tin có trường đó nhưng nó không ghi gì

Dùng null khi:
- Regex không tìm ra kết quả
- 

Nguồn:: [[Tự ngẫm nghĩ, trải nghiệm]]
[[Dùng null khi chắc chắn là người dùng chắc chắn nói là không có giá trị cho việc đó. Còn lại dùng undefined]]
[[Dùng nullish coalescing operator thay cho toán tử OR khi 0, '', NaN cần được trả về true chứ không phải false|nullish coalescing operator]]