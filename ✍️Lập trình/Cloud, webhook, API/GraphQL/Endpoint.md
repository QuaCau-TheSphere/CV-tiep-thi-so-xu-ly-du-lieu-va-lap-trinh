---
share: true
created: 2023-10-30T14:29
updated: 2024-07-27T14:04
---
# Endpoint là gì? Lợi ích trong việc phát triển APIs

In [QC/Test/Management](https://lcdung.top/category/qctest/)Tags [Action Plan](https://lcdung.top/tag/action-plan/), [endpoint](https://lcdung.top/tag/endpoint/)May 27, 2018

Mục lục [[Click vào để xem](https://lcdung.top/endpoint-la-gi-loi-ich-trong-viec-phat-trien-apis/#)]

# Endpoint là gì?

Để dễ hiểu mình sẽ làm ví dụ về **Endpoint.**

Khi App gọi đến API URL: `https://abc.com/foo/bar` và lúc này ta gọi `/foo/bar` là Endpoint.

**Endpoint** là một phần quan trọng trong quá trình phát triển API

# Định nghĩa Hàm (Tạo Action Plan)

Công việc đầu tiên của bạn là nghĩ về những thứ mà API của bạn sẽ cung cấp. Đó có thể là 1 danh sách các hàm CRUD (Create, Read, Update, Delete) thao tác với resourece của bạn. Để giải thích rõ hơn thì đây chính là 1 danh sách các “Action” cần phải làm với mỗi resource:  
**Ví dụ:**

Bạn có một Resouce là Người dùng và bạn cần 1 danh sách hàm như sau:  
**Users:**

- Create
- Read
- Update
- Delete
- List

_Công việc này gần giống với TDD tức là bạn hình dung ra các hàm cần viết và viết các đoạn mã giả giả sử rằng hàm này và class này đã tồn tại rồi đó, sau đó bạn mới định nghĩa chúng._

Nếu API của bạn có chức năng tìm kiếm theo tên hay mã số người dùng thì công việc đó ta liệt vào List nhé:  
**Users:**

- Create
- Read
- Update
- Delete
- List(Name,ID)

Thêm các Params vào có thể tốt và dễ hình dung tuy nhiên không nên thêm quá nhiều và dư như thêm tất cả các thuộc tính vào Create(name,id,age,…) là không nên.

# Lý thuyết Restful

Chuyển một Action Plan thành một Danh sách Endpoint thì cần những hiểu biết căn bản về RestFul API và các “Best Practice” trong việc đặt tên. Tất nhiên thì mỗi công ty, mỗi nhóm có chuẩn đặt tên khác nhau và cũng chả thể so sánh được cái nào là tốt nhất. Tuy nhiên mình sẽ nói về cái phổ biến mà mình nghĩ là OKie nhất cho các bạn.  
RestFul thì gồm nhiều tuy nhiên có 4 cái căn bản sau:  
**GET – POST- PUT -DELETE**

## 1. GET

- `GET /resources` – Tìm một danh sách records từ resource có thể có phân trang thì tốt nhất hoặc lấy toàn bộ records
- `GET /resources/X` – Chỉ cần lấy Record X, ví dụ /users/thanhtriphap -> Lấy Info mình ra nè
- GET /resources/X,Y,Z – Người dùng muốn tìm kiếm trên nhiều điều kiện hay 1 điều kiện mà nhiều giá trị
- GET /places/X/users – Lấy tất cả người dùng đang sinh sống trong vùng X
- GET /users/X/places – Lấy tất cả các nơi mà người dùng này đang hay đã ở
- GET /users/X/places/Y – Tìm kiếm user theo điều kiện X và Places theo điều kiện Y

**[Danger Zone] Auto Increment**

> Trong quá trình học trong trường các bạn thường xài ID dạng Auto-Increment. Tuy nhiên trong thực tế nếu API của ta để như vậy thì người ta có thể biết được số lượng Resource mà ta đang có điều này rất có ích với đối thủ đó chứ.  
> Biện pháp là ta sử dụng UUID – Các bạn có thể tìm UUID cho PHP, Ruby hay Python và các Package hỗ trợ Gen UUID trên GOOGLE.

## 2. DELETE

- DELETE /users/X – Xóa một người dùng
- DELETE /users/X,Y,Z – Xóa một vài dòng dữ liệu
- DELETE /users – Xóa tất cả các dòng dữ liệu (**Không nên**)
- DELETE /users/X/image – Xóa image của người dùng X
- DELETE /users/X/images – Xóa một loạt các hình ảnh của người dùng X

## 3. POST và PUT

Về mặt lý thuyết POST dùng tạo 1 dòng dữ liệu mới còn PUT thì dùng cập nhật một dòng dữ liệu đã có. Khác nhau là vậy tuy nhiên trên nguyên tắc thiết kế thì 2 hành động này như nhau mà thôi có nghĩa là những gì POST làm được thì PUT làm được và ngược lại.  
Tuy nhiên, tất nhiên phải có sự khác nhau căn bản để dùng chứ. Chúng ta xem khái niệm về  
**idempotent :** `Có nghĩa là khi mình gọi đến resource dùng PUT n lần thì behavior vẫn là như nhau, dữ liệu thay đổi của lần thứ n vẫn giống như lần gọi đầu tiên`

Nghe có vẻ hơi khó hiểu đúng không, thôi ví dụ cho dễ nhé:

- Giả sử mỗi sản phẩm chúng ta có 1 hình ảnh đại diện thôi (Chỉ 1 thôi nhé) và mỗi lần ta thay đổi nó tức là thay hình đại diện cho sản phẩm thì dữ liệu vẫn như cũ (Như cũ ở đây có nghĩa là không làm phát sinh thêm dòng nào mới nhé): **PUT /products/ao-so-mi-tay-dai-MB2331/image**
- Cũng ví dụ trên tuy nhiên sản phẩm lại có nhiều hình ảnh thì mỗi lần ta thêm thì có 1 dòng dữ liệu mới nên ta xài POST vì dữ liệu thay đỗi mà: **POST /products/quan-tay/images**

## 4. Danh từ số nhiều, số ít hay Cả hai

Một vài Developer thì dùng danh từ số ít một số lại xài số nhiều.  
Ví dụ:

- GET /user/1 – Trả về user có ID là 1
- GET /user – Thắc mắc user nào sẽ được trả về hay về hết

Do đó mình thường xài **số nhiều** cho các Endpoints:

- GET /users/1 – Trả về user có ID là 1
- GET /users?limit=5 – Trả về 5 user cho một lượt

## 5. Danh từ hay động từ

Trước đây khi POST cái gì đó một vài Dev thường dùng động từ:

- POST /SendMeAMessage
- POST /users/5/send-message

Tuy nhiên hình như hơi có vấn đế, chúng ta chỉ cần 1 động từ duy nhất trong đây là POST PUT hay GET … và URL là **danh từ** chứ không phải động từ. Một vài ví dụ sau:

- POST /users/5/message – Gửi một Message tới User 5

Một cách tuyệt vời hơn chúng ta có thể:

- POST /users/thanhtriphap/message
- PUT /users/thanhtriphap/message/wsis0n

# Xây dựng EndPoints

Sau khi hoàn thành công việc định hình GET, PUT, POST … cho mỗi Action trong Action Plan việc tiếp theo chính là Đặt mỗi Resource trong 1 controller trong đó có các hàm trong Action Plan:

- UsersController
- CategoriesController
- PlacesController

Và hoàn thành việc định tuyến Routing.  
Ví dụ trên **Laravel Framewok**

[![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/I5JPY.png_y9c6c97y15)](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/I5JPY.png_y9c6c97y15)

# Kết luận

Làm bất cứ điều gì nếu chúng ta định hình rõ những công việc sẽ phải làm giúp chúng ta dễ dàng hơn rất nhiều trong công việc sau này. Việc tạo ra các Endpoints là cách để Back End và Develper Mobile hay Front End làm việc với nhau và nâng cao hiệu quả công việc.

Nguồn:: [Endpoint là gì? Lợi ích trong việc phát triển APIs - LCDUNG](https://lcdung.top/endpoint-la-gi-loi-ich-trong-viec-phat-trien-apis/)