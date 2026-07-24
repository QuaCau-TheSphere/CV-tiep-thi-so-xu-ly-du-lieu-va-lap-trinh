---
share: true
created: 2023-10-30T14:29
updated: 2026-07-24T21:47
---
- `encodeURI()` mã hóa các ký tự đặc biệt, ngoại trừ: `~!@#$&*()=:/,;?+`
- `encodeURIComponent()` mã hóa các ký tự đặc biệt, ngoại trừ: `-_.!~*'()`

```js
s = "http://www.example.com/string with + and ? and & and spaces";
encodeURI(s)  //http://www.example.com/string%20with%20+%20and%20?%20and%20&%20and%20spaces
encodeURIComponent(s)  //http%3A%2F%2Fwww.example.com%2Fstring%20with%20%2B%20and%20%3F%20and%20%26%20and%20spaces
```

[javascript - What is the difference between decodeURIComponent and decodeURI? - Stack Overflow](https://stackoverflow.com/a/747712)

Nguồn:: [Should I use encodeURI or encodeURIComponent for encoding URLs?](https://stackoverflow.com/q/4540753/3416774)


If you're encoding a string to put in a URL component (a querystring parameter), you should call `encodeURIComponent`.

If you're encoding an existing URL, call `encodeURI`.
[[Mọi URL đều là URI]]


[[encodeURI nên được đặt tên là fixBrokenURI, còn decodeURI nên được đặt là potentiallyBreakMyPreviouslyWorkingURI]]
