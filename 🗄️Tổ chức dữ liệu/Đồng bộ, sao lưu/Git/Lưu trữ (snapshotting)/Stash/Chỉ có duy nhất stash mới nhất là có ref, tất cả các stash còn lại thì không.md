---
share: true
created: 2023-10-30T14:29
updated: 2026-07-07T14:54
---
the commits are created ; the "past stashes" are not referenced by any ref anymore, they are listed in the reflog for the `stash` ref. So: `git reflog stash`, or `cat .git/logs/refs/stash`. The past stashes will eventually be deleted by the gc mechanism -- as for the reflog entries of any other ref.
[[Ref là hệ thống đặt tên các vật thể git]]. [[Cái nào có ref thì `git gc` sẽ không đụng tới]]
[[Có 2 chỗ để lưu ref|Có 2 chỗ để lưu ref: `.git/refs` và `.git/packed-refs`]]
Nguồn:: 
