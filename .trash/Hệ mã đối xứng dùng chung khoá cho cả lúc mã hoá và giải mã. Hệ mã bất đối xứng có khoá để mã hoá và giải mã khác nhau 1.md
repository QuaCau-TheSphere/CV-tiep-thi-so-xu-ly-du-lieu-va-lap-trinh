---
share: true
created: 2023-10-30T14:29
updated: 2025-10-17T13:28
---
## Hệ mã đối xứng - Private Key
Các hệ mã đối xứng sử dụng chung một khóa K cho cả hai hàm mã hóa và giải mã.

![secret-key.png](https://images.viblo.asia/18905ed4-fe63-4498-af88-90a893a7ca5e.png)

Các ví dụ về hệ mã dòng (OTP) và mã khối (DES, AES) đều là các hệ mã đối xứng.

Có tốc độ tính toán nhanh, Nhưng lại khó để vận chuyển khóa

## Hệ mã bất đối xứng - Public Key
Vấn đề đối với các hệ mã đối xứng đó là rất khó để trao chuyển khóa một cách bí mật và các khóa thường gắn liền với một phiên làm việc. Do đó rất khó để quản lý khóa, hơn nữa hệ mã đối xứng không cung cấp cho chúng ta cơ chế chữ ký điện tử.

![525px-Public_key_encryption.svg.png](https://images.viblo.asia/36dc6d46-fb0f-465b-a73a-b027037f7683.png) _nguồn: [https://en.wikipedia.org](https://en.wikipedia.org)_

Vì vậy, các hệ mã khóa công khai đã ra đời để giải quyết các vấn đề trên, ý tưởng của hệ mã khóa công khai đó là mỗi khóa sẽ gắn liền với một người sử dung (thay vì gắn liền với một phiên làm việc giữa 2 người dùng). Trong hệ mã khóa công khai, khóa sẽ bao gồm một bộ gồm 2 khóa PK (Public Key) và SK (Secret Key). Tin nhắn mã hóa với khóa PK sẽ được giải mã với khóa SK và ngược lại. Khóa PK sẽ được công khai, vì vậy ai cũng có thể sử dụng khóa đấy để mã hóa rồi gửi tin nhắn bí mật cho A, nhưng chỉ có A mới có thể giải mã tin nhắn đó (do chỉ có A mới có khóa SK).

Sơ đồ chung của hệ mã như sau:

```
E(m, pk) = c
D(c, sk) = m
```

Một hệ mã hóa công khai rất nổi tiếng đó là [RSA](https://en.wikipedia.org/wiki/RSA_%28cryptosystem%29)

So với các hệ mã hóa đối xứng, thì hệ mã hóa bất đối xứng có tốc độ tính toán chậm hơn rất nhiều. Vì vậy, người ta thường dùng hệ mã bất đối xứng để vận chuyển khóa bí mật, sau đó phiên làm việc sẽ được mã hóa trên khóa chung này (sử dụng các hệ mã đối xứng).

Nguồn:: [Giới Thiệu Về Các Hệ Mã Hóa](https://viblo.asia/p/gioi-thieu-ve-cac-he-ma-hoa-OEqGj6rNG9bL)