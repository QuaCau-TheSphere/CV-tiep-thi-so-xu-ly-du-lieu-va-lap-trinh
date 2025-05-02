---
share: true
created: 2023-10-30T14:29
<<<<<<<< HEAD:🔠Ký tự, văn bản. Quản lý, viết và xuất bản nội dung/Đồng bộ, sao lưu/Git/Tách, gộp, chuyển nhánh/Merge, rebase/Khi merge, ours là branch hiện tại. Khi rebase, theirs là branch hiện tại.md
updated: 2025-05-01T16:29
========
updated: 2025-03-27T13:05
>>>>>>>> 5f11dac7c895c50f7b336ff591f2140907ee1c3d:🔠Ký tự, văn bản. Quản lý, viết và xuất bản nội dung/Đồng bộ, sao lưu/Git/Chia sẻ, cập nhật dự án/Merge, rebase/Khi merge, ours là branch hiện tại. Khi rebase, theirs là branch hiện tại.md
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