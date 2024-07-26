---
share: true
created: 2023-10-30T14:29
updated: 2024-07-09T14:14
---
### Cách sử dụng sai

```javascript
// ❌ không nên dùng
useEffect(async () => {
  const data = await fetchData();
}, [fetchData])
```

Nếu bạn viết dòng code trên, Linter sẽ báo lỗi ngay lập tức. Vấn đề ở đây là tham số đầu tiên của useEffect phải là 1 hàm trả về **undefined** hoặc là 1 hàm xóa side-effects. Trong khi đó, hàm async lại trả về một promise chứ không phải là function.

### Cách giải quyết
```javascript
useEffect(() => {
  // khi báo hàm lấy data
  async function fetchData() => {
    const data = await fetch('https://yourapi.com');
  }

  // gọi hàm
  fetchData()
    // bắt lỗi
    .catch(console.error);
}, [])
```
Cần xử lý gì thì cứ nhét hết vào `fetchData`. Ở dưới chỉ gọi mỗi hàm thôi.
Nguồn:: https://techmaster.vn/posts/37327/cach-su-dung-ham-async-trong-useeffect-co-vi-du

[[Dùng fetch dạng promise chứ đừng await trong component]]