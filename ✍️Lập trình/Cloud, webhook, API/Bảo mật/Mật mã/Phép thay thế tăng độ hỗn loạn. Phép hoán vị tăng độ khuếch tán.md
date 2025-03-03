---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
- Nếu quan hệ hàm số của bản mã với bản rõ là phi tuyến thì sẽ khó bị tấn công hơn. Việc tạo **hỗn loạn (confusion)** sẽ giúp giải quyết việc này. Nó được thực hiện bằng **phép thay thế (substitution)**.
- Trong ngôn ngữ hay có những từ lặp lại thường xuyên (VD: `the` trong tiếng Anh). Kẻ tấn công có thể thống kê những mẫu này để dò ra khoá. Việc **khuếch tán (diffusion)** sẽ giúp giải quyết việc này. Nó được thực hiện bằng **phép hoán vị (permutation)**.

Các loại mã dựa trên một chuỗi các phép thay thế và hoán vị này gọi là mạng SP ([Substitution–permutation network - Wikipedia](https://en.wikipedia.org/wiki/Substitution–permutation_network))
![[SubstitutionPermutationNetwork-en.svg 1.png]]

Trong khi confusion được thực hiện bằng phép thay thế (substitution) thì diffusion được tạo ra bằng các phép chuyển đổi chỗ (tranposition) hay hoán vị.

Tham khảo:: [users.soict.hust.edu.vn/vannk/AntoanThongtin/MatMaKhoi-KhoaDX.pdf](https://users.soict.hust.edu.vn/vannk/AntoanThongtin/MatMaKhoi-KhoaDX.pdf)
[[✍️Lập trình/Cloud, webhook, API/Bảo mật/Mật mã/Véc tơ khởi tạo (iv) dùng để đảm bảo những bản rõ giống nhau không tạo ra bản mã giống nhau]]