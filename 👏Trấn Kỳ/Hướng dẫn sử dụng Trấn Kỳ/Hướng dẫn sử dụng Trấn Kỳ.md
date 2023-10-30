---
share: true
created: 2023-08-25T14:20
updated: 2023-10-30T18:21
title: Hướng dẫn sử dụng Trấn Kỳ
filename: index
---
# 1. Cài đặt và sử dụng nhanh
[[1.1 Cài đặt PowerShell, Deno, Python, Git, VS Code]]
[[1.2 Lấy code]]

# 2. Thiết lập chương trình
[[2. Thiết lập chương trình]]
[[Hiểu về YAML]]
[[Sử dụng main.ts]]
[[Sử dụng tranky.py]]
[[Thiết lập trên Fibery]]
[[Sử dụng Docker]]
[[Chạy chương trình định kỳ]]
# 3. Hiểu code nói gì
Phần này sẽ cố gắng cung cấp các khái niệm thiết yếu trong việc giúp bạn xây dựng mental model cho code, để bạn hiểu được cái cách một lập trình viên kiến trúc nên một chương trình thế nào. Những thứ sẽ hay được sử dụng:
- Các phép so sánh, ẩn dụ, 
- Các sắp đặt để tạo sự tương phản (juxtaposition) giữa các định nghĩa, ý tưởng 
- Ý đồ thiết kế (design choice) chương trình 

[[3.1 Mô hình xử lý dữ liệu]]
[[Chiều, từ và nhãn]]
[[Hướng dẫn debug]]
[[Ý nghĩa của biểu thức regex trong hàm lọcSốTiền()]]
[[Ý nghĩa của biểu thức regex trong hàm lọcDữLiệuCầnTựĐộngNhậnDạng()]]

> [!NOTE] Hỗ trợ trực tiếp
> Nếu bạn cần sự hỗ trợ trực tiếp, bạn có thể tham gia [các buổi hướng dẫn sử dụng Trấn Kỳ](https://obsidian.quảcầu.cc/%F0%9F%93%90%20d%E1%BB%B1%20%C3%A1n/3%20th%C3%A0nh%20ph%E1%BA%A9m/c%C3%A1c%20bu%E1%BB%95i%20%C4%91%C3%A1p%20%E1%BB%A9ng%20nhu%20c%E1%BA%A7u%20h%E1%BB%8Dc%20c%C3%A1ch%20s%E1%BB%AD%20d%E1%BB%A5ng%20c%C3%B4ng%20c%E1%BB%A5%20v%C3%A0%20t%C6%B0%20duy%20l%E1%BA%ADp%20tr%C3%ACnh%20cho%20nhu%20c%E1%BA%A7u%20c%C3%A1%20nh%C3%A2n%20ho%E1%BA%B7c%20nghi%C3%AAn%20c%E1%BB%A9u/c%C3%A1c%20bu%E1%BB%95i%20h%C6%B0%E1%BB%9Bng%20d%E1%BA%ABn%20s%E1%BB%AD%20d%E1%BB%A5ng%20tr%E1%BA%A5n%20k%E1%BB%B3/?utm_source=CW+X%E1%BB%AD+l%C3%BD+d%E1%BB%AF+li%E1%BB%87u+v%C3%A0+l%E1%BA%ADp+tr%C3%ACnh+%C2%BB+H%C6%B0%E1%BB%9Bng+d%E1%BA%ABn+s%E1%BB%AD+d%E1%BB%A5ng+Tr%E1%BA%A5n+K%E1%BB%B3&utm_medium=vault&utm_campaign=Tr%E1%BA%A5n+K%E1%BB%B3). Chúng là một phần của [các buổi đáp ứng nhu cầu học cách sử dụng công cụ và hiểu tư duy lập trình cho nhu cầu cá nhân hoặc nghiên cứu](https://obsidian.quảcầu.cc/%F0%9F%93%90%20d%E1%BB%B1%20%C3%A1n/3%20th%C3%A0nh%20ph%E1%BA%A9m/c%C3%A1c%20bu%E1%BB%95i%20%C4%91%C3%A1p%20%E1%BB%A9ng%20nhu%20c%E1%BA%A7u%20h%E1%BB%8Dc%20c%C3%A1ch%20s%E1%BB%AD%20d%E1%BB%A5ng%20c%C3%B4ng%20c%E1%BB%A5%20v%C3%A0%20t%C6%B0%20duy%20l%E1%BA%ADp%20tr%C3%ACnh%20cho%20nhu%20c%E1%BA%A7u%20c%C3%A1%20nh%C3%A2n%20ho%E1%BA%B7c%20nghi%C3%AAn%20c%E1%BB%A9u/?utm_source=CW+X%E1%BB%AD+l%C3%BD+d%E1%BB%AF+li%E1%BB%87u+v%C3%A0+l%E1%BA%ADp+tr%C3%ACnh+%C2%BB+H%C6%B0%E1%BB%9Bng+d%E1%BA%ABn+s%E1%BB%AD+d%E1%BB%A5ng+Tr%E1%BA%A5n+K%E1%BB%B3&utm_medium=vault&utm_campaign=Tr%E1%BA%A5n+K%E1%BB%B3).
