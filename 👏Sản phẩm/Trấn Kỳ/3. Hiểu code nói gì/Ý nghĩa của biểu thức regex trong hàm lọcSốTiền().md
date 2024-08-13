---
share: true
created: 2023-09-19T23:23
updated: 2024-07-31T15:28
---

```js
const ANY_CHAR = '[aAàÀảẢãÃáÁạẠăĂằẰẳẲẵẴắẮặẶâÂầẦẩẨẫẪấẤậẬbBcCdDđĐeEèÈẻẺẽẼéÉẹẸêÊềỀểỂễỄếẾệỆfFgGhHiIìÌỉỈĩĨíÍịỊjJkKlLmMnNoOòÒỏỎõÕóÓọỌôÔồỒổỔỗỖốỐộỘơƠờỜởỞỡỠớỚợỢpPqQrRsStTuUùÙủỦũŨúÚụỤưƯừỪửỬữỮứỨựỰvVwWxXyYỳỲỷỶỹỸýÝỵỴzZ0123456789-_]'
const regexSốTiền = new RegExp('=? *(\\d|,|\\.)+ ?(k|tr|d|đ)(?!' + ANY_CHAR + ')', 'giu');
```
Ý nghĩa của biểu thức regex số tiền:
- `＝? ` nghĩa là có thể có một dấu bằng (`＝`) trước số tiền tổng. Dấu bằng đó có thể cách hoặc không cách con số đó
- `(\d|,|\.)+` khớp với một hoặc nhiều chữ số, dấu phẩy hoặc dấu chấm
- ` ?(k|tr|d|đ)` dùng để đảm bảo rằng con số vừa tìm được là số tiền chứ không phải là một con số bất kỳ. Nó biết được điều này bằng việc tìm một trong các ký tự `k`, `tr`, `d` hoặc `đ`. Các ký tự này có thể có hoặc không có một dấu cách với con số đứng trước nó
- `(?!ANY_CHAR)` đảm bảo rằng đứng ngay sau đơn vị tiền không có chữ cái nào hết, phòng trường hợp những ký tự này nằm trong một từ nào đó

Ví dụ:
- `đi chợ 3 tr + 30k`          → bắt được `3 tr`, `40k`
- `gạo 30k + rau 40k = 70k`    → bắt được `30k`, `40k`, `＝ 70k`
- `sách 40 trang, 10 đèn cầy`  → không bắt được cái nào, dù có `40 tr` và `10 đ` ở trong đó

Số tiền bắt buộc phải có đơn vị đằng sau vì có những trường hợp mua nhiều món, hoặc có số trong tên. Vd: `3 ly cà phê 100k`, `keo 502 3k`