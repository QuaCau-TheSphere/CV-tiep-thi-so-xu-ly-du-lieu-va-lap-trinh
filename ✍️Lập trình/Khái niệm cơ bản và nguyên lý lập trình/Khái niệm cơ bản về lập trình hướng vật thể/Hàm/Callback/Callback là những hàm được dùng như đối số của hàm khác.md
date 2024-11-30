---
share: true
created: 2023-10-24T18:26
updated: 2024-11-27T20:22
---
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

Với những hàm được viết với tâm thế là sẽ được truyền vào một hàm khác như là biến như thế này, ta gọi là callback. [[Hàm gọi callback đã xác định sẵn tham số truyền vào cho callback rồi|Những hàm gọi callback đã xác định sẵn tham số truyền vào cho nó rồi]]

