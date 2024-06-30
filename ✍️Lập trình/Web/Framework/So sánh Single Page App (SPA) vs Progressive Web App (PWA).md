---
share: true
created: 2023-10-30T14:29
updated: 2024-04-03T13:36
---
Hôm nay mình thấy một team nói với nhau về **Progressive web app** mà không phân biệt nó khác **Single page app** đến mức nào? Và công nghệ chạy background ra sao! Chỉ biết là nó dùng ajax, javascript thư viện của thằng này thằng kia nên nó là Progressive web app đó, chứ hỏng có hiểu là cơ chế hoạt động nó ra sao hết thấy tội mà thôi cũng kệ… luôn chứ sao 😀

![](https://sp-ao.shortpixel.ai/client/to_auto,q_glossy,ret_img,w_1369,h_451/http://lcdung.top/wp-content/uploads/2018/01/Untitled.png)

Như hình mô tả bên trên của mình thì chắc cũng hiểu sơ sơ tốc độ load của từng loại khái niệm về _**web app, single page app, progressive web app**_!

![](https://sp-ao.shortpixel.ai/client/to_auto,q_glossy,ret_img,w_690,h_257/http://lcdung.top/wp-content/uploads/2018/01/web_development.jpg)

## Web app

![](https://sp-ao.shortpixel.ai/client/to_auto,q_glossy,ret_img,w_550,h_301/http://lcdung.top/wp-content/uploads/2018/01/download.jpg)

Cái này chắc mọi người ai cũng từng nghe web động (_dynamic web app_) cơ chế hoạt động của web app từ thời sơ khai cho đến nay cũng không thay đổi nhiều với phương thức truyền dữ liệu là Post form hoặc reload trang để Get param từ url.

- **Browser (Client site):**
    - Yêu cầu hỗ trợ technique không cần nhiều!
    - Hoạt động: mỗi lần gửi request thì browser phải đợi response, _**load lại**_ rất nhiều thông tin từ server site như gói dữ liệu html, hình ảnh, css, js,…
- **Web server (Server site):** 
    - Mỗi lần nhận response thì Server phải xử lý rất nhiều từ data, bussiness logic và cuối cùng tạo ra view và gửi string html rất nặng về client site.

_**Bất lợi khá nhiều****:**_

1. Tổng lại là thời gian load để xử lý từ 2 phía client và server rất nhiều!
2. Server site xử lý khá nhiều vì phải generate view cho client.
3. Việc develop tốn nhiều công sức đồi hỏi client site và server site phải có sự liên kết!

## Single Page App (SPA)

![](https://sp-ao.shortpixel.ai/client/to_auto,q_glossy,ret_img,w_550,h_300/http://lcdung.top/wp-content/uploads/2018/01/TraditionalLifecycle.jpg)

Vì sự bất lợi của Web app, _**Single page app**_ ra đời để cải thiện các điểm bất lợi còn tồn động và single page app xử lý dựa trên nền các library, framework java script và _**phương thức truyền dữ liệu chính là dùng ajax**_. Ai dùng Angular (Framework) hay React (Library) sẽ hiểu về nó 😛

- **Browser (Client site):**
    - Yêu cầu technique: phải hỗ trợ java script, các library java script dùng ajax là chính.
    - Hoạt động: mỗi lần load page lần đầu khá lâu, vì load master page và khởi tạo các Object model (lưu trữ data vào object java script). Nhưng sẽ _**không tốn thời gian load lại**_ khi chuyển sang các page khác vì mọi thứ đều được các library hoặc framework sẽ render thành view, còn data sẽ được truyền thông qua ajax và được lưu vào các object!
- **Web server (Server site):** 
    - Mỗi lần nhận response thì Server chỉ xử lý data, bussiness logic và gửi data theo kiểu json object dữ liệu rất nhẹ về client site.

_**Thuận lợi:**_

1. Tổng lại là thời gian load để xử lý từ 2 phía client và server giảm rất nhiều!
2. Server site xử lý và trả về gói dự liệu nhẹ hơn nhiều.
3. Việc develop client site và server site có thể tách rời riêng biệt rõ ràng hơn!
4. Việc chuyển trang trên single page và không reload page nên thấy rất nhanh.

**Bất lợi:**

1. Developer phải có kiến thức về java script và các library java script render (React, Angular,…) thật kỹ để phát triển front end.
2. Browser phải hỗ trợ các version java script mới để các library hay framework java script vận hành tốt.
3. Khi reload page thời gian khởi tạo từ phía client vẫn tốn nhiều thời gian.

## Progressive Web App (PWA)

![](https://sp-ao.shortpixel.ai/client/to_auto,q_glossy,ret_img,w_638,h_339/http://lcdung.top/wp-content/uploads/2018/01/sw.jpg)

Để tối ưu hơn tốc độ load từ Single page app, **Progressive web app** ra đời để tận dụng các technique từ Browser đã hỗ trợ Java script, Cache, DB local và phương thức truyền dữ liệu chính là _**Service Worker**_ (Plugin của browser, device dùng thông qua java script và là trái tim của PWA).

- **Browser (Client site):**
    - Yêu cầu technique: phải hỗ trợ Java script, Cache, DB local và Service Worker là phương thức chính để nhận data, lưu trữ vào cache hoặc DB.
    - Hoạt động: Mỗi lần đầu load page thời gian load master page và khởi tạo Service Worker không nhiều như **SPA**. Theo SPA mất 10 giây thì PWA chỉ mất 1 giây. Những lân load page lại thì SPA vẫn tốn 5-10 giây để load thì Service Worker chỉ tốn chưa đến 1 giây.
- **Web server (Server site):** 
    - Mỗi lần nhận response thì Server chỉ xử lý data, bussiness logic và gửi data theo kiểu json object object, dữ liệu rất nhẹ.

_**Thuận lợi:**_

1. Tổng lại là thời gian load để xử lý từ 2 phía client và server giảm rất nhiều!
2. Server site xử lý và trả về gói dự liệu nhẹ hơn nhiều.
3. Việc develop client site và server site có thể tách rời riêng biệt rõ ràng hơn!
4. Việc reload trang không còn là vấn đề như SPA.
5. Trang đã load lần đầu thì các lần sau có thể chạy offline vì mọi thứ đều store dưới local của browser.

**Bất lợi:**

1. Developer phải có kiến thức về java script và các library java script render (React, Vue,…) thật kỹ để phát triển front end.
2. Browser phải dùng version mới để hỗ trợ các version java script để các library hay framework java script sử dụng service worker.
3. Domain phải dùng HTTPS để bảo mật khi truyền dữ liệu.

Trong tương lai mình thấy được **Accelerated Mobile Pages (AMP)** sẽ kết hợp với PWA để tạo ra đột phá về trải nghiệm người dùng tốt hơn về thời gian load có thể là tốn zero giây cho first load 😀

![](https://sp-ao.shortpixel.ai/client/to_auto,q_glossy,ret_img,w_804,h_455/http://lcdung.top/wp-content/uploads/2018/01/app.jpg)


Nguồn:: [So sánh Single Page App (SPA) vs Progressive Web App (PWA) - LCDUNG](https://lcdung.top/sanh-single-page-app-spa-vs-progressive-web-app-pwa/)