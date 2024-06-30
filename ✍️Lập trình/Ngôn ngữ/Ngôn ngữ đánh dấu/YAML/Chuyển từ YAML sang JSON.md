---
share: true
created: 2023-10-30T14:29
updated: 2024-03-20T21:47
---
Tốt nhất là dùng một [YAML Parser Online](https://jsonformatter.org/yaml-parser) để kiểm tra.

Dấu liệt kê `- ` phía trước và dấu hai chấm `:` phía sau sẽ quyết định nhiều thứ
# Khi chỉ xét một dòng
| Có `- ` phía trước A | Có`:` phía sau A | Kết quả: A là...                               | YAML   | JSON            |
| -------------------- | ---------------- | ---------------------------------------------- | ------ | --------------- |
| ✔                    | ✔                | Chuỗi                                          | `A`    | `"A" `          |
| ✔                    | ❌               | Một phần tử của một danh sách                  | `- A`  | `["A"]`         |
| ❌                   | ✔                | Thuộc tính của một vật thể                     | `A:`   | `{"A": null}`   |
| ✔                    | ✔                | Thuộc tính của một vật thể trong một danh sách | `- A:` | `[{"A": null}]` |


# Khi xét 2 dòng
Trong các đoạn code sau, ở trên là YAML, ở dưới là JSON.

## Khi A là chuỗi thì B có là gì thì cũng nằm trong cùng chuỗi với A
| Dòng | Có `- ` phía trước | Có `:` phía sau |
| ---- | ------------------ | --------------- |
| A    | ❌                 | ❌              |

**B không có `- ` phía trước:**

```yaml
A
B
```
```json
"A B" 
```
**B có `- ` phía trước:**
```yaml
A
- B
```
```json
"A - B" 
```
Nếu B có `:` phía sau thì sẽ ra lỗi.

## `- A` 
Khi A chỉ có `- ` phía trước thì A là một phần tử của danh sách.
### `- B`
| Dòng | Có `- ` phía trước | Có `:` phía sau |
| ---- | ------------------ | --------------- |
| A    | ✔                  | ❌              |
| B    | ✔                  | ❌              |

Nếu B cũng chỉ có `- ` phía trước thì A với B là các phần tử của một danh sách
```yaml
- A
- B
```
```json
[
  "A", 
  "B"
]
```
### `- B:`
| Dòng | Có `- ` phía trước | Có `:` phía sau |
| ---- | ------------------ | --------------- |
| A    | ✔                  | ❌              |
| B    | ✔                  | ✔              |

Nếu B có cả `- ` phía trước và `:` phía sau thì B là thuộc tính của một vật thể trong cùng danh sách với A (A và `{B:}` cùng danh sách).
```yaml
- A
- B:
```
```json
[
  "A", 
  {
    "B": null
  }
]
```
###  `B` hoặc `B:` (lỗi) 

| Dòng | Có `- ` phía trước | Có `:` phía sau |
| ---- | ------------------ | --------------- |
| A    | ✔                  | ❌              |
| B    | ❌                 |                |
## `A:`
Khi A chỉ có `:` phía sau thì A là một thuộc tính của một vật thể.
### `B` (Lỗi)
| Dòng | Có `- ` phía trước | Có `:` phía sau |
| ---- | ------------------ | --------------- |
| A    | ❌                 | ✔               |
| B    | ❌                 | ❌              |
```yaml
A:
B
```
Lỗi:
```
ERROR:

while scanning a simple key
  in "<unicode string>", line 2, column 1:
    B
    ^
could not found expected ':'
  in "<unicode string>", line 2, column 2:
    B
     ^
```
### `B:`
| Dòng | Có `- ` phía trước | Có `:` phía sau |
| ---- | ------------------ | --------------- |
| A    | ❌                 | ✔               |
| B    | ❌                 | ✔               |

Nếu A và B chỉ có `:` phía sau và đều cùng thẳng hàng với nhau thì A với B đều là thuộc tính của một vật thể:
```yaml
A:
B:
```
```json
{
  "A": null, 
  "B": null
}
```

### `- B`, `··- B`
| Dòng | Có `- ` phía trước | Có `:` phía sau |
| ---- | ------------------ | --------------- |
| A    | ❌                 | ✔               |
| B    | ✔                  | ❌               |

Nếu B chỉ có `- ` phía trước thì A là một danh sách, B là phần tử của danh sách A
```yaml
A:
- B
```
```json
{
  "A": [
    "B"
  ]
}
```

### `- B:`, `··- B:`
| Dòng | Có `- ` phía trước | Có `:` phía sau |
| ---- | ------------------ | --------------- |
| A    | ❌                 | ✔               |
| B    | ✔                  | ✔               |
Nếu B có `-` phía trước và `:` phía sau, thì A là một danh sách các vật thể, B là thuộc tính của một vật thể trong danh sách đó
```yaml
A:
- B: 
```
```json
{
  "A": [
    {
      "B": null
    }
  ]
}
```
### `··B`
Nếu B thụt dòng so với A và không có `- ` lẫn `:` thì B là giá trị của thuộc tính A.
```yaml
A:
  B
```
```json
{
  "A": "B"
}
```
### `··B:`
Nếu B thụt dòng so với A và chỉ có `:` phía sau thì giá trị của A là một vật thể, và B là thuộc tính của vật thể đó.
```yaml
A:
  B: 
```
```json
{
  "A": {
    "B": null
  }
}
```
## `- A:`
Nếu A có `-` phía trước và `:` phía sau thì A là thuộc tính của một vật thể trong một danh sách.
### `B`, `B:`, `··B` (lỗi) 
### `- B`
| Dòng | Có `- ` phía trước | Có `:` phía sau |
| ---- | ------------------ | --------------- |
| A    | ✔                  | ✔               |
| B    | ✔                  | ❌              |
```yaml
- A:
- B
```
```json
[
  {
    "A": null
  },
  "B"
]
```
### `··B:`
| Dòng | Có `- ` phía trước | Có `:` phía sau |
| ---- | ------------------ | --------------- |
| A    | ✔                  | ✔               |
| ··B  | ❌                 | ✔               |
```yaml
- A:
  B: 
```
```json
[
  {
    "A": null, 
    "B": null
  }
]
```
### `··- B`
| Dòng | Có `- ` phía trước | Có `:` phía sau |
| ---- | ------------------ | --------------- |
| A    | ✔                  | ✔               |
| ··B  | ✔                  | ❌              |
```yaml
- A:
  - B
```
```json
[
  {
    "A": [
      "B"
    ]
  }
]
```
### `··- B:`
| Dòng | Có `- ` phía trước | Có `:` phía sau |
| ---- | ------------------ | --------------- |
| A    | ✔                  | ✔               |
| ··B  | ✔                  | ✔               |
```yaml
- A:
  - B:
```
```json
[
  {
    "A": [
      {
        "B": null
      }
    ]
  }
]
```
# 1
```yaml
A:
  - B:
    C:
```
```json
{
  "A": [
    {
      "C": null, 
      "B": null
    }
  ]
}
```
# 2
```yaml
A:
  - B:
    - C
```
```json
{
  "A": [
    {
      "B": [
        "C"
      ]
    }
  ]
}
```
# 3
```yaml
A:
  - B:
    - C:
```
```json
{
  "A": [
    {
      "B": [
        {
          "C": null
        }
      ]
    }
  ]
}
```