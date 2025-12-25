---
share: true
created: 2023-10-30T14:29
updated: 2025-10-02T14:03
---
- **Phân vùng chính (Primary Partition):** Là phân vùng có thể khởi động được, tức là có thể cài đặt hệ điều hành và chạy nó. Mỗi ổ đĩa cứng chỉ có thể có tối đa 4 phân vùng chính hoặc 3 phân vùng chính và 1 phân vùng mở rộng.
- **Phân vùng mở rộng (Extended Partition):** Là phân vùng không thể khởi động được, chỉ có thể chứa dữ liệu và các tập tin. Phân vùng mở rộng được tạo ra để giải quyết giới hạn số lượng phân vùng chính. Mỗi ổ đĩa cứng chỉ có thể có 1 phân vùng mở rộng, và trong đó có thể tạo ra nhiều phân vùng logic.
- **Phân vùng logic (Logical Partition):** Là các phân vùng con của phân vùng mở rộng, có thể chứa dữ liệu và các tập tin. Số lượng phân vùng logic không bị giới hạn, tùy thuộc vào dung lượng của ổ đĩa cứng.
- **Phân vùng EFI (EFI System Partition):** Là phân vùng dành cho các máy tính sử dụng chuẩn UEFI (Unified Extensible Firmware Interface) thay cho BIOS (Basic Input/Output System). Phân vùng EFI chứa các tập tin khởi động, các driver và các ứng dụng liên quan đến quá trình khởi động của hệ điều hành.
- **Phân vùng khôi phục (Recovery Partition):** Là phân vùng được tạo ra bởi nhà sản xuất máy tính hoặc người dùng để lưu trữ các tập tin cần thiết để khôi phục hệ điều hành khi gặp sự cố. Phân vùng khôi phục thường được ẩn đi để tránh bị xóa hay sửa đổi.

Nguồn:: [Partition là gì? Cách phân vùng ổ đĩa trên Windows](https://hoanghapc.vn/phan-vung-o-dia-tren-windows)