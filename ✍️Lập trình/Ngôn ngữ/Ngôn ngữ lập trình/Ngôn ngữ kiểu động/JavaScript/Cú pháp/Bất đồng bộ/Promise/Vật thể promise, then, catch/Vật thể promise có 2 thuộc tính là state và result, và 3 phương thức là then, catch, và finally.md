---
share: true
created: 2023-10-30T14:29
updated: 2024-11-28T14:08
---
[[Để lấy được giá trị state và result của promise, cần dùng các phương thức then và catch]]
[[Vật thể promise có 2 thuộc tính là state và result, và 3 phương thức là then, catch, và finally]]
[[Kết quả của promise chỉ có thể được lấy ở trong then, và phải ở dạng hàm]]
![](https://javascript.info/article/promise-basics/promise-resolve-reject.svg)

Nguồn:: [Promise](https://javascript.info/promise-basics)
Nguồn:: [Tất tần tật về Promise và async/await - Ehkoo](https://ehkoo.com/bai-viet/tat-tan-tat-ve-promise-va-async-await)

- `.catch(errorHandlingFunction)` tương đương với `.then(null, errorHandlingFunction)`
- `.finally()` không cần đối số, và thường được dùng để dọn dẹp