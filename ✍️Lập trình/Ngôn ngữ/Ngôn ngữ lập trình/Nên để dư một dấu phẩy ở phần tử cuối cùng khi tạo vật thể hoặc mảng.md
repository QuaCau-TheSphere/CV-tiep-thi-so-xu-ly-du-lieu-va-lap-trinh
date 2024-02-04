---
share: true
created: 2023-10-30T14:29
updated: 2024-02-01T21:39
---
## Trailing comma là gì? Tại sao nó từng là lỗi trong JavaScript?

Trailing comma (dấu phẩy đuôi, dấu phẩy cuối) là việc để dư **một dấu phẩy** sau phần tử cuối cùng ở cuối một danh sách (có thể là phần tử trong Array literal, property trong Object literal, tham số của hàm…). Ví dụ:

```
// trailing comma trong Array literal
var categories = ['men', 'women', 'accessories']
// trailing comma trong Object literal
var person = {
  name: 'Harry Potter',
  gender: 'male',
  house: 'Gryffindor',
}
// trailing comma trong tham số của hàm (và trong lời gọi hàm)
function compare(param1, param2) {
  /* ... */
}
```

Như bạn thấy, dấu phẩy vốn để ngăn cách **giữa** các phần tử trong một danh sách, và dấu phẩy cuối là dư thừa về mặt cú pháp. Để dễ hình dung hơn, ví dụ mảng ở trên nếu viết trên cùng một dòng sẽ là `var categories = ['men', 'women', 'accessories',]`. Trong thực tế, với các trình duyệt cũ chỉ hỗ trợ [ECMAScript 3](https://int3ractive.com/2019/01/nhung-dieu-can-biet-ve-ecmascript.html) trở về trước (IE8), trailing comma sẽ gây ra lỗi cú pháp lúc chạy.

![](https://res.cloudinary.com/duqeezi8j/image/upload/f_auto/v1557078885/trailing-comma-ie8-error_ulcpmq.jpg) _Trailing comma gây ra lỗi cú pháp lúc chạy trên IE8. Hình screenshot lấy từ [StackOverflow](https://stackoverflow.com/questions/17490014/website-causes-script-error-in-ie8)._

Tuy nhiên, kể từ ECMAScript 5, trailing comma được chấp nhận cho danh sách phần tử Array và Object property. Việc lấy số phần tử (`array.length`) vẫn đúng với Array có trailing comma.

## Tại sao trailing comma trở thành best practice?

### 1. Phần tử khi thêm vào cuối sẽ luôn đồng nhất và tách bạch

Khi không dùng trailing comma, việc thêm phần tử vào cuối danh sách sẽ gây ảnh hưởng đến phần tử kế cuối vừa được thêm dấu phẩy và commit log của bạn sẽ như thế này:

```
  var categories = [
    'men',
    'women',
```

```
   'accessories'
```

```
   'accessories',
```

```
   'children'
  ];
```

Khi có trailing comma, commit log của bạn sẽ chỉ hiển thị phần thay đổi:

```
  var categories = [
    'men',
    'women',
    'accessories',
```

```
   'children',
  ];
```

### 2. Dễ dàng sắp xếp lại thứ tự và cập nhật danh sách

Vì tất cả các phần tử đều kết thúc bằng dấu phẩy, sắp xếp lại thứ tự phần tử bất kỳ đơn giản và dễ dàng:

![Sắp xếp lại phần tử trong mảng](https://res.cloudinary.com/duqeezi8j/image/upload/v1557079010/trailing-comma-reorder_gloufm.gif) _Sắp xếp lại phần tử trong mảng_

### 3. Giảm số dòng conflict khi merge với version control

![Conflict code hiển thị khi không dùng và có dùng trailing comma](https://res.cloudinary.com/duqeezi8j/image/upload/f_auto/v1557079047/trailing-comma-conflict_fwvzyk.jpg) _Conflict code hiển thị khi không dùng (trên) và có dùng (dưới) trailing comma_

Trong ví dụ không dùng trailing comma, mặc dù phần tử `female` đều thêm cùng một dấu phẩy, Git vẫn không tự động merge dòng này và vẫn báo conflict cùng với dòng thay đổi tiếp theo. Việc theo dõi những dòng conflict vô nghĩa này sẽ gây khó khăn cho người merge và rất dễ gây ra sai sót bị mất code sau khi resolve.

Ngoài ra, khi số dòng thay đổi ít đi thì khả năng conflict code sẽ giảm và khả năng code tự merge sẽ cao hơn.

Nguồn:: [Tại sao lại để dư một dấu phẩy? - Ehkoo](https://ehkoo.com/bai-viet/why-trailing-comma-javascript)

[[JSON không cho phép để dư dấu phẩy, không có comment, bắt buộc phải dùng ngoặc kép, key phải được đóng trong ngoặc kép]]