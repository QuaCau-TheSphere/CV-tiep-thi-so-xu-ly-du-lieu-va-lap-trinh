---
share: true
created: 2023-10-05T16:30
updated: 2026-08-06T15:36
---
Để hỗ trợ cho quản lý và thực hiện các yêu cầu khác, người ta đã và đang sử dụng một số phương pháp tổ chức dữ liệu khác nhau. Phần trình bày tiếp theo sau giới thiệu 3 phương pháp chính.

## Sử dụng các tập tin

Trong thời kỳ đầu của việc ứng dụng tin học trong quản lý và sản xuất, khoảng những năm 60 của thế kỷ trước, người ta sử dụng những tập tin để lưu trữ các dữ liệu (về nhân sự, tài chính, vật tư, giao dịch, . . .). Để thuận tiện trong việc thao tác với các tập tin ấy, người ta xây dựng các chương trình ứng dụng khác nhau như tính toán nguyên liệu, hàng hóa xuất nhập, phân tích kết quả kinh doanh, tính điểm trung bình, đánh giá kết quả học tập của sinh viên.

Việc sử dụng các tập tin ấy có thể dẫn đến một số điểm bất cập chính như sau:

- Có sự phụ thuộc giữa chương trình ứng dụng và dữ liệu. Một sự thay đổi nhỏ trong cấu trúc của dữ liệu có thể làm chương trình ứng dụng không hoạt động được.
- Không có sự nhất quán (consistency). Các tập tin thường được ghi nhận ở một số bộ phận khác nhau của cơ quan nên nếu không có những hướng dẫn thật cụ thể và chi tiết thì cách ghi chép trong những tập tin khác nhau có thể không giống nhau. Thí dụ cùng một địa chỉ nhưng ta thấy những cách ghi khác nhau : Nha Trang, Khánh Hòa, Phú Khánh. Điều này có thể dẫn đến việc xử lý bị sai lạc.
- Thừa dữ liệu (redundancy). Do được thực hiện bởi một số bộ phận trong tổ chức nên thường xuyên xẩy ra hiện tượng thừa dữ liệu do có sự trùng chập, cùng một dữ liệu lại được trình bày trong một số tập tin khác nhau. Các thông số của một sản phẩm có thể nằm ở các tập tin của phân xưởng sản xuất, phòng kế hoạch, bộ phận bán hàng, phòng điều độ. Điều này làm tăng dung lượng lưu trữ và chi phí. Đôi khi cách trình bày các dữ liệu trùng chập này lại khác nhau như trên đã đề cập, dẫn đến kết quả xử lý không còn chính xác.
- Việc tiếp cận dữ liệu khó khăn. Đối với một số thông tin, việc nắm bắt khá khó khăn do các dữ liệu có liên quan nằm rải rác ở một số tập tin. Thí dụ để so sánh thị hiếu của khách hàng ở các khu vực Đồng bằng sông Cửu Long, Tây Nguyên, và Thành phố Hồ Chí Minh cần sử dụng dữ liệu ở một số tập tin.
- Sự phân tán của dữ liệu : Do dữ liệu được phân tán trong nhiều tập tin, định dạng của các tập tin có thể khác nhau, xử lý bằng những chương trình khác nhau, có thể viết bằng những ngôn ngữ lập trình khác nhau, với những phong thái khác nhau. Vì thế việc liên kết chúng gặp nhiều khó khăn.
- Khi trong cùng một lúc, có nhiều người dùng khác nhau cùng sử dụng, nhiều chương trình cùng được thực thi, sẽ xẩy ra các sự tranh chấp (concurrency). Việc quản lý các tranh chấp này rất khó khăn, gần như là không thể thực hiện được.
- Các phiền toái xẩy ra trong các quá trình hiệu chỉnh, cập nhập và xóa bỏ dữ liệu vì ta phải thực hiện đồng thời trên một số tập tin một cách thích hợp. Người ta thấy rằng các quá trình này dễ xẩy ra những sai sót.
- An toàn dữ liệu : Vì dữ liệu có thể được thao tác từ một số chương trình khác nhau nên việc giữ cho dữ liệu an toàn tương đối khó khăn.

  

## Sử dụng các bảng dữ liệu

