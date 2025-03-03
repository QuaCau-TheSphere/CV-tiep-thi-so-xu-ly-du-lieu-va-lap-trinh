---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
### 3. Xác định đường cơ sở

Dựa vào độ phức tạp ở trên, chúng ta đã biết được có bao nhiêu đường dẫn cơ sở mà không sợ bị bỏ sót (**Số đường cơ sở chính là độ phức tạp đồ thị**)

Bây giờ chúng ta đi xác định đường cơ sở:  
![](https://kipalog.kaopiz.com/uploads/f9e7/9912/image.png)

Từ đồ thị dòng, chúng ta đưa ra các đường cơ sở sau:

> 1. **1** > **11**
> 2. **1** > **2,3** > **6** > **7** > **9** > **10** > **1**
> 3. **1** > **2,3** > **6** > **8** > **9** > **10** > **1**
> 4. **1** > **2,3** > **4,5** > **10** > **1**

### 4. Kiểm tra

Chúng ta kiểm tra lại số đường cơ sở đã bằng với độ phức tạp chưa, nếu ít hơn thì chứng tỏ chúng ta đã đưa ra thiếu, nếu nhiều hơn thì một số đường cơ sở chúng ta đưa ra bị thừa hoặc bị trùng lặp với các đường cơ sở còn lại

### 5. Thiết kế testcase

Dựa vào đường cơ sở, chúng ta đưa ra các điều kiện sao cho thõa mãn các điều kiện để chúng đi hết các đường cơ sở đấy => và nó được xem như là 1 testcase

Cấu trúc:

> Test case cho đường dẫn 1
> 
> - Đầu vào: …
> - Đầu ra mong muốn: …
> - Mục đích: …

....
Nguồn:: [Kỹ thuật để testcase không bị bỏ sót.](https://kipalog.kaopiz.com/posts/Ky-thuat-de-testcase-khong-bi-bo-sot)