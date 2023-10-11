---
share: true
created: 2023-09-12T13:33
updated: 2023-09-19T14:01
---
Điều này dễ thấy nhất khi tên file có ở trong biến. Ví dụ, thay vì có thể viết `foo $filename`, ta phải viết `foo "$filename"`. Vì nhỡ `$filename` có khoảng trắng thì 

Khi viết code thì tốt nhất dùng dạng raw. Ví dụ:
```js
const cmd = new Deno.Command("deno", { args: ["run", "--allow-all", "--allow-run", String.raw`${filename}`, câuNhập, '--json-debug'] });
```

Trong việc xử lý URL, dấu cách sẽ được chuyển sang `%20`. Nếu sau đó có tên thì sẽ dễ gây hiểu lầm: `ảnh 1.jpg` → `ảnh%201.jpg`

Nếu code HTTP không xử lý tốt thì khi người dùng tải `Danh sách.pdf` thì thứ họ nhận được là file `Danh`. Họ phải thêm đuôi `.pdf` thủ công

docker và git bắt phải dùng ký tự ascii và không có khoảng trắng

[](https://stackoverflow.com/posts/9123555/timeline)

You should take the spaces out of the filename. Because the filename is used as the identifier for imported modules (i.e. `foo.py` will be imported as `foo`) and Python identifiers can't have spaces, this isn't supported by the `import` statement.

If you _really_ need to do this for some reason, you can use the `__import__` function:

```python
foo_bar = __import__("foo bar")
```

This will import `foo bar.py` as `foo_bar`. This behaves a little bit different than the `import` statement and you should avoid it.