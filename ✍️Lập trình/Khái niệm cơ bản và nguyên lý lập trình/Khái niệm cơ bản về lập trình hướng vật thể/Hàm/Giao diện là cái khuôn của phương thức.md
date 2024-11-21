---
share: true
created: 2023-10-24T18:26
updated: 2024-11-18T21:58
---
[[Phương thức cho ta biết mình có thể làm gì với vật thể]]. [[Lớp là một cái khuôn để tạo các vật thể cho nhanh]]. Giả sử ta có nhiều lớp khác nhau, và các vật thể được tạo ra từ các lớp này đều có cùng một số phương thức giống nhau. Lúc này, ta sẽ có một *tập hợp* các phương thức giống nhau cho tất cả các lớp. 

[[Giao diện là cách để sử dụng vật thể mà không cần biết bên trong nó có gì]]. Tập hợp này được gọi là *giao diện*, vì cũng giống như những nút bấm trên màn hình quy định những gì ta có thể làm được với chương trình mà không cần biết bên trong có gì, những thứ trong tập hợp này quy định những gì ta có thể làm được với vật thể mà không cần biết bên trong có gì. Cái đầu tiên được gọi là GUI, cái sau được gọi là [[API là giao diện của một chương trình|API]].

Ta hay nghĩ phải có vật thể trước đã rồi mới biết mình có thể làm gì với nó. Nhưng thường việc nghĩ trước về những thứ mình có thể làm với nó rồi mới tạo nó ra sẽ hiệu quả hơn. Tức là đầu tiên ta sẽ định nghĩa giao diện, từ đó tạo ra các lớp triển khai giao diện đó, rồi mới tạo vật thể từ các lớp đó sau:
```ts
interface GiaoDiện {...}
class Lớp implements GiaoDiện {...}
const vậtThể = new Lớp()
```