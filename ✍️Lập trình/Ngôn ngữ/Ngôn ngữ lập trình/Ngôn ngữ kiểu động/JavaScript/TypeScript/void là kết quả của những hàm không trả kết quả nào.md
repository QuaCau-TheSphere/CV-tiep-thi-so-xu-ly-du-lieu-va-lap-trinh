---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
Khi hàm không dùng từ khoá `return` thì tức là hàm đó chỉ dùng để gom nhiều hàm khác lại làm một thôi chứ không có chạy gì cả. Đồng nghĩa với việc nó dùng `return void`.

Ví dụ, hàm này:
```js
function chạyHàmVoid(){
	console.log(1+1)
} 
chạyHàmVoid()
```
Không trả về kết quả nào, dù console có hiện ra là 2. 