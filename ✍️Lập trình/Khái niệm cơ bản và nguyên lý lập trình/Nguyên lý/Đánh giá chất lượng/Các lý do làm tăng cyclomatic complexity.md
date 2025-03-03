---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
#### Trường hợp 1: đối với tác giả của mã nguồn

Chỉ số Cyclomatic Complexity của 1 hàm sẽ tăng lên rất nhanh khi bạn viết quá nhiều chức năng xử lý trong đó.

Theo thời gian 1 hàm có thể đã bao gồm mã nguồn xử lý cho cả 1 business case luôn.

Trường hợp này hay xuất hiện khi:

- Dev mới nhận đầu bài; đang liên tục viết code để xử lý cho chạy được. Khi đó, mỗi lần 1 trường hợp nảy ra trong đầu thì Dev sẽ thêm những câu lệnh rẽ nhánh (thường là if) để xử lý vấn đề.
- Khi đang liên tục code, Dev nghĩ ra được trường hợp cần xử lý. Tuy nhiên, để xử lý trường hợp đó thì chỉ cần khoảng 3 dòng code. Do đó, Dev nghĩ rằng không cần tách hàm ra làm gì cho nó dài dòng. Lâu dần, nhiều trường hợp nhỏ như vậy sẽ khiến chỉ số Cyclomatic Complexity tăng cao.
- Dev nghĩ ra được trường hợp cần xử lý. Tuy nhiên, không thể nghĩ ra được tên hàm mới cần đặt như thế nào cho phù hợp với Coding Convention của dự án mà vẫn ngắn gọn. Dẫn đến quyết định thường gặp là: thôi không tách hàm nữa cho nhanh.

#### Giải pháp:

Đề xuất đưa ra giải pháp ở mức dự án:

- Dự án nên làm theo định hướng Test-driven development.
- Sử dụng tool SonarQube và CICD pipeline trong dự án để với mỗi commit bạn sẽ nhận được thông tin đánh giá luôn
- Sau khi Dev implement xong thì cần thiết có giai đoạn PTL review.

Khi Dev đã xác định được input là gì, output mong muốn là gì, các trường hợp cần đối ứng là gì thì

- Các trường hợp cần đối ứng của hàm đã được nhìn nhận từ đầu. Số lượng trường hợp phát sinh trong quá trình làm rất ít. Do đó chỉ số Cyclomatic Complexity có thể est ngay từ đầu để có thể đưa ra quyết định là nên viết 1 hàm hay là tách ra nhiều hàm.
- Do phải viết unit test case trước nên việc thêm các câu lệnh rẽ nhánh trong quá trình phát triển sẽ khiến Dev thấy số lượng unit test case tăng nhanh. Effort bỏ ra để viết unit test case lớn. Dev sẽ dễ dàng đưa ra quyết định là tách hàm hơn. Bởi vì việc tách hàm sẽ khiến việc viết unit test case dễ dàng hơn nhiều.

**_Trường hợp 2_: đối với người bảo trì mã nguồn của người khác**

Khi nhận thông tin về 1 defect, để đảm bảo an toàn (không phá vỡ cấu trúc mã nguồn hiện tại), người bảo trì thường cố gắng thêm các câu lệnh check case by case để fix defect.

Trường hợp này hay xuất hiện khi:

- Defect là 1 trường hợp nhỏ, mức độ ảnh hưởng đến các hàm khác cũng nhỏ. Người bảo trì hoàn toàn không có unit test case của mã nguồn cũ. Do đó thêm 1 câu lệnh bắt đúng điều kiện của trường hợp hiện tại để fix là cách làm thường gặp.
- Dự án nhận làm theo ticket, khi thực hiện est đã làm báo giá rất chặt. Do đó, để đảm bảo thời gian cam kết (VD như xử lý 1 ticket sau 12h), đảm bảo effort bảo trì nằm trong báo giá thì thường dự án cũng sẽ quyết định bổ sung thêm mã nguồn bắt đúng trường hợp bị lỗi vào thay vì đánh giá chỉ số Cyclomatic Complexity hoặc ảnh hưởng đến việc bảo trì tương lai. (tâm lý mặc kệ thằng sau này bảo trì là thằng nào)

**Giải pháp:**

Bạn cần dùng SonarQube hoặc các tool tương tự khác để đánh giá chỉ số Cyclomatic Complexity trước khi tiến hành bảo trì.

- Nếu chỉ số Cyclomatic Complexity của hàm nằm trong giới hạn cho phép <= 9 thì việc thêm 1 câu lệnh rẽ nhánh vào cùng không sao.
- Nếu chỉ số Cyclomatic Complexity của hàm >= 10 rồi thì nên study đầy đủ hàm đó & tiến hành refactor code cho hợp lý. Có thể tách hàm ra được là việc tốt nhất.
Nguồn:: [Xử Lý Cyclomatic Complexity - Độ Phức Tạp Theo Chu Kỳ | CodeLearn](https://codelearn.io/sharing/xu-ly-cyclomatic-complexity)