---
share: true
created: 2023-10-24T18:26
updated: 2026-08-06T15:36
---
![image.png](https://images.viblo.asia/0ebf1f5d-a226-49df-93b3-d99465783033.png)

Mình là TUẤN hiện đang là một Full-stack Developer tại Tokyo 😉. Nếu bạn thấy Blog này hay xin hãy cho mình một like và đăng ký để ủng hộ mình nhé 😊.

Trong bài viết này, mình sẽ nói về Test. Và sẽ cung cấp cho bạn một cái nhìn tổng quan tốt về Test là gì và giới thiệu về cách bạn có thể triển khai nó trên các dự án JavaScript của mình. Ae sẽ sử dụng bốn công cụ rất phổ biến - Jest, Testing Library, Cypress và Supertest.

Đầu tiên khi nói về Test là gì, tại sao nên Test và các loại Test khác nhau có thể được thực hiện.

Sau đó, mình sẽ giới thiệu từng công cụ mà bạn sẽ sử dụng và cuối cùng sẽ đưa ra các ví dụ thực tế cho code VaniJS (JS thuần), ứng dụng React front-end và ứng dụng Node back-end.

GÉT GÔ!🤪

## Mục lục

- [Test là gì và tại sao nó có value](https://viblo.asia/posts/5pPLkG2GLRZ/edit#what-is-testing-and-why-is-it-valuable)
- [Các loại Test khác nhau](https://viblo.asia/posts/5pPLkG2GLRZ/edit#different-types-of-tests)
    - [Test thủ công và tự động](https://viblo.asia/posts/5pPLkG2GLRZ/edit#manual-vs-automated-testing)
    - [Test chức năng so với phi chức năng](https://viblo.asia/posts/5pPLkG2GLRZ/edit#functional-vs-non-functional-testing)
    - [Unit và Integration testing so với end to end testing (e2e)](https://viblo.asia/posts/5pPLkG2GLRZ/edit#unit-vs-integration-testing-vs-end-to-end-testing)
    - [Test hộp trắng so với hộp đen và hộp xám](https://viblo.asia/posts/5pPLkG2GLRZ/edit#white-box-vs-black-box-vs-grey-box-testing)
- [Khi nào Test](https://viblo.asia/posts/5pPLkG2GLRZ/edit#when-to-test)
- [Bộ công cụ](https://viblo.asia/posts/5pPLkG2GLRZ/edit#our-toolset)
    - [Jest là gì](https://viblo.asia/posts/5pPLkG2GLRZ/edit#what-is-jest)
    - [Thư viện Test là gì](https://viblo.asia/posts/5pPLkG2GLRZ/edit#what-is-testing-library)
    - [Cypress là gì](https://viblo.asia/posts/5pPLkG2GLRZ/edit#what-is-cypress)
    - [Supertest là gì](https://viblo.asia/posts/5pPLkG2GLRZ/edit#what-is-supertest)
    - [Tools](https://viblo.asia/posts/5pPLkG2GLRZ/edit#tools-roundup)
- [Cách Test code JS vani](https://viblo.asia/posts/5pPLkG2GLRZ/edit#how-to-test-vanilla-js-code)
- [Cách Test ứng dụng React front-end với thư viện Test Jest và React](https://viblo.asia/posts/5pPLkG2GLRZ/edit#how-to-test-a-front-end-react-app-with-jest-and-react-testing-library)
- [Cách Test ứng dụng React front-end với Cypress](https://viblo.asia/posts/5pPLkG2GLRZ/edit#how-to-test-a-front-end-react-app-with-cypress)
- [Cách Test ứng dụng Node back-end](https://viblo.asia/posts/5pPLkG2GLRZ/edit#how-to-test-a-back-end-node-app)
- [Cuối cùng](https://viblo.asia/posts/5pPLkG2GLRZ/edit#wrap-up)

# Test là gì và Tại sao nó có value

Kiểm thử là thực hiện Test xem một phần mềm có chạy như mong đợi hay không. Điều này thường được QA đảm bảo chất lượng, và nhằm mục đích giảm đến mức tối thiểu số lượng lỗi phát sinh trong quá trình sản xuất.

Bạn Test phần mềm để xác định lỗi, khoảng trống hoặc các yêu cầu còn thiếu và sửa những thứ đó trước khi deploy hoặc Release.

Test là một cách triệt để giúp cải thiện độ tin cậy của dự án, giúp bạn tiết kiệm thời gian sửa lỗi sau này và do đó giảm chi phí và cải thiện cơ hội để khách hàng hoàn toàn hài lòng với sản phẩm của bạn.

![BvIJ1M5-1](https://www.freecodecamp.org/news/content/images/2022/04/BvIJ1M5-1.gif)

# Các loại Test khác nhau

Test có thể được phân loại thành nhiều loại khác nhau theo nhiều yếu tố. Cá nhân mình nghĩ rằng có rất nhiều câu chuyện phiếm về chủ đề này, với hàng trăm thuật ngữ thường đề cập đến những thứ rất giống nhau. Vì vậy, hãy giữ nó đơn giản và chỉ xem xét các thuật ngữ phổ biến nhất và ý nghĩa của chúng.

Điều này sẽ giúp làm rõ nhiều cách mà một phần mềm có thể được Test và hiểu rõ hơn về các công cụ mà bạn sẽ trình bày ở phần sau.

### Test thủ công và tự động

Tùy thuộc vào các công cụ bạn sử dụng để Test phần mềm của mình, bạn có thể phân loại kiểm thử thành kiểm thử thủ công hoặc tự động .

Test thủ công là thực hiện "nhấp chuột vào chức năng trên màn hình" và Test thủ công tất cả các tính năng mà sản phẩm của bạn có, mô phỏng những gì người dùng thực tế sẽ làm.

Test tự động được thực hiện thông qua code, viết các chương trình Test cách ứng dụng của bạn chạy.

Có nhiều framework và thư viện Test mà bạn có thể sử dụng cho việc này. Khi nói đến kiểm thử chức năng (bạn sẽ xem điều đó có nghĩa là gì ở phần sau), hầu hết các thư viện đều hoạt động theo cách tương tự:

- Đầu tiên, bạn xác định đoạn code nào bạn muốn Test.
- Sau đó, bạn cung cấp đoạn code đó một số loại đầu vào hoặc thực hiện một hành động.
- Sau đó, bạn xác định đoạn code đó sẽ làm gì với đầu vào/hành động mà bạn đã thực hiện.
- Và cuối cùng, bạn sẽ so sánh những gì đoạn code đó thực sự đã làm với những gì bạn mong muốn.

Nếu nó làm đúng như những gì bạn đã mong muốn, thì bài Test đã passed. Nếu không, nó đã thất bại.

### Test chức năng so với phi chức năng

Test chức năng đề cập đến các tính năng thực tế của sản phẩm. Ví dụ: nếu bạn có một nền tảng blog, Test chức năng sẽ đảm bảo người dùng có thể tạo các bài viết mới, chỉnh sửa các bài viết đó, duyệt qua các bài viết do người khác viết, v.v.

Test phi chức năng đề cập đến bất kỳ điều gì không liên quan chặt chẽ đến các tính năng cốt lõi của sản phẩm. Và điều đó một lần nữa có thể được phân loại thành các danh mục khác nhau, ví dụ:

- Stress testing: test chịu tải của server chẳng hạn.
- Security testing: test xem một ứng dụng có dễ bị tấn công bởi các cuộc tấn công thông thường hay không.
- Accessibility testing: test xem một ứng dụng có được code theo cách mà có thể giễ dàng truy cập được cho những người khuyết tật hoặc những đối tượng khác nhau hay không.

### Unit vs Integration testing vs End-to-end testing

Một cách khác để phân loại Test là tùy thuộc vào mức độ rộng hay toàn diện của nó.

Unit Test nhằm mục đích Test các chức năng, method riêng lẻ hoặc các đoạn code nhỏ theo cách độc lập. Trong Unit test, các đoạn code nhỏ được Test theo cách riêng biệt.

Intergaration test  là cách các đoạn code riêng lẻ tương tác với nhau và hoạt động cùng nhau. Trong Test tích hợp, bạn ghép các mảnh lại với nhau và xem liệu chúng có tương tác chính xác hay không.

End-to-End Test, còn được gọi là E2E, thực thi các chương trình trong một môi trường giả lập mô phỏng hành vi người dùng thực tế. Lấy một trang web làm ví dụ, code của bạn sẽ mở trong một trình duyệt thực và tất cả các tính năng sẽ được thực thi giống như cách người dùng sử dụng chúng. Test E2E rất giống Test thủ công theo nghĩa đó, nhưng hoàn toàn tự động.

Test E2E là loại rộng nhất hoặc toàn diện nhất trong ba loại này, vì nó đánh giá toàn bộ các tính năng và hành vi, không phải các phần cụ thể trong code của bạn.

### Test hộp trắng so với hộp đen và hộp xám

Phân loại cuối cùng mà bạn sẽ thấy phụ thuộc vào mức độ các Test sẽ tập trung vào chi tiết triển khai hoặc trải nghiệm người dùng.

Giả sử bạn có một trang web đơn giản với một nút, khi được nhấp vào, nó sẽ mở ra một method. Trong code, nút có trình xử lý sự kiện nhấp chuột thực thi một chức năng. Hàm đó thay đổi lớp CSS của phần tử HTML method và điều đó sẽ hiển thị method trên màn hình.

Nói về kiểm thử "hộp trắng" khi bạn cần Test chi tiết triển khai. Ví dụ, theo mô hình này, bạn có thể Test xem lần nhấp vào nút có thực thi chức năng tương ứng hay không và sau khi thực thi chức năng, lớp CSS của phần tử method của bạn được thay đổi tương ứng.

Một cách khác để làm điều này là quên việc triển khai tất cả cùng nhau và chỉ cần Test xem method có được hiển thị sau khi nhấp vào nút hay không. Ae không quan tâm lớp CSS là gì, hoặc chức năng tương ứng có được thực thi hay không. Chỉ tập trung vào việc Test những gì người dùng sẽ cảm nhận được. Đó là Test "hộp đen ".

Và, như bạn có thể đoán, Test "hộp màu xám" chỉ là sự kết hợp của hai cách trước.

Một điều cuối cùng cần đề cập ở đây là các loại Test khác nhau này là không nhất thiết phải loại trừ lẫn nhau. Ý mình là, chúng có thể và thường được thực hiện cùng một lúc trên cùng các dự án.

Rất phổ biến là có cả Test thủ công và tự động, Test chức năng và phi chức năng, Test đơn vị và E2E ... Ý tưởng sẽ luôn là cố gắng dự đoán và giải quyết số lượng vấn đề lớn nhất có thể trong một thời thời gian và effort hợp lý.

# Khi nào Test

Thoạt đầu, đây có vẻ là một câu hỏi đơn giản, nhưng thực tế cũng có nhiều cách tiếp cận khác nhau cho vấn đề này.

Một số người thích Test ứng dụng của họ sau khi nó được phát triển đầy đủ. Những một số khác thích viết các Test case cùng lúc họ viết code ứng dụng và Test từng tính năng khi nó đang được phát triển.

Số còn lại thì thích viết các bài Test trước trước bất kỳ thứ gì khác, xác định theo cách này các yêu cầu tối thiểu để chương trình hoàn thành. Và sau đó, họ viết code ứng dụng theo cách passed các bài Test đó nhanh nhất có thể (điều này được gọi là [phát triển theo hướng Test hoặc TDD](https://en.wikipedia.org/wiki/Test-driven_development)). [TDD này mình cũng đã có nhắc đến trong bột bài viết của mình bạn có thể tham khảo.](https://tuan200tokyo.blogspot.com/2022/09/blog3-mot-so-mo-hinh-lap-trinh-pho-bien.html)

Sau khi bạn đã phát triển một ứng dụng hoặc toàn bộ tính năng và bạn đã có sẵn bộ Test (bộ Test là một nhóm các Test case của một tính năng cụ thể hoặc toàn bộ ứng dụng), một method phổ biến khác là chạy Test mỗi lần bạn thực hiện bất kỳ loại sửa đổi nào đối với code base, để chắc chắn rằng không vị trí nào bị bug sau khi thêm tính năng hoặc function mới.

Cuối cùng, nếu bạn có sẵn hệ thống [CI/CD](https://en.wikipedia.org/wiki/CI/CD) , bạn thường tự động hóa việc thực hiện các bài Test trước khi triển khai. Vì vậy, nếu bất kỳ Test nào không thành công, việc triển khai sẽ bị dừng và một số loại cảnh báo sẽ được gửi đi (tất nhiên luôn tốt hơn việc thấy ứng dụng của bạn bắt lửa trên sản phẩm 🔥😱).

Tương tự như với các loại kiểm thử, việc Test các ứng dụng tại các thời điểm khác nhau là điều thường thấy. Mỗi công ty thường có phương pháo Test riêng hoặc phù hợp với nhu cầu của dự án cụ thể nào đó.

# Bộ công cụ của Test

Được rồi, bây giờ bạn đã rõ ràng hơn một chút về Test là gì và các loại Test có thể thực hiện, hãy xem các công cụ có thể sử dụng trong các ví dụ của bạn.

Như đã đề cập ở trước, có rất nhiều thư viện khác nhau để lựa chọn chạy các Test case. Riêng mình chọn bốn cái này vì chúng là một trong những ứng dụng phổ biến nhất khi nói đến các ứng dụng JavaScript, nhưng bạn phải luôn nhớ rằng có rất nhiều công cụ để test ngoài kia đang chờ bạn khám và phá. 😉

## Jest là gì

[Jest](https://jestjs.io/) là một test-runner Test JavaScript. Test-runner là một phần mềm cho phép bạn chạy Test để đánh giá ứng dụng của mình. [Jest](https://jestjs.io/) là một dự án open source code được duy trì bởi Meta (trước đây là Facebook) và có open source code đầu tiên vào năm 2014.

Dù sao thì ... bạn cũng có thể sử dụng Jest trong các dự án sử dụng [Babel](https://babeljs.io/) , [TypeScript](https://www.typescriptlang.org/) , [Node.js](https://nodejs.org/en/) , [React](https://reactjs.org/) , [Angular](https://angular.io/) , [Vue.js](https://vuejs.org/) , [Svelte](https://svelte.dev/) và các công nghệ khác. Ae có thể cài đặt Jest thông qua NPM giống như bất kỳ thư viện nào và nó yêu cầu rất ít cấu hình để bắt đầu.

Jest được cài đặt theo mặc định khi thiết lập ứng dụng React với [create-react-app](https://create-react-app.dev/) .

Jest thường còn được gọi là Framework Test, vì nó đi kèm với nhiều tính năng tích hợp khác bên cạnh việc chỉ chạy Test (điều này không đúng với tất cả những Test-runer). Một số tính năng đó là:

- Assertion library: Jest đi kèm với rất nhiều chức năng và method tích hợp sẵn mà bạn có thể sử dụng để asserting code của mình (asserting về cơ bản có nghĩa là Test xem một đoạn code có hoạt động như mong đợi hay không).
- Snapshot testing: Jest cho phép bạn sử dụng ảnh chụp nhanh, là một cách để chụp một đối tượng lớn và lưu trữ nó trong bộ nhớ để sau này bạn có thể so sánh nó với một thứ khác.
- Code coverage: Jest cho phép bạn xuất các báo cáo cụ thể của các bài Test. Các báo cáo này cho biết tỷ lệ phần trăm code của bạn hiện đang được Test và thậm chí bạn có thể thấy các dòng code chính xác hiện không được Test.
- Mocking library: Jest cũng hoạt động giống như một thư viện Moking theo nghĩa là nó cho phép bạn mô phỏng dữ liệu (như một hàm hoặc một mô-đun) và sử dụng nó trong các bài Test của bạn.

Một số lựa chọn thay thế nổi tiếng cho Jest là [Mocha](https://mochajs.org/) , [Jasmine](https://jasmine.github.io/) và [Karma](https://karma-runner.github.io/latest/index.html) .

Đây là [một đoạn video nhỏ](https://www.youtube.com/watch?v=SyHzgcFefBk) giải thích Jest là gì.

## Thư viện Test là gì?

Thư viện Test không phải là một Test-runner, mà là một tập hợp các tiện ích sẽ hoạt động cùng với một Test-runner như Jest hoặc Mocha. Tiện ích này là những công cụ bạn có thể sử dụng để Test code của mình một cách dễ dàng và tập trung sâu hơn vào trải nghiệm người dùng (Test hộp đen).

Thư viện Test được phát triển bởi [Kent C Dodds](https://kentcdodds.com/) (người cũng tình cờ là một trong những giáo viên JS giỏi nhất trên trái đất, vì vậy mình khuyên bạn thử ghé vào trang của Ảnh và chil).

Trích dẫn [các tài liệu chính thức:](https://testing-library.com/)

_"Testing Library là một giải pháp rất nhẹ để Test mà không có tất cả các thứ khác dùng để triển khai proect của bạn._ _Các tiện ích chính mà nó cung cấp liên quan đến việc truy vấn các nút tương tự như cách người dùng tìm thấy chúng. Bằng cách này, thư viện Test giúp đảm bảo các Test của bạn cung cấp cho bạn tự tin hơn vào code của mình."_

Giải thích đơn giản hơn thì, với thư viện kiểm thử, bạn có thể Test các phần tử giao diện người dùng (như một Text, một Button, một thẻ Div ...) thay vì Test code chịu trách nhiệm hiển thị giao diện người dùng.

Nguyên tắc đằng sau thư viện là:

_"Các bài Test của bạn càng giống với cách phần mềm của bạn được sử dụng, chúng càng có thể mang nhiều lợi ích cho bạn tự tin hơn với code mình hơn."_

... và đó chính xác là ý của bạn khi Test "hộp đen". 😉

Testing Library thực chất là một tập hợp các thư viện, mỗi thư viện được tạo ra để đạt được cùng một mục tiêu nhưng được điều chỉnh để hoạt động với các công nghệ khác nhau như React, Angular, Vue, Svelte, React Native và hơn thế nữa ... Đó là lý do tại sao bạn có thể nghe thấy "React-testing-library " hoặc "Vue-testing-library ". Nó giống nhau nhưng được điều chỉnh để hoạt động với các công nghệ khác nhau.

Thư viện React-testing-library được cài đặt theo mặc định khi thiết lập ứng dụng React với [create-react-app](https://create-react-app.dev/).

Một thay thế cho thư viện Test là [Enzyme](https://enzymejs.github.io/enzyme/) (một bộ tiện ích Test giao diện người dùng được phát triển bởi Airbnb).

## Cypress là gì?

Cypress là một trình open source test-runner cho phép bạn thực hiện các dự án của mình trong một trình duyệt tự động, giống như cách người dùng làm.

Với Cypress, bạn có thể lập trình trình duyệt sẽ làm gì (như truy cập URL, nhấp vào nút, hoàn thành và gửi biểu mẫu ...) và kiểm tra xem mỗi hành động có khớp với phản hồi tương ứng hay không.

Điều thú vị về điều này là Test giống RẤT NHIỀU những gì người dùng sẽ trải nghiệm. Và vì toàn bộ quan điểm của việc tạo ra phần mềm là người dùng, bạn càng gần với quan điểm của họ, bạn càng nên bắt kịp những lỗi có ý nghĩa nhất trong code của bạn. (Thêm nữa, thật tuyệt khi thấy một trình duyệt tự động duyệt qua toàn bộ ứng dụng của bạn chỉ trong vài giây ... 🤓)

Một tính năng hay khác của Cypress là "Time travel". Trên trình duyệt tự động của Cypress, bạn có thể xem tất cả các Test case mà bạn đã viết và chỉ cần di chuột qua chúng để xem ảnh chụp nhanh bằng giao diện cực kỳ trực quan. Đó là một điều rất hữu ích để hiểu rõ hơn về những component đang bị vỡ  hoặc code bị tèo.

Mặc dù nó có thể được sử dụng để Unit Test và Migration Test, Cypress chủ yếu được sử dụng để Test đầu cuối vì nó có thể dễ dàng đánh giá các tính năng hoàn chỉnh trong vài giây.

Bạn có thể sử dụng Cypress để Test bất kỳ thứ gì chạy trong trình duyệt, vì vậy bạn có thể dễ dàng triển khai nó trên React, Angular, Vue, v.v.

Không giống như Jest và React-Testing-Library, Cypress không được cài đặt sẵn ứng dụng creat-react-app. Nhưng bạn có thể dễ dàng cài đặt nó với NPM hoặc trình quản lý package mà bạn lựa chọn.

Một số lựa chọn thay thế cho Cypress là [Selenium](https://www.selenium.dev/) và [Puppeteer](https://pptr.dev/) .

[Đây là một video hay của Fireship giải thích Cypress là gì và nó hoạt động như thế nào.](https://www.youtube.com/watch?v=BQqzfHQkREo)

Comment bên lề: ... và mỗi khi mình nói về Cypress [, điều này lại hiện lên trong tâm trí mình](https://www.youtube.com/watch?v=BV3CYz34ziE) . 😎

## Supertest là gì?

[Supertest](https://github.com/visionmedia/supertest) là một thư viện mô phỏng các yêu cầu HTTP. Thật tiện lợi khi Test các ứng dụng Node back-end cùng với Jest (như bạn sẽ thấy trong các ví dụ dưới đây).

### Tóm lại của phần giới thiệu về Test

Như một bản tóm tắt nhanh về chủ đề này:

- Jest là thư viện mà bạn sẽ sử dụng để viết và chạy các bài Test cho JavaScript.
- Thư viện kiểm thử hoạt động cùng với Jest và cung cấp cho bạn các chức năng và method để Test giao diện người dùng trực tiếp, và bỏ qua phần code đằng sau nó (Test hộp đen).
- Cypress chạy ứng dụng của bạn trong một trình duyệt mô phỏng và Test xem các hành động được thực hiện trong giao diện người dùng có phản hồi như mong đợi hay không.
- Supertest là một thư viện mô phỏng các yêu cầu HTTP và nó có thể được sử dụng cùng với Jest để Test các ứng dụng back-end.

Bây giờ bạn hãy bắt đầu với phần thú vị ...

![giphy-2](https://www.freecodecamp.org/news/content/images/2022/04/giphy-2.gif)

# Cách Test code Vanilla JS (Code JS thuần)

Được rồi, hãy bắt đầu bằng cách Test một số code JS vani đơn giản. Ý tưởng ở đây là xem cách bạn có thể triển khai Jest trong dự án của mình và tìm hiểu những điều cơ bản về cách hoạt động của nó.

Hãy bắt đầu bằng cách tạo một thư mục mới trong máy của bạn và tạo một ứng dụng Node với `npm init -y`. Sau đó cài đặt Jest bằng cách chạy `npm i -D jest`( `-D là` lưu nó dưới dạng phụ thuộc phát triển).

Bây giờ bạn sẽ thấy một cái gì đó như thế này trong tệp của bạn `package.json`:.`"devDependencies": { "jest": "^27.5.1" }`

Và nói về nó, trong package.json của bạn, hãy thay thế tập lệnh test của bạn bằng `"test": "jest"`. Điều này sẽ cho phép bạn chạy Test của mình sau này bằng cách chạy `npm test`. 

Toàn bộ `package.json`tệp của bạn sẽ trông giống như sau:

```json
{
  "name": "vanillatesting",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "jest"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "jest": "^27.5.1"
  }
}
```

Tuyệt vời, bạn đã sẵn sàng để viết code JS mà bạn thực sự có thể Test! Tạo một tệp index.js và gõ quả code này vào đó:

```js
// index.js
function isPalindrome(string) {
  // O(n)
  // Put a pointer at each extreme of the word and iterate "inwards"
  // At each iteration, check if the pointers represent equal values
  // If this condition isn't accomplished, the word isn't a palindrome
  let left = 0;
  let right = string.length - 1;

  while (left < right) {
    if (string[left] === string[right]) {
      left += 1;
      right -= 1;
    } else return false;
  }

  return true;
}
```

Chức năng này là một trình Test [palindrome](https://en.wikipedia.org/wiki/Palindrome). Nó nhận một string làm tham số và trả về `true` nếu string đó là palindrome và `false` nếu không phải. (Đây là một câu hỏi phỏng vấn kỹ thuật cổ điển, nhưng đó là nội dung cho một bài viết khác .🤫)

Tuyệt vời, vì vậy bây giờ bạn hãy Test chức năng này và xem nó có hoạt động như mong đợi hay không. Hãy tạo một tệp có tên `index.test.js`.

Tệp này là nơi bạn sẽ viết các bài Test của mình. Hậu tố bạn đang sử dụng ( `.test.js`) rất quan trọng ở đây, vì Jest sẽ tự động xác định các tệp .test và thực thi chúng khi bạn ra lệnh cho Jest Test dự án của bạn.

Jest cũng xác định các tệp bằng hậu tố .spec, như `index.spec.js` (Từ "spec" thường có nghĩa là đề cập đến các yêu cầu của dự án của bạn). Cá nhân mình thích .test vì nó cảm thấy rõ ràng hơn đối với mình, nhưng cả hai đều hoạt động như nhau.

Bây giờ bạn hãy viết các bài Test đầu tiên của bạn! Đặt cái này trong tệp index.test.js

```js
// index.test.js
isPalindrome = require('./index.js');

test('neuquen is palindrom', () => {
  expect(isPalindrome('neuquen')).toBe(true);
});

test('bariloche is not palindrom', () => {
  expect(isPalindrome('bariloche')).toBe(false);
});
```

Hãy tóm tắt lại những gì bạn đang làm:

1. Yêu cầu chức năng muốn Test: `isPalindrome = require('./index.js')`
2. Hàm `test()` được cung cấp bởi Jest và bên trong nó, bạn sẽ đặt đoạn code mà bạn muốn Jest thực thi.
3. `test()` có hai tham số. Đầu tiên là mô tả Test, là một tên đặc biệt sẽ hiển thị trên bảng điều khiển của bạn khi chạy Test.
4. Tham số thứ hai là một callback, chứa code Test thực tế.
5. Trong lần gọi lại này, bạn đang gọi hàm expect()  (cũng được cung cấp bởi Jest). `expect()` lấy hàm của bạn làm tham số, chính nó đang nhận một tham số mà bạn đã tạo.
6. Cuối cùng, bạn chain (ý là chấm chấm chấm thành 1 dây vậy đó người ta gọi là chain) hàm .toBe() (cũng do Jest cung cấp) và dưới dạng tham số, bạn chuyển nó value mà bạn mong đợi `isPalindrome()` trả về cho mỗi trường hợp. ("neuquen" là một palindrome nên hàm của bạn sẽ trả về `true`, còn "bariloche" thì không, vì vậy nó sẽ trả về `false`.)

Một trong những điều mình thích nhất ở Jest là cách thiết lập nó rất dễ dàng. Một điều khác mà mình rất thích là cách tự giải thích cú pháp của nó. Lưu ý rằng bạn có thể dễ dàng hiểu các bài Test của bạn sẽ đánh giá những gì chỉ bằng cách đọc chúng.👌

Bây giờ bạn hãy thử điều này! Nếu bạn chạy `npm test` trong terminal sẽ nhận được kết quả  sau:

```
// console
  > jest PASS 
  ./index.test.js
  ✓ neuquen is palindrom (1 ms)
  ✓ bariloche is not palindrom
  
  Test Suites: 1 passed, 1
  total Tests:       2 passed, 2
  total Snapshots:   0
  total Time:        0.244 s
  Ran all test suites.
```

Xin chúc mừng, bạn vừa passed bài Test Jest đầu tiên của mình.

![mr-miyagi-gật-1](https://www.freecodecamp.org/news/content/images/2022/04/mr-miyagi-nod-1.gif)

![Let's-get-this-party-started-yeah-1](https://www.freecodecamp.org/news/content/images/2022/04/lets-get-this-party-started-yeah-1.gif)

Để xem một bài Test thất bại trông như thế nào, hãy thay đổi chức năng của bạn bằng cách chỉnh sửa các dòng return.

```js
function isPalindrome(string) {
  // O(n)
  // Put a pointr at each extreme of the word and iterate "inwards"
  // At each iteration, check if the pointers represent equal values
  // If this condition isn't accomplished, the word isn't a palindrome
  let left = 0;
  let right = string.length - 1;

  while (left < right) {
    if (string[left] === string[right]) {
      left += 1;
      right -= 1;
    } else return 1;
  }

  return 2;
}
```

Bây giờ bạn sẽ nhận được một cái gì đó như thế này:

```
// console
  > vanillatesting@1.0.0 test
  > jest
  
  FAIL  ./index.test.js
  ✕ neuquen is palindrom (4 ms)
  ✕ bariloche is not palindrom
  
  ● neuquen is palindrom
  
  expect(received).toBe(expected) // Object.is equality
  
  Expected: true
  Received: 2
  
  3 | // describe('isPalindrome function', () => {
  4 |   test('neuquen is palindrom', () => {
  > 5 |     expect(isPalindrome("neuquen")).toBe(true)
  |                                     ^
  6 |   })
  7 |
  8 |   test('bariloche is not palindrom', () => {
  
  at Object.<anonymous> (index.test.js:5:37)
  
  ● bariloche is not palindrom
  
  expect(received).toBe(expected) // Object.is equality
  
  Expected: false
  Received: 1
  
  7 |
  8 |   test('bariloche is not palindrom', () => {
  >  9 |     expect(isPalindrome("bariloche")).toBe(false)
  |                                       ^
  10 |   })
  11 | // })
  12 |
  
  at Object.<anonymous> (index.test.js:9:39)
  
  Test Suites: 1 failed, 1 total
  Tests:       2 failed, 2 total
  Snapshots:   0 total
  Time:        0.28 s, estimated 1 s
  Ran all test suites.
```

Bạn đã nhận được một mô tả hay về những bài Test không thành công và chúng đã thất bại tại thời điểm nào. Trong trường hợp của chúng không thành công khi bạn xác nhận các value trả về.

Điều này rất hữu ích và bạn nên chú ý đến những mô tả này, vì một số bài Test của bạn có thể thất bại vì chúng được viết không chính xác. Và bạn thường không viết các Test cas cho các Test case của mình... 😅 Vì vậy, khi bạn thấy Test case không đạt, trước tiên hãy Test xem nó có hoạt động như mong đợi hay không và sau đó xem lại code thực của bạn.

Bây giờ hãy thêm và Test một chức năng khác để hiển thị thêm một số tính năng của Jest:

```js
// index.js
function twoSum(nums, target) {
  // O(n)
  // Iterate the array once
  // At each iteration, calculate the value needed to get to the target, which is target - currentValue
  // If the neededValue exists in the array, return [currentValue, neededValue], else continue iteration
  for (let i = 0; i < nums.length; i++) {
    const neededNum = target - nums[i];
    if (nums.indexOf(neededNum) !== -1 && nums.indexOf(neededNum) !== i) return [nums[i], nums[nums.indexOf(neededNum)]];
  }
  return false;
}

module.exports = {isPalindrome, twoSum};
```

Đây là một câu hỏi phỏng vấn kinh điển khác. Hàm nhận hai tham số, một array số và một số value. Nó xác định xem có hai số trong array có tổng bằng value thứ 2 hay không. Nếu hai value tồn tại trong array, nó trả về chúng trong một array và nếu không, nó trả về false.

Bây giờ bạn hãy viết một số bài Test cho điều này:

```js
({isPalindrome, twoSum} = require('./index.js'));

...

test('[2,7,11,15] and 9 returns [2, 7]', () => {
  expect(twoSum([2, 7, 11, 15], 9)).toEqual([2, 7]);
});

test('[3,2,4] and 6 returns [2, 4]', () => {
  expect(twoSum([3, 2, 4], 6)).toEqual([2, 4]);
});

test('[3,2,4] and 10 returns false', () => {
  expect(twoSum([3, 2, 4], 10)).toBe(false);
});
```

Thấy rằng cấu trúc gần như giống nhau, ngoại trừ bạn đang sử dụng một trình so sánh khác trong hai trong số `toEqual().`

So sánh là chức năng mà Jests cung cấp cho bạn để đánh giá các value. Có rất nhiều loại phù hợp có thể được sử dụng cho nhiều case khác nhau.

Ví dụ, `.toBe()` được sử dụng để đánh giá các nguyên thủy như string, số hoặc boolean. `toEqual()` được sử dụng để đánh giá các đối tượng.

Nếu bạn cần so sánh value trả về với một số bạn có thể sử dụng `.toBeGreaterThan()`, `toBeGreaterThanOrEqual()`v.v.

Để xem danh sách đầy đủ tham khảo [tài liệu](https://jestjs.io/docs/using-matchers)  này.

Nếu bạn chạy Test của mình sẽ nhận được kết quả sau:

```
> vanillatesting@1.0.0 test
  > jest
  
  PASS  ./index.test.js
  ✓ neuquen is palindrom (2 ms)
  ✓ bariloche is not palindrom
  ✓ [2,7,11,15] and 9 returns [2, 7] (1 ms)
  ✓ [3,2,4] and 6 returns [2, 4]
  ✓ [3,2,4] and 10 returns false (1 ms)
  
  Test Suites: 1 passed, 1 total
  Tests:       5 passed, 5 total
  Snapshots:   0 total
  Time:        0.256 s, estimated 1 s
  Ran all test suites.
```

Điều đó thật tuyệt, nhưng kết quả Test của bạn trông hơi lộn xộn. Và khi bộ Test của bạn phát triển và lớn dần lên, có lẽ sẽ khó xác định từng kết quả riêng biệt.

Để giúp bạn giễ thở hơn, Jest cung cấp cho bạn một hàm describe()mà bạn có thể sử dụng để nhóm các bài Test lại với nhau và hiển thị kết quả theo một cách có hệ thống hơn. Tham khảo vd dưới:

```js
({isPalindrome, twoSum} = require('./index.js'));

describe('isPalindrome function', () => {
  test('neuquen is palindrom', () => {
    expect(isPalindrome('neuquen')).toBe(true);
  });

  test('bariloche is not palindrom', () => {
    expect(isPalindrome('bariloche')).toBe(false);
  });
});

describe('twoSum function', () => {
  test('[2,7,11,15] and 9 returns [2, 7]', () => {
    expect(twoSum([2, 7, 11, 15], 9)).toEqual([2, 7]);
  });

  test('[3,2,4] and 6 returns [2, 4]', () => {
    expect(twoSum([3, 2, 4], 6)).toEqual([2, 4]);
  });

  test('[3,2,4] and 10 returns false', () => {
    expect(twoSum([3, 2, 4], 10)).toBe(false);
  });
});
```

Tham số đầu tiên là mô tả mà bạn muốn hiển thị cho nhóm Test và tham số thứ hai là một callback chứa các thứ mà bạn muốn test. Bây giờ nếu bạn chạy lại npm test thì sẽ nhận được điều này 😎:

```
// console
  > vanillatesting@1.0.0 test
  > jest
  
  PASS  ./index.test.js
  isPalindrome function
  ✓ neuquen is palindrom (2 ms)
  ✓ bariloche is not palindrom
  twoSum function
  ✓ [2,7,11,15] and 9 returns [2, 7] (1 ms)
  ✓ [3,2,4] and 6 returns [2, 4]
  ✓ [3,2,4] and 10 returns false
  
  Test Suites: 1 passed, 1 total
  Tests:       5 passed, 5 total
  Snapshots:   0 total
  Time:        0.216 s, estimated 1 s
  Ran all test suites.
```

# Cách Test một ứng dụng React Front-end với Thư viện Test Jest và React

Bây giờ bạn đã biết những điều cơ bản về Jest, hãy cùng xem cách bạn có thể kết hợp nó với thư viện Testing để Test một ứng dụng React.

Đối với điều này, bạn sẽ sử dụng một ví dụ đơn giản. Chỉ là một trang có text ngẫu nhiên, một button chuyển đổi một text thành đoạn text khác, một input text và một nút chuyển đổi để in đoạn text ra.

![Ghi-2022-04-23-at-21.11.24](https://www.freecodecamp.org/news/content/images/2022/04/Recording-2022-04-23-at-21.11.24.gif)

Hãy lưu ý rằng bạn sẽ sử dụng [create-react-app](https://create-react-app.dev/) để tạo ứng dụng này (có cài đặt thư viện Jest và Testing theo mặc định). Nếu không sử dụng create-react-app, bạn có thể cần cài đặt cả hai thư viện và thêm một số cấu hình bổ sung.

Bạn sẽ không thấy bất kỳ code React nào ở đây, bạn chỉ tập trung vào các bài Test. Cố gắng lên bạn thử tự mình code ra một đoàn code mẫu xem nào sau đó test nó bằng cách mình đã chia sẽ. Giờ mình đưa code cho bạn rồi bạn copy rồi test chả ý nghĩa gì.

Cấu trúc thư mục của dự án của bạn như sau:

```
> src
  > components
  - About.jsx
  - App.jsx
  - Index.js
  - setupTests.js
```

Tệp `setupTests.js n`ó được tạo theo mặc định bằng create-react-app với nội dung này:

```js
// jest-dom adds custom jest matchers for asserting on DOM nodes.
// allows you to do things like:
// expect(element).toHaveTextContent(/react/i)
// learn more: https://github.com/testing-library/jest-dom
import '@testing-library/jest-dom';
```

Nó nhập thư viện jest-dom được cung cấp bởi thư viện Test (là import global luôn nhé), cung cấp cho bạn các công cụ và hàm mà bạn có thể sử dụng để Test DOM (như `toHaveTextContent(), toBeInTheDocument()`, v.v.).

Về các tệp Test của bạn, trên thực tế thì mỗi component sẽ có 1 file test hoặc nhiều hơn 1 file test.

Về vị trí đặt chúng, hai method phổ biến là đặt tất cả chúng cùng nhau trong một thư mục duy nhất, giống như `__tests__` hoặc tương tự, hoặc để từng tệp Test trong cùng một thư mục với các component mà nó đang Test.

Mình thích cái sau hơn vì mình thường chuyển từ code component sang code Test, và thật tuyệt khi có chúng ở gần nhau LOVE. Nhưng nó không quan trọng. Miễn là bạn sử dụng các hậu tố `.test` hoặc `.spec`, Jest vẫn sẽ xác định và chạy các tệp.

Sau khi tạo các tệp Test của bạn, cấu trúc thư mục của bạn sẽ trông như thế này:

```
> src
  > components
  - About.jsx
  - About.test.jsx
  - App.jsx
  - Index.js
  - setupTests.js
```

Okêi! Hãy bắt đầu bằng cách Test Component About của bạn.

Trước tiên, hãy Test xem nó có hiển thị chính xác không, như sau:

```js
// About.test.jsx
import {render, screen} from '@testing-library/react';
import About from './About';

describe('About', () => {
  test('About renders correctly', () => {
    render(<About />);
    expect(screen.getByText("I'm the about page!"))
    .toBeInTheDocument();
  });
});
```

Hàm `render` lấy một compoent React làm tham số và hiển thị nó để bạn có thể  Test nó.

`screen` là một đối tượng đi kèm với rất nhiều truy vấn mà bạn có thể sử dụng để Test giao diện người dùng trực tiếp, bỏ qua chi tiết triển khai và tập trung vào những gì người dùng thực sự sẽ thấy.

- Nhập Component `About`:`import About from './About'`
- Sử dụng các hàm `describe` và `test` Jest  như đã đề cập trước đó.
- Import Component `About`:`render( <About/> )`
- bạn sử dụng hàm expect Jest và một tham số, bạn sử dụng đối tượng screen được cung cấp bởi thư viện Test. Và sử dụng truy vấn getByText của nó, truy vấn này quét Component React để tìm văn bản mà bạn truyền làm tham số.
- `.toBeInTheDocument()` trình so sánh của thư viện Test, công cụ này chỉ Test xem kết quả truy vấn trước đó có được hiển thị hay không.

Sau đó, bạn có thể Test xem nút bật tắt "Chuyển state" có hoạt động chính xác hay không, như sau:

```jsx
// About.test.jsx
import {render, screen} from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import About from './About';

describe('About', () => {
  test('Switch state works correctly', async () => {
    render(<About />);
    expect(screen.getByText("It's on!")).toBeInTheDocument();
    userEvent.click(screen.getByText('Switch state'));
    expect(screen.getByText("It's rolling!")).toBeInTheDocument();
    userEvent.click(screen.getByText('Switch state'));
    expect(screen.getByText("It's on!")).toBeInTheDocument();
  });
});
```

Một tiện ích bổ sung được gọi là `userEvent`. Đây là một đối tượng chứa nhiều method mà bạn có thể sử dụng để mô phỏng các sự kiện do người dùng kích hoạt, như nhấp chuột, di chuột, ghi đầu vào, v.v.

- Trước tiên, bạn Test xem string mặc định có được hiển thị hay không: `expect(screen.getByText("It's on!")).toBeInTheDocument()`
- Sau đó, bạn mô phỏng một cú nhấp chuột và Test xem string có thay đổi trên màn hình hay không:

```js
userEvent.click(screen.getByText('Switch state'));
expect(screen.getByText("It's rolling!")).toBeInTheDocument();
```

Và cuối cùng, bạn mô phỏng một lần nhấp khác và Test xem string có đảo ngược trở lại mặc định hay không:

```js
userEvent.click(screen.getByText('Switch state'))
expect(screen.getByText("It's on!")).toBeInTheDocument()
```

Để kết thúc, bạn sẽ viết một bài Test khác để xác minh rằng kiểu nhập văn bản và nút bật tắt của nó hoạt động chính xác.

```js
import {render, screen} from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import About from './About';

describe('About', () => {
  // ...
  test('Input works correctly', async () => {
    render(<About />);

    userEvent.type(screen.getByTestId('testInput'), 'Testing the test');
    userEvent.click(screen.getByText('Print input'));

    expect(screen.getByText('Testing the test')).toBeInTheDocument();

    userEvent.click(screen.getByText('Print input'));
    expect(screen.queryByText('Testing the test')).not.toBeInTheDocument();
  });
});
```

- Một lần nữa, bạn sử dụng `userEvent` để mô phỏng đoạn text được viết vào phần tử input: `userEvent.type(screen.getByTestId("testInput"), "Testing the test")`
- Sau đó, bạn mô phỏng một cú click vào button bật tắt và test xem đoạn text có trong tài liệu hay không:

```js
userEvent.click(screen.getByText('Print input'));
expect(screen.getByText('Testing the test')).toBeInTheDocument();
```

- Và bạn kết thúc bằng cách mô phỏng một lần nhấp khác và Test xem đoạn text không còn nữa hay không:
    
    userEvent.click(screen.getByText('Print input'));expect(screen.getByText('Testing the test')).toBeInTheDocument();
    

Có thể thấy các tiện ích được cung cấp bởi các thư viện Testing và việc kết hợp chúng với Jest dễ dàng như thế nào. 🤓

Bạn có thể chạy tệp Test cụ thể này bằng cách chạy `npm test -- About.test.jsx` và đây là kết quả bạn nhận được:

```
// console
  PASS  src/components/About.test.jsx
  About
  ✓ About renders correctly (34 ms)
  ✓ Switch state works correctly (66 ms)
  ✓ Input works correctly (67 ms)
  
  Test Suites: 1 passed, 1 total
  Tests:       3 passed, 3 total
  Snapshots:   0 total
  Time:        0.997 s, estimated 1 s
  Ran all test suites matching /About.test.jsx/i.
```

Tính năng Jest cuối cùng mà mình muốn giới thiệu cho bạn là test coverage.  
Bạn có thể nhận được một báo cáo phạm vi mà mình đã Test được bằng cách chạy `npm test -- --coverage`.

Điều này sẽ chạy các Test của bạn bình thường và ở cuối báo cáo kết quả, bạn sẽ thấy một cái gì đó tương tự như sau (Nhìn khá trực quan đấy chư nhở):

```
// console
  ...
  
  ----------------|---------|----------|---------|---------|-------------------
  File            | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s 
  ----------------|---------|----------|---------|---------|-------------------
  All files       |      75 |      100 |   85.71 |      70 |                   
  src            |       0 |      100 |       0 |       0 |                   
  App.jsx       |       0 |      100 |       0 |       0 | 7                 
  App.t.js      |       0 |        0 |       0 |       0 |                   
  index.js      |       0 |      100 |     100 |       0 | 5-6               
  src/components |     100 |      100 |     100 |     100 |                   
  About.jsx     |     100 |      100 |     100 |     100 |                   
  ----------------|---------|----------|---------|---------|-------------------
```

Trong báo cáo, bạn có thể thấy rằng component About.jsx của bạn đã được bao phủ hoàn toàn, nhưng các tệp `App.jsx` và tệp index.js của bạn đang không được Test.

Tính năng này rất tiện dụng khi làm việc trên các dự án lớn và bạn muốn nhanh chóng biết liệu hầu hết code của mình có đang được Test chính xác hay không.

# Cách Test ứng dụng Front-end React với Cypress

Bạn đã nói rất nhiều về Jest, vì vậy bây giờ bạn hãy xem cách mà  có thể  Test ứng dụng của mình bằng Cypress.

Bắt đầu cài đặt Cypress bằng cách chạy `npm i -D cypress`.

Cái này sẽ thêm vào file `package.json`:

```json
"devDependencies": {
  "cypress": "^9.5.4"
  }
```

Sau đó, bạn sẽ chạy `npx cypress open`. Thao tác này sẽ mở trình duyệt Cypress và tạo một thư mục `cypress` trong dự án của bạn. Trong thư mục này, bạn sẽ tìm thấy các ví dụ, tài liệu và các tùy chọn cấu hình.

Bạn cũng sẽ tìm thấy một thư mục "integration", trong đó bạn phải thực hiện code các Test case của mình. Vì vậy, hãy tạo tệp About.test.js của bạn trong thư mục đó và sao chép các ví dụ Test tương tự mà bạn đã làm với Jest:

```js
// About.test.js
describe('AboutPage', () => {
  it('Renders correctly', () => {
    cy.visit('http://localhost:3000/about');
    cy.contains("I'm the about page!");
  });

  it('switch btn toggles text', () => {
    cy.contains("It's on!");
    cy.get('.switchBtn').click();
    cy.contains("It's rolling!");
    cy.get('.switchBtn').click();
    cy.contains("It's on!");
  });

  it('Input works correctly', () => {
    cy.get('.testInput').type('Testing the test');
    cy.get('.printInputBtn').click();
    cy.contains('Testing the test');

    cy.get('.printInputBtn').click();
    cy.contains('Testing the test').should('not.exist');
  });
});
```

- Chức năng describe hoạt động giống như trong jest.
- `it()` giống như chức năng test() mà bạn đã thấy trước đây.
- Trong Test case đầu tiên, bạn yêu cầu trình duyệt truy cập vào URL của ứng dụng và Test xem văn bản tương ứng có được hiển thị hay không:

```js
cy.visit('http://localhost:3000/about');
cy.contains("I'm the about page!");
```

- Sau đó, bạn Test xem đoạn text mà mình dự tính sẽ đổi sau khi click chuột thì mặc định có được hiển thị hay không, mô phỏng một lần nhấp và Test xem nó có thay đổi tương ứng không:

```js
cy.contains("It's on!");
cy.get('.switchBtn').click();
cy.contains("It's rolling!");
cy.get('.switchBtn').click();
cy.contains("It's on!");
```

- Và để kết thúc, bạn mô phỏng một input text, mô phỏng một cú click chuột và Test xem input text vào có được hiển thị hay không:

```js
cy.get('.testInput').type('Testing the test');
cy.get('.printInputBtn').click();
cy.contains('Testing the test');

cy.get('.printInputBtn').click();
cy.contains('Testing the test').should('not.exist');
```

Cú pháp hơi khác so với Jest, nhưng ý tưởng và cấu trúc thì khá giống nhau.🤙

Bây giờ nếu bạn chạy lại npx cypress open, một cửa sổ sẽ mở ra với nội dung này:

![image.png](https://images.viblo.asia/6c9adf2e-8655-477d-8d10-3ad3513dd292.png)

Bạn có thể nhấp vào "Run integration spec" và Test của bạn sẽ tự động chạy trong trình duyệt giả. Sau khi chạy Test, trên bảng điều khiển bên trái, bạn sẽ thấy kết quả:

![image.png](https://images.viblo.asia/e535d6e1-03f5-40c7-a993-25587c86d77d.png)

Có thể mở các kết quả đó để xem từng bước mà bài Test được thực hiện. Nếu bạn di chuột qua từng bước, bạn sẽ thấy nó được thực thi trong trình duyệt theo thời gian thực. Một tính năng thực sự hữu ích của Cypress.👌👌

![image.png](https://images.viblo.asia/6f8a29fb-7cf5-469e-8391-22500a3f2993.png)

Như bạn có thể thấy, rất dễ dàng để thiết lập các bài Test với Cypress. Và nếu bạn đã quen thuộc với Jest, bạn có thể nhanh chóng sử dụng nó vì cú pháp không khác lắm.

Nếu bạn đang tự hỏi liệu có hợp lý khi sử dụng cả Jest và Cypress làm người chạy Test trong cùng một dự án hay không, [mình nghĩ rằng điều này sẽ giúp bạn tổng hợp nó một cách khá hay. (Đã có người trả lời nó trên StackOverflow bạn tham khảo nhé)](https://stackoverflow.com/questions/66217682/should-i-use-both-cypress-and-jest-together)

# Cách Test một ứng dụng Nodejs - Back-end

Bây giờ bạn đã có hiểu biết cơ bản về các cách bạn có thể Test ứng dụng giao diện người dùng Front-end, hãy đến với phần Back-end nào.

Đối với Back-end, mình sẽ sử dụng một API Node và Express đơn giản chỉ với 3 endpoints.

Tạo một thư mục và chạy `npm init -y` để tạo một ứng dụng Node. Chạy `npm i express` để cài đặt Express, sau đó chạy `npm i -D jest supertest` để cài đặt cả Jest và Supertest dưới dạng phụ thuộc phát triển.

Bên trong của bạn `package.json`, hãy thêm `"scripts": { "test": "jest" }`.  
Toàn bộ file package.json của bạn sẽ trông như thế này: (hoặc cơ bản nó sẽ giống thế này)

```json
{
  "dependencies": {
    "express": "^4.17.3"
  },
  "devDependencies": {
    "jest": "^27.5.1",
    "supertest": "^6.2.2"
  },
  "scripts": {
    "test": "jest"
  }
}
```

Sau đó, tạo một tệp app.js và gõ đoạn code này vào đó:

```js
// app.js
/* Import and initialize express */
const express = require('express');
const app = express();
const server = require('http').Server(app);
/* Global middlewares */
app.use(express.json());

/* Endpoint 1 */
app.get('/', async (req, res) => {
  try {
    res.status(200).json({greeting: 'Hello there!'});
  } catch (err) {
    res.status(500).send(err);
  }
});

/* Endpoint 2 */
app.get('/isPalindrome', async (req, res) => {
  try {
    const string = req.body.string;
    let result = true;
    let left = 0;
    let right = string.length - 1;

    while (left < right && result) {
      if (string[left] === string[right]) {
        left += 1;
        right -= 1;
      } else result = false;
    }

    res.status(200).json({result: result});
  } catch (err) {
    res.status(500).send(err);
  }
});

/* Endpoint 3 */
app.get('/twoSum', async (req, res) => {
  try {
    const nums = JSON.parse(req.body.nums);
    const target = JSON.parse(req.body.target);

    let result = false;

    for (let i = 0; i < nums.length; i++) {
      const neededNum = target - nums[i];
      if (nums.indexOf(neededNum) !== -1 && nums.indexOf(neededNum) !== i) result = [nums[i], nums[nums.indexOf(neededNum)]];
    }

    res.status(200).json({result: result});
  } catch (err) {
    res.status(500).send(err);
  }
});

/* Export server object */
module.exports = server;

/* Initialize server */
server.listen(3001, () => console.log('Server is listening.'));
server.on('error', (error) => console.error(error));
```

Như bạn có thể thấy, endpoint 1 chỉ trả về một tin nhắn chào mừng. Endpoint 2 và 3 là 2 API chữa nội dung là 2 hàm mà bạn đã code trước đó. Bây giờ các tham số trong  request và các giá trả về sẽ để trong response. 😉

Tạo một tệp  app.test.js và gõ đoạn code này vào trong đó:

```js
// app.test.js
const supertest = require('supertest'); // Import supertest
const server = require('./app'); // Import the server object
const requestWithSupertest = supertest(server); // We will use this function to mock HTTP requests

afterEach((done) => {
  // afterEach function is provided by Jest and executes once all tests are finished
  server.close(); // We close the server connection once all tests have finished
  done();
});

test('GET "/" returns greeting', async () => {
  const res = await requestWithSupertest.get('/');
  expect(res.status).toEqual(200);
  expect(res.type).toEqual(expect.stringContaining('json'));
  expect(res.body).toEqual({greeting: 'Hello there!'});
});

describe('/isPalindrome', () => {
  test('GET "/isPalindrome" neuquen returns true', async () => {
    const res = await requestWithSupertest.get('/isPalindrome').set('Content-type', 'application/json').send({string: 'neuquen'});
    expect(res.status).toEqual(200);
    expect(res.type).toEqual(expect.stringContaining('json'));
    expect(res.body).toEqual({result: true});
  });

  test('GET "/isPalindrome" bariloche returns true', async () => {
    const res = await requestWithSupertest.get('/isPalindrome').set('Content-type', 'application/json').send({string: 'bariloche'});
    expect(res.status).toEqual(200);
    expect(res.type).toEqual(expect.stringContaining('json'));
    expect(res.body).toEqual({result: false});
  });
});

describe('/twoSum', () => {
  test('GET "/twoSum" [2,7,11,15] and 9 returns [7, 2]', async () => {
    const res = await requestWithSupertest.get('/twoSum').set('Content-type', 'application/json').send({nums: '[2,7,11,15]', target: '9'});
    expect(res.status).toEqual(200);
    expect(res.type).toEqual(expect.stringContaining('json'));
    expect(res.body).toEqual({result: [7, 2]});
  });

  test('GET "/twoSum" [3,2,4] and 6 returns [4, 2]', async () => {
    const res = await requestWithSupertest.get('/twoSum').set('Content-type', 'application/json').send({nums: '[3,2,4]', target: '6'});
    expect(res.status).toEqual(200);
    expect(res.type).toEqual(expect.stringContaining('json'));
    expect(res.body).toEqual({result: [4, 2]});
  });

  test('GET "/twoSum" [3,2,4] and 10 returns false', async () => {
    const res = await requestWithSupertest.get('/twoSum').set('Content-type', 'application/json').send({nums: '[3,2,4]', target: '10'});
    expect(res.status).toEqual(200);
    expect(res.type).toEqual(expect.stringContaining('json'));
    expect(res.body).toEqual({result: false});
  });
});
```

Hãy phân tích những gì bạn đang làm:

- Mocki một  yêu cầu với `requestWithSupertest.get('/')`
- Sau đó, "break" đối tượng res thành nhiều mảnh và Test từng phần của nó:
    - Test state phản hồi: `expect(res.status).toEqual(200)`
    - Test định dạng của response: `expect(res.type).toEqual(expect.stringContaining('json'))`
    - Test phần nội dung response: `expect(res.body).toEqual({ greeting: "Hello there!" })`

Các Test case khác tương tự, ngoại trừ bạn đang gửi dữ liệu trong các yêu cầu giả (mock requests), như thế này:

```js
const res = await 
  requestWithSupertest.get('/isPalindrome')
  .set('Content-type', 'application/json')
  .send({string: 'bariloche'});
```

Như bạn có thể thấy, Test theo cách này thực sự đơn giản khi bạn đã quen thuộc với Jest. Chỉ cần Supertest trợ giúp một chút để mô phỏng yêu cầu HTTP và phần còn lại chỉ là xác nhận Response. 👏👏

Bạn có thể chạy Test của mình với lệnh `npm test` và bạn sẽ nhận được phản hồi sau:

```
// console
  PASS  ./app.test.js
  ✓ GET "/" returns greeting (46 ms)
  /isPalindrome
  ✓ GET "/isPalindrome" neuquen returns true (18 ms)
  ✓ GET "/isPalindrome" bariloche returns true (3 ms)
  /twoSum
  ✓ GET "/twoSum" [2,7,11,15] and 9 returns [7, 2] (4 ms)
  ✓ GET "/twoSum" [3,2,4] and 6 returns [4, 2] (3 ms)
  ✓ GET "/twoSum" [3,2,4] and 10 returns false (2 ms)
  
  Test Suites: 1 passed, 1 total
  Tests:       6 passed, 6 total
  Snapshots:   0 total
  Time:        0.552 s, estimated 1 s
  Ran all test suites.
```

# Cuối cùng

Mình đã trình bày những kiến ​​thức cơ bản về bốn công cụ rất phổ biến sẽ cho phép bạn Test cả front-end và back-end của một số JS app.

Tất nhiên còn nhiều hơn thế nữa, bao gồm tất cả các công cụ bạn đã thấy ở trên và nhiều tính năng mình cũng chưa đề cập, và hằng hà xa số những công cụ khác. Nhưng chung quy lại thì ý tưởng thường thì nó cũng gần giống như trên.

Như mọi khi, mình hy vọng bạn thích bài viết này và học được điều gì đó mới.

Cảm ơn và hẹn gặp lại các bạn trong những bài viết tiếp theo! 😍

Nếu bạn thấy thích blog của mình thì nhấn theo dõi để ủng hộ mình nhé. Thank you.😉

Nguồn:: [Blog#9: Tất tần tật về cách Test một ứng dụng bằng Jest, Testing Library, Cypress và Supertest (Cơ bản về test) - (Series: Bí kíp Javascript - PHẦN 7)](https://tuan200tokyo.blogspot.com/2022/10/blog9-cach-test-ung-dung-bang-jest.html)
