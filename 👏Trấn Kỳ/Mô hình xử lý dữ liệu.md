---
share: true
created: 2023-09-12T16:42
updated: 2023-10-08T22:01
---
Hai khối dữ liệu quan trọng nhất trong đây là khối khai báo và khối câu nhập. Chúng đều có $n$ chiều. Các chiều này được khai báo trong cấu hình. Trong mỗi chiều lại chứa $2$ danh sách: danh sách từ và danh sách nhãn. Ví dụ, trong chiều chi tiêu của khốiKhaiBáo $2$ danh sách này có dạng như sau:
- danhSáchTừ:   `['rau'       , ... , 'xăng', 'nhớt xe', ... ]`
- danhSáchNhãn: `['Lương thực', ... , 'Xe'  , 'Xe', ... ]`

Ta biết được nhãn của mỗi từ thông qua việc chúng có cùng chỉ số với nhau.

Ta có thể gọi những danh sách này qua các chỉ số trong vật thể. Ví dụ:
- danhSáchTừ của chiều chi tiêu của khốiKhaiBáo:   `khốiKhaiBáo[0][0]`
- danhSáchNhãn của chiều chi tiêu của khốiKhaiBáo: `khốiKhaiBáo[0][1]`

- danhSáchTừ của chiều PTTT của khốiKếtQuả:   `khốiKếtQuả[1][0]`
- danhSáchNhãn của chiều PTTT của khốiKếtQuả: `khốiKếtQuả[1][1]`

Nói chung, chỉ số của một danh sách có dạng `tênVậtThể[i][j]`, với:
- $i$ là chỉ số chiều:
    - $i = 0$: chi tiêu
    - $i = 1$: phương thức thanh toán
    - $i= 2$: nơi mua
    - ...
- $j$ là chỉ số danh sách:
    - $j = 0$: danh sách từ
    - $j = 1$: danh sách nhãn của từ
    - $j = 2$: danh sách vị trí của từ (chỉ có ở khốiKếtQuả) 

Ví dụ, với câu nhập `gạo, xà bông 50k ở chợ vợ trả` thì khốiKếtQuả sẽ trông như sau:

| $j →$ $i ↓$ | $0$                    | $1$                                                 | $2$                     |
| ----------- | ---------------------- | --------------------------------------------------- | ----------------------- |
| $0$         | `[ 'gạo', 'xà bông' ]` | `[ 'Lương thực/tinh bột', 'Sinh hoạt/đồ vệ sinh' ]` | `[ [0, 3]`, `[5, 12]` ] |
| $1$         | `[ 'vợ trả' ]`         | `[ 'Tiền mặt' ]`                                    | `[ [23, 29]` ]          |
| $2$         | `[ 'chợ' ]`            | `[ 'Tiểu thương' ]`                                 | `[ [19, 22]` ]          |

Xem thêm ưu và nhược điểm của cách biểu diễn dữ liệu này và của những cách khác tại đây: https://softwareengineering.stackexchange.com/q/446480/192731


[[Hướng dẫn đọc code cho người thấy việc biết lập trình là quan trọng nhưng không thể biến nó trở thành ưu tiên cao nhất]]
[[Mô hình trích chọn từ]]