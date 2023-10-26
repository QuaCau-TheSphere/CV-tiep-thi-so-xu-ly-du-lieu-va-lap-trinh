---
share: true
created: 2023-09-26T21:52
updated: 2023-10-24T18:26
---
Hãy xem lại hàm `__init__()` mà chúng ta đã xây dựng trong ví dụ đầu tiên:

```python
def __init__(self, 
                title: str,
                authors: str = '',
                publisher: str = '',
                year: int = 2020,
                edition: int = 1):
    """Hàm tạo của class"""
    self.title = title
    self.authors = authors
    self.publisher = publisher
    self.year = year
    self.edition = edition
    self.__private = True
    Book.count += 1
```
`__init__()` là một hàm đặc biệt trong Python: hàm tạo (constructor).

Về mặt hình thức `__init__()` hoàn toàn tương tự như một lệnh khai báo [hàm trong Python](https://tuhocict.com/function-ham-trong-python/). Hàm `__init__()` ở trên nhận các tham số title, authors, publisher, year và edition. Chúng ta cũng sử dụng kỹ thuật chỉ báo kiểu (type hint) và cung cấp giá trị mặc định cho các tham số.

Constructor trong Python bắt buộc phải có tên là `__init__` và phải có ít nhất một tham số, thường đặt tên là `self`. Nếu có nhiều tham số, `self` bắt buộc phải là tham số đầu tiên.

Tên gọi tham số `self` được đặt theo quy ước của Python chứ không bắt buộc. Bạn có thể đặt bất kỳ tên gọi nào khác. Những bạn có xuất phải điểm là C++ hay C# thường có xu hướng đặt là this.


> [!NOTE]- Constructor và Initializer
> Nói một cách chính xác, `__init__()` không phải là constructor theo nghĩa đen của khái niệm này trong lập trình hướng đối tượng. Hàm `__init__()` là một initializer – hàm chịu trách nhiệm khởi tạo các giá trị cho object. Initializer không chịu trách nhiệm khởi tạo object.
> 
> Trong Python, hàm `__init__()` không chịu trách nhiệm tạo ra object của class. Python sử dụng một ‘magic method’ có tên gọi là `__new__()` để tạo object của mỗi class.
> 
> Magic method là một số phương thức được Python tự động tạo cùng với class và được Python gọi tự động nhằm thực hiện những công việc đặc biệt.
> 
> `__new__()` mới thực sự là constructor của Python class.
> 
> Ví dụ, khi gặp lệnh tạo object `b = book()` thì Python sẽ tự động chạy hàm `__new__()` đầu tiên. Kết quả của hàm `__new__()` là object của class book. Sau đó Python tiếp tục tự động chạy `__init__()`. Object do `__new__()` tạo ra được truyền sang cho `__init__()` thông qua tham số đầu tiên (self) trong danh sách.
> 
> Vì lý do này, bạn có thể đặt bất kỳ tên gì cho self cũng được nhưng phải để nó ở đầu danh sách tham số.
> 
Vai trò quan trọng hàng đầu của hàm tạo trong Python là tạo và gán giá trị cho instance attribute. Tất cả các tham số còn lại trong danh sách tham số của `__init__()` cung cấp giá trị để tạo ra instance attribute cho object.

Với hàm tạo như trên, bạn có thể tạo object của class Book bằng những cách sau:

```python
b1 = Book('Lập trình hướng đối tượng với Python', 'Nhật Linh', 'Tự học ICT', 2022, 2)
b2 = Book(title = 'Nhập môn lập trình Python', authors= 'Nhật linh', publisher= 'Tự học ICT')
b3 = Book('A new book')
```

Dễ thấy rằng, lệnh tạo object bằng hàm tạo không khác biệt gì so với lời gọi hàm thông thường.

Nguồn:: [[tuhocict]], [Giới thiệu chung về class trong Python, constructor | Tự học ICT](https://tuhocict.com/class-trong-python-khai-niem-khai-bao/)