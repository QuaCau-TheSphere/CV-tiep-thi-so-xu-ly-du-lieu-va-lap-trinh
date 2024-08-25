---
share: true
created: 2023-10-30T14:29
updated: 2024-08-25T20:39
title: ~ và ^ là để chỉ các commit trước đó
---
```
G   H   I   J
 \ /     \ /
  D   E   F
   \  |  / \
    \ | /   |
     \|/    |
      B     C
       \   /
        \ /
         A

A =      = A^0
B = A^   = A^1     = A~1
C = A^2
D = A^^  = A^1^1   = A~2
E = B^2  = A^^2
F = B^3  = A^^3
G = A^^^ = A^1^1^1 = A~3
H = D^2  = B^^2    = A^^^2  = A~2^2
I = F^   = B^3^    = A^^3^
J = F^2  = B^3^2   = A^^3^2
```


Lưu ý: `A~2 = D`, nhưng `A^2 = C`

> [!tip] Cách nhớ
> - `~` nằm ngang nên nó chỉ đi thẳng
> - `^` có sự hội tụ giữa hai đường nên nó là dành cho merge

[![Illustration of relative references in Git](https://i.stack.imgur.com/Ye1H7.jpg)](https://i.stack.imgur.com/Ye1H7.jpg)

[[HEAD là commit hiện tại]]. [[@ là viết tắt của HEAD]]
Nguồn:: [[✍️Lập trình/Ξ Nguồn và tài nguyên hỗ trợ/Ξ Nguồn/Stack Overflow]], [What's the difference between HEAD^ and HEAD\~ in Git? - Stack Overflow](https://stackoverflow.com/q/2221658/3416774)