---
share: true
created: 2023-10-24T18:26
updated: 2024-04-27T16:19
---
```js
api.getUser('pikalong', function (err, user) {
  if (err) throw err
  api.getPostsOfUser(user, function (err, posts) {
    if (err) throw err
    api.getCommentsOfPosts(posts, function (err, comments) {
      // vân vân và mây mây...
    })
  })
})
```

Ví dụ trên khi được viết lại bằng Promise sẽ là:

```js
api
  .getUser('pikalong')
  .then((user) => api.getPostsOfUser(user))
  .then((posts) => api.getCommentsOfPosts(posts))
  .catch((err) => {
    throw err
  })
```

Trích từ:: [Tất tần tật về Promise và async/await - Ehkoo](https://ehkoo.com/bai-viet/tat-tan-tat-ve-promise-va-async-await)
Promise được sinh ra để giải quyết những rắc rối của việc dùng quá nhiều callback. [[Callback là những hàm được dùng như đối số của hàm khác]]

[[await với async là cách để viết hàm bất đồng bộ với tư duy khi viết hàm tuần tự]]
[[Thực chất promise không giải quyết được chuyện lồng, vì promise cũng lồng vào nhau như if thôi. Thứ nó giải quyết là việc các giá trị trả về từ promise trông như không lồng vào nhau gì cả]] 