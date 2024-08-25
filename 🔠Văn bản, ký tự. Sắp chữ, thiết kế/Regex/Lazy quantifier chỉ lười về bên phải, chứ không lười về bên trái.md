---
share: true
created: 2023-10-24T16:28
updated: 2024-08-25T20:40
---
Nếu bạn có chuỗi sau:
```
START START word word word END
```
và có regex này với cờ `gm`:
```
START.*?END
```

Thì kết quả sẽ không phải là:
```
START word word word END
```

mà là nguyên chuỗi gốc.

Nhưng nếu chuỗi có dạng:
```
START word word word END END
```

Thì nó sẽ ra đúng kết quả.

Nguồn:: [[Stack Overflow]], [Why is the lazy quantifier indeed lazy to the right, but not to the left?](https://stackoverflow.com/q/77134671/3416774)
