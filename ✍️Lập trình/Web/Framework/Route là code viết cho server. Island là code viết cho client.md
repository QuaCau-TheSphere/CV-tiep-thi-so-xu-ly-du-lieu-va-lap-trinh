---
share: true
created: 2023-10-30T14:29
updated: 2024-05-13T22:20
---
[[Các hàm được môi trường thực thi cung cấp không hoạt động được ở island]]
If all your JavaScript only runs in the client, then you don't have the problem of how do I share signals from the server to the client, simply because there is no js code running on the server. Same is true if everything is running on the server. When all code only ever runs in the same runtime, you avoid the whole "how do I share stuff with the other runtime" which is a pretty complex problem.

Regarding why sharing signals doesn't work per import statement across runtimes: It's the same problem as when you open your website in Chrome, trigger some signal update and then open the same site in Firefox. Despite you having updated the signal in Chrome, it won't be updated in Firefox, simply because they both run in their own runtime and have no clue update each other

Every other framework which renders parts on the server and parts of it on the client has this problem. Doesn't matter if they are built around the island concept or something else
Nguồn:: [Discord](https://discord.com/channels/684898665143206084/991511118524715139/1238477389663834152)

[[Route không bao giờ được gửi đến client. Island được chạy ở cả server và client]]
[[Render phía máy chủ nhanh và SEO tốt. Render phía người dùng phù hợp cho những ứng dụng cần tương tác nhiều]]
