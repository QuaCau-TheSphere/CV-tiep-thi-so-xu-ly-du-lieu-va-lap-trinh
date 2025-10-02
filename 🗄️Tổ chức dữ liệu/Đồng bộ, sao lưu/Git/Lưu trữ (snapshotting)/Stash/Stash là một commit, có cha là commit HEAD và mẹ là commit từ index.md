---
share: true
created: 2023-10-30T14:29
updated: 2025-05-02T12:48
---
> A stash entry is represented as a commit whose tree records the state of the working directory, and its first parent is the commit at HEAD when the entry was created. The tree of the second parent records the state of the index when the entry is made, and it is made a child of the HEAD commit. The ancestry graph looks like this:
> 
> ```
>        .----W
>       /    /
> -----H----I
> ```
> 
> where H is the HEAD commit, I is a commit that records the state of the index, and W is a commit that records the state of the working tree.

Các cách để thấy has của stash:
```
git reflog stash
git log --walk-reflogs stash
git log --reflog --oneline
git stash list --oneline
```

`git log --reflog --oneline` là alias của `git reflog`
`git stash list` thực ra là alias của `git reflog stash` (với một định dạng khác)

Nguồn:: [git - What is the difference between a stash and a regular commit? - Stack Overflow](https://stackoverflow.com/q/79602329/3416774)