---
share: true
created: 2023-08-25T14:20
updated: 2025-08-01T08:23
---

Để `regex.test()` ngay trong `if`:
```js
var string = 'aaa lấy tôi bbb'
var regex = new RegExp('lấy tôi', 'gi');
console.log("kết quả của regex.test khi ở ngoài if:", regex.test(string))
if (regex.test(string)) {
    console.log("Nếu dòng này hiện nghĩa là điều kiện bằng true")
}

//kết quả của regex.test khi ở ngoài if: true
```

Cách sửa: tạo biến cho `regex.test()` trước:
```js
var string = 'aaa lấy tôi bbb'
var regex = new RegExp('lấy tôi', 'gi');
test = regex.test(string)
console.log("kết quả của regex.test khi ở ngoài if:", test)
if (test) {
    console.log("Nếu dòng này hiện nghĩa là điều kiện bằng true")
}

//kết quả của regex.test khi ở ngoài if: true
//Nếu dòng này hiện nghĩa là điều kiện bằng true
```

[Regex.test(value) returns true when logged but false within an if statement](https://stackoverflow.com/a/59694184/3416774)

