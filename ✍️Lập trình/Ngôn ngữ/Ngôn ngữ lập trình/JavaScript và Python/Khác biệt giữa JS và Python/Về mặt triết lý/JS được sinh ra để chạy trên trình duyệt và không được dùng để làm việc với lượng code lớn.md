---
share: true
created: 2023-10-24T18:26
updated: 2024-02-01T21:39
---
Eric Lippert, một trong những implementers của JScript và ở trong hội đồng ECMA vào cuối thập kỷ 90 nói về  the mid to late 1990s, so I can provide some historical perspective here.
> Hãy nhớ lại mục đích thiết kế cơ bản của JS vào những năm 1990. **Làm cho con khỉ nhảy múa khi bạn rê chuột.** Chúng tôi coi inline expression script là bình thường, các khối script từ hai đến mười dòng là phổ biến, và quan niệm rằng ai đó có thể viết *hàng trăm dòng* trên một trang thực sự rất bất thường. Tôi nhớ lần đầu tiên tôi xem một chương trình JS mười ngàn dòng và câu hỏi đầu tiên của tôi dành cho những người đang nhờ tôi giúp đỡ vì nó quá chậm so với phiên bản C++ của họ là một phiên bản kiểu "bạn điên à?! 10 ngàn dòng code JS?! "

>Let's remember what the fundamental design purpose of JS was in the 1990s. **Make the monkey dance when you move the mouse**. We thought of inline expression scripts as normal, we thought of two-to-ten line script blocks as common, and the notion that someone might write a _hundred lines_ of script on a page was really very unusual. I remember the first time I saw a ten thousand line JS program and my first question to the people who were asking me for help because it was so slow compared to their C++ version was some version of "are you insane?! 10KLOC JS?!"

Nguồn:: [Why is Math.random() not designed to be cryptographically secure?](https://security.stackexchange.com/a/181623/94500)

JavaScript là dynamic typing, có nghĩa là một biến có thể nhận bất cứ kiểu dữ liệu nào (ví dụ integer sau đó lại gán thành string). Đây là một ưu điểm lớn với những script nhỏ (vài dòng đến vài chục dòng) vì nó giúp lập trình nhanh hơn. Nhưng với những ứng dụng lớn, có nhiều module, điều đó khiến việc xử lý dữ liệu nhiều khi rơi vào bế tắc do không biết dữ liệu của biến là gì (và nó đã bị thay đổi từ khi nào).

JavaScript không hỗ trợ static typing, là kiểu lập trình mà mỗi biến sẽ được khai báo kiểu dữ liệu trước và sẽ gặp lỗi nếu được gán giá trị có kiểu dữ liệu khác. TypeScript là ngôn ngữ cung cấp tính năng này.

Nguồn:: [So sánh nhỏ: TypeScript vs JavaScript | manhhomienbienthuy](https://manhhomienbienthuy.github.io/2022/03/01/so-sanh-nho-typescript-vs-javascript.html)

Trong khi đó, [[Python tập trung vào việc cung cấp một ngôn ngữ lập trình tổng quát, dễ đọc và dễ viết]] 