Trong một số cơ quan, người ta tổ chức dữ liệu thành các danh sách khác nhau và lưu trữ dưới dạng các bảng dữ liệu (spreadsheet) và dùng những công cụ như MS Excel để xử lý. Đối với những dữ liệu nhỏ, ít người sử dụng, yêu cầu xử lý không phức tạp thì phương pháp này tỏ ra đơn giản, dễ thực hiện, và khá hiệu quả mặc dù vẫn còn một số khuyết điểm như trùng chập dữ liệu, hay các phiền toái khi cập nhập.

Tuy nhiên, khi khối lượng dữ liệu lớn (thí dụ [superstore sale.xls](https://community.tableau.com/docs/DOC-1236) do Micheal Martin thu thập), các tập tin quá lớn, quá trình xử lý chậm, không hiệu quả. Mặt khác sai sót rất dễ xẩy ra. [Raymond Panko](http://panko.shidler.hawaii.edu/SSR/Mypapers/whatknow.htm "What We Know About Spreadsheet Errors") đã tổng hợp số liệu từ 13 công ty kiểm toán cho thấy trung bình có đến 88% các bảng dữ liệu có sai sót, thậm chí trong 6 công ty, con số đó là 100%.

Ghi chú

Trong các phương pháp tổ chức dữ liệu bằng các tập tin và bằng các bảng dữ liệu, các tập tin chỉ chứa các dữ liệu, không có cơ chế để liên kết các tập tin này với nhau. Các tập tin dạng này được gọi là các tập tin trơn (flat file).

  

## Sử dụng Cơ sở dữ liệu

Sử dụng cơ sở dữ liệu (CSDL) là phương pháp thông dụng nhất hiện nay. Toàn bộ dữ liệu được tập trung và tổ chức theo những khuôn mẫu thống nhất. Khi CSDL được tổ chức theo mô hình quan hệ, dạng phổ biến nhất, dữ liệu được lưu trữ trong các bảng, còn gọi là các [quan hệ](https://xdulieu.com/co-so-du-lieu/cs3-mo-hinh-quan-he/mq5-mo-hinh-co-so-du-lieu-quan-he.html "Tại sao sử dụng thuật ngữ") theo thuật ngữ của CSDL. Nhưng không giống như các bảng dữ liệu thông thường, trong các quan hệ có những cơ chế để các bảng có thể móc nối, liên kết với nhau.

Ngoài ra, cấu trúc của hệ thống CSDL cũng có một số điểm khác biệt. Các chương trình ứng dụng không giao tiếp trực tiếp với CSDL mà qua một trung gian gọi là hệ quản trị cơ sở dữ liệu (HQTCSDL) như trên Hình 1.

![[Người dùng, giao diện, chương trình ứng dụng, hệ quản trị cơ sở dữ liệu, cơ sở dữ liệu.png]]
Hình 1 Sơ đồ cấu trúc của hệ thống cơ sở dữ liệu

Việc sử dụng cơ sở dữ liệu để quản lý và khai thác dữ liệu có các ưu điểm sau:

- Có sự độc lập giữa chương trình ứng dụng và dữ liệu. Điều này cho phép cấu trúc dữ liệu có thể thay đổi rất nhiều mà vẫn không ảnh hưởng đến chương trình ứng dụng.
- Do dữ liệu được tập trung nên giải quyết được hay kiểm soát được vấn đề trùng chập dữ liệu và không nhất quán trong trình bày. Do đó giảm thiểu các sai sót gây ra do hai vấn đề trên.
- Chất lượng dữ liệu được nâng cao. HQTCSDL cung cấp những cơ chế sàng lọc để chỉ đưa các dữ liệu đạt các điều kiện nhất định mới được đưa vào cơ sở dữ liệu.
- Dữ liệu được chia sẻ tốt hơn, khả năng truy cập đến nhiều loại dữ liệu hơn.
- HQTCSDL đã cung cấp một số công cụ chính để làm việc với cơ sở dữ liệu nên việc thực hiện các chương trình ứng dụng được đơn giản hơn, rút ngắn hơn, quá trình triển khai dễ dàng hơn.
- Bảo trì hệ thống dữ liệu dễ dàng hơn.

![](https://xdulieu.com/co-so-du-lieu/cs1-khai-quat/nguoi-may.png) 
Nguồn:: [Các phương pháp tổ chức dữ liệu](https://xdulieu.com/co-so-du-lieu/cs1-khai-quat/kq2-cac-phuong-phap-to-chuc-du-lieu.html)
