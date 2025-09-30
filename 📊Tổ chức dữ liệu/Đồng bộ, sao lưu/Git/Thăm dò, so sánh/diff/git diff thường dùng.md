---
share: true
created: 2023-10-30T14:29
updated: 2025-05-02T17:23
---
![](https://i.sstatic.net/GhE7a.png)
Mặc định điểm cuối là working tree. Để thay đổi điểm cuối thì dùng --cache
## So sánh cùng một tệp giữa hai commit
```bash
git diff <commit 1> <commit 2> -- <file>
```
## So sánh hai tệp khác nhau giữa hai commit
```bash
git diff <commit 1>:<file 1> <commit 2>:<file 2>
```

