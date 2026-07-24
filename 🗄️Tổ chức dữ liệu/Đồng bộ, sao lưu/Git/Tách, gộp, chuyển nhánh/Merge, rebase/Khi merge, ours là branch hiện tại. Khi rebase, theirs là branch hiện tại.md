---
share: true
created: 2023-10-30T14:29
updated: 2026-07-06T21:41
---
[[git merge B nên được hiểu là git merge A with B. git rebase A nên được hiểu là git rebase B to A]]
Giả sử ta có 2 branch `A` và `B`. Ta đang ở A:
```
$ git branch
* A
  B
```

Khi merge là lấy commit từ branch khác về branch hiện tại, nên `A` sẽ là `ours`:
```
$ git merge -X ours B
```
Khi rebase thì bị ngược như vậy là vì 
```
# Nếu là rebase thì A là theirs
$ git rebase -X theirs B
```

Có lẽ thay vì dùng `ours` – `theirs`, ta nên dùng `current` – `theirs` cho merge, và `current` – `ours` cho rebase?
