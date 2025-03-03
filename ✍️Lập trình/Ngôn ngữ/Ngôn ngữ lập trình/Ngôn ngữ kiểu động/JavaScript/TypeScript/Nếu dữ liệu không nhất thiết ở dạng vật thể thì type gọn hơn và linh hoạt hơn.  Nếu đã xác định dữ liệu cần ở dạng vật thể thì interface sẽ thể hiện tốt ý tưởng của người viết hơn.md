---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
Trong TypeScript, nếu ta muốn khai báo kiểu cho vật thể, ta có thể dùng từ khoá  `type` hoặc `interface`. `type` làm được gì thì `interface` cũng làm được như thế. Vậy thì khi nào nên dùng `type` và khi nào nên dùng `interface`?

```ts
type CâuNhập = string
type DanhSáchCâuNhập = Array<CâuNhập>
type SốTiền = number
```

Không như từ khoá `interface`, từ khoá `type` sử dụng dấu bằng. Trong toán học, **dấu bằng thể hiện mối quan hệ đồng nhất**. `a = b` khi và chỉ khi a và b đồng nhất. Sự đồng nhất này thậm chí còn hơn cả sự tương đương. Đây là một ý tưởng rất quan trọng trong toán học, mà ta lại hiểu được rất dễ dàng. Chính vì điều này, việc dùng `type` làm ta **ngay lập tức lĩnh hội được ý tưởng rằng đây là mối quan hệ đồng nhất**. Việc sử dụng `type` thay cho `interface` làm cho biểu thức gọn gàng hơn. Nó cũng khiến cho ta có thể linh hoạt thay đổi kiểu dữ liệu, không khiến ta bị đóng khung vào việc phải lưu dữ liệu dưới dạng vật thể. 

<sub>Và thực ra, hệ thống kiểu (type system) trong khoa học máy tính có nguồn gốc từ lý thuyết hình thái (type theory) trong toán học. </sub>

```ts
interface ĐộngVật {
	meomeo: boolean; 
}
interface Mèo extends ĐộngVật {
	meomeo: boolean; 
}
```

Tuy nhiên, điều mà từ khoá `type` truyền tải khác với điều mà từ khoá `interface` truyền tải. Không giống như kiểu, vốn bắt nguồn từ toán học, giao diện là một khái niệm đến từ khoa học máy tính. Tầm quan trọng của giao diện đến từ việc [[Giao diện là cách để sử dụng vật thể mà không cần biết bên trong nó có gì|nó là cách để sử dụng vật thể mà không cần biết bên trong nó có gì]]. Nếu lấy một vật thể cụ thể như bóng đèn làm ví dụ, thì giao diện của nó sẽ là cái đui đèn: chỉ cần người dùng có cái đui đó và nhà sản xuất tạo ra bóng đèn có cái đui đó thì đèn sẽ hoạt động. Người dùng không cần quan tâm cái đèn được tạo ra như thế nào, nhà sản xuất cũng không cần biết người dùng sẽ dùng cái đèn ra sao. Họ không cần quan tâm đến nhau để có thể đáp ứng được nhu cầu của nhau một cách hàng loạt. Nó là cái thứ mà người dùng thấy ở cái bóng đèn, là thứ bóng đèn giao tiếp với họ.

Cho nên, dù đúng là có thể dùng cả `type` và `interface` để khai báo kiểu cho vật thể, không có nghĩa là chúng truyền tải những ý đồ giống nhau. Ta không nên chỉ quan tâm mỗi việc làm sao để code chạy được, mà còn phải quan tâm đến tính dễ bảo trì, mở rộng và bắt lỗi của code. Việc thể hiện rõ được ý đồ của mình sẽ khiến ta đọc code dễ dàng hơn. Nếu sử dụng `interface` thì IDE có thể hiểu được ý mình tốt hơn và cho thông báo lỗi cụ thể hơn. Nếu đã xác định dữ liệu cần phải được lưu dưới dạng vật thể thì dùng `interface` sẽ tốt hơn.


Nguồn:: ![Why use Type and not Interface in TypeScript - YouTube](https://www.youtube.com/watch?v=Idf0zh9f3qQ&lc=UgxfYYiGoHCcnsqUTR54AaABAg)
Nguồn:: [TypeScript: Documentation - TypeScript for JavaScript Programmers](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html)

[[Dùng lớp khi ta có logic nghiệp vụ thực sự cần được thực thi. Dùng giao diện để tạo ràng buộc kiểu cho biến]]