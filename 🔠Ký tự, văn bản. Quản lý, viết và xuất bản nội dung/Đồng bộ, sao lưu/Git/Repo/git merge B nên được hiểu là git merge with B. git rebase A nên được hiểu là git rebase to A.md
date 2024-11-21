---
share: true
created: 2023-10-30T14:29
updated: 2024-09-19T23:08
---
Giả sử ta có 2 branch `A` và `B`. Ta đều muốn gắn B lên A.

Khi merge là lấy commit từ nơi khác về mình. Nên nếu muốn gắn B lên A thì phải đứng ở A để gọi lệnh merge lên B:
```
git switch A
git merge B
```
Tức là lúc này nên đọc lệnh này là
```
git merge B into A
```

Còn rebase là bứng commit hiện tại sang nơi khác. Nếu muốn gắn B lên A thì phải đứng ở B để gọi lệnh rebase lên A:
```
git switch B
git rebase A
```

[[Khi merge, ours là branch hiện tại. Khi rebase, theirs là branch hiện tại]]
Nguồn:: ![Merge vs Rebase \[Intermediate Git Tutorial\] - YouTube](https://youtu.be/xot40u-_1FI?si=NZpW5vl5Fq-WtjJL)