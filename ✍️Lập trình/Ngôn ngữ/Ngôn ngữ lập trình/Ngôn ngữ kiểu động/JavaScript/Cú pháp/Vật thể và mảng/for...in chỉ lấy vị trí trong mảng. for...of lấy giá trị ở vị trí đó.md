---
share: true
created: 2023-10-24T18:26
updated: 2025-03-03T18:48
---
Giả sử ta có một mảng:
```js
const dsMàu = ['đỏ', 'cam', 'vàng'];
```
Đây là kết quả khi ta dùng `for...in`:
```js
for (const i in dsMàu) {
   console.log(i); // "0", "1", "2"
}
```
Còn đây là kết quả khi ta dùng `for...of`:
```js
for (const i of dsMàu) {
   console.log(i); // "đỏ", "cam", "vàng"
}
```

## So sánh đặc điểm

|                         | `for...in`                                                                           | `for...of`                                                                                        |
| ----------------------- | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------- |
| Thứ được duyệt          | Các `key` của các thuộc tính đếm được (enumerable properties) của vật thể            | Các phần tử của một vật thể lặp được (iterable object)                                            |
| Vật thể dùng được       | Chuỗi, mảng, vật thể đơn giản                                                        | Chuỗi, mảng, tập hợp, ([[Map trong JS tương đương với dictionary trong Python\|ánh xạ, từ điển]]) |
| Vật thể không dùng được | Tập hợp, ([[Map trong JS tương đương với dictionary trong Python\|ánh xạ, từ điển]]) | Vật thể đơn giản                                                                                  |

## Ví dụ kết quả
Bảng dưới đây so sánh kết quả khi `console.log()` trong `for...in` và `for...of` với từng đối tượng khác nhau. Ví dụ, với hàng 1 thì nó sẽ trông như này:
```js
for (const i in {a: 1, b: 2, c: 3}) {
  console.log(i);
}
for (const i of {a: 1, b: 2, c: 3}) {
  console.log(i);
}
```

| Đối tượng | Ví dụ                           | Kết quả khi dùng `for...in`            | Kết quả khi dùng `for...of` |
| --------- | ------------------------------- | -------------------------------------- | --------------------------- |
| Vật thể   | `{a: 1, b: 2, c: 3}`            | `a, b, c (object property names)`      | `TypeError (not iterable)`  |
| Tập hợp   | `new Set(['a', 'b', 'a', 'd'])` | `undefined (no enumerable properties)` | `a, b, d (Set values)`      |

Nguồn:: [Sự khác biệt giữa for....in, for....of and forEach trong javascript](https://anonystick.com/blog-developer/su-khac-biet-giua-forin-forof-and-foreach-trong-javascript-2020041337746860)

## Dùng `for...in` tiện hơn khi thao tác với nhiều mảng cùng lúc, hoặc khi cần thao tác giữa các phần tử
Việc thao tác với nhiều mảng cùng lúc, hoặc so sánh giữa các phần tử đều có một đặc điểm chung là **cần chỉ số**:

VD về việc thao tác với nhiều mảng cùng lúc:
```js
arr1 = ['John', 'Mary', 'Tom']; 
arr2 = ['cat', 'dog', 'mouse']

for (const i in arr1) {
    console.log(arr2[i])
}
```

VD về việc thao tác giữa các phần tử:
```js
arr = [1, 3, 2]; 

for (const i in arr) {
    const sum = arr[i] + arr[i+1]
    console.log(sum)
}
```

Trong những trường hợp này, nếu dùng `for...of` thì sẽ cần lấy lại chỉ số. Hàm lấy chỉ số là `indexOf()`. Nhưng nó có nhược điểm là chỉ lấy chỉ số đầu tiên, nên có thể không chính xác.

## Dùng `for...in` trong TypeScript
Khi dùng:
```js
for (const i in mảng)
```
Trong TypeScript thì sẽ thấy `i` có kiểu là chuỗi chứ không phải là số. Nếu để trực tiếp vào nơi cần kiểu là số thì sẽ bị báo lỗi không đúng kiểu, VD như `mảng[i -1]`, `if (i===0)`. Để xử lý thì có những cách sau:
- Tạo thêm biến phụ: `const ii = Number(i)`
- Chạy `for...of` ở một mảng mới là mảng chỉ chứa chỉ mục của mảng cũ:
  ```js
  for (const i of Object.keys(mảng).map(Number))
  ```

[[Nếu cần tạo một mảng mới từ mảng cũ thì dùng map() tiện hơn dùng for]] 