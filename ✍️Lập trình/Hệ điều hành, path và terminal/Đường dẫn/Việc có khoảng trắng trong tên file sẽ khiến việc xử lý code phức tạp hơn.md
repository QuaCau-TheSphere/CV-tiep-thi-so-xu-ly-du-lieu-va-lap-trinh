---
share: true
created: 2023-09-12T13:33
updated: 2024-08-25T20:38
---
Điều này dễ thấy nhất khi tên file có ở trong biến. Ví dụ, thay vì có thể viết `foo $filename`, ta phải viết `foo "$filename"`. Vì nhỡ `$filename` có khoảng trắng thì 

Khi viết code thì tốt nhất dùng dạng raw. Ví dụ:
```js
const cmd = new Deno.Command("deno", { args: ["run", "--allow-all", "--allow-run", String.raw`${filename}`, câuNhập, '--json-debug'] });
```

Trong việc xử lý URL, dấu cách sẽ được chuyển sang `%20`. Nếu sau dấu cách có ký tự số thì sẽ dễ gây hiểu lầm: `ảnh 1.jpg` → `ảnh%201.jpg`.

Nếu code HTTP không xử lý tốt thì khi người dùng tải `Danh sách.pdf` thì thứ họ nhận được là file `Danh`. Họ phải thêm đuôi `.pdf` thủ công.

Docker và Git bắt phải dùng ký tự ASCII và không có khoảng trắng

[[Tên mô đun Python sẽ được dùng làm identifier. Identifier không được có dấu cách]]

