---
share: true
created: 2023-10-30T14:29
updated: 2024-07-21T14:01
---
Chính vì [[Có thể xem nội dung file với hash là như nhau. Nhưng file thì có thể có kích thước vô cùng lớn, còn hash thì luôn chỉ có 40 ký tự|nội dung file với hash là như nhau, nhưng file thì có kích thước vô cùng lớn, còn hash thì chỉ có 40 ký tự]], nên thay vì ta phải quản lý file, thì ta chỉ cần quản lý hash của chúng là được. Điểm trừ tất nhiên là ta không thể tái tạo lại nội dung file từ hash, vì hàm băm là hàm một chiều. Nhưng điều đó không quan trọng, nếu tất cả những gì ta cần là quản lý.

Folder cũng tương tự như vậy. Thay vì quản lý một folder với các file, ta chỉ tạo ra một file là danh sách chứa các hash của các file trong folder đó, rồi quản lý cái hash của cái file đó là được. 

Nguồn:: 