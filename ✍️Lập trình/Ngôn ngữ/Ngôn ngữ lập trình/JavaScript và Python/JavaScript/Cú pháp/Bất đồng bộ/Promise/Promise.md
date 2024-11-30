---
share: true
created: 2023-10-30T14:29
updated: 2024-11-30T13:56
description: Thứ gì được truyền vào `resolve()` sẽ được truyền vào `result` và vào `then()`. Thứ gì được truyền vào `reject()` sẽ được truyền vào `result` và vào `catch()`
---
[[Vật thể là những dữ liệu có những thuộc tính thành phần]]. [[Lớp là một cái khuôn để tạo các vật thể cho nhanh]]. `Promise` vừa là tên của một lớp được định nghĩa sẵn trong JS, vừa là tên hay được đặt cho các vật thể được tạo ra từ lớp đó:
```js
const promise = new Promise(...);
```

Vế trái của biểu thức này là vật thể `promise`. Vế phải của biểu thức này là lớp `Promise`. Ta hãy lần lượt xét hai vế này, xem chuyện gì xảy ra bên trong chúng.

## Lớp `Promise`
Lớp `Promise` không nhận đối số là các giá trị như bình thường mà là cả một hàm. Hàm này được đặt tên là hàm thực thi (executor):
```ts
function hàmThựcThi(...){}
const promise = new Promise(hàmThựcThi);
```

Bạn đã dành thời gian để tìm hiểu về `Promise`, tức là bạn đang quan tâm làm sao để xử lý các hàm bất đồng bộ, để làm sao việc thực thi các hàm tốn thời gian để chạy không trở thành kỳ đà cản mũi việc chạy các hàm không liên quan khác. Khi bạn gặp một hàm như vậy, bạn hãy cho nó vào bên trong hàm thực thi. Việc gom chúng lại thành một mối sẽ giúp bạn chỉ phải quản lý một lần. Vì hàm thực thi chứa các hàm chạy tốn thời gian, nên bản thân nó cũng sẽ tốn thời gian để chạy. [[Sự bất đồng bộ có tính lây lan. Bất kỳ hàm nào gọi hàm bất đồng bộ đều trở thành hàm bất đồng bộ|Bất kỳ hàm nào gọi hàm bất đồng bộ đều sẽ trở thành hàm bất đồng bộ. Sự bất đồng bộ có tính lây lan.]]

Đối số của hàm thực thi, đến lượt nó, cũng là 2 hàm khác nhau, được gọi lần lượt là hàm giải quyết và hàm từ chối:
```js
function hàmThựcThi(hàmGiảiQuyết, hàmTừChối){
    // ...
    hàmGiảiQuyết(...)
    // ...
    hàmTừChối(...)
}
```

Khi [[Code giống như các nốt nhạc, bộ máy giống như nhạc công, còn môi trường thực thi giống như nhạc cụ|bộ máy]] của JS đọc tới dòng này:
```js
const promise = new Promise(hàmThựcThi);
```
thì sẽ có 2 chuyện được xảy ra:
- Vật thể `promise` sẽ được tạo ra với hai thuộc tính là `state` và `result`. `state` sẽ được gán sẵn giá trị là `pending`. `result` thì chưa được gán giá trị nào, hay nói cách khác giá trị của nó là `undefined`
- Hàm thực thi sẽ được chạy

Không cần biết bên trong hàm thực thi viết những gì, rồi sẽ tới lúc hàm giải quyết hoặc hàm từ chối sẽ được gọi. **Số phận của vật thể `promise` sẽ được định đoạt thế nào tuỳ thuộc vào việc hàm nào được gọi trước.** Nếu hàm giải quyết được gọi trước, thì thuộc tính `state` của vật thể đang từ `pending` sẽ được gán giá trị mới là `fulfilled`. Ngược lại, nếu hàm từ chối được gọi trước, thì thuộc tính `state` của nó sẽ được gán giá trị mới là `rejected`. **Ở cả hai trường hợp, giá trị được truyền vào trong hàm giải quyết/hàm từ chối sẽ được gán cho `result`.**

Đáng lẽ là bạn phải định nghĩa hàm giải quyết và hàm từ chối. Nhưng khi chúng được dùng làm đối số cho hàm được dùng làm đối số cho lớp `Promise` (tức là hàm thực thi), thì JS sẽ tự động [[resolve, reject là hai hàm được JS cung cấp sẵn để làm đối số cho hàm thực thi|định nghĩa sẵn]] hai hàm này luôn, bạn không cần định nghĩa gì cả. Và thường người viết hay đặt tên cho hàm giải quyết là `resolve` và hàm từ chối là  `reject`. Kết hợp với việc dùng [[Hàm vô danh, hàm mũi tên, lambda là những cái tên khác nhau cho cùng một thứ|cú pháp mũi tên cho hàm]], bạn sẽ hay thấy người ta viết code như này:
```js
const promise = new Promise((resolve, reject) => {
    // ...
    resolve(giáTrịSẽĐượcGánChoResult)
    // ...
    reject(giáTrịSẽĐượcGánChoResult)
});
```

Các tác giả của JS đã thiết kế lớp `Promise` để *không* nhận kết quả của hàm thực thi. Tức là việc bạn `return` trong hàm thực thi không có tác dụng gì, ngoài trừ việc làm cho nó kết thúc sớm. Nếu nó kết thúc trước khi hàm giải quyết hoặc hàm từ chối được gọi thì vật thể `promise` sẽ ở trạng thái `pending` mãi mãi. Nếu nó có lỗi thì mặc định là đang gọi hàm từ chối.

