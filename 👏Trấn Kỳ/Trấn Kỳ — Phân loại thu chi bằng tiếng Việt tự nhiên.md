---
share: true
created: 2023-09-05T16:17
updated: 2024-01-30T23:52
title: Trấn Kỳ — Phân loại thu chi bằng tiếng Việt tự nhiên
alias: Trấn Kỳ
description: Phân loại câu nhập bằng tiếng Việt tự nhiên
filename: index
---
Bạn có cảm thấy chán nản, mất năng lượng vì phải tốn quá nhiều thời gian để phân loại chi tiêu cũng như các loại dữ liệu khác không? Nay đã có Trấn Kỳ. Nếu bạn là người cần phân loại tất cả các chi tiêu của mình một cách rõ ràng (việc nhắm hờ mỗi tháng chi chừng bao nhiêu tiền là không đủ với bạn), và bạn cần một chương trình:
- [x] Tích hợp được vào hệ thống vận hành hiện tại của bạn: báo cáo ngân hàng, Google Keep, Google Sheet, Notion, Obsidian, Fibery, Odoo, v.v. 
- [x] Cho phép bạn khai báo dữ liệu theo thói quen và cách phân loại của chính mình
- [x] Tự động phân loại, gắn nhãn thông tin chứ không bắt bạn phải tự xử lý
- [x] Không giam dữ liệu của bạn tại chương trình 
- [x] Không có bất cứ quảng cáo mời mọc hoặc theo dõi dữ liệu nào
- [x] Dùng được trên điện thoại khi không có mạng

Thì chương trình này dành cho bạn.
![[Hemi Head_med.png]]

