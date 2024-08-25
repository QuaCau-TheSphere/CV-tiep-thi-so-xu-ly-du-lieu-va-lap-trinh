---
share: true
created: 2023-10-30T14:29
updated: 2024-08-18T15:05
alias: CORS ngăn chặn việc script ở tab này điều khiển tab kia
---
## What is Same Origin Policy?

![](https://images.viblo.asia/9c0d86ff-0393-43e0-9109-80fe89fb7d2b.jpeg)

**Same-origin policy** (SOP) là một trong những chính sách bảo mật quan trọng nhất trên trình duyệt hiện đại, nhằm ngăn chặn JavaScript code có thể tạo ra những request đến những nguồn khác với nguồn mà nó được trả về. Ba tiêu chí chính để so sánh request bao gồm:

- Domain (tên miền)
- Protocol (giao thức)
- Port (cổng kết nối)

Nói đơn giản thì request sẽ được coi là hợp lệ chỉ khi nó thỏa mãn 3 tiêu chí ở trên (cùng domain,cùng protocol và cùng port)

### Example

Thử tưởng tượng khi chúng ta đang mở 2 tab, 1 tab là facebook, tab kia là 1 trang web nào đó có chứa mã độc. Sẽ rất nguy hiểm nếu như các đoạn script ở bên tab chứa mã độc có thể tự do thao tác lên tab facebook phía bên kia, và **SOP** sinh ra với nhiệm vụ ngăn chặn các hành động này.

Dưới đây là vd về list các pages vi phạm **SOP** của site origin( [http://www.example.com](http://www.example.com)) :

- [http://www.example.co.uk](http://www.example.co.uk) (khác domain)
- [http://example.org](http://example.org) (khác domain)
- [https://example.com](https://example.com) (khác protocol)
- [http://example.com:8080](http://example.com:8080) (khác port)

### Bypass Same-Origin Policy

Mặc dù ưu điểm bảo mật của **SOP** là rõ ràng, tuy nhiên trong một số trường hợp điều này lại gây khó khăn cho các nhà phát triển.

Điển hình Internet Explorer có hai ngoại lệ có thể bỏ qua **SOP**:

- Nếu 2 domain cùng thuộc trust zone
- Không bao gồm cổng, nghĩa là với IE thì [http://company.com:81/index.html](http://company.com:81/index.html) và [http://company.com/index.html](http://company.com/index.html) đều cùng source.

Nếu một công ty có nhiều web application cùng yêu cầu xác thực tại một nơi, vd như [http://store.company.com](http://store.company.com) cần xác thực tại [http://login.company.com](http://login.company.com) trước. Việc nhận dữ liệu trả về từ request đến [http://login.company.com](http://login.company.com) không khả thi vì đã bị chặn do vi phạm **SOP**.

Chúng ta có nhiều cách để giải quyết trong trường hợp này, thường dùng nhất là **Cross Origin Resource Sharing** (CORS). Tuy nhiên chúng ta sẽ nói về CORS ở phần khác.
Nguồn:: [[Viblo]], [Security testing tutorial (Part 4): Same Origin Policy & Cookies](https://viblo.asia/p/security-testing-tutorial-part-4-same-origin-policy-cookies-bWrZnOLwlxw)

[[CORS là để trình duyệt bảo vệ người dùng, không phải để bảo vệ máy chủ]]
[[Origin là sự kết hợp của protocol, hostname và port]]
