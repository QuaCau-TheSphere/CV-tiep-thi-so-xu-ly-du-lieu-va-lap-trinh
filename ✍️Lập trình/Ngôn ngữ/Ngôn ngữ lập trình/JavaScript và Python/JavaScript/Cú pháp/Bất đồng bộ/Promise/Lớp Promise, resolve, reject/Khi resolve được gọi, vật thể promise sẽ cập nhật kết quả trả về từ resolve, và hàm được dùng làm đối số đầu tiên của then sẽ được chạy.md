---
share: true
created: 2023-10-30T14:29
updated: 2024-11-27T15:44
---
Lúc tạo vật thể promise thì [[Đối số của Promise là một hàm. Nó được gọi là hàm thực thi (executor)|đối số được dùng cho lớp Promise là một hàm được gọi là hàm thực thi]]:
```ts
function hàmThựcThi(biến1, biến2){}
const promise = new Promise(hàmThựcThi);
```

Đối số của hàm thực thi, đến lượt nó, cũng là 2 hàm khác nhau, được gọi lần lượt là hàm giải quyết và hàm từ chối:
```js
function hàmThựcThi(hàmGiảiQuyết, hàmTừChối){
    // ...
    hàmGiảiQuyết(giáTrịTrongHàmGiảiQuyết)
    // ...
    hàmTừChối(giáTrịTrongHàmTừChối)
}
const promise = new Promise(hàmThựcThi);
```

Đáng lẽ là bạn phải định nghĩa hàm giải quyết và hàm từ chối. Nhưng khi chúng được dùng làm biến cho hàm được dùng làm biến cho lớp `Promise` (tức là hàm thực thi), thì JS sẽ tự động [[resolve, reject là hai hàm được JS cung cấp sẵn để làm đối số cho hàm thực thi|định nghĩa sẵn]] hai hàm này luôn, bạn không cần định nghĩa gì cả. Và thường người viết hay đặt tên cho hàm giải quyết là `resolve` và hàm từ chối là  `reject`. Cho nên bạn sẽ hay thấy code người ta viết tắt lại như này:

```js
const promise = new Promise((resolve, reject) => {
    // ...
    resolve(giáTrịTrongHàmGiảiQuyết)
    // ...
    reject(giáTrịTrongHàmTừChối)
});
```

Nhớ rằng, [[Vật thể promise có 2 thuộc tính là state và result, và 3 phương thức là then, catch, và finally]]. Khi `resolve()` được gọi:
- Thuộc tính `state` đang từ `pending` sẽ được gán giá trị mới là `fulfilled`
- Giá trị được truyền vào trong `resolve()` sẽ được gán vào thuộc tính `result` 
- Hàm được dùng làm đối số đầu tiên của `then()` sẽ chạy

Ngược lại, khi `reject()` được gọi:
- Thuộc tính `state` đang từ `pending` sẽ được gán giá trị mới là `rejected`
- Giá trị được truyền vào trong `reject()` sẽ được gán vào thuộc tính `result`  
- Hàm được dùng làm đối số thứ hai của `then()` sẽ chạy

Nguồn:: [[Tự ngẫm nghĩ, trải nghiệm]]
