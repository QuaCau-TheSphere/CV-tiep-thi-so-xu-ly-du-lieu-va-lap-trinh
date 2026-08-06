---
share: true
created: 2023-10-30T14:29
updated: 2026-08-06T15:36
---
### Chuyện làm web thời xưa

Thời xưa, người ta chẳng cần bundler gì sất. Câu chuyện này giống như chuyện thời xưa người ta không cần điện thoại ấy.

Để xây dựng một trang web, cần các nguyên liệu chính là HTML, CSS và JS. Điều này nghe đơn giản và dễ hiểu đúng không?

### Chuyện làm web thời nay

Còn thời nay, chẳng ai build website với chỉ HTML, CSS, JS cả. Ít nhất ấy, thì cũng có một vài thứ khác bổ trợ như html-inspector, jQuery, React, Angular, .. và còn nhiều loại module javascript khác nữa.

Còn chưa kể app script không chỉ một file là xong logic cho cả trang web được, dev cần tách ra nhiều files để dễ quản lý code hơn, như là theo từng phần của trang web chẳng hạn: script-header.js, script-footer.js, script-about-page.js, …

Và thế là, `<script>` tags trong cái body hay header hay cả hai bắt đầu xếp hàng dài nối nhau như thế này:

```html
<body>
    <script src="script-header.js"></script>
    <script src="script-footer.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html-inspector/0.8.2/html-inspector.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
</body>
```

Thêm nữa nếu mấy cái script ở trên mà phụ thuộc vào nhau, không được sắp đúng vị trí thì bạn sẽ gặp các lỗi dạng như “Uncaught ReferenceError: $ is not defined“

![](https://i0.wp.com/beautyoncode.com/wp-content/uploads/2021/11/error-require.jpeg?resize=768%2C205&ssl=1)

Lỗi này xảy ra khi bạn viết code jquery trong file script-header.js mà load script jQuery ở sau file này. Thì lúc trình duyệt đọc đến file script-header.js nó sẽ báo lỗi là không tìm thấy jQuery.

Để sửa lỗi này thì các mô-đun được sử dụng ở những loại mô-đun cần được sắp xếp đúng thứ tự. Và thử tưởng tượng nếu có nhiều script thì việc sắp xếp chúng theo đúng thứ tự cần ưu tiên script nào load trước, cái nào load sau là cả một vấn đề, chưa nói chuyện nhìn vào cũng hơi hoa mắt.

### Tui - bundler ra đời

Chính vì cái sự đa dạng và phong phú của các modules được sử dụng ngày càng nhiều, và sự dính chùng vào nhau khi mô-đun A dùng code của mô-đun B rồi mô-đun C dùng code của mô-đun D, nên tui – **bundler** mới được ra đời.

Cám ơn tui đi 🥳

Nhiệm vụ chính của tui là gom hết tất cả các loại script lại cùng nhau theo thứ tự ưu tiên mà bạn đặt cho tụi nó và cho ra một file script duy nhất.

![](https://i0.wp.com/beautyoncode.com/wp-content/uploads/2021/11/bundler-1.png?resize=768%2C300&ssl=1) **Chưa kể, nếu bạn:** – không muốn xài javascript nữa, mà muốn xài typescript? Tui ok luôn

– không muốn xài HTML mà xài React? Tui ok luôn

– không muốn xài CSS mà xài SASS? Tui cũng ok luôn

Chưa hết, tui còn bao trọn gói các loại modules khác như là lodash, firebase, … ![](https://i2.wp.com/beautyoncode.com/wp-content/uploads/2021/11/Screen-Shot-2021-11-16-at-22.21.54.png?resize=768%2C474&ssl=1) Yên tâm, tui sẽ giúp bạn build hết mấy cái đứa ở trên đó về HTML, CSS, JS cho browser có thể hiểu và dựng trang web của bạn lên được.

Quá ngon rồi đúng chưa 😊

Nguồn:: [[Viblo]], [module bundler là gì? Parcel – một bundler nói “không” với config](https://viblo.asia/p/module-bundler-la-gi-parcel-mot-bundler-noi-khong-voi-config-gDVK2o9vZLj)
