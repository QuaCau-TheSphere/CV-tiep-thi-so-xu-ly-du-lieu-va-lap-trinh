---
share: true
created: 2023-10-30T14:29
updated: 2025-05-22T23:49
---
[[Tất cả các thư mục bắt đầu bằng _ hoặc . mặc định đều bị bỏ ra]]. `_includes` cũng không phải là ngoại lệ. Nhưng việc bỏ ra đó chỉ là trong lúc build, chứ những tệp trong đó vẫn có thể được dùng cho plugin, template engine, processor, v.v.

if these assets are exported by their own (not imported by other files), yeah. I'd place them outside this folder. 


`_includes` phải ở trong `src`. ([[Tất cả mọi thứ đều phải ở trong src. Tất cả các đường dẫn đều bắt đầu từ src]])
Nguồn:: [The \_config file - Lume](https://lume.land/docs/configuration/config-file/#includes)
[Discord](https://discord.com/channels/794537085641818124/1375147431532171366)