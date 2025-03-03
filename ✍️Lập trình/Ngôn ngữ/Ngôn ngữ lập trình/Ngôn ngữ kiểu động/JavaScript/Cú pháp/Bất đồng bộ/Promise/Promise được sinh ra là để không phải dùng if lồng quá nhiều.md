---
share: true
created: 2023-10-24T18:26
updated: 2025-03-03T18:48
alias: Promise được sinh ra để giải quyết những rắc rối của việc dùng quá nhiều callback.
---
Promise được sinh ra để giải quyết những rắc rối của việc dùng quá nhiều callback. [[Callback là những hàm được dùng như đối số của hàm khác và đã xác định sẵn đối số truyền vào cho nó rồi]]
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


[[await với async là cách để viết hàm bất đồng bộ với tư duy khi viết hàm tuần tự]]
[[Sự bất đồng bộ có tính lây lan. Bất kỳ hàm nào gọi hàm bất đồng bộ đều trở thành hàm bất đồng bộ]]
Tham khảo:: [Tất tần tật về Promise và async/await - Ehkoo](https://ehkoo.com/bai-viet/tat-tan-tat-ve-promise-va-async-await)