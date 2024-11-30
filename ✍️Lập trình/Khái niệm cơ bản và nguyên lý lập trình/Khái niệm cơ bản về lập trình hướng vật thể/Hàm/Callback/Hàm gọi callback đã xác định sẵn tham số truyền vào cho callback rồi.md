---
share: true
created: 2023-10-30T14:29
updated: 2024-11-27T20:31
---
[[Callback là những hàm được dùng như đối số của hàm khác]]. Ví dụ như ta hay thấy người ta viết thế này:
```js
function callback(x) {
  return x + 1;
}
hàmGọi(callback); 
```

Nhưng để code này chạy được được thì phải truyền đối số cho callback vào chứ? Nên đáng lẽ phải gán giá trị cho `x` rồi thì code mới chạy được chứ?
```js
function callback(x) {
  return x + 1;
}
const x = 123;
hàmGọi(callback(x)); 
```

Nhưng nếu viết như vậy thì `callback(123)` mới được dùng làm đối số của `hàmGọi()`. Giá trị được truyền vào `hàmGọi()` là `124`, chứ không phải là `callback`. Để được gọi là callback, [[Callback là những hàm được dùng như đối số của hàm khác|nó phải là hàm được dùng như đối số của hàm khác]].

Thực ra nãy giờ ta chưa xét xem `hàmGọi()` có những gì trong đó. Nếu xét thì sẽ thấy nó đã định nghĩa sẵn giá trị sẽ được truyền vào hàm được gọi rồi:
```js
function hàmGọi(callback){
	const x = ...
	callback(x)
} 
```

Điều này cũng có nghĩa là callback bắt buộc phải có đúng thứ tự và kiểu biến được hàm gọi cho trước