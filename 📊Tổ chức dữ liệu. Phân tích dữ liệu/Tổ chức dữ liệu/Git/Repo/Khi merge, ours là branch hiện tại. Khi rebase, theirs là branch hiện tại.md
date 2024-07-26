---
share: true
created: 2023-10-30T14:29
updated: 2024-07-21T12:32
---
Khi merge là lấy commit từ branch khác về branch hiện tại
```
# Xem branch hiện tại
$ git branch
* branch-a

# Nếu là merge thì branch-a là ours
$ git merge -X ours branch-b  

# Nếu là rebase thì branch-a là theirs
$ git rebase -X theirs branch-b
```

Có lẽ thay vì dùng `ours` – `theirs`, ta nên dùng `current` – `theirs` cho merge, và `current` – `ours` cho rebase?