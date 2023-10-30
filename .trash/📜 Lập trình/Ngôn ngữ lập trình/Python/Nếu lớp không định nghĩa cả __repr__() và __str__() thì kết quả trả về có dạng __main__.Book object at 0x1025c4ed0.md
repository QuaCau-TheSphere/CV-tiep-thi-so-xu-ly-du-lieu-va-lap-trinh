---
share: true
created: 2023-09-27T22:34
updated: 2023-10-30T14:30
---
```python
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author

odyssey = Book("The Odyssey", "Homer")

print(odyssey)
print(repr(odyssey))
print(str(odyssey))
```

```
<__main__.Book object at 0x1025c4ed0>
```

This output is the default string representation of an object that’s inherited from the `object` class. The `object` class is the base class for all Python classes. It shows:

- **`__main__.Book`:** The name of the class and where it’s defined
- **`0x1025c4ed0`:** The memory address of the object

Nguồn:: [[Real Python]], [When Should You Use .\_\_repr\_\_() vs .\_\_str\_\_() in Python? – Real Python](https://realpython.com/python-repr-vs-str/)
