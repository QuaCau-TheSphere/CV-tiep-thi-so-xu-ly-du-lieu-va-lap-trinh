---
share: true
created: 2023-10-30T14:29
updated: 2026-10-02T15:35
---
## Yêu cầu chức năng
Phải có:
- Dùng được với những nền tảng không cấp API

Có thì tốt:
- Phân loại độ khẩn cấp, quan trọng
- Có log 
- Nhắc hẹn
- Trả lời tự động những thứ bot có thể trả lời được
- Bấm vào là mở ra được nơi chat 
- Có bản web 

## Giải pháp
Tốt nhất là trở thành notification center. Nếu là dùng web thì là tạo một trình duyệt riêng.

### Cách 1: chuyển tiếp thông báo nhận được sang một nơi khác
Nhược điểm là chỉ dùng được cho Android.

Các bước cài đặt
1. Cài Tasker trên điện thoại Android. Cấp hết các quyền cần thiết
2. Import [profile này](https://taskernet.com/shares/?user=AS35m8lzsj4d9AypQpFbngaGm31G9aDGS2iHxuemGuaJEbTFdhTS9XhDmhTOWhnwKalKBPQ5&id=Profile%3AWebhook+Momo)
3. Triển khai chương trình [QuaCau-TheSphere/lay-thong-bao-tren-dt](https://github.com/QuaCau-TheSphere/sound/) lên Deno Deploy. Xem [demo](https://anxin.quacau.deno.net/)

![Tasker - Querying All Notifications And Going Through Them - YouTube](https://www.youtube.com/watch?v=sG37APnlmGI)

### Cách 2: tạo một trình duyệt riêng chỉ để quản lý các nền tảng chat
Nhược điểm là chỉ dùng được cho nền tảng nào có phiên bản dành cho web