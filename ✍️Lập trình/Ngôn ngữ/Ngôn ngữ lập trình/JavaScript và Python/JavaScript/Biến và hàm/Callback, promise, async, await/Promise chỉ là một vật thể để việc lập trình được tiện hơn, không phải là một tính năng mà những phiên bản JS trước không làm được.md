---
share: true
created: 2023-10-24T18:26
updated: 2024-04-27T16:19
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
const promise = new Promise(hàm)
//    ^ vật thể     ^ Lớp
```

Hàm này được quy định có 2 đối số có tên là `resolve` và `reject`:
```js
function hàm(resolve, reject) {} 
```

Vật thể `promise` sau khi được tạo ra từ lớp `Promise` sẽ có 3 phương thức: `then`, `catch`, `finally`. 


```js
fetch("https://jsonplaceholder.typicode.com/todos/1")
.then(res => res.json())
.then(d => console.log(d))
```
Nguồn::

