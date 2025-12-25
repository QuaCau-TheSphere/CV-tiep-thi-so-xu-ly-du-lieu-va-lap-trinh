---
share: true
created: 2023-10-30T14:29
updated: 2025-10-17T12:10
---
Khi dùng `git status` và nó ghi `On branch main`nghĩa là tệp `.git/HEAD` đang ghi `ref: refs/heads/main`. Nếu nội dung `.git/HEAD` chỉ ghi commit chứ không phải ref nhánh thì đó là trạng thái mất đầu.

[[Ref là hệ thống đặt tên các object]]
[[Có 2 chỗ để lưu ref|Có 2 chỗ để lưu ref: `.git/refs` và `.git/packed-refs`]]