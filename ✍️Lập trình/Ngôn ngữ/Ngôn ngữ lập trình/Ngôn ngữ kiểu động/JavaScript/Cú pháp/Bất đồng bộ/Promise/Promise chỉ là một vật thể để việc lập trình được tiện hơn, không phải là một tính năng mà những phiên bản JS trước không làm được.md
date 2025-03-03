---
share: true
created: 2023-10-24T18:26
updated: 2025-03-03T18:48
---
[[Lớp là một cái khuôn để tạo các vật thể cho nhanh]]. Thông thường để tạo một vật thể mới qua một lớp ta dùng thế này:
```js
const xeMáy = new Xe('2 bánh')
const ôTô   = new Xe('4 bánh')
const xeTải = new Xe('12 bánh')
//    ^ vật thể   ^ Lớp
```

Promise là một vật thể, và nó được tạo ra từ lớp `Promise`. Lớp này không nhận đối số là chuỗi như bình thường mà là cả một hàm:
```js
const promise = new Promise(hàmThựcThi)
//    ^ vật thể     ^ Lớp
```

Hàm này sẽ được thực thi ngay khi bạn khai báo mà không cần bạn phải gọi nó thực thi như thông thường:
```js
function hàmBìnhThường(){} // chỉ mới khai báo, chưa thực thi
hàmBìnhThường() // Tới lúc này mới thực thi

const promise = new Promise(hàmThựcThi) // hàmThựcThi() được thực thi ngay tại dòng này
```
[[Đối số của Promise là một hàm. Nó được gọi là hàm thực thi (executor)|Hàm thực thi này được quy định là có 2 đối số. 2 đối số này đến lượt nó lại là 2 hàm khác]]. Hàm đầu tiên có tên là `resolve` còn hàm sau thì có tên là `reject`:
```js
function hàmThựcThi(resolve, reject) {} 
```

[[Vật thể promise có 2 thuộc tính là state và result, và 3 phương thức là then, catch, và finally]]
Vật thể `promise` sau khi được tạo ra từ lớp `Promise` sẽ có 3 phương thức: `then`, `catch`, `finally`. 

```js
fetch("https://jsonplaceholder.typicode.com/todos/1")
.then(res => res.json())
.then(d => console.log(d))
```


[[Phương thức cho ta biết mình có thể làm gì với vật thể]]
[[Đường cú pháp là những loại cú pháp giúp việc đọc dễ dàng hơn. Muối cú pháp là những loại cú pháp giúp việc viết sai trở nên khó khăn hơn]]