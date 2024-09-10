---
share: true
created: 2024-01-12T14:31
updated: 2024-08-18T15:05
---
JSON là để cho máy viết, không phải cho người viết. Người muốn viết thì dùng YAML sẽ tốt hơn.
- Key phải được đóng trong ngoặc kép để:
	- Không dụng phải những reserved word trong JS, 
	- Không phải quan tâm xem "ký tự" là gì khi giải quyết unicode ([[Tuỳ vào phương thức mã hoá mà mỗi ký tự Unicode sẽ được biểu diễn bởi 1-4 đơn vị mã, 1-2 đơn vị mã, hoặc chỉ một đơn vị mã duy nhất]]) 
	- Tương thích hơn với Python, vì Python cũng bắt đóng ngoặc kép tất cả các key
- 
[[YAML thì để con người dễ đọc, còn JSON là để máy dễ đọc]]

Nguồn:: ![Douglas Crockford: The JSON Saga - YouTube](https://youtu.be/-C-JoyNuQJs?si=YbirDd_LCVQWUYNx&t=339)

Nếu muốn dùng comment thì có thể xài tạm:
```json
{"//": "A way to use comments in json"}
```
Còn không thì dùng JSONC