---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
## Callback là những hàm được dùng như đối số của hàm khác
Khi viết hàm ta có thể viết hàm con
```js
function hàmMẹ() {
    const a = 1
    function hàmCon(x){
        return x + 1
    }
    return hàmCon(a) + 1;
}
const kếtQuả = hàmMẹ()
console.log(kếtQuả) // 3
```

Giờ nếu như ta không định nghĩa hàm con ở bên trong mà ở bên ngoài, thì ta phải truyền nó vào trong hàm mẹ:
```js
function hàmCon(x){
    return x + 1
}
function hàmMẹ(hàmCon) {
    const a = 1
    return hàmCon(a) + 1;
}
const kếtQuả = hàmMẹ(hàmCon)
console.log(kếtQuả) // 3
```

Việc tách hẳn ra như vậy khiến cho mối quan hệ giữa chúng không còn là mẹ con với nhau nữa, mà chỉ là hàm nào gọi hàm nào mà thôi:
```js
function hàmĐượcGọi(x){
    return x + 1
}
function hàmGọi(hàmĐượcGọi) {
    const a = 1
    return hàmĐượcGọi(a) + 1;
}
const kếtQuả = hàmGọi(hàmĐượcGọi)
console.log(kếtQuả) // 3
```

Viết lại tên của chúng như thế này không làm thay đổi kết quả của code, nhưng lại thay đổi cách nghĩ của chúng ta. Đột nhiên, ta nhận ra được rằng ta có thể **tự do thay đổi hàm được gọi mà không phải thay đổi hàm gọi nữa**:
```js
const kếtQuả1 = hàmGọi(hàmĐượcGọi1)
const kếtQuả2 = hàmGọi(hàmĐượcGọi2)
const kếtQuả3 = hàmGọi(hàmĐượcGọi3)
```

Với những hàm được viết với tâm thế là sẽ được truyền vào một hàm khác như là biến như thế này, ta gọi là callback. 

## Callback đã xác định sẵn đối số truyền vào cho nó rồi
Ví dụ như ta hay thấy người ta viết thế này:
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

Nhưng nếu viết như vậy thì `callback(123)` mới được dùng làm đối số của `hàmGọi()`. Giá trị được truyền vào `hàmGọi()` là `124`, chứ không phải là `callback`. Để được gọi là callback, [[Callback là những hàm được dùng như đối số của hàm khác và đã xác định sẵn đối số truyền vào cho nó rồi|nó phải là hàm được dùng như đối số của hàm khác]].

Thực ra nãy giờ ta chưa xét xem `hàmGọi()` có những gì trong đó. Nếu xét thì sẽ thấy nó đã định nghĩa sẵn giá trị sẽ được truyền vào hàm được gọi rồi:
```js
function hàmGọi(callback){
	const x = ...
	callback(x)
} 
```

Điều này cũng có nghĩa là callback bắt buộc phải có đúng thứ tự và kiểu biến được hàm gọi cho trước