Khi hàm giải quyết được gọi:
- Thuộc tính `state` đang từ `pending` sẽ được gán giá trị mới là `fulfilled`
- Giá trị được truyền vào trong hàm giải quyết sẽ được gán vào thuộc tính `result` 
- Hàm được dùng làm đối số thứ nhất của `then()` sẽ chạy

Ngược lại, khi hàm từ chối được gọi:
- Thuộc tính `state` đang từ `pending` sẽ được gán giá trị mới là `rejected`
- Giá trị được truyền vào trong hàm từ chối sẽ được gán vào thuộc tính `result` 
- Hàm được dùng làm đối số thứ hai của `then()` sẽ chạy

## Vật thể `promise`
[[Vật thể promise có 2 thuộc tính là state và result, và 3 phương thức là then, catch, và finally|Vật thể promise có 2 thuộc tính và 3 phương thức]]. 2 thuộc tính đó là `state` và `result`. 3 phương thức đó là `then()`, `catch()` và `finally()`. 

Khi [[Code giống như các nốt nhạc, bộ máy giống như nhạc công, còn môi trường thực thi giống như nhạc cụ|engine]] của JS đọc tới dòng này:
```js
const promise = new Promise(hàmThựcThi);
```
thì một vật thể `promise` được tạo ra với hai thuộc tính là `state` và `result`. `state` sẽ được gán sẵn giá trị là `pending`. `result` thì chưa được gán giá trị nào, hay nói cách khác giá trị của nó là `undefined`.

**Bạn không lấy được giá trị của `result` một cách trực tiếp, mà phải lấy qua `then()` hoặc `catch()`.** Ta hãy nói về `then()` trước. Tương tự như hàm thực thi của lớp `Promise`, khi mà cả 2 đối số của nó đều là hàm, cả 2 đối số của `then()` cũng là hàm. Sự sắp xếp này là có ý đồ:

| Vị trí đối số của... | ...hàm thực thi | ...`then()`                 |
| -------------------- | --------------- | --------------------------- |
| 1                    | Hàm giải quyết  | Hàm nhận kết quả giải quyết |
| 2                    | Hàm từ chối     | Hàm nhận lý do từ chối      |

Chắc bạn cũng đã đoán được cơ chế hoạt động của chúng. Khi hàm giải quyết được gọi trong hàm thực thi, hàm được dùng làm đối số thứ nhất của `then()` sẽ được gọi. Giá trị được truyền vào hàm giải quyết sẽ được truyền vào hàm này. Tương tự, khi hàm từ chối được gọi trong hàm thực thi, hàm được dùng làm đối số thứ hai của `then()` sẽ được gọi. Giá trị được truyền vào hàm từ chối sẽ được truyền vào hàm này. 

> [!Important] Tóm lại
> - Thứ gì được truyền vào hàm làm đối số thứ nhất của hàm thực thi, sẽ được truyền vào `result` và vào hàm làm đối số thứ nhất của `then()`
> - Thứ gì được truyền vào hàm làm đối số thứ hai của hàm thực thi, sẽ được truyền vào `result` và vào hàm làm đối số thứ hai của `then()`

`catch()` thực ra là `then()` khi đối số thứ nhất là `null`. Tức là, thứ gì được truyền vào hàm từ chối, sẽ được truyền vào hàm làm đối số của `catch()`. Tức là có thể viết lại bảng trên như sau:

|                                           | Nơi thông báo kết quả khi... | Nơi tiếp nhận kết quả khi... |
| ----------------------------------------- | ---------------------------- | ---------------------------- |
| ...hàm bất đồng bộ chạy thành công        | Hàm giải quyết               | `then()`                     |
| ...hàm bất đồng bộ gặp trục trặc khi chạy | Hàm từ chối                  | `catch()`                    |

Bảng 1 là dành cho cấp độ code, còn bảng 2 là ở cấp độ tư duy của con người. 

Còn `finally()` được dùng cho những công việc dùng để dọn dẹp mọi thứ sau khi chạy hàm bất đồng bộ, dù nó có được giải quyết hay không. Thường các hàm bất đồng bộ ít khi do bạn tự viết ra, mà là do các thư viện viết giùm bạn. Bạn sẽ được tài liệu của chúng hướng dẫn cụ thể hơn cách dùng `finally()` này.

Hàm thực thi của lớp `Promise` chứa hàm bất đồng bộ. Kết quả từ các hàm này sẽ được phát tán ra bên ngoài bằng các hàm giải quyết và từ chối. Tức là lớp `Promise` là bên cung cấp dữ liệu (producer). Dữ liệu đó được tiếp nhận trong thuộc tính `state` của vật thể `promise` và được xử lý trong `then()` và `catch()`. Tức là vật thể `promise` là bên tiêu thụ dữ liệu (consumer). 

Bằng cách này, việc chạy các hàm tốn thời gian để chạy sẽ không trở thành kỳ đà cản mũi cho việc chạy các hàm không liên quan khác, mà không gặp phải tình trạng callback hell. Nhược điểm của việc này là, bạn vẫn chỉ được nhận giá trị của chúng ở bên trong `then()`, vẫn chưa thể dùng được viết code với tư duy của việc chạy code tuần tự được. Để làm được điều này, bạn cần dùng tới [[await với async là cách để viết hàm bất đồng bộ với tư duy khi viết hàm tuần tự|await]].

Tham khảo:
- [Promise](https://javascript.info/promise-basics)
- [Promise - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [Tất tần tật về Promise và async/await - Ehkoo](https://doi-thoai.deno.dev/tat-tan-tat-ve-promise-va-async-await.5J.1)
```dataview
LIST rows.file.link
FROM "✍️Lập trình/Ngôn ngữ/Ngôn ngữ lập trình/JavaScript và Python/JavaScript/Cú pháp/Bất đồng bộ/Promise"
group by split(file.folder, "/")[8]
WHERE file.name != this.file.name
```

