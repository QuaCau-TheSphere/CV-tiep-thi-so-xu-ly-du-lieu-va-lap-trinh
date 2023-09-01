# Hướng dẫn đọc hiểu code
## Cấu trúc script
```
I. Khai báo
II. Dán nhãn, tạo vật thể
    1. Tạo khốiKhaiBáo
    2. Lọc từ, dánNhãnTừ và tạo khốiCâuNhập
III. Làm sạch kết quả
    1. Loại bỏ từ đơn bị nhận diện sai
    2. Loại bỏ nhãn chi tiêu bị trùng lặp
    3. Chọn PTTT cuối cùng trong câu nhập
IV. Đếm tiền
V. Tạo kết quả
    1. xửLýDấuThanhVàViếtTắt
    2. xửLýViếtTắt
    3. tạoKếtQuả
```

# Nguyên lý hoạt động
2 khối dữ liệu quan trọng nhất trong đây là khối khai báo và khối câu nhập. Chúng đều có 3 chiều: chi tiêu, phương thức thanh toán, nơi mua. Trong mỗi chiều lại chứa 2 danh sách: danh sách từ và danh sách nhãn. Ví dụ, trong chiều chi tiêu của khốiKhaiBáo 2 danh sách này có dạng như sau:
- danhSáchTừ:   ['rau'       , ... , 'xăng', 'nhớt xe', ... ]
- danhSáchNhãn: ['Lương thực', ... , 'Xe'  , 'Xe', ... ]
Ta biết được nhãn của mỗi từ thông qua việc chúng có cùng chỉ số với nhau.

Ta có thể gọi những danh sách này qua các chỉ số trong vật thể. Ví dụ:
- danhSáchTừ của chiều chi tiêu của khốiKhaiBáo:   khốiKhaiBáo[0][0]
- danhSáchNhãn của chiều chi tiêu của khốiKhaiBáo: khốiKhaiBáo[0][1]

- danhSáchTừ của chiều PTTT của khốiCâuNhập:   khốiCâuNhập[1][0]
- danhSáchNhãn của chiều PTTT của khốiCâuNhập: khốiCâuNhập[1][1]

Nói chung, chỉ số của một danh sách có dạng tênVậtThể[i][j], với:
- i là chỉ số chiều:
    - i = 0: chi tiêu
    - i = 1: phương thức thanh toán
    - i= 2: nơi mua
- j là chỉ số danh sách:
    - j = 0: danh sách từ
    - j = 1: danh sách nhãn của từ
    - j = 2: danh sách vị trí của từ (chỉ có ở khốiCâuNhập) 

Ví dụ, với câu nhập 'gạo, xà bông 50k ở chợ vợ trả' thì khốiCâuNhập sẽ trông như sau:
┌─────────┬──────────────────────┬───────────────────────────────────────────────────┬──────────────────────┐
│ i ↓ j → │          0           │                         1                         │          2           │
├─────────┼──────────────────────┼───────────────────────────────────────────────────┼──────────────────────┤
│    0    │ [ 'gạo', 'xà bông' ] │ [ 'Lương thực/tinh bột', 'Sinh hoạt/đồ vệ sinh' ] │ [ [0, 3], [5, 12] ]  │
│    1    │     [ 'vợ trả' ]     │                  [ 'Tiền mặt' ]                   │     [ [23, 29] ]     │
│    2    │      [ 'chợ' ]       │                 [ 'Tiểu thương' ]                 │     [ [19, 22] ]     │
└─────────┴──────────────────────┴───────────────────────────────────────────────────┴──────────────────────┘
Xem thêm ưu và nhược điểm của cách biểu diễn dữ liệu này và của những cách khác tại đây: https://softwareengineering.stackexchange.com/q/446480/192731

dữ liệu thô người dùng khai báo -> khối khai báo


Một số phím tắt thường dùng cho việc đọc hiểu code:
| Phím tắt         | Chức năng                                                 |
| ---------------- | --------------------------------------------------------- |
| Alt + Z          | Word wrap                                                 |
| Ctrl + Shift + [ | Thu gọn khối code                                         |
| Ctrl + Shift + ] | Mở rộng khối code                                         |
| Ctrl + Shift + . | Mở danh sách các hàm và biến                              |
| F12              | Đến nhanh những nơi hàm hoặc biến được sử dụng            |
| Ctrl + Space     | Mở danh sách gợi ý điền nhanh                             |
| Ctrl + K Z       | Mở zen mode                                               |
| Ctrl + \         | Chia màn hình thành các editor (hay còn gọi là tab group) |
| Ctrl + 1, 2, 3   | Di chuyển giữa các editor                                 |
| F6               | Đổi panel                                                 |
| Ctrl + B         | Mở sidebar trái (VS Code gọi là primary sidebar)          |
| Ctrl + Shift + B | Mở sidebar phải (VS Code gọi là secondary sidebar)        |


