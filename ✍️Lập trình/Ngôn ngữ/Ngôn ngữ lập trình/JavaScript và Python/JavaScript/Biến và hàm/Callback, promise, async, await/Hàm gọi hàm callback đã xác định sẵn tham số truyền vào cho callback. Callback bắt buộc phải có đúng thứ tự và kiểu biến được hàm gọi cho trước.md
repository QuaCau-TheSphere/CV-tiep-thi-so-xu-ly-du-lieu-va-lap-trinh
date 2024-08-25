---
share: true
created: 2023-10-30T14:29
updated: 2024-08-18T15:05
---
[[Callback là những hàm được dùng như đối số của hàm khác]]. Khi dùng những hàm có callback, ta thắc mắc không biết tham số đã được truyền vào như thế nào? Ví dụ như:
```js
function callback (e) {
  console.log('clicked');
}

hàmNgoài(callback);
```

Ta thấy `callback()` là một hàm. Để nó hoạt động được thì phải truyền tham số vào. Nên đáng lẽ code trên phải là như vậy mới đúng chứ?

```js
function callback (e) {
  console.log('clicked');
}

const e = hàmNgoài();
callback(e)
```

Thực ra có thể nghĩ là `hàmNgoài()` đã được viết sẵn như vậy ở đâu đó:
```js
function hàmNgoài(callback){
	const e = ...
	callback(e)
} 
```