[[1.2 Lấy code|Tải Trấn Kỳ]]{ .md-button .md-button--primary } [Lý do viết Trấn Kỳ](https://obsidian.quảcầu.cc/📐 dự án/trấn kỳ/9 blog/lý do viết trấn kỳ?utm_source=CW+Ti%E1%BA%BFp+th%E1%BB%8B+s%E1%BB%91%2C+x%E1%BB%AD+l%C3%BD+d%E1%BB%AF+li%E1%BB%87u+v%C3%A0+l%E1%BA%ADp+tr%C3%ACnh+%C2%BB+Gi%E1%BB%9Bi+thi%E1%BB%87u+Tr%E1%BA%A5n+K%E1%BB%B3&utm_medium=vault&utm_campaign=Tr%E1%BA%A5n+K%E1%BB%B3&utm_content=ph%E1%BA%A7n+m%E1%BB%9F+%C4%91%E1%BA%A7u){ .md-button .md-button--primary }
# Tính năng
## Phân loại thông tin
Ví dụ, với câu nhập đầu vào là:
```
thăn bò 30k lườn gà 20k (giảm giá) cho Parid ở coopmart vợ trả 
```

Kết quả đầu ra sẽ là:

| Tên                         | Giá trị          |
| --------------------------- | ---------------- |
| Món đồ                      | thăn bò, lườn gà |
| Loại món đồ                 | Lương thực       |
| Phương thức thanh toán      | vợ trả           |
| Loại phương thức thanh toán | Tiền mặt         |
| Nơi mua                     | CoopMart         |
| Loại nơi mua                | Siêu thị         |
| Người thụ hưởng             | Parid            |
| Loại người thụ hưởng        | Gia đình         |
| Số tiền                     | 50000            |
| Ghi chú                     | giảm giá         |

Chương trình có thể tự động bắt được các giá trị trên nhờ vào [[2. Thiết lập chương trình|cấu hình bạn đã thiết lập]] từ trước. Ở ví dụ này, bạn đã thiết lập như sau:

| Từ khoá từ câu nhập... | ...thuộc nhãn phân loại... | ...thuộc chiều dữ liệu   |
| ---------------------- | -------------------------- | ------------------------ |
| `thăn bò`, `lườn gà`   | `Lương thực`               | `Món đồ`                 |
| `vợ trả`               | `Tiền mặt`                 | `Phương thức thanh toán` |
| `coopmart`             | `Siêu thị`                 | `Nơi mua`                |
| `Parid`                | `Gia đình`                 | `Người thụ hưởng`        |
| `20k`, `30k`           | Không thiết lập            | `Số tiền`                |
| `giảm giá`             | Không thiết lập            | `Ghi chú`                |

## Giá trị mặc định
Ví dụ, bạn có thể thiết lập để chương trình tự hiểu là nếu bạn không điền từ khoá gì trong chiều `Phương thức thanh toán` thì mặc định đó là `tiền mặt`.

## Tiếp nhận từ khoá chưa được khai báo một cách trực tiếp
Sẽ có những lúc bạn muốn một từ khoá nào đó chưa kịp khai báo trong cấu hình xuất ra ở kết quả. Bạn có thể thiết lập các ký tự để chương trình hiểu là dữ liệu đó nên được cho vào mục nào.

Ví dụ, bạn mới gặp `Iris` và muốn tặng `dưa hấu` cho bạn ấy. Bạn chưa kịp khai báo tên của `Iris` vào cấu hình. Bạn có thể thiết lập ký tự `@` dành cho chiều `Người thụ hưởng`. Khi đó, bạn có thể dùng câu nhập:
```
tặng dưa hấu cho @Iris 50k
```

Lúc này chương trình sẽ tự hiểu `Iris` là `Người thụ hưởng`.

Nếu sau đó không xuất hiện dấu `@` lần nữa thì từ khoá sẽ dừng khi gặp dấu cách đầu tiên. Nếu từ khoá chứa nhiều dấu cách thì bạn thêm một dấu `@` nữa ở ngay cuối. Ví dụ:
```
tặng dưa hấu cho @chị Iris@ 50k
```

Bạn có thể khai báo ký tự đứng trước khác với ký tự đứng sau. Thường gặp nhất là khi bạn cần có một ghi chú nào đó. Ví dụ:
```
tặng dưa hấu cho @chị Iris@ 50k (sau đó mới biết chị Iris dị ứng dưa hấu)
```

## Viết tắt 
Ví dụ, bạn muốn viết tắt `as`, `st` cho nhanh, nhưng vẫn muốn kết quả hiện ra đầy đủ là `ăn sáng`, `siêu thị`. Bạn còn có thể dùng viết tắt cho những câu nhập phức tạp.

Ví dụ:
- `as` → `ăn sáng`
- `st` → `siêu thị`
- `xăng` → `xăng 50k`
- `trọ` → `tiền trọ 3tr chuyển khoản (vay qua nhóm Tình Thân)`

## Hiểu từ ghép
Ví dụ, nếu lúc thiết lập cấu hình bạn có khai báo ba từ khoá `bún`, `bò`, và `bún bò`, và trong câu nhập có chữ `bún bò` thì chương trình sẽ hiểu đây là một từ chứ không nhận diện nhầm là có hai từ `bún` và `bò`.

## Một từ khoá có thể thuộc về nhiều nhãn phân loại
Ví dụ, từ khoá `ăn trưa với` vừa có thể thuộc nhãn `Mối quan hệ`, vừa có thể thuộc nhãn `Thực phẩm`

## Nhập liệu và tạo báo cáo ngay trên hệ thống bạn đang dùng
Ví dụ, Google Keep là một phần mềm ghi chú rất phổ biến với mọi người. Nó:
- Có trên iOS, Android và web
- Mở rất nhanh và có thể mở trong tình trạng không có mạng
- Đồng bộ nhanh chóng trên tất cả các thiết bị
- Hoàn toàn miễn phí
- Cho phép nhiều người cùng chỉnh sửa một ghi chú
- Sử dụng giọng nói
- Nhập số lượng lớn

Việc có thể nhập liệu từ Google Keep sẽ giúp cho bạn có thể nhập nhanh những khoảng chi tiêu chung với khối lượng lớn vào lúc bạn không có đầu óc để phân loại, phù hợp cho gia đình, nhóm bạn, công ty những lúc chợ búa, du lịch, tổ chức sự kiện, v.v.

![[Keep to Fibery.png]]
Hiện tại đã có sẵn phần bổ trợ (add-on) để nhập dữ liệu từ Google Keep và xuất dữ liệu sang Fibery. Bạn có thể tự viết những phần bổ trợ khác cho phù hợp với bạn.

# Các tính năng hỗ trợ khác (a.k.a. yêu cầu phi chức năng) 
- **Viết cho người Việt** nên:
	- Xử lý được từ ghép và [[Tiếng Việt có 2 cách đặt dấu thanh|các cách đặt dấu thanh khác nhau]]
	- Tên biến, tên hàm hoàn toàn bằng tiếng Việt
- **Viết cho người cần sử dụng trên các webapp khác** như Fibery, Google Sheet nên:
	- Chỉ sử dụng JavaScript thuần 
	- Đảm bảo regex không chạy lâu
	- Có sẵn build script để chuyển từ TypeScript sang JavaScript
- **Viết cho người không muốn bị ràng buộc vào một nền tảng nào** nên sẽ là một chương trình mã nguồn mở và tự do
- **Viết cho người phải tự học lập trình** nên:
	- Có rất nhiều ghi chú, hướng dẫn để cung cấp các khái niệm thiết yếu trong việc giúp bạn xây dựng mental model cho code, để bạn hiểu được cái cách một lập trình viên kiến trúc nên một chương trình thế nào. Những thứ sẽ hay được sử dụng:
		- Các phép so sánh, ẩn dụ, 
		- Các sắp đặt để tạo sự tương phản (juxtaposition) giữa các định nghĩa, ý tưởng 
		- Ý đồ thiết kế (design choice) chương trình 
	- Tên commit cố gắng tuân thủ [conventional commit](https://www.conventionalcommits.org/en/v1.0.0/)
	- Có script kiểm thử

![Giao diện khởi động](https://i.imgur.com/rBe2iQ9.png)
# Không chỉ mỗi phân loại thu chi
Thật ra, chương trình này không hẳn nên được đặt tên là "Phân loại thu chi", vì bạn còn có thể dùng nó để phân loại nhiều thứ khác. Ví dụ:
- **Ý tưởng**: `Kĩ thuật viết văn %topic_Writing @tác_giả_a`
- **Mối quan hệ**: `Gặp @ông_A bàn về việc X, có đi ăn ở !nhà_hàng_Y 200k ck vcb`
- **Công việc**: `Công việc A cần giao cho @bạn_B liên hệ với @@đối_tác_C tại !quán_D với chi phí dự kiến 300k ck vcb và nhận output &&item_X`
- **Cảm xúc**: `xem phim:Inception thấy chấn động`
- **Sức khoẻ:** `chạy bộ 100m, hít đất 30 cái`

Bạn muốn đọc gì tiếp theo?

[[1.2 Lấy code|Tải Trấn Kỳ]]{ .md-button .md-button--primary } [Lý do viết Trấn Kỳ](https://obsidian.quảcầu.cc/📐 dự án/trấn kỳ/9 blog/lý do viết trấn kỳ?utm_source=CW+Ti%E1%BA%BFp+th%E1%BB%8B+s%E1%BB%91%2C+x%E1%BB%AD+l%C3%BD+d%E1%BB%AF+li%E1%BB%87u+v%C3%A0+l%E1%BA%ADp+tr%C3%ACnh+%C2%BB+Gi%E1%BB%9Bi+thi%E1%BB%87u+Tr%E1%BA%A5n+K%E1%BB%B3&utm_medium=vault&utm_campaign=Tr%E1%BA%A5n+K%E1%BB%B3&utm_content=ph%E1%BA%A7n+cu%E1%BB%91i+b%C3%A0i){ .md-button .md-button--primary } [[Hướng dẫn sử dụng Trấn Kỳ|Hướng dẫn sử dụng Trấn Kỳ]]{ .md-button .md-button--primary }