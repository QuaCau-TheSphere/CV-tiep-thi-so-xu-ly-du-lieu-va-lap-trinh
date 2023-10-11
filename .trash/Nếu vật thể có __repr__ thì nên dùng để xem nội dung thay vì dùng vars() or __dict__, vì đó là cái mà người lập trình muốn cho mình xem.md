---
share: true
created: 2023-09-27T15:07
updated: 2023-09-27T15:15
---
I was advised to not use `vars()` or `__dict__`, just use the actual API of the classes. If an object isn't printing well without that introspection, then that's the devs fault for not writing proper string and print methods (usually via `__repr__`). Or in other words, Python defers the responsibility to display the objects to the dev, while JS takes that responsibility.
Nguồn:: [Is it correct that Python does not encourage us to read objects's content?](https://langdev.stackexchange.com/q/2966/223)

[[__repr__() trả về mô tả chi tiết để người lập trình bảo trì và sửa lỗi. __str__() trả về mô tả đơn giản cho người dùng sử dụng]] 