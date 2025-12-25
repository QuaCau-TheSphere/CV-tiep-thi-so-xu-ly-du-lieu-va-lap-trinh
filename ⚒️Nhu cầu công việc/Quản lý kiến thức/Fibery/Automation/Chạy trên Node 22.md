---
share: true
created: 2023-10-30T14:29
updated: 2025-10-13T09:05
---
Có vẻ như toàn bộ script sẽ được bọc trong một hàm. `return` của hàm này sẽ cho thông báo
Nguồn:: [What is the JS version? - API & Programming - Fibery Community](https://community.fibery.io/t/what-is-the-js-version/4837/9?u=ooker)
[[Node với Deno là những môi trường thực thi của JavaScript]]

Ngày xưa thì dùng Node 12. Mà Node 12 thì không có Temporal, nên nếu muốn dùng thì phải bundle với polyfill của Temporal. Nhưng nếu làm vậy thì script lại quá lớn, Fibery không chịu. Nên mới chấp nhận dùng dạng ISO.