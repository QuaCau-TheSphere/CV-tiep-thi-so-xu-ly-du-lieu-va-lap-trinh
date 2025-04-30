---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
title: "Có 2 chỗ để lưu ref: `.git/refs` và `.git/packed-refs`"
---
[[Ref là hệ thống đặt tên các object]]. Mỗi file trong `.git/refs` là một ref. Nội dung mỗi file chỉ là commit hash. Nó dùng cho những ref thay đổi thường xuyên như branch. Còn `.git/packed-refs` là một file. Mỗi dòng trong đó là một commit hash và một ref. Nó dùng cho những ref ít thay đổi như tag. Việc này sẽ giúp làm git chạy nhanh hơn, vì đọc nhiều dòng một file sẽ nhanh hơn là đọc nhiều file một dòng.

Nguồn:: [Git - git-pack-refs Documentation](https://git-scm.com/docs/git-pack-refs)

[[Cái nào có ref thì `git gc` sẽ không đụng tới]]