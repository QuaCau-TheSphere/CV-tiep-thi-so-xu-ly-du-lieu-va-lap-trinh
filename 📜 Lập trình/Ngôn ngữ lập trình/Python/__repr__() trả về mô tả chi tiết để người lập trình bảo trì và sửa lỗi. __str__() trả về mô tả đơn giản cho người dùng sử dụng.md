---
share: true
created: 2023-09-27T15:07
updated: 2023-10-24T18:26
---
Nguồn:: [[Real Python]], [When Should You Use .\_\_repr\_\_() vs .\_\_str\_\_() in Python? – Real Python](https://realpython.com/python-repr-vs-str/)

I was advised to not use `vars()` or `__dict__`, just use the actual API of the classes. If an object isn't printing well without that introspection, then that's the devs fault for not writing proper string and print methods (usually via `__repr__`). Or in other words, Python defers the responsibility to display the objects to the dev, while JS takes that responsibility.
Nguồn:: [Is it correct that Python does not encourage us to read objects's content?](https://langdev.stackexchange.com/q/2966/223)
[[Trong REPL, gọi trực tiếp vật thể ra thì kết quả là __repr__(). Nếu dùng print thì kết quả là __str__()]]
[[Nếu lớp không định nghĩa cả __repr__() và __str__() thì kết quả trả về có dạng __main__.Book object at 0x1025c4ed0]] 